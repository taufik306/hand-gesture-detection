# Gesture Filters Webcam App

A single-page browser app that opens the webcam, detects hand gestures with MediaPipe Hands, and maps each gesture to a live visual effect on the camera feed.

## Features

- Fullscreen webcam view
- Hand tracking from MediaPipe's 21 landmarks
- Gesture recognition for:
  - fist
  - thumbs up
  - peace sign
  - pointing finger
  - open hand
- Gesture-to-effect mapping:
  - fist → dither
  - thumbs up → volumetric lighting
  - peace sign → VHS with chromatic aberration
  - pointing finger → spotlight
  - open hand → water ripple
- Start and Stop controls for the webcam session

## Files Generated

- `index.html` — the full application, including HTML, CSS, webcam logic, gesture classification, and canvas-based visual effects
- `README.md` — project summary and run instructions

## Dependencies Required

This project does not require a package install or build step.

Runtime requirements:

- A modern browser with:
  - webcam support via `navigator.mediaDevices.getUserMedia`
  - ES module support
  - Canvas 2D support
- Internet access at runtime to load external MediaPipe assets from CDNs:
  - `@mediapipe/tasks-vision@0.10.35`
  - MediaPipe hand landmarker model file
- A local web server to serve the page over `http://localhost` or `http://127.0.0.1`

## How to Run

From the project directory:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://127.0.0.1:8000
```

Click **Start camera**, allow webcam permission, and try the supported gestures.

## Notes

- Camera access usually will not work correctly if you open `index.html` directly from the filesystem; use a local web server.
- The gesture classifier is rule-based and derived from the 21 hand landmarks, so recognition quality can vary with lighting, pose angle, and occlusion.
