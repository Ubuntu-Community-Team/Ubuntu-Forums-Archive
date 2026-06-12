---
title: "Boot Repair Problem"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by yahia3 on 2014-05-11
[FONT=arial]Hi

I just used BootRepair for fixing the booting on my machine. I used Ubuntu Desktop 14.04 Live CD for the installation. My machine supports UEFI. This is the URL of the boot summary:

[http://pa](http://pa)[/FONT][FONT=arial]ste.ubuntu[/FONT][FONT=arial].com/74454[/FONT][FONT=arial]24/

Your help is really appreciated.

Thanks
Yehia[/FONT]

---

### Post by grahammechanical on 2014-05-11
Your link to the boot repair report does not work. Could you please provide a little more information about your machine specifications and describe what is wrong.

Regards.

---

### Post by oldfred on 2014-05-11
Is this your link?
[http://paste.ubuntu.com/7445424/](http://paste.ubuntu.com/7445424/)

I thought efi partitions were supposed to be close the the front of a drive per UEFI spec. Windows makes it a second or even third install sometimes, but it still is before any large partitions on drive. Your efi partition is at end of drive.
And most desktops do not need a separate /boot partition. Did you reinstall without the /boot partition or use Boot-Repair without ticking the separate /boot partition. It looks like you have a /boot but current configuration does not use it. Not sure if correctly configured or not?

Are you booting in UEFI mode as that is how you have installed. And do you have secure boot off?

---

