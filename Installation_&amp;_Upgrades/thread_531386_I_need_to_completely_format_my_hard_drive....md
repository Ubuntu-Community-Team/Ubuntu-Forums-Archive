---
title: "I need to completely format my hard drive..."
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by donteatsoap7 on 2007-08-21
I want everything [including Windows] gone from my hard drive but the live cd never loads the installation is also takes a while for it to boot up.
So how can I remove everything and install ubuntu?

---

### Post by trak87 on 2007-08-21
If you are doing a complete overwrite of Windows with Ubuntu, you don't need to format the drive. During Ubuntu installation, you can choose to use the entire drive and the installer will wipe out the old and create the new partitions (in ext3 and swap file formats) for you.

If you are having trouble with the installer disk (many have, including me) download the "Alternate" Ubuntu install disk. This disk will use a completely text-based installer. It worked for me.

---

### Post by donteatsoap7 on 2007-08-21
Where can I find the text based install disk?

Oh, nevermind. I found it.



Thanks for helping!

---

### Post by trak87 on 2007-08-25
I see you found the link. For others, the starting point is [http://www.ubuntu.com/](http://www.ubuntu.com/) and then follow the "download" or "Get Ubuntu" links. Bittorrent is the best way to download IMO because that protocol features strict error checking. But to be sure one should always run the 'md5sum' program to see that the file you got is exactly -- bit for bit -- the correct file. Once you get it (an .iso file), burn it to disk using the iso (or image) mode of your burner program. Then just boot it up and install Ubuntu.

---

