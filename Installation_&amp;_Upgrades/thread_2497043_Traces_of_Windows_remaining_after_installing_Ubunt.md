---
title: "Traces of Windows remaining after installing Ubuntu"
date: 2024-04-21
forum: Installation &amp; Upgrades
---

### Post by cbiweb on 2024-04-21
[SIZE=3]I did a new install of 22.04 on my Windows 11 laptop.  I did not dual boot, I just installed right over Windows.
But it appears there is still a Windows partition on my machine. You can see the FAT32 partition in the screenshot.

How can I get rid of all traces of Windows? [/SIZE]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293665&stc=1[/IMG][SIZE=3][/SIZE]

---

### Post by jeremy31 on 2024-04-21
If you delete that partition you might not be able to boot.  The Ubuntu installer made that partition and it contains important boot loader files

---

### Post by cbiweb on 2024-04-21
[SIZE=3]> **jeremy31 said:**
> If you delete that partition you might not be able to boot.  The Ubuntu installer made that partition and it contains important boot loader files

But it's FAT32, which is Windows related, or not?
 I can't do without it?

I've reinstalled 5 times because of problems with getting the passphrase to unlock the volume.
Is there an option I'm missing during installation that would get rid of any Windows residue?

Or perhaps this is something Microsoft did with Windows 11 to keep their tentacles in there, lol.
[/SIZE]

---

### Post by yancek on 2024-04-21
That is the EFI partition and in all likelihood was there with your install of windows and Ubuntu simply put its EFI boot files in a separate directory on that partition.  That partition needs to be there to boot.  You can remove the directory for windows from that partition.  Run:  ls /boot/efi/EFI and you should see a directory named Microsoft which you can delete if you don't intend to use windows.  You might do an online search for using UEFI with Ubuntu so you have a basic understanding.

---

### Post by jeremy31 on 2024-04-21
> **cbiweb said:**
> [SIZE=3]

But it's FAT32, which is Windows related, or not?
 I can't do without it?

I've reinstalled 5 times because of problems with getting the passphrase to unlock the volume.
Is there an option I'm missing during installation that would get rid of any Windows residue?[/SIZE]

It is the EFI System Partition and it is required for booting in UEFI no matter what OS you have. 
I am guessing your issue is more related to grub and luks

---

### Post by cbiweb on 2024-04-21
[SIZE=3]> **yancek said:**
> T...Run:  ls /boot/efi/EFI and you should see a directory named Microsoft which you can delete if you don't intend to use windows...

This is what I get when I do that:

[FONT=courier new]BOOT ubuntu[/FONT][/SIZE]

---

### Post by cbiweb on 2024-04-21
> **jeremy31 said:**
> It is the EFI System Partition and it is required for booting in UEFI no matter what OS you have. 
I am guessing your issue is more related to grub and luks

Okay, so what do I do? I'm not knowledgeable enough to know what to do.  I could Google, but I was hoping a support forum would be faster.

I want pure Linux with no traces of Windows.

Do I need to wipe my entire hard drive, and go from there??

---

### Post by coffeecat on 2024-04-21
> **cbiweb said:**
> 
I want pure Linux with no traces of Windows.

Do I need to wipe my entire hard drive, and go from there??

Why? You don't have any "traces of Windows".

Do you have an issue with booting Ubuntu? If not, leave well alone.

---

### Post by cbiweb on 2024-04-21
> **coffeecat said:**
> Why? You don't have any "traces of Windows".

Do you have an issue with booting Ubuntu? If not, leave well alone.

Perhaps I'm still not understanding something....

Is FAT32 not a Windows thing?

Also, when I boot up I get a screen offering a choice to boot Ubuntu or "Advanced options for Ubuntu", as if I'm dual booting - which of course I'm not.

My brother has 22.04 and he doesn't see that. This makes me wonder if there is Windows stuff wandering around.

---

### Post by #&amp;thj^% on 2024-04-21
> **cbiweb said:**
> Perhaps I'm still not understanding something....

Is FAT32 not a Windows thing?


Not Really just a windows thing. :)

Mine has never seen a windows install, and see here:
```
inxi -p | grep efi
  ID-3: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat

```
yancek has explained that to you>>>" That partition needs to be there to boot"
```
ls /boot/efi/EFI
BOOT  ubuntu

```

Nothing to worry about.

---

### Post by coffeecat on 2024-04-21
> **cbiweb said:**
> Perhaps I'm still not understanding something....

Is not FAT32 a Windows thing?

FAT32 is a filesystem developed by Microsoft, but hasn't been used for Windows installations for almost a quarter of a century. Although it has its imitations, fat32 is useful for such things as SD cards, USB pendrives, and - as has already been explained - EFI partitions. Heck - even Apple has been using fat32 for its EFI partitions on its Mac computers for donkeys years, and it would be misguided to think that the EFI partition on an Apple Mac is a "trace of Windows". As it would be just as misguided to think of all the USB pendrives and SD cards as having a "trace of Windows"

I re-iterate: do not delete your EFI partition. If you do, you will have a severe emotional reaction when next you try to boot your machine.

> **cbiweb said:**
> Also, when I boot up I get a screen offering a choice to boot Ubuntu or "Advanced options for Ubuntu", as if I'm dual booting - which of course I'm not.

That's normal - nothing to do with dual booting. The advanced options choice is - well - advanced options for Ubuntu. The hint is in the text. You'll find the opportunity there to boot with the previous kernel and a memtest - at least last time I looked.

> **cbiweb said:**
> My brother has 22.04 and he doesn't see that.

Without more information on his system, I doubt anyone could do more than guess.

> **cbiweb said:**
> This makes me wonder if there is Windows stuff wandering around.

One last comment: the output of the ls command in an earlier post of yours showed only BOOT and ubuntu folders, not the Microsoft folder than yancek thought might have survived. I hate to disappoint you, but even there, there is no trace of Windows that I can see.

---

### Post by cbiweb on 2024-04-21
> **coffeecat said:**
> ...I hate to disappoint you, but even there, there is no trace of Windows that I can see.

That's a good disappointment to have.

Thank you for explaining things more clearly.

---

### Post by MAFoElffen on 2024-04-23
> **cbiweb said:**
> Perhaps I'm still not understanding something....

Is FAT32 not a Windows thing?

Yes. You were not understanding something.

FAT32 is a filesystem. FAT32 filesystem format is widely used for USB drives, flash memory cards and external hard drives for compatibility between all platforms. It is used by UEFI for it's EFI partition... Which a UEFI partition is required to be: 
[LIST]
[*]Formatted as FAT32
[*]Marked with ESP & Bootable flags
[/LIST]
So is it "a Windows thing"? Sort of yes, and no. That filesystem is more a Universal thing, not specifically just Windows.

---

