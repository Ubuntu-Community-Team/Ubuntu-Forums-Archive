---
title: "error while installing ANY distro"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by TwanDeezy on 2010-02-13
OK, I've tried to install:
Mint 6, 7 XFCE, and 8
jolicloud
easypeasy
and probably another or two..

Oh, I'm installing this on my Acer Aspire One 751h, so I am using a USB key and UltraISO, with the exception of jolicloud, which has its own USB creator, and most recently I tried Mint 6 using UNetBootIn.

Anyway, I keep getting the same general error, but with different files...  Sometimes its errno5: input/output error, and other times its parts of a file (blah/doowop/dadada/video....)  I don't know if its a driver problem or what, but I've seen video, sound, and other random stuff..  each time it gives a different one though.  Either way, the main paragraph in the window talks about having a dirty CD, needing to replace my hard drive, or burning a new CD at a slower speed...  I've checked the md5sum, and that's not the problem.  

I'm wondering if my problem is that I'm creating the USB from one computer, and then trying to install it on the 751h.  Another thing that might be causing the problem, but I doubt, is the fact that when I set up the partition, I select "use entire disk".  

Another question, Does it make a difference if the drive letter changes?  On our main computer, the USB is mapped to drive E:, but on the 751h, it shows up as D:.  If I have to change it on the 751h, how can I without an OS?  when trying to install linux, it wiped out my windows, and I don't feel like re-installing it just to change it in a few minutes.

---

### Post by 199DMF on 2010-02-13
try a real distro

---

### Post by Satoru-san on 2010-02-13
> **TwanDeezy said:**
> 
Another question, Does it make a difference if the drive letter changes?  On our main computer, the USB is mapped to drive E:, but on the 751h, it shows up as D:.  If I have to change it on the 751h, how can I without an OS?  when trying to install linux, it wiped out my windows, and I don't feel like re-installing it just to change it in a few minutes.
Is this a WUBI install? if not, I am very confused as to what you are talking about there.

---

### Post by lenoirrichelieu on 2010-02-13
The post is very confusing indeed.
 
The lettter allocated is dependent on number of devices. For example: if you have a computer with 1 partition and 1 DVD then those will be C: and D: and your USB will be E:. If you have 2 partitions and 1 DVD then those will be C: D: E: and the USB  will be F:.
 
Should be no problems with an installation USB created as it is not computer-dependent. Is just another way to install an OS.

---

### Post by TwanDeezy on 2010-02-13
Sorry for being so confusing.  No its not a WUBI install, and I do know that the drive letters depend on what partitions/peripherals you have on the computer.  But you can remap the flashdrive/USB device to whatever letter you want.  

Anyway, I'm trying to find out why I keep getting the same errors when I try so many different methods..  but thanks anyway..

---

