# TusovaPlayer

A simple audio player with a graphical interface built on FLTK and SDL2_mixer. It supports playback of common audio formats, playlist navigation, looping, volume control, and seeks through the track.

## Features

- Playback of audio files via SDL2_mixer
- Supported formats: MP3, WAV, OGG, FLAC, OPUS
- Add single files or scan directories recursively
- Playlist navigation (next / previous track)
- Play / pause / resume / stop
- Loop mode
- Volume control
- Seek bar with playback position
- Track metadata display (title, artist, album, copyright)
- Elapsed and total time display
- Custom FLTK widgets (buttons, sliders, roller, time display)

## Requirements

- C++ compiler (g++ or clang++)
- FLTK (with PNG image support)
- SDL2
- SDL2_mixer

### Debian / Ubuntu

```
sudo apt install build-essential libfltk1.3-dev libsdl2-dev libsdl2-mixer-dev
```

### Arch

```
sudo pacman -S base-devel fltk sdl2 sdl2_mixer
```

## Build

```
make
```

Or compile manually:

```
g++ -o TusovaPlayer src/*.cpp -lfltk -lfltk_images -lSDL2 -lSDL2_mixer
```

## Usage

```
./TusovaPlayer [files or directories...]
```

Examples:

```
./TusovaPlayer song.mp3
./TusovaPlayer ~/Music
./TusovaPlayer track1.flac track2.ogg ~/Albums
```

If a directory is passed, it is scanned recursively for supported audio files.

## Controls

| Button     | Action                                  |
|------------|-----------------------------------------|
| Play/Pause | Toggle playback                         |
| Prev       | Previous track                          |
| Next       | Next track                              |
| Loop       | Enable / disable looping                |
| Volume     | Adjust volume (0–128)                   |
| Seek bar   | Jump to a position in the current track |

## Project Structure

```
TusovaPlayer/
├── include/          header files
│   ├── Audio.h
│   ├── AudioPlayer.h
│   ├── Error.h
│   ├── OOFL*.h       custom FLTK widget wrappers
│   ├── TusovaPlayer.h
│   └── dir_scan.h
├── src/              implementation files
│   ├── Audio.cpp
│   ├── AudioPlayer.cpp
│   ├── OOFLTime.cpp
│   ├── TusovaPlayer.cpp
│   ├── dir_scan.cpp
│   └── main.cpp
└── title.png         window icon
```

## Notes

- `title.png` must be present in the working directory for the window icon to load.
- If the playlist is empty at startup, the program exits with an error.
- Directory scanning uses `scandir` with `alphasort`, so tracks are loaded in alphabetical order.
