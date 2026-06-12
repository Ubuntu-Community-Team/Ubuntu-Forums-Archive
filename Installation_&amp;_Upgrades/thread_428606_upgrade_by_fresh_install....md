---
title: "upgrade by fresh install..."
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by chamstar on 2007-04-30
Hi Ive been running Ubuntu for about 4 months dual boot with Windows and I'm almost ready to make the full switch. I recently upgraded to Fiesty by following the guidelines on a blog (rename dist.sources method). 
However since Ive been playing with Ubuntu Ive install loads of packages, messed with settings etc. and the install is a bit bloated, what I really want to do now I get know Ubuntu is to install Fiesty from fresh, at the moment I have the following partitions:

windows NTFS
ubuntu 
share FAT32
swap

All my files are on the share, symlinked from my home folder.

Are there any things to watch out for if download the fiesty install cd and just write over/format the linux partition, leaving the others in place?

Many thanks to all involved in Ubuntu, this is the first time Ive really been able to switch from Windows.

Kris.

---

### Post by ola on 2007-04-30
Hi!

Make sure that you backup your files on the Linux partition (I recommend you to backup the other partitions as well if you can) and you should be good to go!

Just be careful when selecting partitions in the installer.

Good luck!

---

### Post by chamstar on 2007-04-30
Yeah that could be the big mistake, formatting my share! Backup is in hand. Shall report back how it goes!
Kind of debaiting if to wipe the Windows partition and just have Ubuntu, the only application I use on Windows is Fireworks and Dreamweaver - might have a go at getting them working in WINE...

Cheers Kris.

---

### Post by chamstar on 2007-05-03
All was well... 
I backuped up Evolution by copying the .evolution folder in home - this contains your emails etc. but not your login details so I had to restore those, luckily I only have one POP account. I also backed up my RSS feeds and bookmarks.

So now I just have to reinstall Ruby and Rails again... can't quite remember how to do it. I have tried using Synaptic but for some some reason gem doesn't work when you do that, it only works if you download it and run setup.rb.

---

