---
title: "Xubuntu error on LiveCD"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Lean 946 on 2007-08-17
Hi!
I have a promem with LiveCD: the mouse if freeze and it's bottons doesn't work, the up/down bars are gone, and it runs very slow. The cd check tool says the cd has not faliures.

This is my PC Configuration:

Intel Pentium III Processor 1Ghz
192MB of RAM DIMM
20GB of Disk, formatted in NTFS with Windows XP (wanted to test if cd worked and if I can partition the HDD)
32MB of VRAM
1 CD-RW, 1 DVD-ROM and 1 DVD-RW.

Can you please Help Me??!?!?!
Thank You.

PD: Windows sux, I was Using a Xubuntu 7.04 Feisty Fawn Live CD downloaded with BitTorrent, the original copy finded in Ubuntu Home Page, downloaded with a 64kbps Connection.

---

### Post by Pumalite on 2007-08-17
With 256 MB RAM or less you are better off with Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
If you want a system that installs easier and run faster in your computer.

---

### Post by Lean 946 on 2007-08-20
Thanks Pumalite, but, I'm on 64k, and download (with uTorrent) the Xubuntu LiveCD took me 4 weeks!! So, people on IRC have recomended me the Alternate Install CD, but it's 550MB more (again, I mean) to download.
I appreaciate your help, but I was expecting another solution. Now i'm testing Dream Linux LiveCD and it works fine (a friend copied to me).
Thanks.

---

### Post by Lean 946 on 2007-09-04
I'm testing another distros like Puppy Linux or Dream Linux, but if anyone can help, i'll appreacciate that.:popcorn:

---

### Post by santiagoward2000 on 2007-09-04
Hi everyone,
I was having similar problems using Xubuntu Feisty's LiveCD. I had to use Edgy to install it, and the upgrade to Feisty using the Update Manager. I think Feisty is a little too heavy. My computer also has 192mb RAM.

---

### Post by Lean 946 on 2007-10-14
The worst: I Tried with other distros: Linux Mint has the same problem. :x
Anyway, DreamLinux just works fine, but has a little problems with graphics (wrong resolution on screen, in my case, i suppose is the video card). I'll try Tuqito or kubuntu.

Thanks for your help. ;-)

---

### Post by Pumalite on 2007-10-14
Try: Zenwalk, DSL, Puppy.

---

### Post by Lean 946 on 2007-10-14
> **Pumalite said:**
> Try: Zenwalk, DSL, Puppy.

Puppy: unbottable (I don't know why)
Damn Small Linux: Frezzes on start up (1 millon hours to make the ramdisk folder :-D )
Zenwalk: I'll Try it.

Thanks.

---

### Post by Lean 946 on 2007-10-15
Fixed the Mouse issue:
Xubuntu appears to only search for mouse on PS/2 and USB ports. I bought another mouse and presto!!! Prblem fixed!!!
But........
The installer freezen when it's installing Xubuntu:
It says (in spanish):
Installing the System: 15 %.
And below:
Detecting file systems. :x
I don't know why. Can you please help me!?!?!?!

---

### Post by Pumalite on 2007-10-15
You might need a smaller distro. Or:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(burn at 4x)

---

### Post by gophert on 2007-10-15
> **Lean 946 said:**
> Fixed the Mouse issue:
Xubuntu appears to only search for mouse on PS/2 and USB ports. I bought another mouse and presto!!! Prblem fixed!!!
But........
The installer freezen when it's installing Xubuntu:
It says (in spanish):
Installing the System: 15 %.
And below:
Detecting file systems. :x
I don't know why. Can you please help me!?!?!?!

There is a small configuration error in Xubuntu 7.04.  It attempts to mount stuff while running the partitioner.  What you need to do boot up the cd, and before the install, go into the File System, and turn off the auto-mount. Open a File Manager, then go to Edit, Preferences, Advanced Tab, click on the Configure link and uncheck the top two,  **Mount removable drives when hot-plugged** and **Mount removable media when inserted**.  Close out all, then start your install.

---

### Post by Lean 946 on 2007-10-21
I tried with the alternate install as you said, but i have the following error:
(its in spanish, install in tex mode, but i traducte it):
Xubuntu-desktop installed
85%
and freezes there.
Then, i reboot the computer mannually and it says:
Booting from first Hadr disk


GRUB loading...
error 15.

and the freeze again.

What's my problem? Does anyone can help me???

Thanks, Lean

---

### Post by Lean 946 on 2007-10-21
Thank's gophert, but i'm great with my new mouse.
I think its a great idea to publish my bug with the mouse in the Ubuntu bugs.

Thanks,
Lean :)

---

### Post by Lean 946 on 2007-10-21
Now i'm installing Kubuntu and appears to don't have any issue with nothing, now is coping files and installing. I'll inform you later.

Lean.

[Ubuntu user Nro. 18238: Kubuntu Flavor.]("http://http://ubuntucounter.geekosophical.net/img/kubuntu-user2.php?user=18238")

---

### Post by Lean 946 on 2007-10-21
Kubuntu is installed and fully fuctional!!!!!!
it is the coolest thing ever!!!!!!!!!

---

### Post by Lean 946 on 2007-10-26
Ihave installed Xubuntu thru Kubuntu:
```
sudo apt-get update
sudo apt-get instal xubuntu-desktop
```
And wait for XFCE to download :)

---

