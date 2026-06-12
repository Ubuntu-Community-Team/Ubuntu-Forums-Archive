---
title: "Realtek HD Audio on FUjitsu Amilo"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by rabidmachine9 on 2007-12-31
hi everybody,
I just installed kubuntu and I'm having some problems on my soundcard insallation 
I'm using a fujitsu amilo M-p 1451G and my soundcard is a Realtek HD Audio
this is what I'm doing:
1.I'm downloading the linux drivers from this site [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)  
2.I unzip the folder
3.I run ./install
I'm geting back a very big output like that is ending whith that:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied
Remove Folder.....
./install: 100: alsaconf: not found

---

