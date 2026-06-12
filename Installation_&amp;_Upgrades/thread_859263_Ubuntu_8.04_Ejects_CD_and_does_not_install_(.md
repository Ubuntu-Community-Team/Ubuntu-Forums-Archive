---
title: "Ubuntu 8.04 Ejects CD and does not install :("
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by nxd on 2008-07-14
I've looked through most of the topics and did not find a solution to this problem so I decided to post a topic.

I downloaded the LiveCD 8.04 ISO from one of the mirrors and burned it to a cd.  When I boot my pc from the cd, everything goes well, and it gets to the screen where it asks whether or not I want to Run from Live CD, Install, etc.  

The problem is, when I choose Run From Live CD, or Install options, the Building Linux Kernel box pops up, like expected; then the ubuntu loading bar, and then BAM! the computer ejects the cd, and ubuntu says, Please take out the cd and press enter to restart.  Ofcourse when I do that, I get a bootloader missing error, as I have no OS installed on the pc.

Need HELP!

Some of my specs:

HP 2500z Tablet PC
AMD Turion(TM) X2 Ultra Dual-Core Mobile Processor ZM-80 (2.1 GHz) 
3GB Ram
ATI Radeon(TM) HD 3200 Graphics

---

### Post by VMC on 2008-07-14
> **nxd said:**
> .... then the ubuntu loading bar, and then BAM! the computer ejects the cd, and ubuntu says, Please take out the cd and press enter to restart.  Ofcourse when I do that, I get a bootloader missing error, as I have no OS installed on the pc.

I'm not sure about the "bootloader missing error", but did you first verify the media burn with Media Check? Sounds like something else happened and I'm sure you have tried this more one once.

---

### Post by Slim Odds on 2008-07-14
> **nxd said:**
> The problem is, when I choose Run From Live CD, or Install options, the Building Linux Kernel box pops up, like expected;

???  like expected???

Neither running the Live CD or installing should build a kernel. They both use prebuilt kernels.

I think maybe your CD is bad.

---

### Post by avtolle on 2008-07-14
Did you check the md5sum of the iso before burning the iso as an image to CD at a slow speed (4x). I agree you have a bad CD there, and the above two things are things to check (along with the integrity of the CD once burned, as mentioned above).

---

### Post by tC_Crazy on 2008-07-14
I have the exact same problem, my friend, but unforunately the fix is not that great. I posted a question here yesterday, but received no response after a while so I went back to Google. After a half hour of searching, I found that there is a problem with ACPI in the tx2500z BIOS. If you view the install messages (CTRL+ALT+F1?) while it's loading, it will throw a overheat error, even with temps as low as 60*. I will see if I can find the thread again, but I believe the solution was to set acpi=off in the install parameters. However, you will need to set your CPU fan to always on in the BIOS, and it will be at full-spin (read jet-engine turbine preparing for takeoff) at all times. 

Until HP comes out with a BIOS update which fixes this bug... we'll have to live with this. I haven't personally tried this yet (just got the laptop on Saturday), but others have... agian, I'll try to track down the thread.

---

### Post by tC_Crazy on 2008-07-14
I found 2 threads on the topic... basically there are three options for the time being: install and boot with acpi=off (kills thermal detection, wireless, BT, touchscreen, audio), compile a generic kernel without thermal, or remove the thermal module from initramfs. 
:(

[http://ubuntuforums.org/showthread.php?t=849964](http://ubuntuforums.org/showthread.php?t=849964)
[http://ubuntuforums.org/showthread.php?t=845911&page=2](http://ubuntuforums.org/showthread.php?t=845911&page=2)

---

### Post by showri on 2008-09-01
you have to set acpi=off and install.if you are doing a fresh install highlight install ubuntu option and press e.then you would see a kernel line at the end of that line type acpi=off.Then it should install properly

---

### Post by gali98 on 2008-09-01
Anyone with a tx2500 series should follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=873188](http://ubuntuforums.org/showthread.php?t=873188)
it will get you set up.
Kory

---

