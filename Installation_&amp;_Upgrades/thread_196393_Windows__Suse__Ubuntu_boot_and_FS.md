---
title: "Windows / Suse / Ubuntu boot and FS?"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by bazzer on 2006-06-14
Hi All

I'm in the process of making my ultimate home PC, one that boots to XP, Suse and Ubuntu. I understand the basics of the install I think - Install XP first, then Ubuntu, then Suse and let Suse's boot loader take care of the selection between OSs.

I've got a 200GB drive (new, bought for this!) and a 40GB drive I am going to install in the PC. The PC currently has a 20GB and the 40GB drive, with all my 'My Docs' and my MP3s on the larger one, just in case Windows dies.

I Understand the way Linux installs this way, so that your data is protected if the OS goes screwy, so that's all good...

I don't fully understand the partitioning but though, and I have a couple of questions.

1 - What do I format the drives as? I want to be able to access my files and MP3s from either OS. I've heard good and bad things about FAT32, and how large drives can sometimes fragment a lot. Would my 200GB drive work ok like this? I'm not really happy with using ext3 under XP as I've ready more bad news about this!

2 - I've tried to dual boot Suse and Dapper Drake Ubuntu, but I believe Suse destroyed the Ubuntu install - This makes me a little suspicious! - hence is there a crash course on partitioning that I can read up on before tonight (!) when I'll begin?

TIA
Bazzer

---

### Post by ajgreeny on 2006-06-14
You could format a partition as fat32 which you then use for all your own files, eg word processor docs, spreadsheets, jpeg's etc etc, in fact all the stuff that would go into My Docs in windows, or home in linux distro's.  In theory you could share this between all your systems without too many problems.

If you share your linux distro's home partition there can, I believe, be problems over different versions of the same linux programs or packages, as the configuration of lots of these progs is stored as hidden files in your home folder, which, incidentally, I always find it helpful to show in my file manager, both in linux and windows.

Like you I've triple booted for some time with (K)ubuntu as my main system, together with WinXP, and at the moment a second install of Dapper which I use as a testbed for all sorts of things which may break the setup.  I play around on that without worrying and can do whatever I like with no danger of causing any problems to anything that is important.

I have in the past, however, had Suse10, Mepis, Fedora Core5, and Mandriva on this machine without too many difficulties.  I always keep a copy of the entries for the ubuntu grub before installing these distro's as I have found like you that most of them seem to ignore my ubuntu system when producing their own grub menus.  After booting into the new distro, I add ubuntu's grub entry to the new grub menu, and so far at least I have always been able to get back to ubuntu without difficulty.  It would be great if all distro's found other linux already installed as well as ubuntu does, then you wouldn't have to fuss about like this to get back to ubuntu.

In answer to your Q1, I would personally use ext3 for the linux partitions.  I have found it quicker than reiser, though my only experience of that was in Suse10, which I couldn't get on with - Yast seemed so laborious and slow compared to apt-get for program installation.

For Q2, I'm afraid I don't know of anything but I think there must be something in the ubuntu wiki's.  Have a look there and see what you can find.

I'll bet you keep coming back to ubuntu, though!

---

### Post by bazzer on 2006-06-14
Ah, I think it becomes a little clearer with Google and about a million linux forums! I think I'll do as you said and use ext3 for the linux system partitions, and maybe ext3 or more likely ntfs for all my data.

I'll HAVE to come back to Ubuntu, as my new employer (2 and a half weeks away) use it as their front end desktop! I'm pretty happy with most aspects of Suse, but I come from a Windose background so it's a little shaky for me!

---

### Post by ajgreeny on 2006-06-14
_DO NOT_ use ntfs for all your data files as you will not be able to write to this partition, not safely anyway, from linux.  This is why I suggested using a fat32 partition which linux can both read and write to.

---

### Post by bazzer on 2006-06-14
[QUOTE=ajgreeny]_DO NOT_ use ntfs for all your data files as you will not be able to write to this partition, not safely anyway, from linux.  This is why I suggested using a fat32 partition which linux can both read and write to.[/QUOTE]

Ah, yes... Noted that one! Trouble with FAT32 jobbers is that they can't really be any bigger than about 32Gigs. I've got about that much in MP3s already, and I'm buying more CDs every day! I didn;t want to have to split them up you see....

---

