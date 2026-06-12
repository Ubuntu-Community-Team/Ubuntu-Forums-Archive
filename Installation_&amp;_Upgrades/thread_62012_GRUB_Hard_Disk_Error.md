---
title: "GRUB Hard Disk Error"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by katiad on 2005-09-03
Hi everyone. Loading Ubuntu onto my brother's computer and... running into problems. Was trying to dual boot with a fresh install of XP Pro. Right after installation, when the computer rebooted, got this error:

GRUB Hard Disk Error

Did a little research, tried to troubleshoot, to no avail. Ended up deleting everything altogether after quite some time. Now reinstalling XP again... and wish to try to avoid getting this error a second time.

What's the best/easiest way to boot up Ubuntu without GRUB? And why would this error have shown itself? I set the BIOS settings to LBA or Large instead of Auto - no luck there... Ideas on what I can do?

I have Partition Magic - I've heard that's got a boot loader - could I use that? And if so - how and when? :)

Thanks for your ideas!

---

### Post by skoal on 2005-09-03
My suggestion?  

Well, for one, I had no problem installing Ubuntu on the same drive as windows (hda1 = ntfs (5GB), hda2 = /boot, hda3 = swap, hda4 = /, 5 GB or remaining space).  What does your partitioning scheme look like?  There are some threads in these forums which make suggestions for a dual boot with Windows.

Did grub return an error # with that message?  That would help diagnose your problem.  

Also, stay away from Partition Magic while installing any linux distro alongside Windows.  Let grub take care of it for you.  Partition Magic has some funky logical partition requirements, making it impractical to boot if you have, for example, (hda1 - windows, hda(2-4) - linux, hda5 - ntfs, fat32 (logical drives), etc).  You will get a partition magic boot error which is quite unrecovable and not supported (even at present) with the latest version from Powerquest.

\\//_

---

### Post by chippy57 on 2005-09-03
[QUOTE=katiad]Hi everyone. Loading Ubuntu onto my brother's computer and... running into problems. Was trying to dual boot with a fresh install of XP Pro. Right after installation, when the computer rebooted, got this error:

GRUB Hard Disk Error

Did a little research, tried to troubleshoot, to no avail. Ended up deleting everything altogether after quite some time. Now reinstalling XP again... and wish to try to avoid getting this error a second time.

What's the best/easiest way to boot up Ubuntu without GRUB? And why would this error have shown itself? I set the BIOS settings to LBA or Large instead of Auto - no luck there... Ideas on what I can do?

I have Partition Magic - I've heard that's got a boot loader - could I use that? And if so - how and when? :)

Thanks for your ideas![/QUOTE]

Do as Skoal says and keep well away from BootMagic.it creates a heap of probs I found it easier to install xp first then ubuntu and just let grub do its stuff and write to the mbr, initially ubuntu was the primary boot OS but after trawling the threads here I found out how to get XP to boot after the timeout which I ajusted to 5 secs....now everything is hunky dory.

good luck

chips

---

### Post by katiad on 2005-09-04
Well, I didn't use either partiion magic or its boot loader. Partition scheme was pretty standard - shared on the same drive, windows hda1, linux hda2, swap space. Nothing elaborate. I've never had any problems installing dual boot, either - except this time.

Reinstalled/rebooted several times. Nothing different. No error #'s - just the standard startup messages, and then "GRUB Hard Disk Error" where it should've actually booted.

---

### Post by essexman on 2005-09-04
[QUOTE=katiad]Well, I didn't use either partiion magic or its boot loader. Partition scheme was pretty standard - shared on the same drive, windows hda1, linux hda2, swap space. Nothing elaborate. I've never had any problems installing dual boot, either - except this time.

Reinstalled/rebooted several times. Nothing different. No error #'s - just the standard startup messages, and then "GRUB Hard Disk Error" where it should've actually booted.[/QUOTE]
You sound as if you are quite expierienced with Linux?

As you are probably aware (seeing that you have already tried tweeking your BIOS settings) > GRUB Hard Disk Error is a serious stage 1 error, and usually indicates a BIOS problem. You may have already tried re-scanning the drive via BIOS, if not, worth trying. 

Otherwise, I am looking at what you have already done and wonder if it is time to get physical? Maybe unplug your drive, boot, reboot and switch off, plug the drive back in and reboot.  This will give the BIOS a chance to resan the drive, this way you can be sure.

