---
title: "grub boot"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by wiko on 2008-09-12
hello everyone,
I'm trying to install uuu 8.04 on my desktop but after installation uuu can't boot.

this is my configuration:

sdb 120gb IDE (ntfs winxp)
sda 160gb SATA (120Gb ntfs - 40gb for Ubuntu)

I wrote at first sdb because I'm using the IDE HDD as master first drive.
Where I should put grub?
What about its configuration?

thanks guys,
and sorry for my bad english.

---

### Post by caljohnsmith on 2008-09-12
> **wiko said:**
> hello everyone,
I'm trying to install uuu 8.04 on my desktop but after installation uuu can't boot.

this is my configuration:

sdb 120gb IDE (ntfs winxp)
sda 160gb SATA (120Gb ntfs - 40gb for Ubuntu)

I wrote at first sdb because I'm using the IDE HDD as master first drive.
Where I should put grub?
What about its configuration?

thanks guys,
and sorry for my bad english.
If you can use your BIOS to boot from the SATA HDD, that would be ideal, because then you can install Grub just to the SATA drive without touching your IDE drive. Then you can add an option to your Grub menu to boot Windows on the IDE drive. Use the following to figure out which HDD is which:
```
sudo fdisk -lu
```
That will probably show your IDE drive is actually sda and not sdb. When you get to the last step in the Ubuntu installation, click on the "advanced" button, and then tell Grub to install to "/dev/sdb" (or whichever is your SATA drive). Let me know how it goes.

---

### Post by wiko on 2008-09-12
perfect! thanks a lot!
Now i'm trying to enable the second monitor on my GeForce FX 5200.
Uuu has installed the restricted drivers automatically.. but nothing..
Can you tell me something?
thank you

---

### Post by caljohnsmith on 2008-09-12
> **wiko said:**
> perfect! thanks a lot!
Now i'm trying to enable the second monitor on my GeForce FX 5200.
Uuu has installed the restricted drivers automatically.. but nothing..
Can you tell me something?
thank you
Have you made sure your restricted drivers are enabled? If you go to System > Admin > Restricted drivers (I'm not in Ubuntu right now--I'm going from memory, I think that is where it is), it will give you the option to enable/disable restricted drivers. That would at least be the first place to start.

---

### Post by wiko on 2008-09-12
yes they are enabled...

---

