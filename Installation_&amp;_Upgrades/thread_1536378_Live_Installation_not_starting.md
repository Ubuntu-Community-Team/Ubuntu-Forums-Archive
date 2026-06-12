---
title: "Live Installation not starting"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by lucacerone on 2010-07-22
Dear all,
I'd like to install Ubuntu 10.04 32 bit, over my Ubuntu 10.04 Amd64.
When I insert the live CD (that is working, I've used it yesterday to 
install on my desktop at work),
the Boot from CD is skipped (but is configured properly
in the BIOS, in fact when I installed the 64bit version I had no trouble
at all) and the existing OS is loaded instead.
It seems to me to read some error related with the device (but 
is fast and can't be sure what the message says).
After Ubuntu has been loaded, I can read and explore the CD.
I'd like to know how to solve this issue, any advice?
I'd want to boot from cd again, but if you know how to start
live installation when Ubuntu is already running, may you please let me know? 
Any help is appreciated,
Cheers, -Luca

---

### Post by dstew on 2010-07-22
Usually, I would try harder to make sure the BIOS settings are properly set. If you can't get the CD to boot, you can install from within Linux, by putting the installation .iso file into its own hard disk partition, and booting that partition. It is somewhat complicated. Here is a [How-To]("https://help.ubuntu.com/community/Installation/FromLinux").

---

### Post by varunendra on 2010-07-22
Physically disconnect your hard drive and try booting from the cd again. If it still can't, then definitely either BIOS is misconfigured or the CD has somehow become defective!

If you want to read the error message, try pressing 'Pause' key on the keyboard as the message comes up.

However, physically disconnecting the hard drive part is just for overriding the possible 'priority' issues in BIOS, otherwise an installed OS has no part to play at the stage of selecting a boot device. If the cd is clean & bootable, and BIOS has been set to boot from it first, it should boot!!



[B]PS:
[/B]Sometimes a weak or dirty lens or otherwise exhausted drive is also the culprit. In such cases, the cd might be read well in the up & running OS (maybe due to advanced drivers?) but the system won't boot from it. I've faced such conditions many a times in the past. (Often cleaning the CD with toothpaste, or trying so many times would do the job! ;))

---

### Post by lucacerone on 2010-07-31
Sorry for the delay but I couldn't access the computer.
The Bios settings should be fine,
I always could install or run cds at startup
without any issue.
I'll try again and send you the message I get at startup!
Cheers, and thanks for the help!

---

### Post by lift_test on 2010-07-31
I have a similar issue, I can boot from the desktop cd but not from the alternate install cd.  Seems very strange.  I'm going to try downloading the alternate again.

---

### Post by varunendra on 2010-07-31
You can check your whether your ISO files are bootable or not in virtualbox.

If virtualbox is able to boot from them, then perhaps the CDs are defective, or maybe drive is having problem in reading the boot sector.

For me, using the iso files to boot virtualbox has been the guaranteed method of verifying their integrity.


**PS:**
I've edited my previous post to add some of my own experience. Not very useful, but may help :).

---

### Post by lucacerone on 2010-08-05
Dear all, I've solved using an the Alternate i386 version.
Thanks for your advices, it's a pity though that I can't run
the Live CD :(

---

### Post by varunendra on 2010-08-05
Have you tried Live USB? Its extremely easy to create and more promising & useful if your PC's BIOS has the option to boot off USB disk.

[Here's]("http://www.ubuntu.com/desktop/get-ubuntu/download") an easy 'how to' guide. (goto step2>select "usb stick">select your OS>click "Show Me" on the page).

---

