---
title: "ffmpeg installation: opus not found"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by prkhr4u on 2013-11-13
I am trying to install ffmpeg via:
```
./configure --prefix="$HOME/ffmpeg_build" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --bindir="$HOME/bin" --extra-libs="-ldl" --enable-gpl --enable-libass --enable-libfdk-aac \
  --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx \
  --enable-libx264 --enable-nonfree --enable-x11grab
```

I am getting error:
```
ERROR: opus not found
```

I have aslo installed libopus using [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
and successfully installed it using :
```
cd ~/ffmpeg_sources
wget http://downloads.xiph.org/releases/opus/opus-1.0.3.tar.gz
tar xzvf opus-1.0.3.tar.gz
cd opus-1.0.3
./configure --prefix="$HOME/ffmpeg_build" --disable-shared
make
make install
make distclean
```

all the files of opus are successfully installed such as
libopus.a
libopus.la
opus.pc
and other header files

pl tell how to resolve this??
I am using ubuntu 12.04 desktop

---

### Post by prkhr4u on 2013-11-13
the problem has been solved. I contacted the IRC channel #ffmpeg.
had to reset the PKG_CONFIG_PATH environment variable to opus.pc directory

---

### Post by FakeOutdoorsman on 2013-11-13
I went through the guide on 12.04 and did not experience the same issue and the following command from the guide should have done what you needed:

```
PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig"
```

---

### Post by prkhr4u on 2013-11-13
the command needed to be modified a bit to work.
Earlier i used it,but couldn't work(error: opus not found) but the i used:
```
PKG_CONFIG_PATH="/home/ffmpeg_build/lib/pkgconfig"
```
and everything worked.
I don't know,both are same although

---

### Post by FakeOutdoorsman on 2013-11-14
"$HOME" and "/home" are different:

```
$ echo $HOME
/home/prkhr4u
```

$HOME is an environment variable and refers to the home directory of the user, while /home is just the /home directory.

---

### Post by prkhr4u on 2013-11-14
Thanks for the clarification

---

### Post by shatrughna-win on 2014-08-07
i am also getting the same error ."opus not found". i have installed upto libvpx. should i have to reinstall  libopus and libvpx again by defining path as"
PKG_CONFIG_PATH="/home/ffmpeg_build/lib/pkgconfig" or can i directly resume with this command.
pls rply soon ....@[**[COLOR=#000000]prkhr4u[/COLOR]**]("http://ubuntuforums.org/member.php?u=904072")

---

