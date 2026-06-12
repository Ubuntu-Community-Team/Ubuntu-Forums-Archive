---
title: "Booting issues"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by kamyl2 on 2017-03-12
Hello,

Ive recently purchased a new laptop with windows 10 preinstalled. Right after getting it I resetted windows, removing all the vendor junkware, And I proceeded to install ubuntu. Now, I have 2 disks, 120GB SSD with Win10 on it, and 1TB HDD, almost empty so far. I wanted to keep windows on SSD and install Ubuntu on HDD. I downloaded Ubuntu, prepared a USB stick and proceeded with installation. It seems to have installed successfully (no error messages), but it just doesn't boot. After restarting, laptop boots windows10 as if nothing was installed. Boot manager has only option to boot windows. I tried to install grub manually via terminal, but it didn't work. Also tried boot-repair, didn't do the trick either. [Pastebin with boot-repair output.]("http://paste2.org/mEw5x4EO") Not sure what else to try. Anybody having any suggestions?

---

### Post by kc1di on 2017-03-12
Hi kamyl2 and welcome to Ubuntu,
this article may be of help to you in sorting it all out. [http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/]("http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/")

---

### Post by RobGoss on 2017-03-12
Hello and welcome, Are you dual booting Windows and Ubuntu?

With the newer machines they are now setup with **UEFI**, being the case when installing Ubuntu alongside Windows there are a few steps to take. Example: If Windows is installed in **UEFI**, then you will need to install Ubuntu in the same way **UEFI**, if you don't you will not be able to see the Grub menu and choose which OS you want to use in fact, you will have to go into the **BIOS** and configure the BIOS each time you want to choose a OS

Oldfred has some great information of UEFI that should help
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2017-03-12
You are showing the very new NVMe drive with Windows.
The newest Ubuntu does work with NVMe drives, but that should be just your Windows drive anyway.
But bootinfoscript which is part of the Boot-Repair report does not parse NVMe mounted drives. So we do not have all the details.
UEFI install even on sdb, puts ubuntu/grub initial boot files in /dev/nvme0n1p1 your ESP - efi system partition.

But I think your real issue is that you have an Acer.

Acer has a unique requirement, that you must set a UEFI supervisory password (never lose that or erase as soon as configured) and enable "trust" on the ubuntu/grub .efi boot files from inside the UEFI. This is actually better than many other systems that we just have to create work arounds for.

Make sure you have newest UEFI from Acer. Some older threads mention their version of UEFI had to be downgraded. But newer threads mention newest UEFI from Acer works.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by kamyl2 on 2017-03-12
@oldfred Oh thank you so much, good sir! Solution from your first link worked like a charm. Altho I have quite a few boot options to choose when I fire up my laptop, windows shows up there three times, not sure if I didn't mess something up when I was trying to solve this issue before. But anyway, it works :D 

Thanks alot guys for fast responses :D

---

### Post by oldfred on 2017-03-12
Glad you got it working.

If you ran Boot-Repair, it creates a new grub file 25_custom with all the .efi files it finds in the ESP.
You may not need all or any of them. It you do not want any of them, just turn off execute bit on that file.

So if you have the 25_custom file.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

