---
title: "Kubuntu 6.10 kernel upgrade (-&gt; 2.6.19.1)"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by eztoril on 2007-01-17
Hi all,

My name is Martin Tengklint. I'm currently trying to finish my HTPC project. The system runs on a Core2Duo processor, Nvidia 6800 video card, having two tuner cards (DVB + analog). KDE is my desktop environment and Kubuntu 6.10 (kernel 2.6.17.10) is my distribution. As HTPC software, I'm running MythTV.
 
To get the DVB card up and running, I must compile a new kernel (2.6.19.1), which includes the new linuxtv.org DVB drivers. However, when I am compiling the new kernel and install it, Kubuntu halts on startup (upon showing the splash screen (the progress bar doesn't move)). After like 10 min. I get into a BusyBox shell looking like:

[B]------------------------------------------------------------------------------
BusyBox vx.xx (200x.0x.0x-xxxx+xxxx) Built-in shell (ash) 
Enter 'help' for a list of built-in commands. 

/bin/sh: can't access tty; job control turned off 
initramfs>
------------------------------------------------------------------------------[/B]
I can in GRUB menu still choose my old kernel, 2.6.17.10, and everything works fine. However I cannot get a new kernel to boot!

I've used my old .config-file upon compiling (using make oldconfig) to answer new feature questions only.

I've tried to compile the linuxtv.org drivers only, but the new drivers are dependant of the new kernel (2.6.19.1).

1. What to get it working?

2. Does anyone know any good "Compile HOWTO" to follow, which works in my situation?

3. Does anyone have a good general .config file for me to use when compiling?

4. Is there any special key to press (or any option to enable) when booting the new kernel to temporarily disable the splash screen and hopefully see any generated output that could explain my problem? Currently I don't see any error message, only a halting splash screen.

5. Is there any log available that may cover my problem?

Please help me!
Many thanks in advance!

Best regards,
   Martin

---

### Post by Theimon on 2007-01-18
Try this HowTo and read all the links and tips twice. Also read the descriptions given in the menuconfig. Also it is wise to keep Google by your side. If you're not sure about an option, leave it to recommended settings.  [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by eztoril on 2007-01-20
Hi again,

Thanks for your answer. I successfully compiled and installed the new kernel, using the old .config file (and answered default ('ENTER') on every question concerning kernel features). As stated in the HowTo guide, I deselected the DVB budget cards support. However, the same problem occurs! :( 

Luckily, the splash screen does not come up during bootup anymore, giving me more information about my problem. the console output states:

--------------------------------------------------------------------------
[B]Starting up ...
Uncompressing Linux... Ok, booting the kernel.
[   35.468021] ACPI: Getting cpuindex for acpiid 0x1
[   35.468054] ACPI: Getting cpuindex for acpiid 0x2
[   35.468084] ACPI: Getting cpuindex for acpiid 0x3
[   38.296054] usb 1-2: can't set config #1, error -71
ALERT! /dev/sda1 does not exist. Dropping you to a shell!

BusyBox v.1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/B]
---------------------------------------------------------------------------

It seems Kubuntu is having problems to find my disk. I'm using an Samsung internal SATA 250 GB HDD. Maybe Kubuntu has problems with SATA disks?

Does anyone know what is the problem? Please advice me what to do!

Best regards,
Martin

---

### Post by Theimon on 2007-01-20
Make sure you select SATA support in the drivers section. Otherwise it won't be able to find your harddisk.

---

### Post by eztoril on 2007-01-20
Hi again,

Yes! To enable SATA support in xconfig solved my problem. The system now boots up! :D 
Thanks again for your help!

A small thing, though, where did my splash screen go? I want to enable it again.

Best regards,
Martin

---

### Post by Theimon on 2007-01-20
You have to check if usplash and related packages are installed properly. With my previous custom kernel I lost my splash image as well and couldn't get it back no matter what I tried. Didn't really bother me tho. Just remove "quiet splash" from Grub and it'll give you a big verbose list when booting :)
As long as the list keeps moving you're doing fine ;)

---

