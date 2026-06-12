---
title: "Ububtu 12.04 is the main boot instead of windows"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by Mesh F90 on 2012-08-30
hi, I installed Ubuntu 12.04 on my Asus laptop, I used 11.11 for a while so im familiar with Ubuntu.

the issue is the 12.04 is the main boot instead of windows, I didn't have the issue when I had 11.11.

when I recover my windows and finished, on first boot I get Command screen with something like "get" i forgot the word, now im stock with both.

my windows 7 is genuine I dont want to lose it, and Windows recovery doesnt work anymore, when get into it, it gets me out

any help please

---

### Post by mastablasta on 2012-08-30
you should have backed up your recovery on DVD before any dual boot install.
 
ok but what's done is done. first how did you do the dual boot? is it a wubi install or normla side by side?
 
if normal side by side you can change the boot order in grub.
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
 
i don't know how this is done in wubi but you might need to change windows boot loader there. not sure.

---

### Post by Mesh F90 on 2012-08-30
> **mastablasta said:**
> you should have backed up your recovery on DVD before any dual boot install.
 
ok but what's done is done. first how did you do the dual boot? is it a wubi install or normla side by side?
 
if normal side by side you can change the boot order in grub.
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
 
i don't know how this is done in wubi but you might need to change windows boot loader there. not sure.

normal install by cd, then it rebooted and showed side by side installation, where i choose HDD amount for each OS

---

### Post by darkod on 2012-08-30
But what is it that you are actually trying to do? Just change the default OS in the grub menu or completely restore your computer to factory state?

Because the windows recovery would usually restore it to factory state, as you bought it, which means not only ubuntu gets deleted and all data inside, it also deletes all data in your windows and all programs you installed.

So I wonder why would you want to go into it anyway.

---

### Post by Mesh F90 on 2012-08-30
> **darkod said:**
> But what is it that you are actually trying to do? Just change the default OS in the grub menu or completely restore your computer to factory state?

Because the windows recovery would usually restore it to factory state, as you bought it, which means not only ubuntu gets deleted and all data inside, it also deletes all data in your windows and all programs you installed.

So I wonder why would you want to go into it anyway.

i did it and i got getgrub black screen, kind of like DOS command screen

---

### Post by Mark Phelps on 2012-08-30
> **Mesh F90 said:**
> normal install by cd, then it rebooted and showed side by side installation, where i choose HDD amount for each OS

Unfortunately, what you did NOT know is that changing the Win7 OS partition size this way can result in corrupting Win7 -- rendering it unbootable.

If you had the foresight BEFORE you did this, to create and burn a Win7 Repair CD using the Win7 Backup feature, you would then have had a CD you could have used to repair the boot loader -- and be back in business.

As mentioned, doing a full restore basically wipes everything you have done from the drive -- which only should be done as a last resort.  Furthermore, if you resize partitions on the drive, Restore sometimes will NOT work because it either gets confused by the Linux partitions, or the Windows partition is too small.

So basically, if your Restore got far enough to erase the drive, about the only thing you can do now is to try to get it back to its original condition.

So, what is it you really want to do at this time?

---

### Post by darkod on 2012-08-30
I'm not sure the OP is talking about win7 not working, at least not that way. I think he wants to say he started the restore process and even if you cancel it, often it starts touching the boot sector right away and messes up your grub.

To the OP: Is that what happened? You actually srated the windows recovery process and never finished it? Or you did finish it and it still has left overs of grub on the boot sector?

If you did start and finish the recovery process, that has little to do with ubuntu. That process usually should restore your computer to how it came from the factory. Is that what you want? That would also delete all your data.

---

### Post by Mesh F90 on 2012-08-31
> **Mark Phelps said:**
> Unfortunately, what you did NOT know is that changing the Win7 OS partition size this way can result in corrupting Win7 -- rendering it unbootable.

If you had the foresight BEFORE you did this, to create and burn a Win7 Repair CD using the Win7 Backup feature, you would then have had a CD you could have used to repair the boot loader -- and be back in business.

As mentioned, doing a full restore basically wipes everything you have done from the drive -- which only should be done as a last resort.  Furthermore, if you resize partitions on the drive, Restore sometimes will NOT work because it either gets confused by the Linux partitions, or the Windows partition is too small.

So basically, if your Restore got far enough to erase the drive, about the only thing you can do now is to try to get it back to its original condition.

So, what is it you really want to do at this time?


I want to get rid of Ubuntu

---

### Post by Mesh F90 on 2012-08-31
> **darkod said:**
> I'm not sure the OP is talking about win7 not working, at least not that way. I think he wants to say he started the restore process and even if you cancel it, often it starts touching the boot sector right away and messes up your grub.

To the OP: Is that what happened? You actually srated the windows recovery process and never finished it? Or you did finish it and it still has left overs of grub on the boot sector?

If you did start and finish the recovery process, that has little to do with ubuntu. That process usually should restore your computer to how it came from the factory. Is that what you want? That would also delete all your data.

before recovery was working well, but when it is finished, i get black screen with getgrub error, i think it means i still have Ubuntu as a boot loader, to get useing my laptop again i must insert Ubuntu cd again and install it in order to use Win7

---

### Post by darkod on 2012-08-31
> **Mesh F90 said:**
> before recovery was working well, but when it is finished, i get black screen with getgrub error, i think it means i still have Ubuntu as a boot loader, to get useing my laptop again i must insert Ubuntu cd again and install it in order to use Win7

Well, the windows restore process should wipe everything and install the factory default. Including the bootloader. Why that is not working, I have no idea. That would be a better question for a windows forum or your computer manufacturer support.

You can install generic MBR bootloader using the ubuntu live cd. That bootloader acts the same as the windows one. If you want to try that, boot with the ubuntu cd in live mode, open terminal and execute:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

The will be some warnings after the first command I think, just ignore them and continue. It's normal. DO NOT start anything about configuraing lilo. Just ignore what it says about missing a configuration and run those exact commands.

That will install generic MBR that can boot your windows provided the restore process finished correctly. Since it didn't remove grub, I can't really be sure it finished correctly.

---

