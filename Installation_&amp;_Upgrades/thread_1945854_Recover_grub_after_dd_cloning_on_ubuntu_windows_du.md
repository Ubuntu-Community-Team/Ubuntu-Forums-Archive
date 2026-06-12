---
title: "Recover grub after dd cloning on ubuntu windows dual boot"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by myle00 on 2012-03-23
Hi all,

I'm having issues where I go into an infinite boot loop. Here's some background: I have a dual boot Windows 7 64 bit / ubuntu 64 bit. Recently things went wrong with my laptop and I had to send it in to dell to be fixed. Before sending it to dell, I booted into ubuntu from a live USB and using dd I cloned the hard drive to a second external hard drive (dd if=/dev/sda of=Backup.img). 

Dell replaced the hard drive and mother board among other things. Now, I did the opposite from a live USB: dd if=Backup.img of=/dev/sda. From the ubuntu live USB I can see all the partitions and access all the data both from the Windows and ubuntu partitions. The problem is that I cannot boot into either.

When I start the computer, as soon as it's passed the dell logo and tries to boot it shuts down again and starts again. When I hold down the shift key during the boot, all I see is the words grub boot or similar and then it shuts down and goes through the loop. 

I went through the boot-repair process but it didn't make any difference. Here's the paste bin output: [http://paste.ubuntu.com/897116/](http://paste.ubuntu.com/897116/)   I think something most have gotten corrupt when the computer got fried before I sent it in. But since I can access the files from the live USB shouldn't I be able to fix it?

Thanks in advance for any help,
M.

---

### Post by darkod on 2012-03-23
I see the usb stick has EFI boot files on it. But the hdd has no EFI files. Are you using BIOS boot or EFI boot?

Also, make sure you set the sata mode in BIOS to the same value as before. If it was AHCI, set it to AHCI again, or IDE. Win7 can't boot if you change the sata mode.

Reinstall grub2 from live mode in any case, did you try that?

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by myle00 on 2012-03-23
> **darkod said:**
> I see the usb stick has EFI boot files on it. But the hdd has no EFI files. Are you using BIOS boot or EFI boot?
I don't really know what you're talking about since I'm a Linux newbie (although I guess booting is not specific to Linux ;) ), but I downloaded the live USB recently while the ubuntu install on the hard drive was installed a while back.

> **darkod said:**
> Reinstall grub2 from live mode in any case, did you try that?

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

This fixed it! Thank you very much. It's embarrassing, but in the Boot-repair utility I saw the reinstall GRUB box checked so I assumed that it already tried that. I wonder now what the difference is and why the Boot-repair utility wasn't able to fix it?

Thanks again,
M

---

