---
title: "Installing Ubuntu Fiesty on Gateway T-8615"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by jallen0514 on 2007-09-23
Okay I recently got a Gateway T-8615 laptop with the following specs:

OS: Vista Home Premium
HDD: 160 GB Sata
CPU: Intel Core 2 Duo 1.5 GHz
Video Chipset: Intel GM965 Express Chipset
Ram: Generic 1GB
DVD: DVD-RW 8x

Okay well I originally tried to use a Ubuntu Edgy LiveCD and it wouldn't even get into the install without showing the X org screen. I tried doing it manually with sudo dpkg-reconfigure xserver-xorg at the command prompt and using the versa as the driver and set it all as it's spposed to be but I still reboot and get the same error over and over again. I tried the same steps with a Ubunut Fiesty alternate edition I burned myself and installed in text mode and finished the installation and I still get the same error even after tying to configure it on my own. The fiesty disc is fine, I also used it to install Ubuntu on my desktop.

I've been reading forum threads all weekend and trying to get this installed, after reading several webpages and what has worked for others doesn't seem to work for me. I can get into the command prompt and log in, and I can boot into Vista from Grub just fine. I even edited the kernal's boot config by added that noapic to the kernal and rebooting. Still no dice. Pumalite seems to be the man to ask for help around here, I'm hoping I've given you enough info to help get me started on a solution, I'm going out, but I'll check my email and reply as soon as I can.

---

### Post by Pumalite on 2007-09-23
Have you done your partitioning with Vista's partitioner?

---

### Post by jallen0514 on 2007-09-23
Yeah I partitioned it with disk management and set aside 10 GB as just unallocated space.

---

### Post by Pumalite on 2007-09-23
Can't install in 'unallocated' space. 10 GB is the bare minimum.

---

### Post by jallen0514 on 2007-09-23
Ahh, well that makes me feel like a complete idiot. So is the lack of space the possible reason that the X org isn't working with my display? It seemed to install fine as far as I could tell, it showed as a 4GB minimum HDD space to install. And I can't remember but I thought I created a simple volume, I know it was 10 GB, now it shows an available 10.77 GB of unallocated that I'm gonne make a simple volume.

---

### Post by Pumalite on 2007-09-23
Better use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), grab that 'unallocated space' and make a partition out of it, format ext3 if you want, then install. If you get at the end of the install and end up at a white or 'blank' screen:
Ctrl+Alt+F1 to get a command line. At the command line:
sudo dpkg-reconfigure xserver-xorg, accept defaults, choose 'vesa' as the driver, then: startx

---

### Post by jallen0514 on 2007-09-23
Okay I'm not too good with Linux, but when I installed Ubuntu I didn't set up the network configuration, so I'm not sure if I can get GParted with apt-get unless it's on the Ubuntu LiveCD. And after I used GParted, do I just do startx at the command prompt?

---

### Post by Pumalite on 2007-09-23
Get the Gparted that is the stand alone, burn to CD, boot from it, program. Get wired to the Internet if necessary. You can configure your wireless later.

---

### Post by jallen0514 on 2007-09-23
Alright I'm burning the iso to a disc right now, I'll edit after I'm done. Thanks for all the help man, I really appreciate it.

---

### Post by Pumalite on 2007-09-23
You are welcome. Good luck.

---

### Post by jallen0514 on 2007-09-23
Well I used GParted to create an NF3 10.77 GB partition. I installed Ubuntu Fiesty, and now BusyBox is stuck saying "/bin/sh: can't access tty; job control turned off (initramfs)"\ :confused:

---

### Post by Pumalite on 2007-09-24
Here is a mix of fixes for your problem. Apply what suits you:(thanks to dannyboy)

o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by jallen0514 on 2007-09-24
Okay so if I'm on the alternative disc, that doesn't use the GUI to install, what exactly do I do. I was looking at the partitions and noticed that when I tried making the target directory at the /dev/hda1/ directory it told me that /dev/hda1/ didn't exist. I show a /sda1/ directory when I did the partition managing from the Ubuntu disc, and honestly I'm at a loss. I only have the Fiesty alternative disc with me in class. If I use the regular LiveCD and format the partitions and install again I'll be able to get to the terminal off the LiveCD, correct?

---

### Post by Pumalite on 2007-09-24
Can you get a command line with Ctrl+Alt+F1?

---

### Post by jallen0514 on 2007-09-24
Yeah I can get the command line only when I pick recovery mode from Grub, not in just the regular Ubuntu boot, it gives me that error /bin/sh: can't access tty; job control turned off (initramfs).

---

### Post by Pumalite on 2007-09-24
Let's try this in Recovery Mode, at the command line:

sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by jallen0514 on 2007-09-24
Okay I booted in recovery mode and used vesa and default for everything else and entered startx at the command line and got this:

```
Build Date: 04 April 2007
Module Loader Present

(==) Log File: "/var/log/Xorg.0.log"
(==) Using Config File: "/etc/X11/xorg.conf"

Backtrace:
0: /usr/bin/x11/x(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/x11/x(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/bin/x11/x(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xde) [0xb7d63ebc]
5: /usr/bin/x11/x

Fatal server error.
Caught signal 11. Server aborting.

XIO: fatal error IO error 104 (connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.
```

I downloaded Explore2fs on my Vista partition, is there any hopes of me resolving it by editing some files or something from the ubuntu partition in Windows?

---

### Post by jallen0514 on 2007-09-24
Alright, after finding a few more topics and opening the Xorg.0.conf file with Explore2fs I found this topic: [similar problem](http://ubuntuforums.org/showthread.php?p=2714457). It seems they have the same hardware and got it to boot Ubuntu with 16-bit color. I read the last post that explains how he finally got it working, but I don't know how to do all of that so I'm asking for help on that.

> Partialy solved.

I went to intellinuxgraphics.org to compile the lastest intel drivers and I read this from the documentation:

Quote:
3.1 Agpgart

To compile agpgart, you must recompile kernel.

Note: from kernel 2.6.20, agpgart can only build into kernel rather than building as modules.
Feisty comes with a 2.6.20-15 kernel and in the configuration It include agpgart like a module. Therefore, I recompiled the kernel including agpgart inside and now, when boot, I have agpgart device in /dev.

Xorg runs with intel driver but in 16bits of color depth... xorg.conf have 24bits how preferred color depth so It's solved in part.

---

### Post by Pumalite on 2007-09-24
That's something beyond my capabilities. But let's take a look at xorg,conf:
Post:
cat /etc/X11/xorg.conf

---

### Post by jallen0514 on 2007-09-24
Okay I zipped it and uploaded it: [link](http://www.mediafire.com/?0km8fxzijj2)

---

### Post by Pumalite on 2007-09-24
Everything seems OK. (Driver		"vesa"). I don't know what else to tell you, except to try a different distro to see if your incompatibility is with Linux or only with Ubuntu.

---

### Post by jallen0514 on 2007-09-25
Well I installed Mepis, and it's working fine. Guess I'll just use Ubuntu on my desktop. Thanks so much for all the help man.

---

### Post by Pumalite on 2007-09-25
You are welcome. Good luck.

---

