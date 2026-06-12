---
title: "Installed but won't boot."
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by crazyants on 2007-06-28
Ok so after much trouble, II finally got a release of ubuntu to install (7.04), so I'm finally really happy i can stop living off the live CD But here come's another problem.

After I install, I restart the comp right? so I do it. It starts up and says "

"DISK BOOT FAIL, INSERT SYSTEM DISK AND PRESS ENTER"

I'm confused. Shouldn't it start after I just installed it? I'm in the live CD right now and I can see the stuff that has been put onto the HDD, but I wouldn't know what to do it there was something I could do.

---

### Post by dabl on 2007-06-28
Sounds like you need to re-arrange the boot sequence in BIOS -- sounds like it isn't seeing the CD ROM drive as the first boot device. :)

---

### Post by crazyants on 2007-06-28
've already done that with the BIOS, and have tried booting up without a CD in the drive.

---

### Post by confused57 on 2007-06-28
You could possibly try reinstalling grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Does your bios recognize the drive correctly & is set to "auto"?  If it's IDE, are the HD jumper pins set to cable select(or master/slave)?

---

### Post by crazyants on 2007-06-28
Please explain the IDE thing you just described. I have found out that my bios for some reason is not detecting my HDD. In the beggining it tryings to detect a primary and secondary drive and finds nothing. Have I forgotten to do something with my hardware.

---

### Post by confused57 on 2007-06-28
> **crazyants said:**
> Please explain the IDE thing you just described. I have found out that my bios for some reason is not detecting my HDD. In the beggining it tryings to detect a primary and secondary drive and finds nothing. Have I forgotten to do something with my hardware.
This explains hard drive jumper settings(master/slave/cable select):
[http://www.mysuperpc.com/hdu/jumper_pins.shtml](http://www.mysuperpc.com/hdu/jumper_pins.shtml)

If this is a hard drive that you just installed, you might want to check that the IDE cable & power connectors are secure & connected correctly.  Cable select would probably work, but if the jumper is set to master, the hard drive must be attached to end connection on the IDE cable and if set to slave, then attach to the connector next to the end connector...the connection on the other  end  is for the MOBO IDE controller.  
Do you have any other hard drives that are being detected OK in bios?

You can boot up the live cd, open a terminal(Applications---Accessories---Terminal), and check the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
evidently Ubuntu recognized the drive, since you installed to it...this command will show your hard drive(s) and partitions.

I'm no expert with computer hardware, I've built a couple, so there's probably something I've overlooked or am not aware of that might be causing your problem.

Did you try to reinstall grub with the live cd?

---

### Post by crazyants on 2007-06-28
Yes I have tried reinstalling grub from the live CD, with no affect mind you.

Here's the fdisk info:


Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1158     9301603+  83  Linux
/dev/hda2            1159        1216      465885    5  Extended
/dev/hda5            1159        1216      465853+  82  Linux swap / Solaris

---

### Post by confused57 on 2007-06-28
I would suggest that you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download & hopefully it will be able to boot your Ubuntu installation and maybe give some idea of what the problem might be.

---

### Post by crazyants on 2007-06-28
And to complete the information I was giving earlier, It appears that my cables are secure, and My jumper is set to master (it's my only HDD).

I'll try the super grub disc.

---

### Post by crazyants on 2007-06-28
Super grub disk did not boot my installation in any automatic choice because it seems I keep on getting a error 15, and this is the first time I decided to switch over to linux to..  

I would possibley need a link or some help with the manual choices.

---

### Post by confused57 on 2007-06-28
I haven't personally experienced this problem, but from what I've read it can be hard to diagnose...you might read some of the suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=100368&highlight=Disk+error](http://ubuntuforums.org/showthread.php?t=100368&highlight=Disk+error)

---

### Post by crazyants on 2007-06-28
It turns out that error 15 is "file not found."

---

### Post by confused57 on 2007-06-28
I must have missed you were getting a grub error 15:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

The Disk Failure message is probably a bios error, not a grub errog.

---

### Post by crazyants on 2007-06-28
links aren't working ....

---

### Post by confused57 on 2007-06-28
> **crazyants said:**
> links aren't working ....
They both worked for me approx 30 seconds ago, they may not help you but may be worth reading.

---

