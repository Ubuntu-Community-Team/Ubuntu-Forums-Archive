---
title: "Cannot multiboot Ubuntu10.04 from Windows XP bootloader"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by jokus on 2010-06-01
Hello Folks,

I am trying to install Ubuntu10.04 on my machine which already has on it, Win XP. Lemme lay down the setup of my machine first of all. 

I got a new 320GB HDD of which I have taken 20GB as the primary partition and installed Win XP on it. Took another 220GB as an extended partition for my data storage. Around 63GB was remaining which I left it as unallocated. Decided to try Ubuntu, but preferred to boot it from the windows bootloader. Downloaded and burned the Ubuntu-10.04-desktop-amd64.iso(have a AMD x3 425 machine) and tried an install on 30GB of the 63 left. 

I did not try any partition scheme. I chose the manual partition option, made a 28GB ext4 partition, made it primary, mounted the /,  took another 2GB for the swap and proceeded. Chose advanced option and installed grub on the 28GB(/dev/sda6) and completed the installation. 

Since no grub was installed, Ubuntu was not available. So then, used the bootpart utility to point grub to the windows bootloader, but it did not work, was giving me error when I chose Ubuntu from the bootmenu modified by the bootpart.

So tried booting with the same install cd, chose Live Ubuntu this time and mounted the 28GB, copied the first 512bytes using dd if=/dev/sda6 of=ubuntu bs=512 count=1 to a usb drive. Rebooted into windows and copied the file to C:\ and added it to the boot.ini. Rebooted and tried choosing Ubuntu from the boot menu but it does not work. I get a blank screen with the cursor blinking.

The machine is new and BIOS is LBA enabled by auto. Now what am I doing wrong. How do I go about solving the situation. Could you guys please shed some light over this.

Thanks.

---

### Post by jokus on 2010-06-01
Is Wubi the only way to go about doing this ?

---

### Post by darkod on 2010-06-01
Why are you trying so hard to make the windows bootloader work, when Microsoft hasn't? Just use grub2 on the MBR.
As for wubi, have in mind that wubi is not developed to serve as long term install, just a quick try (which you can also do with the cd in live mode). Sooner or later it will start having issues. Why would you force an OS to be installed inside another OS? Do you have XP installed inside another OS?

Of course, you can do as you wish. Keep ignoring the potential of grub2 and try to make XP bootloader work. Unfortunately I can't help with that because I don't know. I'm not even sure XP bootloader can handle chainloading to grub2.

---

### Post by jokus on 2010-06-01
Thanks for your reply Darko.

But the fact is that the machine is not really mine and hence I would like to keep the XP bootloader intact. At any point I need to uninstall Ubuntu, if grub2 is installed, would it not be a problem ?

---

### Post by darkod on 2010-06-01
> **jokus said:**
> Thanks for your reply Darko.

But the fact is that the machine is not really mine and hence I would like to keep the XP bootloader intact. At any point I need to uninstall Ubuntu, if grub2 is installed, would it not be a problem ?

Depending on the approach. Unfortunately many people simply delete the ubuntu partition first and when they reboot and get grub error and can't boot anything, they complain of course. :)

But if you first restore windows bootloader to the MBR of the disk, later deleting the ubuntu partition is no problem. By the way, you can install generic MBR which can boot windows (as long as the boot flag is set to the correct partition because windows depends on it), even without having XP/Vista/7 install media, if that is your worry.

You can do it using a command from lilo (you will not run lilo as your bootloader). When you have decided you've had enough of ubuntu, boot into ubuntu and do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr (instead of /dev/sda use the correct disk name if different)

Ignore the warnings it will give. That installs generic mbr on /dev/sda. Restart and windows should boot straight. Then just delete the ubuntu partition(s) and use them as ntfs.

---

### Post by kansasnoob on 2010-06-01
> **jokus said:**
> Thanks for your reply Darko.

But the fact is that the machine is not really mine and hence I would like to keep the XP bootloader intact. At any point I need to uninstall Ubuntu, if grub2 is installed, would it not be a problem ?

