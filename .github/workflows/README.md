# GitHub Actions Workflows

This directory contains automated build workflows for Waifu2x-Extension-GUI.

## Workflows

### 1. 🔨 CI - Quick Build Test (`ci.yml`)
**Trigger:** Push/PR to source code
- Quick compilation test
- Runs on every code change
- Fast feedback for developers

### 2. 🏗️ Build (`build.yml`)
**Trigger:** Push to main/master branches
- Full build with Qt dependencies
- Creates deployable artifacts
- Uploads build results

### 3. 🚀 Release Build (`release.yml`)
**Trigger:** 
- Git tags (v*)
- Manual workflow dispatch

**Features:**
- Optimized release build
- Bundles Qt dependencies with windeployqt
- Creates ZIP package
- Automatically creates GitHub Release for tags

## Usage

### Automatic Builds
Push code to trigger builds automatically:
```bash
git add .
git commit -m "Your changes"
git push
```

### Manual Release Build
1. Go to **Actions** tab on GitHub
2. Select **Release Build** workflow
3. Click **Run workflow**
4. Enter version number (optional)
5. Click **Run workflow** button

### Create Release with Tag
```bash
git tag v3.41.02
git push origin v3.41.02
```

This will:
- Build the release version
- Create a GitHub Release
- Upload the build package automatically

## Build Requirements

- **Qt Version:** 5.15.2
- **Compiler:** MinGW 8.1.0 (64-bit)
- **Modules:** qtmultimedia
- **OS:** Windows

## Artifacts

Build artifacts are available in the **Actions** tab after successful builds:
- Download from workflow run summary
- Available for 90 days (GitHub default)

## Troubleshooting

**Build fails:**
- Check Qt installation logs
- Verify .pro file syntax
- Check compiler errors in build log

**Executable not found:**
- Check build output directory
- Verify qmake configuration
- Check for compilation errors

**Qt dependencies missing:**
- Ensure windeployqt runs successfully
- Check Qt modules are installed
- Verify Qt bin directory in PATH
