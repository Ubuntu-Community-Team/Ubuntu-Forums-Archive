---
title: "Ubuntu 14.04.1 - how to upgrade X.org server to version 1.16.1?"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by aljosa2 on 2014-10-28
Hi all, 
I have recently upgraded one of two hard drives to a speedy SSD - results are really fantastic.
Unfortunately, Fn keys for changing screen brightness are still not working on my Asus N750JV-T4069H notebook ((Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M). I am able to adjust screen brightness using the power indicator icon on the top right corner of the screen, but brightness level is automatically reset to maximum on every restart, which is pretty annoying.

After some experimenting with various versions of Ubuntu (14.10 included) and its official flavours, I intend to switch to Ubuntu 14.04.1 LTS.
Before anything else, I will upgrade kernel to 3.17.X.
If it's at all possible to upgrade X.Org Server to version 1.16.1, can someone please suggest ways and guide me step by step how to win against all those codes, commands, scripts and similar things...
Thanks in advance for any replies :)

---

### Post by hectorsales on 2014-10-28
I think you should wait to release to Ubuntu 14.04.2 when the release was made ubuntu team gives you the ability to update the Xorg(1.16.1), the kernel (3.16) and the mesa drivers ( 10.3).

Best Regards.

---

### Post by aljosa2 on 2014-10-29
February 2015?

---

### Post by hectorsales on 2014-10-29
I'm no sure but i has read on some webs sites that is possible towards the end of the year (December 2014 ). When ubuntu 14.04.2 is released you can upgrade** (Point Releases)** the kernel 3.16 (tha use utopic), the Xorg 1.16 (that use utopic) and the mesa drivers 10.3 (that use utopic).

[FONT=arial black][/FONT][B]It will be something like this:

[/B][https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Best Regards.

---

### Post by aljosa2 on 2014-10-29
thank you very much :)

---

### Post by jhay2 on 2014-10-29
aww . december 2014 if 14.04.2 released my mesa 10.1.0 will upgrade to mesa 10.3 ? how can i prevent that ? mesa 10.3 has a bugs on my old graphic card ,i already tried that version when i boot ubuntu 14.10 on usb , blender is crashing at startup of the application , both  mesa 10.3 and 10.4 development version have an issue with radeon_fbo.c , that bug makes me to decide not to upgrade ubuntu 14.04 to 14.10 ,  how can i prevent my mesa to upgrade to 10.3 ? thanks

---

### Post by hectorsales on 2014-10-29
> **jhay2 said:**
> aww . december 2014 if 14.04.2 released my mesa 10.1.0 will upgrade to mesa 10.3 ? how can i prevent that ? mesa 10.3 has a bugs on my old graphic card ,i already tried that version when i boot ubuntu 14.10 on usb , blender is crashing at startup of the application , both  mesa 10.3 and 10.4 development version have an issue with radeon_fbo.c , that bug makes me to decide not to upgrade ubuntu 14.04 to 14.10 ,  how can i prevent my mesa to upgrade to 10.3 ? thanks

No, **the upgrade it's optional**, **only upgrade if you want**  putting the commands that ubuntu team will propose.To update the kernel and graphics drivers to the version that  use utopic** to do it explicitly** with the commands that ubuntu team will propose.

Best Regards

---

### Post by jhay2 on 2014-10-29
i just want to upgrade x.org and kernel and other software ,but not mesa , upgrading system is very easy right? by just typing sudo apt-get upgrade 

but how can i upgrade all software on my system without upgrading mesa ?is this possible. 

sorry for hijacking the thread . :)

---

