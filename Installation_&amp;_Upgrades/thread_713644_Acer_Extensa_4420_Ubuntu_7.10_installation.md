---
title: "Acer Extensa 4420 Ubuntu 7.10 installation"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by drteming on 2008-03-02
I picked up an Acer Extensa 4420-5237 from a large retail chain store several weeks ago.  It sports the AMD Athlon64 TK-55 CPU, 2 GB of DDR2 memory and ATI Express X1250 integrated graphics.  After many trials and tribulations, I got Gutsy Gibbon up and running with the full glory of Compiz-Fusion to boot.  I've seen several threads about the installation process, but none addressing the complete procedure.  I'd like to share my experiences.

First of all, a few general issues:

1.  The live CD will not work.  The boot-up process hangs at "bcm43xx_Microcode5.fw" error.  This is actually due to the X1250 graphics.

2.  Installation of Gutsy Gibbon has to be done via the alternate CD.

3.  After installation, the boot up process will hang at the same spot as the live CD.  This has to be fixed by booting into recovery mode.

4.  I installed the 32-bit version.  I had problems with the wireless driver and firmware with the 64-bit version.

5.  I could not for the life of me get Compiz Fusion to work without xgl, despite the newest ATI driver supporting AIGLX.


So here goes:

The first thing that I did after I brought the notebook home was to make the recovery DVD's with the Acer utility.  I then reinstalled Vista after formatting and repartitioning the harddrive.  My harddrive is partioned as such:

Partition 1 (40GB):  Vista

Partition 2 (85GB):  Programs and storage

The remaining free space, around 25GB, I left unformatted for Ubuntu.


Installing Ubuntu:

1.  Boot into Vista, download the latest driver from ATI:  [[COLOR="Red"]LINK[/COLOR]]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

2.  Save the driver to an easily accessible directory in Vista.  In my case, **D:\Ubuntu**

3.  Shutdown, boot up from Ubuntu alternate CD, make sure you have a wired network connection.

4.  Install Ubuntu from the alternate CD.  The process is pretty much self explanatory.  At the partitioning step, I chose "manual" and selected the free space I had on my harddrive and selected automatic partitioning of the space.  The installation process will also ask you what network connection you want to use, and I chose the wired connection.

5.  After installation, remove CD and reboot.  Choose the recovery mode at the Grub OS selector screen.  The following is necessary because for some reason, I could not get networking to work in the recovery mode.

6.  At the prompt, change to root directory

```
cd ..
```

7.  Make a directory in which to mount whatever drive on which the ATI driver is stored

```
mkdir vista
```

8.  Mount the drive (sda2 because my D:\ drive in Vista is on partition 2.  If you stored the driver on C:\, then use sda1)

```
mount /dev/sda2/Ubuntu vista
```

9.  Change into the directory where the ATI driver is stored

```
cd /vista/Ubuntu
```

10.  Run the ATI driver

```
./ati-driver-installer-8-02-x86.x86_64.run
```

11.  Reboot

```
shutdown -r now
```

12.  Now you should be able to boot into Ubuntu.  Click on the restricted driver notification.  Click to enable the wireless networking adaptor and download the firmware.  Also note that the ATI driver is marked as in use, but the enable box is not checked.  Do **NOT** check it at this time.  You have to uninstall the ATI driver installed in step 10.  That was just so you could boot into Ubuntu.  The ATI driver package was made for Fedora and SUSE.  Go into terminal and enter:

```
cd /usr/share/ati
```

```
sudo ./fglrx-uninstall.sh
```

13.  Now, pull up the restricted driver manager from the System menu and click to enable the ATI driver.  Download and install the updates from the Update Manager as you wish.  Reboot.

14.  For Compiz Fusion, I had to install XGL.  The newest ATI driver supports AIGLX but I could not get it to work.  First though, edit xorg.conf and compiz per these instructions:  [[COLOR="Red"]LINK[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects")

15.  Install XGL

```
sudo apt-get install xserver-xgl
```

16.  Restart x-server with Ctrl-Alt-Backspace.

17.  Enable Compiz Fusion: [[COLOR="Red"]LINK[/COLOR]]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200")


Hopefully, this guide will be short-lived and will be made obsolete by Hardy-Heron and the next round of ATI drivers.

---

### Post by FALSEFLAG on 2008-03-23
installed Ubuntu Studio Heron beta today on same machine. Was ALL JOY! except for wireless, may still have to handcut broadcom driver and manually package it. Fusion is running great except for a few lockups during initial configuration and the occasional pixel glitch that goes away once you drag something across it.

---

### Post by FALSEFLAG on 2008-03-24
was 64bit version of heron and the gl performance seems to degrade over time, maybe a memory leak...trying 32 bit today and hope I can get the broadcom wireless driver up, was running 32 bit vista before so its possible the hardware drivers do have some 64 bit issues. On a bright note, even under 64bit, failsafe gnome runs flawlessly w/ cabled ethernet support. Once the bugs are shaken out I feel certain I will dump vista and goto just Myth or Studio in my grub menu :-) Heron kmaimho! I think we are looking at the OS of the future!I think I may go native Compriz on the desktop this time and see if that helps with the gl issues in Fusion. Once I get stable I'm ytubin the results and will be giving the uberlecture on realtime CompF00z interfacing, yeh, BAyehBEE! 
PS> had rotating deskcube with fire/water/locate mouse, shaky move fade to desk running for several hours b4 it started glitching out, was using propeeATI driver and didn't have issues till I screwed with some other gl poop.

---

### Post by drteming on 2008-04-28
The final release of 8.04 worked wonderfully.  After installation, refreshing the update manager detected the wireless card and automatically downloaded the driver and firmware.  Also, the ATI driver works as advertised.  The headphone jack is working perfectly as well.

---

### Post by SuperMike on 2008-07-13
Wireless is working for me by following drteming's advice using Ubuntu 8.04. Still not certain if Bluetooth is working because I can't mate it with my Blackberry yet. Note I'm new at understanding Bluetooth stuff, though. Screen resolution and sound are okay. No video flicker or issues like that. Chose Advanced Video Effects feature and used Restricted Video Driver for that. It worked fantastic with no problems on video effects.

Couldn't get Euro keyboard key to work -- wish I had a script that fixed that as I have European clients. Would also like $ symbol (the second one on the keyboard) to act like a British Pound.

---

### Post by Villemus on 2008-07-21
I've got the livecd (8.04) running on my extensa 4420, but I can't get my wireless to work. I'm kind of a newb but I ran a lspci in a terminal and it shows my broadcomm adaptor on there. Anyone else have this problem?

---

### Post by SuperMike on 2008-07-23
> **Villemus said:**
> I've got the livecd (8.04) running on my extensa 4420, but I can't get my wireless to work. I'm kind of a newb but I ran a lspci in a terminal and it shows my broadcomm adaptor on there. Anyone else have this problem?

Report the bug on Launchpad. Then, switch to installing on the hard drive and using the Alternate CD, but not the AMD64 version. It works fine in that case.

---

