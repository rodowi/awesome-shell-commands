# awesome-shell-commands [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> A curated list of tasks done from the command line


## Contents

- [Hardware specs](#hardware-specs)
- [Media](#media)
- [Misc](#misc)
- [Operating system](#operating-system)
  - [Disk](#disk)


## Hardware specs

Querying the OS to get hardware info.

- Connected usb devices: `lsusb`
- Details on a usb device: `lsusb -d vendorId:productId -v`
- Get graphic controllers: `lspci | grep -i vga`
- Get graphic controllers (detailed): `lshw -C video`

## Media

From GIFs to movie editing.

### File conversion

- GIF to MP4 and viceversa: `ffmpeg -f gif -i infile.gif outfile.mp4`
- OGV to MP4: `ffmpeg -i out.ogv -strict -2 out.mp4`
- PNG to PDF: `convert grid.png -gravity center grid.pdf`
- Make a GIF from a screencast:
```sh
ffmpeg -i mem-01.ogv frames/ffout%03d.png
convert -loop 0 frames/ffout* mem-01.gif
convert mem-01.gif -fuzz 10% -layers Optimize optimized.gif
```

### Image editing

- Resize your 100MB smartphone picture: `convert IMG_2000.jpg -resize 1024x IMG_2000_resized.jpg`

### Video editing

- Clip video (starting from second 3): `ffmpeg -i take-3.mp4 -ss 00:00:03 -t 00:02:04 output.mp4`
- Crop video: `ffmpeg -i in.mp4 -filter:v "crop=out_w:out_h:x:y" out.mp4`
- Speed video up: `ffmpeg -i take-4.mp4 -filter:v "setpts=0.5*PTS" take-4-faster.mp4`
- Remove audio from video: `ffmpeg -i loud.mp4 -c copy -an muted.mp4`
- Resize video: `ffmpeg -i larger.mp4 -filter:v scale=720:-1 -c:a copy smaller.mp4`
- Pull video metadata: `exiftool take.mp4`
- Timelapse a video:
```sh
ffmpeg -i input.mp4 -r 1 -f image2 frames/%05d.png
ffmpeg -i frames/%05d.png timelapse.mp4
```

## Misc

KEWL

- Nyancat: `nc -v nyancat.dakko.us 23`

## Operating system

Querying info about the OS

- Architecture: `uname -m`
- Distro: `cat /etc/*release`
- Distro name: `lsb_release -cs`
- Most recent kernel messages: `dmesg | tail`
- Packages installed (debian|ubuntu): `dpkg -l`
- Specific package installed: `dpkg -l nvidia*`
- Watch memory every 5 seconds: `watch -n 5 free -m`

### Disk

- Mounted partitions (in human-friendly units): `df -h`
- Summary of disk space used by directories: `du -hs *`


## Contribute

Contributions welcome! Read the [contribution guidelines](contributing.md) first.


## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law,  has waived all copyright and
related or neighboring rights to this work.
