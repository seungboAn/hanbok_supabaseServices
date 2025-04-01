# Supabase Services Package

A Flutter package containing extracted Supabase logic from the Hanbok Virtual Fitting application for reuse in other projects.

## Getting Started

This package provides services to interact with Supabase, including authentication, storage, and edge functions for image processing.

### Installation

Add this package to your `pubspec.yaml`:

```yaml
dependencies:
  supabase_services:
    path: ../supabase_services  # Adjust path as needed
```

Or if using git:

```yaml
dependencies:
  supabase_services:
    git:
      url: https://your-repo-url.git
      path: supabase_services
```

### Configuration

1. Create a `.env` file in your app root with your Supabase credentials:

```
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
```

2. Initialize the package in your app's `main.dart`:

```dart
import 'package:supabase_services/supabase_services.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  
  // Initialize Supabase services
  await SupabaseServices.initialize();
  
  runApp(MyApp());
}
```

## Features

- Authentication (anonymous and email)
- File upload to Supabase storage
- Edge function integration
- Image processing with Supabase edge functions

## Services

- `SupabaseService`: Core service for interacting with Supabase
- `EnvService`: Service for loading environment variables
- `InferenceService`: Service for image processing with edge functions

## Usage Example

```dart
// Get the Supabase service instance
final supabaseService = SupabaseServices.supabaseService;

// Upload an image
final result = await supabaseService.uploadUserImage(
  imageBytes,
  'image/jpeg',
  authToken
);

// Get presets from Supabase
final presets = await supabaseService.getPresetImages();

// Sign in anonymously
final token = await supabaseService.signInAnonymously();
``` 