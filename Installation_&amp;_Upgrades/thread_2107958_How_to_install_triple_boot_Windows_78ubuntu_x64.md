---
title: "How to install triple boot Windows 7/8/ubuntu x64"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by X01 on 2013-01-23
I have Windows 7 and 8 installed on different HDDs and am using Windows 7 boot loader.
I have made a new partition on the same HDD as Windows 7 for installing Ubuntu.

Is it possible to triple boot with Ubuntu using the Windows 7 boot loader, and how would I go about doing this?

I see during the Ubuntu installation there is an option for selecting your partition, but I am confused to the other options and really don't know what I'm doing.
Not sure what to select for boot loader installation nor what mount point is for.

Thank you.

---

### Post by dino99 on 2013-01-23
Kind of question posted a million times here & there on ubuntuforums  ):P):P


as you does not tell us details about your hardware (bios/uefi mainly) its hard to give a custom answer, so here is a standard installation made on system using a bios:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by X01 on 2013-01-23
Thanks for the reply, but I'm still in the dark here.

---

### Post by oldfred on 2013-01-23
I would not use the Windows 7 boot loader. Grub is designed to boot multiple systems where Windows only boots Windows. There is EasyBCD which some do use. But you have two MBR's so you can keep the Windows boot loader in one drive and the grub2 boot loader in the other drive, even if not same drive as install. 

I do normally suggest having Windows on one drive and Ubuntu on the other which each fully configured to boot without other drive, because drives fail.

Also Windows always puts its boot files into one active partition. So which ever Windows you installed second will have its boot files in the first install and have no boot files in its install. You can do a repair so grub can see both and let you boot either. Windows also installs to the active partition on the drive set as boot in BIOS.
         To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Post this to see your current partitions:
sudo fdisk -lu
If gpt use this instead.
sudo parted -l

I assume you know this, since it also applies to dual booting two copies of Windows.
       
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by X01 on 2013-01-24
Thanks for the info. I don't want to risk messing up my system at the moment, so I'll forget it for now.

---

### Post by Thee on 2013-01-24
Here is how you can do it...

Start installing Ubuntu, and when asked where to install GRUB, choose / root of the partition where you are installing it. Do NOT install it in MBR.

After you finish the installation and reboot, you wont be able to boot into Ubuntu, you will have your windows boot loader with choices you already have.

Next, boot into windows and install EasyBCD:
[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

EasyBCD will allow you to edit Windows boot loader entries. From there, add a new OS to the boot menu and choose:
Linux; Grub2; and partition where Ubuntu is installed.

Now when you reboot, you will have 1 more choice at the boot menu - Ubuntu. And you will still have your Windows boot loader.

The only down side of this is, when you select to boot to Ubuntu, you will be presented with GRUB boot loader with the same boot options that you had in Windows boot loader, but I guess that isn't a big deal as it is the closest to what you asked. You only have to press Enter twice to boot to Ubuntu or wait until it boots in automatically.

Hope that helps.

---

### Post by X01 on 2013-01-24
> **Thee said:**
> 

Hope that helps.

Thank you. That is very helpful and exactly what I want to know.
;)

---

### Post by Thee on 2013-01-24
No problem, hope it works out ;)

---

### Post by X01 on 2013-01-25
> **Thee said:**
> No problem, hope it works out ;)

Worked out great. :P
Odd thing is if I choose Unbuntu from the Windows 7 boot loader, my monitor switches off for a  few seconds, then back on again, and boots right into Ubuntu.
Not that I'm complaining :KS

---

### Post by Thee on 2013-01-25
lol that is strange, but glad it works :)

---