Don't mess with machines you don't own :P

---

### Post by jokus on 2010-06-01
Yes, infact the issue is with the lack of install media(maybe at the point of time) only by which I can restore the bootloader. That was the reason for me going this way to boot from the Windows bootloader itself. 

So what is this generic bootloader ? Will the above said commands install a actual windows bootloader to the MBR or some other bootloader ? The issue is, should this bootloader does not load windows and am without a windows install media, it would be an issue.

---

### Post by jokus on 2010-06-01
:-) 

Well ... its not like I can't use it, just that I want to keep it intact but I also want Ubuntu for now..!

---

### Post by darkod on 2010-06-01
> **jokus said:**
> Yes, infact the issue is with the lack of install media(maybe at the point of time) only by which I can restore the bootloader. That was the reason for me going this way to boot from the Windows bootloader itself. 

So what is this generic bootloader ? Will the above said commands install a actual windows bootloader to the MBR or some other bootloader ? The issue is, should this bootloader does not load windows and am without a windows install media, it would be an issue.

It definitely works. I call it like that because it's not the windows 'original' bootloader but it does exactly the same job. In fact, unless you run the boot info script for example, which will say "lilo is installed on the MBR of /dev/sda", you won't even notice any difference compared to windows bootloader. It's not like you get a lilo menu, or grub menu.

XP will boot directly, the same as when it's only OS with windows bootloader on the MBR.

---

### Post by oldfred on 2010-06-01
The windows boot loader only look to a primary partition that is active (boot flag in linux) and jumps to the boot sector of that partition. The lilo boot loader does the same thing but will be reported as a lilo boot loader. Many other rescue disks will install windows compatible boot loaders. 

I have to agree with kansasnoob - If you really want linux install it to a external drive or even just a USB flash. You can do a full small install into 4GB if you are careful or if you have an 8GB flash drive you can easily run the full install. You can do the unetbootin install but check on persistence to be able to save any data.

---

### Post by _Mark_ on 2010-06-01
If you need to fix the windows mbr fire up the xp disc and select recovery console and run fixmbr, you can do this if you overwrite the mbr with grub

Also could you not install grub on the partition Ubuntu is installed on and it will find the xp install and add it to grub, not sure if this will work as have never tried it.

You may have to change the ubuntu partition to bootable for this to work, the boot flag can be changed in Gparted

---

### Post by darkod on 2010-06-01
> **_Mark_ said:**
> 
Also could you not install grub on the partition Ubuntu is installed on and it will find the xp install and add it to grub, not sure if this will work as have never tried it.

You may have to change the ubuntu partition to bootable for this to work, the boot flag can be changed in Gparted

That won't really work. Yes, grub2 will find XP and add it to the list. But with grub2 being on a partition, you need a way to get to it. Grub doesn't care about the boot flag, only windows depends on it.

That's what we are discussing. The OP already put grub2 on the ubuntu partition but it can't chainload from the XP bootloader.

---

### Post by _Mark_ on 2010-06-01
> **darkod said:**
> That won't really work. Yes, grub2 will find XP and add it to the list. But with grub2 being on a partition, you need a way to get to it. Grub doesn't care about the boot flag, only windows depends on it.

That's what we are discussing. The OP already put grub2 on the ubuntu partition but it can't chainload from the XP bootloader.

Fair enough, I can't have read the original post correctly then :confused:

I Know the fixmbr works ok from the xp recovery console (as have had to use it many times)so that is an option i guess

---

### Post by jokus on 2010-06-01
Guess I have to stick to the generic loader method to get this working. It was just that I have read this chainloading of grub from windows bootloader somewhere before. Will look into that to see if it is possible and update this.

---

### Post by jokus on 2010-06-01
> **_Mark_ said:**
> Fair enough, I can't have read the original post correctly then :confused:

I Know the fixmbr works ok from the xp recovery console (as have had to use it many times)so that is an option i guess

fixmbr is always an option, fact is I might not get hands on the windows install media at that point of time. So was looking for a workaround.

---

