---
title: "Compile FFmpeg with libfdk_aac"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by theo2 on 2013-09-11
I been reading on how to convert mp3 to m4a, and found that I must compile FFmpeg if I'll use the AAC encoder, libfdk_aac.

But reading FFmpeg [guide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") on how to compile FFmpeg with libfdk_aac makes no sense for a beginner like me. 

To use libfdk_aac the [encoding guide]("https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide") says:
> [COLOR=#000000][FONT=Verdana]Requires ffmpeg to be configured with [/FONT][/COLOR]--enable-libfdk_aac --enable-nonfree[COLOR=#000000][FONT=Verdana].[/FONT][/COLOR]

Where do I put those flags?

Do I put it here somewhere?:
```
cd ~/ffmpeg_sources
git clone --depth 1 git://github.com/mstorsjo/fdk-aac.git
cd fdk-aac
autoreconf -fiv
./configure --prefix="$HOME/ffmpeg_build" --disable-shared
make
make install
make distclean
```

Or maybe here somewhere?
```
cd ~/ffmpeg_sources
git clone --depth 1 git://source.ffmpeg.org/ffmpeg
cd ffmpeg
PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig"
export PKG_CONFIG_PATH
./configure --prefix="$HOME/ffmpeg_build" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --bindir="$HOME/bin" --extra-libs="-ldl" --enable-gpl --enable-libass --enable-libfdk-aac \
  --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx \
  --enable-libx264 --enable-nonfree --enable-x11grab
make
make install
make distclean
hash -r
```
If I'm reading the compile guide right I guess that these two chunks of code is what I need to compile FFmpeg.

---

