---
title: "Locating and fixing a corrupted file"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by Doom972 on 2015-01-26
Since this is my first thread, I'll give a small introduction: I have an old laptop which until recently ran WinXP. Since this laptop could barely keep up with the latest versions of the programs I ran on it, I decided to try a more lightweight OS. I first tried Ubuntu 14.04 LTS, which worked, but slowly (I didn't realize that the Unity interface requires that many resources). After reading about the different variants of Ubuntu I decided to try Xubuntu.

After I installed Xubuntu, I noticed several different errors on boot-up (The only one I remember was "Malformed File"). I booted up the USB I used to install Xubuntu and picked the "Check disc for defects" option. At the end of the test it said that there was an error in one file. I ran an MD5 test on the image I used (xubuntu-14.04.1-desktop-i386.iso) and it was the same one I found on [this page]("https://help.ubuntu.com/community/UbuntuHashes"). I used Universal USB Installer 1.9.5.9 to make the bootable USB three times and I still get the same result when I pick "Check disc for defects".

Is there a way to figure out which file it is and fix it? Is there something else I should do?

My laptop's specs:

CPU: Intel Atom 1.66 GHz
RAM: 896 MB (+128 reserved for VRAM)
GPU: Nvidia ION-Lite

HDD Partitions:
16 GB root partition
2 GB swap space
142 GB home partition.

---

### Post by Bucky Ball on 2015-01-26
*Thread moved to **Installation & Upgrades**.*

Welcome. Did you totally wipe the USB prior to making it a USB installer? Best to completely format the USB first. I've only used UNetbootin and you need to format the USB to FAT32 first. The process of creating the USB installer does not format the USB during the process so if you have any files on the USB already, the end result will be a Ubuntu install USB with whatever files you had on there in the first place still there and intact. This can cause problems. 

If you had, for instance, a pic file on there, then created the USB installer, that pic file will still be there and can cause headaches. Try completely reformatting the USB if you haven't done that aleady, then run your USB creator. 

Just a thought. Good luck. ;)

---

### Post by Doom972 on 2015-01-26
Thanks for the assitance, but I did format it twice on each time I (re)created it. In each of the three attempts I first formatted it (using FAT32 of course) in Windows 7 (On my desktop computer - not the one I want Xubuntu on) and then again on Universal USB Installer (There is a small checkbox you can mark that causes it to format the USB drive) just to be sure.

---

### Post by kerry_s on 2015-01-26
have you tried using unetbootin to make the installer ?

does it even effect anything running ?

general tips from a fellow atom user:
install "intel-microcode" it will fix any firmware issues, just install & forget, it's automatic at boot.

in bios change your video setting to "dvmt" & "dvmt maximum" that will give you 256mb for video on the fly, if you watch movies, youtube, etc... it'll play smoother. i lived on 1gb max for a long time before i upgraded to 2gb which is the max. a very good upgrade to make, plus ssd are cheap now, i grabbed a 50gb from amazon for $40.

those are the important things, can't think of anything else just now.

---

### Post by Doom972 on 2015-01-26
> **kerry_s said:**
> have you tried using unetbootin to make the installer ?

No, I used Universal USB Installer, which is recommended on the official Ubuntu site, but I'll try unetbootin if you think it might help. I'll report later if it made any difference.

> does it even effect anything running ?

I got some errors on boot and the only consistent one is "Malformed file". I want to make sure that I have a proper installer to either fix the problem or at least rule out a corrupted installation file as the cause of it.

> general tips from a fellow atom user:
install "intel-microcode" it will fix any firmware issues, just install & forget, it's automatic at boot.

How do I do that? Should I use the apt-get command?

> in bios change your video setting to "dvmt" & "dvmt maximum" that will give you 256mb for video on the fly, if you watch movies, youtube, etc... it'll play smoother. i lived on 1gb max for a long time before i upgraded to 2gb which is the max. a very good upgrade to make, plus ssd are cheap now, i grabbed a 50gb from amazon for $40.

Will it take that additional memory from my RAM? Because I'm low on that as it is. I don't want to invest money into my laptop. I'll eventually get a new one, but not soon.

> those are the important things, can't think of anything else just now.

Thanks for the assistance.

---

### Post by kerry_s on 2015-01-26
yes you can use apt-get or synaptic if installed.
sudo apt-get install intel-microcode

no, you currently have it set on fixed so it's always taking 128, which is max for fixed. dvmt is like hyper threading for the cpu, except for gpu, given when needed.

---

### Post by Doom972 on 2015-01-26
Just used unetbootin to create a new bootable USB drive and checked for defects - no errors this time. Thanks :)

---

### Post by sammiev on 2015-01-26
[MKUSB]("https://help.ubuntu.com/community/mkusb") is what i prefer for burning ISO to a USB.

---

### Post by ajgreeny on 2015-01-26
That error is an old bug that still, to the best of my knowledge, has not been properly solved.
[https://bugs.launchpad.net/bugs/1311247](https://bugs.launchpad.net/bugs/1311247)

Note that there is a workaround that seems to stop it happening by changing the line
**GRUB_DEFAULT=0**
to 
**GRUB_DEFAULT=1**
in /etc/default/grub.
It seems to be only some users who see this bug, not all.

---

