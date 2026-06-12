---
title: "Upgrade to 16.04 issues"
date: 2016-08-01
forum: Installation &amp; Upgrades
---

### Post by morrism on 2016-08-01
I was running 14.04 on both my laptop and desktop. A message popped up to upgrade to 16.04. I did this with this laptop on Saturday with no problems and it is working fine. I did the same with my desktop today. I now have a big problem. The upgrade seemed to take a long time (almost 4 hours). It reached the end, cleaned up files and asked if I wanted to restart. I clicked yes. I'm now stuck with the purple ubuntu screen with the 5 dots underneath. It cycles through the dots twice and then stops with all the dots highlighted. I'm not sure what to do as there is a significant amount or irreplaceable data. 

Any suggestions about how to restore access as the whole thing is just frozen

If there isn't a solution to this. How do I go back to 14.04 or re-install 16.04 if the computer is frozen? The boot menu has 10.04 (presumably the last time it was updated from disc). I can't find an option to upgrade from that

---

### Post by oldfred on 2016-08-01
Did you have any ppa or proprietary drivers installed. You have to uninstall or revert to open source before upgrading as more often than not they interfere with upgrade?

What are specs/model of system.

Did you review Release notes to see if any known issues apply? Particularly Video driver section?
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

---

### Post by morrism on 2016-08-01
The setup and loaded software were the same on the Laptop and desktop, which is why I'm confused. Both are Acer, laptop Aspire 5742z, Desktop Aspire X1430

---

### Post by kansasnoob on 2016-08-01
A quick google search shows that box has  AMD Radeon HD 6320 graphics. Maybe you could try booting with the nomodeset boot parameter :confused:

AMD graphics are problematic on 16.04:

[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

But this concerns me:

> The boot menu has 10.04 (presumably the last time it was updated from disc). I can't find an option to upgrade from that 

Do you mean the grub menu shows only 10.04?

---

### Post by morrism on 2016-08-02
> **kansasnoob said:**
> 
But this concerns me:



Do you mean the grub menu shows only 10.04?

I presume so. The screen after the esc to boot menu, comes up with list of options, up and down arrow, most up to date version shown is 10.04

---

### Post by grahammechanical on 2016-08-02
The Ubuntu live session will give you access to the hard drive and you can then copy your data off the drive. Do you have a place to put it? You may need to create another partition to copy your data to. Then you can re-install.

Or, at the Grub boot menu select Advance options for Ubuntu and then select a Linux kernel with recovery mode and at the recovery menu slect Resume. That may get you to a working desktop without using a proprietary video driver. Then you can change video drivers in Software & updates>Additional Drivers tab.

Has Ubuntu 10.04 ever been on that machine? An upgrade from one version to another will remove or over-write the existing OS. And that will include the lsb-release text file that Grub uses for the labels in its menu. Also, all the kernels from the previous Ubuntu version are removed. 

Regards

---

