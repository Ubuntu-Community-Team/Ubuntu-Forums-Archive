---
title: "Can not install 14.04 with windows 8 from an usb flash drive"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2014-07-27
When I try to install 14.04 Ubuntu I get a message that the usb flash drive is being blocked by current security settings but I can not find a way to change them from the bios screen. I had 12.04 on it for more then a year the only issue I had was I had to switch from uefi to bios to boot Ubuntu I hope we can fix that when installing this time.

Computer is a gateway NE56R47u laptop.

Any help is appreciated, I hope the master oldfred stops bye.
Thanks to all in advance.

---

### Post by oldfred on 2014-07-27
Hi, Wild Man.

One or two others with Gateways seem to have limited UEFI. Not sure of your version.
When in BIOS mode secure boot is off as BIOS has no secure boot mode.
Do you have a setting for secure boot somewhere in UEFI/BIOS?
Do you have the latest UEFI/BIOS version from Gateway?

But Ubuntu live installer is secure boot enabled using Microsoft key, so it should work with secure boot on or off.
But grub does currently have a bug and will not boot Windows from grub menu with secure boot on, so generally better to have secure boot off.

There are some models of Gateways or Packard Bell that are 32bit UEFI for Windows even though CPU is 64 bit. (Some will  do anything to prevent users from running anything but Windows.)
 Ubuntu does not (yet) have a 32 bit version.

Post this just to see current partitions:

sudo parted -l

found this old thread, somebody named oldfred was trying to help someone with a Gateway. :) He said secure boot was under authentication?

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

---

### Post by wildmanne39 on 2014-07-28
I just got the bios updated, and I keep getting an offer for a free upgrade to 8.1 but I keep putting it off, but since I have to reinstall I was thinking maybe I should update to windows 8.1 before installing ubuntu 14.04 what do you think or should I just leave it for now?

The updated bios did not give me the option to turn secure boot off, but I do have fast startup off.

The blocked message I got could that have been from the new flash drive I bought because it has some kind of password security on it?
I can not load ubuntu at all so I can not run that command yet.
I am in the woods with very little and very slow connection so my replies will most likely be slow.
Thank you

---

### Post by oldfred on 2014-07-28
I would update to 8.1. I also thought Microsoft was stopping support on Windows 8 or in effect you have to go to 8.1.

But 8.1 also likes to make itself first in UEFI boot order.
It used to be that any Windows maintenance would reset UEFI boot order, but those with 8.1 seem to have Windows always first. 
So the work arounds to rename files like those with UEFI that only boot Windows seems to be required.

It was reported that Microsoft required all vendors to allow users to turn off secure boot. So if you do not have that setting they would be in violation of that promise. Of course we do not know if that is true, but every system we have seen so far, other than some tablet type systems have a secure boot on/off setting.

---

### Post by wildmanne39 on 2014-08-03
I finally got home to a good internet coonection and update windows to 8.1 then I installed ubuntu 14.04 and it is working good.

I do have to switch from UEFI to bios legacy but it does work.

Thank you oldfred!!!

---

