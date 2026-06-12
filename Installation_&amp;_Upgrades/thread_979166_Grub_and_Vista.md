---
title: "Grub and Vista"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Palmada on 2008-11-11
Hello everyone. My problem is somewhat different from other grub and vista issues I've found. I've tried searching the forums and google, but found nothing similar (it could simply be due to lack of wasting enough hours...).

I have a problem with a shy GRUB. I have an ASUS X53 laptop that runs the Kubuntu 8.10 amd64 live cd with almost no problems.

I had Vista, and I want to transition to Kubuntu. So I tried dual-booting. But after a successful install, I reboot and it goes back to Vista without giving me a boot choice. I've then formated the Vista partition (not much love for it), reinstalled Kubuntu and now it simply asks for a boot device. It would appear that GRUB isn't locating itself on the MBR...

I'm fairly new at this whole Linux world... 

Can anyone help with an insight? Any help whatsoever is appreciated.

---

### Post by Dazed_75 on 2008-11-11
I am a bit puzzled by your description.  It says you formatted the Vista partition and THEN installed Kubuntu.  It does not say anything about your partition/formatting choices during the install (such as manual, guided using the entire disk, guided - resizing ...).  So it is hard to say what transpired.  There really was no need to first format the Vista partition.

That said, it is also true that Vista uses a different MBR (Master Boot Record) which refers to a boot program in Vista.  If you formatted the partition (which does nothing to the MBR) in a way that that the setup for grub would see that file not existing, it is not clear what would happen.

Finally, since you have wiped Vista anyway, try loading the live CD and doing a scratch Kubuntu install and selecting the option to use the entire disk.

---

### Post by caljohnsmith on 2008-11-11
How about booting your Live CD, open a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
That will help clarify what your current HDD setup is, and also whether Grub is properly installed to the MBR (Master Boot Record).

---

### Post by Palmada on 2008-11-12
Hello to the both of you.

Sorry about not informing you of those details, they slipped my mind.

I formatted everything manually; I don't have my laptop with me right now to type in those commands, but I'll resume what I've been doing:

I first had an NTFS vista partition, followed by what I formatted as an EXT3 partition for the Kubuntu installation and finally another NTFS partition (with all sorts of data I didn't want to wipe).

I got mad at Vista and didn't really want to keep it (it's a memory hog), so I formatted so as to make the two 1st partitions into a single EXT3 partition followed by the data NTFS partition.

I know formatting doesn't do anything to the MBR, but I always kept the option to write GRUB to the MBR (in the advanced settings at the end of the installation), so, in (my) theory, GRUB should replace what Windows placed there. If you say that Vista uses a different site on the MBR, then doesn't that mean I have to wipe the whole MBR and install GRUB? (A prospect that scares me a bit...)

Finally I don't want to use the whole disk since I want to keep that data NTFS partition (I'd move the contents to an external HDD, but the live cd has been having problems reading that partition).

When I get home today I'll post the output of those commands, caljohnsmith.

And thanks for the replies.

---

### Post by caljohnsmith on 2008-11-12
> **Palmada said:**
> 
I know formatting doesn't do anything to the MBR, but I always kept the option to write GRUB to the MBR (in the advanced settings at the end of the installation), so, in (my) theory, GRUB should replace what Windows placed there. If you say that Vista uses a different site on the MBR, then doesn't that mean I have to wipe the whole MBR and install GRUB? (A prospect that scares me a bit...)

You are correct; if you click on the "advanced" button in the final stage of the installation, it should show that Grub is being installed to (hd0) or /dev/sda, which is what you want, because then Grub will replace the Windows MBR. In other words, you shouldn't need to do anything to let the Kubuntu installer place Grub in the MBR, since that should be the default.

I suspect your problem might be that since you deleted the Vista partition, and since most likely the Vista partition marked as bootable, your HDD now doesn't have any partitions flagged as bootable; some BIOSes will refuse to boot a drive that doesn't have a partition marked as bootable, and you could get an error similar to what you got (even if Grub is properly installed). If that is your problem, the easy solution is to just mark a partition as bootable. But anyway, when you get the chance to post those commands, we will know for sure whether any of your partitions are marked as bootable. :)

---

### Post by Palmada on 2008-11-12
So, here's the outputs:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    75891059    37945498+  83  Linux
/dev/sda2        75891060    83875364     3992152+   5  Extended
/dev/sda3        83888128   312577581   114344727    7  HPFS/NTFS
/dev/sda5        75891123    83875364     3992121   82  Linux swap / Solaris

> Missing operating system
> ff04

So, I'll assume that you're right and no drive is marked as bootable. I'll retry installing and try to pay more attention to the formatting options.

---

### Post by caljohnsmith on 2008-11-12
Wait! You don't have to reinstall. Just do this from the terminal:
```
sudo fdisk /dev/sda
```
Press "a", then "1" for the partition, the "w" to write the change" and finally "q" to quit.

EDIT: I see that Grub isn't installed correctly either, so if you want to do a reinstall first, that's fine; but you may have to do the above procedure anyway to mark one of your partitions as bootable, because I don't think the Kubuntu installer does it automatically. Let me know how it goes. :)

---

### Post by Palmada on 2008-11-12
Coolness. It's installing as I speak, though, I'll report when it's done.

One thing: I just noticed that on the advanced options the boot loader was being installed to "(hd0)" and I changed it to "/dev/sda1" (the linux partition) just to try it out.

EDIT: I'm starting to think I jump the gun a bit :p

---

### Post by caljohnsmith on 2008-11-12
> **Palmada said:**
> Coolness. It's installing as I speak, though, I'll report when it's done.

One thing: I just noticed that on the advanced options the boot loader was being installed to "(hd0)" and I changed it to "/dev/sda1" (the linux partition) just to try it out.
Since it looks like you have a Windows MBR in sda right now, installing Grub to the boot sector of sda1 will actually work if you flag the sda1 partition as the bootable one. I wouldn't recommend it though, because if you have any problems with Grub, in some cases you won't get any Grub errors to give you a clue what is going on. That would be the main advantage of installing Grub to the MBR, and since Windows is no longer on that HDD, I don't see any reason to keep the Windows MBR; but it's up to you.

---

### Post by Palmada on 2008-11-12
Like I said, it's a bit too late to cry over spilled milk. :p 97% done!

---

### Post by Palmada on 2008-11-12
Huzzah! Success!

Everything is booting fine apparently. I'm posting from the fresh install! Thanks a bunch!

Thanks for your help. I've posted below the output from the terminal again, though, since it would appear something is wrong.

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75891059    37945498+  83  Linux
/dev/sda2        75891060    83875364     3992152+   5  Extended
/dev/sda3        83888128   312577581   114344727    7  HPFS/NTFS
/dev/sda5        75891123    83875364     3992121   82  Linux swap / Solaris
> Missing operating system
> ff04

---

### Post by caljohnsmith on 2008-11-12
Glad it's working. The output of those commands is as expected, since you chose not to install Grub to the MBR. Anyway, have fun with Kubuntu.

---

### Post by Palmada on 2008-11-12
I will. Though I've already managed to crash it lol

---