### Post by grahammechanical on 2014-10-29
> [COLOR=#000000]sorry for hijacking the thread . [/COLOR]

Then start your own thread. Or ask the moderator to do it for you.

---

### Post by grahammechanical on 2014-10-29
@aljosa2

I do not think that Ubuntu will go onto the linux 3.17 series kernel. According to the minutes of the Kernel Team meeting the intention is to move Vivid Vervet on the kernel 3.18 series.

[http://voices.canonical.com/kernelteam/2014/10/28/kernel-team-meeting-minutes-october-28-2014/](http://voices.canonical.com/kernelteam/2014/10/28/kernel-team-meeting-minutes-october-28-2014/)

To get an idea of the joys and sorrows of installing the kernel ourselves see this thread
[URL="http://ubuntuforums.org/showthread.php?t=2240948"]
http://ubuntuforums.org/showthread.php?t=2240948[/URL]

Some of us are already trying out kernel 3.18. But not me, though. It sounds too hairy.

[http://ubuntuforums.org/showthread.php?t=2249161](http://ubuntuforums.org/showthread.php?t=2249161)

[http://ubuntuforums.org/showthread.php?t=2250143](http://ubuntuforums.org/showthread.php?t=2250143)

Regards.

---

### Post by jhay2 on 2014-10-30
i already created a  thread before regarding mesa 10.3 but theres no one answer my thread :(

---

### Post by aljosa2 on 2014-10-30
*Phoronix, 29 October 2014*

*The Linux kernel is finally being optimized for use of solid-state hybrid drives (SSHDs) that follow the ATA 3.2 standard. Jason Akers published the Linux SSHD kernel patches this week on the kernel mailing list and hopefully they'll be finalized in time for merging with the Linux 3.19 kernel. With the patches properly implemented and enabling the SSHD feature, there's a 50% improvement in boot times, 45% improvement in application launch times, a 3x faster browser, and 4x faster SQLite performance. *

*Phoronix, 29 October 2014 *

*Keith Packard has made available the first test release for the upcoming X.Org Server 1.17 release. This release is coming a bit late but Keith is still hoping to have xorg-server 1.17.0 ready for release at the end of the year or around early January. *

----

By the way, yesterday I bought a new Asus X750JN-TY027H notebook (Intel® Core™ i7-4710HQ; Bit 64; Nvidia GeForce GT840M) for my wife. While opening the package, some strange sounds were coming out of notebook. So I decided to disassembly it and discover what might be the cause. Nothing strange on the first sight. If it's already opened, why not replace 1TB HDD 5.400 rpm with the HDD 750GB 7.200 rpm from my "old" Asus? Guess what I found under HDD - CMOS battery fallen out!!!
OK, problem fixed, and after upgrading BIOS to newest version, I've installed 14.04.1 LTS. On clean installation, I have an issue with the touchpad (Elantech) not working - all the rest seems ok. I will see if I can solve this issue by installing new 3.17.2 kernel and after that installing missing Nvidia driver and all Ubuntu updates.

**The best thing is that unlike Asus N750JV, Fn keys for changing screen brightness are working like a charm (out of the box) on Asus X750JN!!!**

---

### Post by aljosa2 on 2014-12-17
Hello everybody, any fresh news about this:

[I]hectorsales:
"I'm no sure but i has read on some webs sites that is possible (release of ubuntu 14.04.2) towards the end of the year (December 2014 )." 

grahammechanical:
"I do not think that Ubuntu will go onto the linux 3.17 series kernel. According to the minutes of the Kernel Team meeting the intention is to move Vivid Vervet on the kernel 3.18 series."[/I]

I also have another important question:
with all various kernels (3.18 included), touchpad on my wife's notebook Asus X750JN-TY027H is still completely dead, and there are too many errors inside dmesg:

> xinput
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave pointer  (2)]

[http://paste.ubuntu.com/9490982/](http://paste.ubuntu.com/9490982/)

Is this the problem solution which I'm waiting for:

[I]Phoronix, 16 December 2014
New Input Drivers Coming For Linux 3.19 Kernel
One of the latest pull requests for the Linux 3.19 kernel is the input driver subsystem pull, which includes numerous updates along with a few new drivers. The new drivers will benefit some Google Chromebooks in running the latest upstream kernel. The two new drivers for the Linux 3.19 kernel input area include for Elan hardware and the Godix touch panel. The Elan hardware driver is for an I2C touch-pad and touchscreen found in several Google Chromebook models. This Elan I2C/SMbus touchpad driver was developed by EMC and beyond being found in some Chromebooks this device is also found in various laptops.[/I]

Thanks in advance for any reply :)

---

### Post by rexmtorres on 2015-04-04
@aljosa2 where you able to fix the screen brightness control issue? I have the same issue on my N750JV, too, running 14.10.

---

