---
title: "Operating System blow up updating from Ubuntu 12 to 14"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by blomkvist on 2015-07-10
Short description of my problem:
- my mom had a laptop with W Vista; I made a dual boot installation of Ubuntu 12 using a disk partition, so I kept all the old data of windows in a big partition and created a new small partition to use Ubuntu
- that has been working for a long time; recently I visited my mom and there was a suggested update from Ubuntu 12 to 14. I accepted it and as update took a looooong time, I went to my home
- around 12h after starting the update my mom turned off the computer (pressing the on/off button for a while)
- now I can boot neither from Ubuntu nor Windows

The text shown in Ubuntu is:
[I]mount: mounting /dev/loop0 on /root failed: invalid argument
...some mount error lines...
Target fulesysten doesn't have requested /sbin/init
No init found. Try passing init=bootarg.

Busybox v1.21.1 .........some stuff

(initframs)_[/I]

What I've tried:
- I guess it was screewd something on the Grub thing, I booted from a Grub Live USB, but it couldn't find the Ubuntu OS installed, just the Windows
- I boot from a Ubuntu Live CD, go to the  and I tried to find the old Ubuntu installation files and folders, but....I couldn't find them in any partition!!! F*** me! Where did they go??
- The old Ubuntu partition has 24 from 33GB used, as I can see in the Live USB disk utility, but I cant see any content....so there must be something there I cant see

any suggestion?

---

### Post by dino99 on 2015-07-10
you now need to do a fresh install over the borked installation.

---

### Post by blomkvist on 2015-07-10
Yeah, I think so, but I would like to recover the pictures and documents before re-install and I can't find them. Any suggestion to find them?

---

### Post by kansasnoob on 2015-07-10
Was that an encrypted install? Maybe only /home was encrypted?

Could you please post a screenshot of Gparted using a live DVD/USB? That would be helpful as well as a link to the boot info summary created by Boot Repair which can also be run from the live session:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by howefield on 2015-07-10
To recap, you have a Windows partition and an Ubuntu partition, the files you are looking for are in the Windows partition, yes ?

Can you post a screenshot of the file manager and a shot of gparted from the Live CD.

---

### Post by blomkvist on 2015-07-10
It wasn't an encrypted install, it's my moms computer so I did it easy.
Kansasnoob I will try to use Boot Repair, but at this moment I will be happy if I just could rescue user data (pics and music) which I can't find now.

Howefield, yes I have 2 partitions; I can see all data contained on Windows partition but not the data on the Ubuntu part.
I will try to capture screen next time
Thks!

---