Some people have fixed the problem by installing LILO instead.  i would recommend keep trying with GRUB for a bit as it has been a life (computer) saver for me on many occasions.

---

### Post by katiad on 2005-09-05
[QUOTE=essexman]You sound as if you are quite expierienced with Linux?[/QUOTE]

Only experienced enough to sound intelligent. *lol* My main box is still XP simply because... I've never had any problems with it. *lol* So while I adore Linux for a great many reasons, and I've installed various distros quite a few times and mucked around, I just haven't made a big switch, and thus, I'm not *near* as experienced as I'd like to be. Ubuntu is, however, making me rethink things a bit. I'm *very* impressed with this distro.

[QUOTE=essexman]
As you are probably aware (seeing that you have already tried tweeking your BIOS settings)  is a serious stage 1 error, and usually indicates a BIOS problem. You may have already tried re-scanning the drive via BIOS, if not, worth trying. 

Otherwise, I am looking at what you have already done and wonder if it is time to get physical? Maybe unplug your drive, boot, reboot and switch off, plug the drive back in and reboot.  This will give the BIOS a chance to resan the drive, this way you can be sure.
[/QUOTE]

Could be. I'll give it a shot tomorrow, with any luck. :) (at work right now)

[QUOTE=essexman]
Some people have fixed the problem by installing LILO instead.  i would recommend keep trying with GRUB for a bit as it has been a life (computer) saver for me on many occasions.[/QUOTE]

Right.... Not really sure how I'd go about doing that if I can't access the computer, though.... LiveCD?

---

### Post by skoal on 2005-09-06
[QUOTE=katiad]Well, I didn't use either partiion magic or its boot loader. Partition scheme was pretty standard [..][/QUOTE]
Katiad, I think in your case, there are two things causing this problem:

1. Motherboard BIOS (as suggested by essexman) has problems with your disk geometry.

2. Possible partitioning scheme (in lieu of 1).

(Possible sol'n, listed in order of easiest implementation):

1. Change the hard disk setting in BIOS to LBA (instead of auto), or just enter the exact drive geometry settings (provided by your manufacturer).

2. Update BIOS with a newer revision, if possible.

3. Install XP first as before and then Ubuntu.  However, use the following partitioning scheme:

partition - size (filesystem):

XP - ~7GB (NTFS)
/boot - 128MB (?)
swap - ? (?)
/ - ? (?)
/shared, /data, or whatever - rest of disk (fat32)

In other words, include the /boot partition and try to create it under the 8GB threshold (problems with some BIOS's, but _older_ ones at that).  That would probably require having your XP partition as only ~7GB.  Well, then you could tack on a /shared, /data, or whatever partition after the /, make it the remaining drive space, and format it as FAT32.  You'll be able to share that folder in both XP and Ubuntu easily that way.

\\//_

---

### Post by essexman on 2005-09-06
[QUOTE=skoal]Katiad, I think in your case, there are two things causing this problem:

1. Motherboard BIOS (as suggested by essexman) has problems with your disk geometry.

2. Possible partitioning scheme (in lieu of 1).

(Possible sol'n, listed in order of easiest implementation):

1. Change the hard disk setting in BIOS to LBA (instead of auto), or just enter the exact drive geometry settings (provided by your manufacturer).

2. Update BIOS with a newer revision, if possible.

3. Install XP first as before and then Ubuntu.  However, use the following partitioning scheme:

partition - size (filesystem):

XP - ~7GB (NTFS)
/boot - 128MB (?)
swap - ? (?)
/ - ? (?)
/shared, /data, or whatever - rest of disk (fat32)

In other words, include the /boot partition and try to create it under the 8GB threshold (problems with some BIOS's, but _older_ ones at that).  That would probably require having your XP partition as only ~7GB.  Well, then you could tack on a /shared, /data, or whatever partition after the /, make it the remaining drive space, and format it as FAT32.  You'll be able to share that folder in both XP and Ubuntu easily that way.

\\//_[/QUOTE]
 The thing that concerns me most is that there seem to be a few forum posts from users who have had this problem with an Ubuntu installation, but not the same problem with othe Distros such as Suse.

I don't know enough about Ubuntu to understand how this can be.

I have noticed that the most recent release of Breezy refers to > [http://www.ubuntuforums.org/showthread.php?t=62576](http://www.ubuntuforums.org/showthread.php?t=62576)> GRUB tries harder to boot even when the BIOS fails to pass a boot
drive (#13511
Does this mean that the problem is a Horey problem?

---

