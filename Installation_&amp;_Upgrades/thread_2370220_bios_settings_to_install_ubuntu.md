---
title: "bios settings to install ubuntu"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by alvpizz on 2017-08-31
hello, 
I am asking this question here because i am hoping to find someone who has had a similar problem, or who knows how to solve it, because it may also be an ubuntu issue.

I use ubuntu since 8 years already so I am not new anymore, but computer's bios change strangely, and get difficult and insane I think. i recently buyed a new computer to replace my old one, ant it's an Asus N552VW. It came with windows 10 in it, but i make no use of it, and wanted to install ubuntu. at the first try it freezed out constantly as i tried to start ubuntu from usb stick to install it. I then found out that the bios settings must be modified, because of UEFI stuff ecc. my bios settings are posted in the pictures, that show all 5 the bios's settings:

[https://drive.google.com/open?id=1sOiJKELy7Zi3t4bkVJT2ffqqlJakQ34o0A](https://drive.google.com/open?id=1sOiJKELy7Zi3t4bkVJT2ffqqlJakQ34o0A)

[https://drive.google.com/open?id=1cO-p7oWad20PaoL4rezL9LQrjw9WT00qPA](https://drive.google.com/open?id=1cO-p7oWad20PaoL4rezL9LQrjw9WT00qPA)

[https://drive.google.com/open?id=1G3pXUMPa-WFr19_Yrz9utH6-qd9gg3FB8g](https://drive.google.com/open?id=1G3pXUMPa-WFr19_Yrz9utH6-qd9gg3FB8g)

[https://drive.google.com/open?id=13OJBPFg3XVyaqK3b5dlnATT0JSs0PMLuTQ](https://drive.google.com/open?id=13OJBPFg3XVyaqK3b5dlnATT0JSs0PMLuTQ)

[https://drive.google.com/open?id=180ZShgrv70T86JJZsnMOfFIPR9bAAPOb1g](https://drive.google.com/open?id=180ZShgrv70T86JJZsnMOfFIPR9bAAPOb1g)

with these settings, that should be correct as i have read on many other pages, i should be able to start ubuntu and install it. but this doesnt happen, or, better, it does not happen the most of the times. 3 times it worked and I managed to install ubuntu, removing windows, and the rest of the times the computer got stucked on a screen like this one: 

[https://drive.google.com/open?id=1uekkVsmyudY0km5ujJ2qvpL5YJ2IZX08-w](https://drive.google.com/open?id=1uekkVsmyudY0km5ujJ2qvpL5YJ2IZX08-w)

no matter how much time i left it there, it would not move. this happened both with ubuntu and ubuntu mate, and this is the problem i get told to happen when the bios settings are wrong, but i have changed them! anyway, 4 times, just 4 times out of at least 50 tries i have maked, ubuntu started and I installed it. 1 time i managed to install ubuntu mate 17.04 . it worked for one boot time, during which i installed some applications and (i think, I am not sure) i installed updates. then, trying to reboot, after i inserted my password, it would freeze. I tried again, and installed ubuntu 17.04. this time i am sure, I installed applications and updates, and then after reboot it freezes as ubuntu mate 17.04 after i insert my password. ubuntu 17.04 also had the problem, that when i clicked "turn off", it freezed without turning off, so i had to force it with the power botton. last time i installed ubuntu 16.04, and this OS does not even start. i see grub, select ubuntu, and then i get an error message as it is starting, telling: 
" /dev/sda1 has unsupported feature(s): metadata_csum
e2fsck: get a newer version of e2fsck
fsck exited with satus code 8
[ 9.502245] tpm_crb MSFT0101:00: can't request regionn for resource [mem 0xfed40080-0xfwd40fff]"

the result of all this is that i can't use my new computer, not still. I am trying to start it from usb stick in order to install again ubuntu 17.04, but it is not starting. i've also just seen a post telling that ubuntu freezes after installing updates and rebooting: this should mean that there is an issue with ubuntu itself, but after it is installed. if anyone knows what to do to get my computer working, i'd like it very much, thanks

---

### Post by oldfred on 2017-08-31
I am not sure about some of the Intel settings. I thought some may conflict but not sure anymore.
What video card?
Did you update UEFI from Asus to newest for your system?

You did not show lower level menus on drives & Secure boot settings.
Drives should be set to AHCI not RAID nor IDE.  Some of the Intel settings may make it seem like RAID to Linux.
You should have CSM off. I think only Dell needs it on, but you still want to boot in UEFI boot mode both from USB flash drive and once installed from hard drive. Just noticed one thread where user said he had to have CSM on, but you still boot in UEFI.
How you boot install media is how it installs UEFI or BIOS. But that may not be default from UEFI for system once installed.

See link below in my signature for general UEFI install info.
Some other Asus threads. Issues are more common across various models of same brand.
       Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/) 
            ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by alvpizz on 2017-08-31
i am reading about UEFI installation, but if i try to load from usb in UEFI mode it freezes anyway

---

### Post by alvpizz on 2017-08-31
> **oldfred said:**
> I am not sure about some of the Intel settings. I thought some may conflict but not sure anymore.
What video card?
Did you update UEFI from Asus to newest for your system?

You did not show lower level menus on drives & Secure boot settings.
Drives should be set to AHCI not RAID nor IDE.  Some of the Intel settings may make it seem like RAID to Linux.
You should have CSM off. I think only Dell needs it on, but you still want to boot in UEFI boot mode both from USB flash drive and once installed from hard drive. Just noticed one thread where user said he had to have CSM on, but you still boot in UEFI.
How you boot install media is how it installs UEFI or BIOS. But that may not be default from UEFI for system once installed.

See link below in my signature for general UEFI install info.
Some other Asus threads. Issues are more common across various models of same brand.
       Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/) 
            ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

unfortunately I am understanding very little, I updated nothing to last version from asus.
video card is nvida geforce gtx 960M
i can ad lower level menus but i enabled almost everything
Drives should be set to AHCI not RAID nor IDE.  Some of the Intel settings may make it seem like RAID to Linux. what does this mean?

---

### Post by oldfred on 2017-08-31
Some setting somewhere in UEFI should display RAID, IDE, or AHCI. It may say Intel SRT or something similar. You want AHCI. 

If you have nVidia you need nomodeset as one of the boot parameters. You may need others as the threads above mention.

You have nomodeset to grub line. If you only have installed Ubuntu, then you will not normally get grub menu, but have to press escape right after Asus logo but before grub loads. May have to press several times to catch it.
But if you have UEFI fast start up on then you may not have time to press any key. I did not see that setting in your screens but Windows requires it so it must be somewhere.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Once you have booted, you will need to go into system settings & install the recommended nVidia driver. Do not download a driver directly from nVidia.
You can also use recovery mode boot, second line in grub to get to command line and install nVidia driver from there if needed.

---

