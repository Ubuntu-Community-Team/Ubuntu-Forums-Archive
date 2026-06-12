---
title: "Uninstalling Programs"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Village Idiot on 2006-06-20
Hi Folks...I've been using Ubuntu 6.06 for just over a week now and I love it! I would like to do a few things and I need a little help. First, I would like to remove a few programs that I will never use such as, all Email clients and bit torrent. Ive tried to use "add/remove" but it won't let me remove them. I went to Synaptic and I'm not sure if I need to mark them for removal or complete removal? I'm tight on space, 40 GIG hdd, I have internet mail accounts and I don't like using Torrents.
  I have XMMS and Rythmbox and movie player. I would like to get one program that will play everything, DVD, MP3, mpeg, etc... I took a look at MPlayer and it seems to be an all in one player. Any comments as to weather it's worth the download?
                             Thank you!

---

### Post by renzokuken on 2006-06-20
mplayer is the bees knees as far as video playing goes in my opinion, although i wouldnt personally use it for audio files.

my suggestion is, use mplayer for all video media, and use a seperate audio player (my recommendation would be Quod Libet)

---

### Post by gerbman on 2006-06-20
[QUOTE=Village Idiot]I went to Synaptic and I'm not sure if I need to mark them for removal or complete removal?[/QUOTE]If you know you won't be using the program again, mark it for complete removal. Doing so should remove all configuration files and folders (like the one it creates in your home directory).

---

### Post by Village Idiot on 2006-06-21
Thank you for the replies! All help is apreciated. Before I go and remove anything, what is the difference between removal and complete removal? Also, are there settings for audio? When I play a movie or music the volume is almost 100% and it isn't what it used to be.

---

### Post by renzokuken on 2006-06-21
i think removal just removes the program, whereas complete removal also remove any dependencies.........

i would use normal removal

---

### Post by rcarring on 2006-06-21
I might be missing something, but I run Dapper on either an 8GB or 10Gb image and have yet to even hit 6GB used. 

You can save a lot of space by running

```

sudo apt-get clean

```

which will remove debs downloaded locally for installation from the cache. I get at least 100MB difference when purging old debs.

The programs you mention really don't take up that much room.

---

### Post by renzokuken on 2006-06-21
apt-get clean runs automatically every so often anyway

---

