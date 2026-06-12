---
title: "No DVI signal during Ubuntu install"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by CyClyst on 2010-06-30
Hello
 
I would like to dual boot ubuntu and windows 7. I already have windows 7 installed and partitioned. 
 
I downloaded and burned the ubuntu install CD. 
 
When I boot from CD I get to a main menu where I can choose to install ubuntu, run ubuntu without install etc etc. 
 
When I go to install ubuntu a loading screen appears. 
 
After awhile though my screen goes blank and my monitor says no DVI input. Lame. 
 
I think switching to VGA would solve this...however my graphics card only has DVI input. What can I do so the install works with DVI input?
 
My graphics card is: ATI Radeon HD 5670 1GB GDDR5 16X PCIe Video Card 
 
 
THANK YOU SO MUCH!!!!

---

### Post by CyClyst on 2010-06-30
Can anyone help me?

So far I have tried deleting quiet splash and also activating boot option nomodeset. Neither of those fixed the problem.

What now?

---

### Post by oldfred on 2010-06-30
nomodeset worked for me but I have nvidia.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Kernel update splash screen issue.
[http://ubuntuforums.org/showthread.php?t=1503509](http://ubuntuforums.org/showthread.php?t=1503509)

---

### Post by CyClyst on 2010-06-30
Could someone elaborate on the previous post please? 

I do not have ubuntu installed yet so I cannot get to any kind of terminal.

I have seen a couple of different threads try to solve this problem with NVIDIA graphics cards but couldsomeone help me out with my ATI graphics card?

---

### Post by oldfred on 2010-06-30
If you press f6 on the initial screen it should give you various options to try some of the setting from the kernalmodesetting link. First use the try Ubuntu before running the install.

---

### Post by CyClyst on 2010-06-30
Using this workaround:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

I used the option xforcevesa

I was able to start the install!

Just a minor concern: What drivers do I need to install if any now?

---

