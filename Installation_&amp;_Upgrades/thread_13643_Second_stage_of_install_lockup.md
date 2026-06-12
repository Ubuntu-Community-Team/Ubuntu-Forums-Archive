---
title: "Second stage of install lockup"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Neg127 on 2005-02-02
Hello,

I have installed ubuntu on a desktop of mine and I want to install it on another.  But there is an issue I am having.

I get through the first install process then it reboots the pc.  It has me remove the media and then it  reboots the pc.  Then it goes through the boot sequence there are no errors in any section in the second process where its booting the system from the hard drive.  But once it gets to the screen for the configuration settings its hard locked, numb lock caps lock are stuck.

I have tried passing options to the on the initial boot process where it starts the first install sequence such as acpi=off and that did not make a difference either.  Is there a way I can get a log from using a live cd and read through it to see what the possible errors could be.  That way I could get it figured out?

This is on an athlon xp machine 2200+ with 512mb mem, nforce2 chipset, nvidia 5200, and a logitech usb mouse. 

I have gotten gentoo to run just fine on this system, ran it for a couple of months ad just got tired of compiling every thing from source.  I would love to get ubuntu working so if any one could point me in the correct direction.

If you need any more information just let me know and I will supply what ever is asked.

Thanks

---

### Post by Neg127 on 2005-02-02
I did some more researching and found out that ubuntu has some issues with larger hard drives when they are set to auto in the bios.  I simply entered my bios and changed it from auto and manually edited the cylinders and other information to get my bios to see the 160GB drive that I am installing the system to.

Once I set the hard drive setting manually and rebooted it then went through the first part of the second install process and its now downloading the the security updates and finishing the install process.

Hope this post will be useful to some one else and figuring out an install issue. 

Thanks
Neg127

---

