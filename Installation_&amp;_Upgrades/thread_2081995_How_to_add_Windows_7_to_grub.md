---
title: "How to add Windows 7 to grub"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by s0ftcorn on 2012-11-08
hello,

i installed Kubuntu on my Lenovo S205, i had another partition with a working Windows 7. But grub did not add Windows 7 to the menu? Is there any possibility i could add it manually?

---

### Post by darkod on 2012-11-08
There is, but if it didn't add it automatically it means it didn't find it, so maybe something went wrong. Maybe the win7 boot files are gone, etc.

In this case it's best to run boot-repair to create the bootinfo summary. Post the link it will give you.

Right now you don't need to run the Recommended Repair, just the option to create the bootinfo so we can see what is where.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by s0ftcorn on 2012-11-08
[http://paste.ubuntu.com/1342931/](http://paste.ubuntu.com/1342931/)

---

### Post by oldfred on 2012-11-08
Is there some reason you have grub legacy?

With grub legacy partitions are numbered differently than grub2. The first partition is hd0,0 in legacy where it is hd0,1 in grub2. Your manual entry may work if you just change it to hd0,0.

But you have your entry inside the automagic area. When you run sudo update-grub, it rewrites everything inside the automagic area. You have to move your Windows boot stanza outside the automagic area. Either before (way up in menu) or after.

With grub legacy it almost never found a Windows 7 install and that is one of the advantages of grub2's os-prober. It finds the Windows 7 boot partition and adds a boot stanza for that.

Better to just uninstall grub and install grub2. Boot repair has that as one of its options to repair your system.

---

### Post by s0ftcorn on 2012-11-08
As i have a Lenovo S205 i need grub legacy, because of all this efi-related stuff. Basically grub2 won't load. With grub legacy booting Kubuntu works just fine. And as far as i have seen it there are no guides  for the Lenovo S205 concerning the install of grub2.

---

### Post by oldfred on 2012-11-08
This was for 11.10 and UEFI.

How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

I would think the improvements in the UEFI install process with 12.04 & 12.10 have made it even easier.

---

### Post by s0ftcorn on 2012-11-08
do i need to reinstall my kubuntu for this to work?

---

### Post by darkod on 2012-11-08
If you insist, you should be able to keep using grub1.

But if you installed it yourself it seems you didn't remove/purge grub2 totally before that, since /boot/grub/grub.cfg it part of grub2. grub1 uses only /boot/grub/menu.lst.

And your question "how to add win7" is little confusing since menu.lst does show entry for win7. If it doesn't work, say that, not asking how to add something that's already there.

As oldfred said, the entry for win7 is inside menu.lst but it's wrong. Instead of rootnoverify (hd0,2) it should be rootnoverify hd(0,0). Edit the file, save it, reboot and see if it can load win7.

If it works, you can also remove /boot/grub/grub.cfg.

---

### Post by s0ftcorn on 2012-11-08
> **darkod said:**
> If you insist, you should be able to keep using grub1.

But if you installed it yourself it seems you didn't remove/purge grub2 totally before that, since /boot/grub/grub.cfg it part of grub2. grub1 uses only /boot/grub/menu.lst.

And your question "how to add win7" is little confusing since menu.lst does show entry for win7. If it doesn't work, say that, not asking how to add something that's already there.

As oldfred said, the entry for win7 is inside menu.lst but it's wrong. Instead of rootnoverify (hd0,2) it should be rootnoverify hd(0,0). Edit the file, save it, reboot and see if it can load win7.

If it works, you can also remove /boot/grub/grub.cfg.

Ah, the entry of Windows 7 was my attempt to add it, which... didnt work. Also changing it to hd(0,0) didnt work.
It would be nice if i could start using grub2 without reinstalling my kubuntu, right now im only using it because its working and i did not get grub2 to work.
Sooo how can i install grub2?

---

### Post by darkod on 2012-11-08
Did you try it with makeactive too? Something like:
```
title Win7
rootnoverify (hd0,0)
makeactive
chainloader +1
```

Purging grub and reinstalling grub2 is very easy when you can boot ubuntu. Test the above first, and if it doesn't work (even if it does) you can decide whether you want to switch to grub2. Note that I can't promise you it will work on your machine, I can't know that. But returning to grub1 from live mode using chroot would be easy too.

---

### Post by s0ftcorn on 2012-11-08
> **darkod said:**
> Did you try it with makeactive too? Something like:
```
title Win7
rootnoverify (hd0,0)
makeactive
chainloader +1
```

Purging grub and reinstalling grub2 is very easy when you can boot ubuntu. Test the above first, and if it doesn't work (even if it does) you can decide whether you want to switch to grub2. Note that I can't promise you it will work on your machine, I can't know that. But returning to grub1 from live mode using chroot would be easy too.

Trying makeactive didnt work too. But when i install grub2 how do i manage the efi stuff? I think i had to install to an special partition or something like that. Is that correct?

---

### Post by darkod on 2012-11-08
Grub2 is not related to EFI boot.

And you are not using EFI boot since you have msdos table on the disk and win7 can't boot in EFI on msdos table, it needs gpt table.

I can't see a reason why grub2 wouldn't work, unless there is some really specific issue with your machine. Also, when reading on the internet don't forget that lots of information is sometimes wrong, even without intention. Someone tried something, did it wrong, and made a blog post how it's impossible to work on that machine.

I can understand if there are issues using EFI dual boot (maybe), but since no one is making you use EFI boot, and you are not using it, I can't see why grub2 can't work.

If you are willing to try, boot your ubuntu and try this:
```
sudo apt-get remove --purge grub grub-common grub-pc
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

That will first remove both grub1 (package name grub) and grub2 (package grub-pc) and their config files. After that it will install grub2 (grub-pc) again and create new config files.

It should detect win7 by default and should make the correct boot menu. You can give it a shot if you want to.

---

### Post by oldfred on 2012-11-08
There are two versions of grub2, grub-pc for BIOS and grub-efi for UEFI systems. You have installed in BIOS mode so you just need to uninstall grub and install grub2. You will still be in BIOS mode. If you want UEFI, it is a total new install as the drive has to have gpt partitioning not MBR as you have.

Boot-Repair has an uninstall/reinstall function. Or you can run these commands.

If you can boot & make sure Internet is working as it has to download new grub-pc:

#purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

Example if is you cannot boot at all and have to chroot, you skip chroot. Should be same as above commands.

kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by s0ftcorn on 2012-11-08
Awwwwww, yeah! Cant remember the last time i was so happy hearing my windows 7 booting :D

I did exactly what darkod said, and as i can read from oldfred's post im in bios mode. Is this fine or has the UEFI-Mode some kind of advantage?

---

### Post by oldfred on 2012-11-08
I would not change. 

UEFI is the new thing, it also has to have the gpt partitioning which is also required for drives over 2TB and suggested for SSDs. 

But BIOS/MBR has worked for years and if it is working for you, then you do not have to change.

---

