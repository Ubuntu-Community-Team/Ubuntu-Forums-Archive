---
title: "Installing Studio Ubuntu from HDD"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by SPr on 2007-05-26
Hi,

I have the alternative (non-live) DVD iso for Studio Ubuntu but no DVD burner. I was wondering if it is possible to install Studio from my hard drive rather than DVD.

I have a spare partition (/dev/hda2) on which I extracted the .iso file. I then extracted initrd from initrd.gz. I added an entry to /boot/grub/menu.lst pointing to vmlinuz and initrd (I've deleted this entry now so I can't post it here).

The installer booted and ran but failed when it tried to detect the CD as the CD doesn't exist.

I used AptonCD and IsoMaster to create a repository on a couple of CDs containing the packages from the Studio Ubuntu .iso file. The installer didn't detect these CDs as being the correct discs either.

Is it possible to use this method to install Ubuntu Studio?

Which files are essential on the CDs for the installer to recognize the CDs? There is example-preseed.txt included in the iso to automate the installation; could this be used to point the installer to my repo CDs?

Sorry for all the questions but I have reached the end of my limited Linux know-how.

---

### Post by sean1979one on 2007-05-26
From a terminal run these 2 commands:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update 

then you can install you want with Synaptic: Open Synaptic, search the keyword "ubuntustudio", mark you want to install, enjoy!
Good luck!

---

### Post by SPr on 2007-05-28
Hi,

thanks for your reply.

I actually want to keep my Ubuntu Installation on /dev/had3 intact. I have it set up exactly as I need it. OK, I do have images of all my partitions so if anything goes wrong I can run repairs but I would like to run both OSs.

I have the dvd image on my HDD and I was wondering if this can be used to install Studio Ubuntu on /dev/hda2 without burning the image to dvd.

I think I may have worded my question rather better this time :)

I tried writing the image of /dev/hda3 to /dev/hda2 so I could upgrade it to Studio but something went seriously wrong :lol: It booted to the desktop without asking to login and was running as root!

---

### Post by blacksadness on 2007-05-28
i've heard about net install disks, don't know where to find them though, i guess using some sort of net install or maybe ubuntu server if you have it, you could install ubuntu then do an upgrade to ubuntustudio..

---

### Post by SPr on 2007-05-28
Thanks.

That may be a possibility if I can't figure out anything else.

---

### Post by shen-an-doah on 2007-05-28
I don't know about installing from the hard drive, but full instructions on how to "upgrade" a feisty install to studio can be found on my blog, [here](http://ubuntumusic.blogspot.com/2007/05/upgrade-to-ubuntu-studio.html). It's probably simpler than trying to do it from your hard drive and could save you burning a load of CDs.

---

### Post by SPr on 2007-05-28
Hi,

I have managed to install Studio Ubuntu from my HDD.

1. Extracted the files from the Studio Ubuntu Alternative (not live) DVD .iso (In Feisty right click>extract here).

2. Copied them to an empty partition on my external HDD.
Feisty places the files in folder named with a _FILES suffix. Just copy the files and folders         
from the iso.

3. Used IsoMaster to make two new .isos.
I removed packages from /pool/main until it was < 700MB and saved it to my HDD
I did the same thing again but removed different packages so each file on the original .iso was in at least one new .iso
I don't know how necessary it is to make 2 CDs but this was part of my experiments into installing Studio without a DVD and I used only one of the CDs in the end.

4. Burn them to CDs.

5. Booted from one of the CDs.

6. From the menu chose "Install Studio Ubuntu".

7. Let the install continue until the installer fails to read a missing file.

8. Hit Alt+F2.

9. Hit Enter.

10. Typed:
```
umount /cdrom
```

11. Removed the CD; the installer seems to insist on using it.
12. ```
mount -t ext3 /dev/sda1 /cdrom
```
13. Hit Alt+F1
14. Hit "Retry" in the error box.
15. The installation should continue from the external HDD.

This is where I met my first problem.

The installer couldn't find the kernel to install it. I was sent back to the menu to choose the next step. I repeated the "Install base system" step again and this time I was presented with a list of kernels; I chose the one with the 2.6.20-15-generic suffix.

The next problem was in choosing which software to install. The "Audio" programs (the ones I wanted most) wouldn't install at all :( The other three options worked a treat.

Grub was installed with no problems and I was able to boot into Studio Ubuntu :D

It's all a bit of a hack but it has worked for me :) I have no idea if anyone else can make this work though.

And now my headaches.

---

### Post by shen-an-doah on 2007-05-28
> **SPr said:**
> The installer couldn't find the kernel to install it. I was sent back to the menu to choose the next step. I repeated the "Install base system" step again and this time I was presented with a list of kernels; I chose the one with the 2.6.20-15-generic suffix.

The next problem was in choosing which software to install. The "Audio" programs (the ones I wanted most) wouldn't install at all :( The other three options worked a treat.

I'm not sure how studio is set up, but it could be because you didn't install the low-latency kernel, which is intended for audio work...

---

### Post by SPr on 2007-05-28
:lol: That will most likely be the trouble then. Thanks for the tip :)

---

