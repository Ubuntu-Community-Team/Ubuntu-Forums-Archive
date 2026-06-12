---
title: "help with modest specs"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by thenok on 2009-12-03
Hi I have a computer with a 4gb hdd and read a previous post about barebone specs [http://ubuntuforums.org/showthread.php?t=710667](http://ubuntuforums.org/showthread.php?t=710667)

I downloaded the iso and installed it
I now find myself not knowing what to install (using the package manager) for my basic needs.
Can anyone tell me exactly what packages I need to install to be able to:
play music
play movies (wmv avi flv mkv files at least)
open pdfs
and open microsoft office files

I tried several times to do this but always managed to occupy lots of space with files that dont do anything of cant even manage to open a damm wmv file
(I used the first iso from the site with the modest specs just in case)

Any help is appreciated, even if just for the packages that enable one of the items in the upper list.
Thanks in anticipation.

---

### Post by raymondh on 2009-12-03
Let's see ....

- browser (Firefox ? )
- email (thunderbird ?)
- media player (banshee ?)
- openoffice
- and a terminal

Yes, there are dependencies that will be installed.  As a reference, a fresh install of regular, 9.04 along with updates and installing some applications has already taken 3.6gb.  With a minimal install, I don't think you should come close to that.

To play various media formats/codecs ... [you need to install ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats")

Regards,

---

### Post by dstew on 2009-12-03
I can help you with some of this. I assume you have the minimal system installed as described [here]("http://www.psychocats.net/ubuntu/minimal"), and want to install packages using Synaptic. Did you use the whole disk to install, or do you have smaller partitions?

For a pdf viewer, the standard package is [evince]("http://packages.ubuntu.com/karmic/evince"). But, with any pdf viewer, there are lots of graphical things that it will need to do, so the package depends on a lot of graphical software libraries. Before you install it, Synaptic checks for these dependencies, and will install them with the package. So the total size of installed software is much larger than the package itself.
There are other pdf viewer you can check out. Epdfview is one. It might have a smaller footprint than evince, since it depends on different libraries. You need to activate the Universe repository to see the epdfview package. Usually, one would activate a repository using the System --> Preferences --> Software Sources menu item, but in your minimal system you may not have this. To activate a repository using the command line, see [this how-to]("https://help.ubuntu.com/community/Repositories/CommandLine").

You can look at packages that will show you Word documents, and play music by searching Synpatic using various search terms. My guess is that 4 Gb will be tight to do all the things you want to do, but you can try.

Another option is to do a [persistent install of an Ubuntu Live CD]("https://help.ubuntu.com/community/LiveCD/Persistence"). The Ubuntu live CD has software on it to view pdfs, and I think play music. A persistent install of a Live CD can be done on a 2 Gb flash drive, or on a hard-disk partition of similar size.

---

### Post by JBAlaska on 2009-12-03
Try [LXDE](http://lxde.org/), it's light fast and sexy, and has most of the apps you'll need built in. (It's in synaptic)

Then add the stuff you need to play avi's, mp3's, dvd's, flash and stuff:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by thenok on 2009-12-03
yes i am using Synaptic package manager, very dificult for a first-timer...
Although there are dependencies, I find that some arent all that dependent
For example I installed a player and it couldnt play any files cuz I wasnt dependent on the codecs (at least not when i was installing it)

---

