# FFmpeg Kit Binaries

This repository hosts FFmpeg Kit binaries for iOS development, providing a reliable download source for the retired `ffmpeg-kit-ios-https` package.

## 📖 Background

[FFmpeg Kit](https://github.com/arthenica/ffmpeg-kit) was officially retired in January 2025, causing download failures for many Flutter projects that depend on `ffmpeg_kit_flutter`. This repository preserves working FFmpeg Kit v6.0 binaries to ensure continued compatibility.

## 🗂️ Available Binaries

### iOS HTTPS Package (v6.0)
- **File**: `ffmpeg-kit-https-6.0-ios-xcframework.zip`
- **Size**: ~150MB
- **Architecture**: Universal (arm64, x86_64)
- **Features**: HTTPS support enabled
- **Deployment Target**: iOS 13.0+

### Included Frameworks
- `ffmpegkit.xcframework`
- `libavcodec.xcframework`
- `libavdevice.xcframework`
- `libavfilter.xcframework`
- `libavformat.xcframework`
- `libavutil.xcframework`
- `libswresample.xcframework`
- `libswscale.xcframework`

## 🚀 Usage

### For Flutter Projects

1. **Use with custom fork of `ffmpeg_kit_flutter`:**
   ```yaml
   dependencies:
     ffmpeg_kit_flutter:
       git:
         url: https://github.com/statecs/ffmpeg_kit_flutter.git
         ref: main
   ```

2. **Direct download URL:**
   ```
   https://github.com/statecs/ffmpeg-kit-binaries/raw/main/ffmpeg-kit-https-6.0-ios-xcframework.zip
   ```

### For Custom Podspec

```ruby
Pod::Spec.new do |s|
  s.name = 'ffmpeg-kit-ios-https'
  s.version = '6.0'
  s.source = { 
    :http => 'https://github.com/statecs/ffmpeg-kit-binaries/raw/main/ffmpeg-kit-https-6.0-ios-xcframework.zip'
  }
  
  s.vendored_frameworks = [
    'ffmpegkit.xcframework',
    'libavcodec.xcframework',
    'libavdevice.xcframework',
    'libavfilter.xcframework',
    'libavformat.xcframework',
    'libavutil.xcframework',
    'libswresample.xcframework',
    'libswscale.xcframework'
  ]
end
```

## ⚙️ Installation

### Prerequisites
- iOS 13.0 or later
- Xcode 12.0 or later
- CocoaPods 1.10.0 or later

### Setup Steps

1. **Update your `pubspec.yaml`:**
   ```yaml
   dependencies:
     ffmpeg_kit_flutter:
       git:
         url: https://github.com/yourusername/ffmpeg_kit_flutter.git
         ref: main
   ```

2. **Update iOS deployment target** in `ios/Podfile`:
   ```ruby
   platform :ios, '14.0'
   ```

3. **Clean and rebuild:**
   ```bash
   flutter clean
   flutter pub get
   cd ios && pod install && cd ..
   flutter build ios
   ```

## 🔧 Build Settings

Add these to your iOS project's build settings:

```ruby
config.build_settings['ENABLE_BITCODE'] = 'NO'
config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '14.0'
```

## 📋 Supported Features

### Audio Codecs
- AAC, MP3, Opus, Vorbis
- FLAC, PCM (various formats)
- AMR-NB, AMR-WB

### Video Codecs
- H.264, H.265/HEVC
- VP8, VP9
- MPEG-4, MPEG-2

### Protocols
- HTTP/HTTPS
- File I/O
- Memory buffers

### External Libraries
- libx264 (H.264 encoder)
- libx265 (HEVC encoder)
- libvpx (VP8/VP9)
- libmp3lame (MP3 encoder)
- libopus (Opus codec)

## ⚠️ Important Notes

1. **License**: These binaries are built with GPL license. Ensure compliance with GPL requirements in your project.

2. **App Store**: GPL-licensed binaries may not be suitable for App Store distribution. Consider LGPL alternatives for commercial apps.

3. **Architecture**: Binaries include both arm64 (device) and x86_64 (simulator) architectures.

4. **Size**: FFmpeg frameworks are large (~150MB). Consider app size impact.

## 🆘 Troubleshooting

### Common Issues

**Build Error: "Framework not found"**
```bash
# Clean and rebuild
cd ios && rm -rf Pods Podfile.lock && pod install && cd ..
flutter clean && flutter build ios
```

**CocoaPods Download Error**
- Verify the download URL is accessible
- Check internet connection
- Try clearing CocoaPods cache: `pod cache clean --all`

**Linker Errors**
- Ensure `ENABLE_BITCODE = 'NO'` in build settings
- Check iOS deployment target is 14.0+

**Header Not Found**
- Verify framework paths in build settings
- Check header search paths include framework directories

## 📚 Documentation

- [Original FFmpeg Kit Documentation](https://github.com/arthenica/ffmpeg-kit/wiki)
- [Flutter FFmpeg Plugin](https://pub.dev/packages/ffmpeg_kit_flutter)
- [FFmpeg Official Documentation](https://ffmpeg.org/documentation.html)

## 📄 License

These FFmpeg binaries are distributed under the **GPL v3.0** license, as per the original FFmpeg Kit project.

- **GPL Compliance Required**: If you distribute apps using these binaries, you must comply with GPL requirements
- **Source Code**: You may need to provide source code for your application
- **Alternative**: Consider LGPL variants for commercial distribution

## 🔗 Related Links

- [FFmpeg Kit Original Repository](https://github.com/arthenica/ffmpeg-kit)
- [Flutter FFmpeg Plugin](https://pub.dev/packages/ffmpeg_kit_flutter)
- [FFmpeg Official Site](https://ffmpeg.org/)

---
