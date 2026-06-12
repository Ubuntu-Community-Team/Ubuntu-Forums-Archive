---
title: "Newbie Grub/MBR problems"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Supersuggan on 2006-08-29
Hello,
Let me first say that I am completely new to Linux and Ubuntu. Yesterday I finally decided to try to install Ubuntu as a dual boot with my existing WinXP.

I have to HDD:s: 1 (40Gb With Windows), 2 (200 Gb for Data).
I repartitioned the drives in Partition Magic as follows:

Drive 1: Partition 1 = Windows XP
         Partition 2 (1 Gb) = for Ubuntu Swap (figured it gives better performance to keep swap on a separate (physical) disk (at least it does i Win as I am informed)

Drive 2: Partition 1 = Data (NTFS)
         Partition 2 = Ubuntu (ext3)

I ran the Live CD, and reformatted the swap and Ubuntu partitions there. I choose to Mount Swap on HD1:2, and / on HD 2:2, then installed.

When I rebooted I encountered a problem that I understand others have seen:

My machine stopped at something like (didn't write it down):
"Grub stage 1.5 
Grub error 5"

A couple of reboots gave the same, but once it also somehow managed to get a "grub error 22" (don't rememeber what I was trying).

And that's it. 

Google let me know that Grub error 5 has something to do with damaged MBR, so I had to overwrite it using XP install CD and fixmbr.

That erased grub, I believe, and I could once more boot into XP (which wasn't backed up...)

So now I am sitting here in XP again, trying to learn more before about partitions, filesystems and grub before having another go at it.

The strange thing is that the whole 200 Gb disc is now out of reach in XP.
Windows knows it's there, but says (under "volumes" in properties) that it contains only 196 or so Gb of MBR. 
Yeah ringt!
Using GetDataBack I can clearly browse all my files - they are still there! It seems like the MBR got seriously screwed up on 
both my discs by the Ubuntu insallation(-attempt).
So now I wonder what i did wrong, Isn't there any (allmost) foolproof guides to partitioning a dual XP/ubuntu install?
So far Google or what I found in the forums didn't give me any clear advice.

thanx in advance

---

### Post by zxee on 2006-08-29
You don't say what type of drives you have i.e. ide, sata, scsi, ect.
You can use the live/install cd to install grub from. There are other options too like editing the windows bootloader: [http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)
If you have mixed sata/ide disks editing NTLDR might be a better choice.

---

### Post by Supersuggan on 2006-08-29
Sorry, forget to say: they are both IDE.

Also, if anyone has a quick fix for restoring the second (data) drive to a readable state, it would be apreciated!

I Will look at your links and see if they can help me, thanks.

---

### Post by zxee on 2006-08-30
IMO this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) is the best documentation at the forums. It is somewhat hard to find though.
Take a look at partitioning and the install guide for your architecture. Hope that helps.

---

