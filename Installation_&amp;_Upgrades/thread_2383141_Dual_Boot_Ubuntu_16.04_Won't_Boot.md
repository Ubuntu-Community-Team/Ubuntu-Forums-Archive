---
title: "Dual Boot Ubuntu 16.04 Won't Boot"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by schatzwk on 2018-01-21
I have an Acer Aspire TC-780A. I have installed version 16.04 alongside Windows 10. 

I have done the following:
[LIST]
[*]disable Secure Boot (I've seen differing opinions on this; I've actually tried it both ways. Yes, this is my second attempt at installing Ubuntu.)
[*]disable Fast Startup
[*]shrink volume of partition containing Windows 10 OS
[*]installed Ubuntu with manual partitioning
[*]ran boot-repair: [https://paste.ubuntu.com/26431152/](https://paste.ubuntu.com/26431152/)
[*]booted into Windows and changed default boot entry of the Windows bootloader, per the boot-repair instructions
[/LIST]

At boot-up, the machine still automatically boots to Windows. If I hit F12 to open the boot menu, it only shows Windows Boot Manager and the live USB image. Running efibootmgr from live version of Ubuntu shows ubuntu as "inactive" (i.e. doesn't have an asterisk). Any changes I make through efibootmgr get undone upon rebooting.

I have seen others with Acer machines saying that you must go to "BIOS" and set the EFI as "trusted." Sadly, mine does not seem to give me this option. My "BIOS" version is 2.18.1263.

I realize that there are many posts that are very similar to mine, but I have spent hours reading through these posts and haven't found a solution yet.

Can anyone tell me how to get Ubuntu to boot instead of Windows?

---

### Post by westie457 on 2018-01-21
Follow the advice in this post. [https://ubuntuforums.org/showthread.php?t=2380145&p=13720690#post13720690](https://ubuntuforums.org/showthread.php?t=2380145&p=13720690#post13720690)
Let us know how it goes.

---

### Post by oldfred on 2018-01-21
Some old threads mention downgrading UEFI as a version from Acer did not work.
But newer threads say newest UEFI from Acer works, so make sure you have newest UEFI from Acer for your model system.

Some more examples, some users have described what they did better than others.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by schatzwk on 2018-01-21
Regarding pt. 2 of your advice that you linked to, if my UEFI does not give me the option of "trusting," does that mean I have to install a different UEFI?

If so, how do I know what UEFI I need?

---

### Post by oldfred on 2018-01-21
Did you check with Acer and see what is the newest UEFI version for your model.
And in UEFI it will tell you what version you already have.
I see you did post it already: My "BIOS" version is 2.18.1263

[https://www.acer.com/ac/en/ID/content/support-product/6990;-;](https://www.acer.com/ac/en/ID/content/support-product/6990;-;)

Most say to be able to set supervisory password, you have to have Secure Boot on. Then it opens extra items, maybe on another screen?

---

### Post by schatzwk on 2018-01-21
I have tried setting the password and enabling secure boot. It doesn't show me any options regarding any sort of "trusting." 

It seems to me that I would need a completely different UEFI altogether -- not just an upgrade -- if I want to have the option of setting the EFI to "trusted." But I don't know anything about installing a new UEFI, so I'm a little hesitant. The Acer Product Support page doesn't seem to offer any hints. It also makes it sound like it might be risky to go messing around with the UEFI installation. 

This is a new machine, so I don't have any important files on it. What is the worst that could happen if I screw up the BIOS/UEFI upgrade? (Actual question; not rhetorical...)

---

### Post by oldfred on 2018-01-21
Now most UEFI will still install, just do not have a power failure in the middle of the update.
Before it was possible to totally brick a system with a bad BIOS update.
I have updated every system I have had and never had an issue. But do try to be careful.

My systems have 3 ways to update UEFI. You download the update file. Then my UEFI can read it directly from a FAT32 formatted partition or drive. I have put it in my ESP. 
Also most update from Windows or a DOS bootable flash drive with the update files.

Best to read the manual, it should have more info on the specifics of your model.
And Acer seems to be consistent across models, so other model instructions may apply. 
But only use the UEFI/BIOS that is specific to your model system.

---

