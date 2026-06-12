---
title: "Wont boot up after installation next to W7"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by Colin Richards on 2012-04-19
I had problems booting Windows 7 after a crash, just would not boot.  So I trailed Ubuntu from a cd in the cd drive.  Everything worked fine and I could access the data on all the hard drives, and see everything also. 

So in order to make things faster and also to be able to run a virus checker on the drive I installed Ubuntu fully on a part of the disc that the windows 7 is installed on.  Everything seemed to work well.  

So I tried to reboot without the cd in and got an error: grub no devise installed or something like that.
So I rebooted with the Ubuntu cd in and then got the same error.  Then I rebooted and tried to go to the bios and got a totally black screen with nothing on.

I rebooted and got the cd to respond and it loaded Ubuntu, though it is asking me if I would like to trail or install again, which is weird if it is already installed. I am now running the trial version using the cd.

Why will it not boot with out the cd in?

Should I get an option to boot into either windows or Ubuntu?

Any help would be appreciated.  I have the latest stable Ubuntu 11.10.

Colin Richards

---

### Post by nothingspecial on 2012-04-20
*Thread moved to **Installation & Upgrades**.*

---

### Post by darkod on 2012-04-20
It seems there is no bootloader on the hdd, so you can only boot with the cd in live mode.

Go into live mode and run the boot info script from the link in my signature. Post the results as explained there. That will show more details of the current setup.

It looks like you only need to add the grub2 bootloader to the MBR of your disk, but lets not speculate without the results first.

---

