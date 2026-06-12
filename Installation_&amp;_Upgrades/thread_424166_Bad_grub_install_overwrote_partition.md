---
title: "Bad grub install overwrote partition"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by drippy on 2007-04-26
I recently re-installed Windows, so naturally it overwrote grub.  I was trying to put it back, following a guide I found:

I did:
```

> sudo grub
find /boot/grub/stage1
 (hd0,4)
root (hd0,0)
setup (hd0, 4)

```


This did NOT work.  I tried again, this time using:
  setup(hd0)
which gave me grub back.

However, now I can't access one of my drives.
Under disk manager it says I have:
/dev/hda1 = NTFS (Windows)
/dev/hda2 = NTFS
/dev/hda5 = ext3 (/)
/dev/hda6 = swap
/dev/hda4 = NTFS (inaccessible)

I tried pressing 'enable' but nothing happens.  I'm not sure exactly what happened, however I have lots of data on hda4 and would really hate to lose that partition.  Is there any way to recover it??  Any help appreciated.

---

### Post by zvacet on 2007-04-26
Boot up your Cd and selec**t Recover a broken system**.In the begining it is look like you install it again but you are just going to the partition step.in your uper left corner you will see sign 
**rescue mode**.Then you will be asked to choose your root device.if you make right choice it  will continue with boot.That way you will come to the next window and you will see option **Reinstall GRUB boot loader**.You will be asked where you want to install grub.Type hd0.Grub will be reinstaled and after that choose reboot.Good luck.

---

### Post by drippy on 2007-04-26
I don't think I need to reinstall grub.  Grub works right now and my OS loads.  It's just that for some reason, I can't access one of my partitions on my HD.  Neither Linux nor Windows will recognize that parition as valid.

---

### Post by az on 2007-04-26
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by triwave on 2007-04-26
> **zvacet said:**
> Boot up your Cd and selec**t Recover a broken system**.In the begining it is look like you install it again but you are just going to the partition step.in your uper left corner you will see sign 
**rescue mode**.Then you will be asked to choose your root device.if you make right choice it  will continue with boot.That way you will come to the next window and you will see option **Reinstall GRUB boot loader**.You will be asked where you want to install grub.Type hd0.Grub will be reinstaled and after that choose reboot.Good luck.

I'm trying to figute out how to install GRUB (it seems to not be anywhere on my install). I installed xubuntu 7.04 Fiesty from alternate CD.

I do the restore steps you mention and after selecting the partition to use as root I get a couple options - none of which are installing GRUB. 

1) execute a shell in /dev/hda5
2) execute a shell in the installer environment
3) choose a different root file system
4) reboot

How do I get GRUB on my harddisk from my install?

BTW - the GRUB package is not installed on my machine by default - should it be?

---

### Post by zvacet on 2007-04-27
Yes it should.Sorry for not be helpfull.Try **az** advice.

---

