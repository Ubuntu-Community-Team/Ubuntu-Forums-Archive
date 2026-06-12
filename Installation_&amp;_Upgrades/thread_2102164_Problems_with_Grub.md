---
title: "Problems with Grub"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by LexZep on 2013-01-06
Hello!

Yesterday i bought a new Laptop with Ubuntu on it(ASUS X55U-SX008D). First i tried to install Windows beside Ubuntu because my father didn't want to learn everything new. The installation didn't work because of EFI - i don't know why :/
So I reinstall Ubuntu and everything worked till today. 

Now i get this error:

error: file ' /boot/grub/x86_64-efi/normal.mod' not found
grub rescue>

I am not able to start the Ubuntu disk and reinstall the OS - i get this info: 
Reboot and select proper boot device or insert boot media in selected boot device


 
I also tried this:

[LIST=1]
[*]Type ls to get a list of partitions
[*]Enter set prefix=(hd0,msdos6)/boot/grub [you will  almost certainly  have to enter a different drive/partition in the  brackets, you may just  have to try all of those listed by ls until you find the one that  works.
[*]Type insmod normal
[*]Type normal and you will get your boot prompt back!
[/LIST]


The system gives respronse:


-> error: disk 'hdo,gpt3' not found
or
-> unknown filesystem




I hope you can help me! 

Alex

---

### Post by darkod on 2013-01-06
First, do you have msdos or gpt table on the disk? And do you boot in uefi or the older legacy mode?

Windows works with uefi only on gpt disks. Ubuntu doesn't care.

But if you are using uefi boot then you need to install both ubuntu and windows in uefi mode. That means booting the ubuntu cd/usb from the uefi device, not the legacy device.

If you are starting from scratch, it better not to use uefi. In that case disable it in bios if there is such option. Select the boot mode as Legacy Only.

Then you can boot the ubuntu cd in live mode, wipe the disk if you don't have any important data on it, and create new blank msdos table.

After that you can start installing, first windows giving it as much space as you want (bot not the whole hdd), and then ubuntu in the rest of the hdd.

---

### Post by LexZep on 2013-01-07
First, thanks for the answer!

Everytime I tried to install Windows(before i installed Ubuntu) - the Windows setup showed something like "Installation not available because the disk is in GPT style." :s

I start the Bios Setup - under "Boot" there is an point called Boot configuration with "Launch PXE OpROM". I can set it from Enabled to disabled. I don't know if there is an option to deactivate Uefi or maybe I just don't find it.


The deactivation/activation of "Launch PXE OpROM" dind't change my problem - I am still not able to boot from the Ubuntu Disk. It still says "Reboot and select proper boot device or insert boot media in selected boot device".

Alex

---

### Post by darkod on 2013-01-07
No, PXE is fot boot over a network.

It seems the machine is not UEFI capable, which is good, no problem.

But it also seems your hdd has GPT table and windows can't work on GPT without uefi. You will have to write new blank msdos table on the disk, which means you will lose all data on it. If there is anything you want to keep, make a backup first.

After you have msdos table on the disk, you can install first windows or ubuntu, which ever you like. People usually install windows first, then ubuntu but it can work the other way too.

---

