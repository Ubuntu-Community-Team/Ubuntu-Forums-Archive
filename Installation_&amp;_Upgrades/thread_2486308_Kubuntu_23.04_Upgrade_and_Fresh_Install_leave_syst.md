---
title: "Kubuntu 23.04 Upgrade and Fresh Install leave system unbootable"
date: 2023-04-25
forum: Installation &amp; Upgrades
---

### Post by jlynde on 2023-04-25
I have a Dell M6800 laptop on which I am trying to get Kubuntu 23.04.  Initially, it had 3 SSD drives.  One had Mageia 8, and the other two had Kubuntu 22.10.  I was only actively using one of the Kubuntu 22.10 installs.

So the first thing I tried was to just click on the Upgrade notification and do the upgrade in place.  But when the process had completed my system would not boot.  I made a previous post here:  [https://ubuntuforums.org/showthread.php?t=2486233](https://ubuntuforums.org/showthread.php?t=2486233)  I started this new thread because I have some additional information.

After the initial issue I tried to see if I could fix the problem but I was not able to figure it out so I decided to try some different approaches.  In order to try to simplify the scenario I took out two of the disks and just left one SSD which was the second (still bootable) Kubuntu 22.10 installation.  I booted that one, and then clicked on the Upgrade again and went through the process again.  This time?  Yeah, same exact result.  System will not boot - just like before.  I was hoping it was just a fluke the first time but apparently not. 

Anyway, the next thing I did was to boot from the 23.04 USB stick I had created.  That works just fine so I don't think there is a hardware issue or any incompatibility with the Kernel or OS.  I then choose Install Kubuntu and proceeded to use a custom partition layout and execute a completely fresh install.  The process seemed to go just fine.  But, you guessed it - the system would not boot.  So the laptop can run Kubuntu 23.04 when booted from USB stick but not from the hard drive in either case.  

I'm not an expert in debugging these sorts of issues so I would really appreciate it if someone would help me figure out where to look for errors in logs or whatever.  I am happy to help collect whatever information you may need as long as you tell me how to do that.  BTW, it is already on the latest BIOS (A26).

Thanks,
John

---

