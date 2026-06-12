---
title: "Grub problem: dual boot Win 7 and Ubuntu"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Hafswerk on 2012-02-24
Hello,

I am trying to set up the following:

goal:
I want windows bootloader to handle startup, and have set this up using  EasyBCD. I have added a linux/grub2 option which appears at startup. Win  7 starts properly and works. I want the Ubuntu option to load grub 2  off the ubuntu partition.

SSD, 120GB:
Win boot partition
Windows 7 64bit partition
200Mb ext4 mounted to "/boot" (i installed ubuntu bootloader here)
rest of the drive, Ubuntu 11.10 64bit "/" partition

Second harddrive:

ntfs storage partition
linux swap partition
ext4 partition mounted to /home
another ntfs storage

All partitions are primary. I deleted all partitions and completely reinstalled win 7 before posting here to make sure it's as clean as possible. It did not change the problem. All partitions look fine in windows and through the ubuntu Live environment.

When i boot i see win bootloader correctly with both options. choosing Ubuntu (expected outcome: to be forwarded into grub2) takes me to a Grub4DOS prompt, where i'm stuck.

This same setup has worked before with Mint 12. The same Live USB stick has been used on a laptop without problems.

Any ideas on what to do would be most appreciated.

---

### Post by Mark Phelps on 2012-02-24
This is an Ubuntu forum, not a Windows forum.  Nearly everyone here uses GRUB for booting and few know anything at all about EasyBCD.

Your best bet is to go to the EasyBCD forums at NeoSmart Technologies.  You can post your question there, and the EasyBCD experts there will be able to help you.

---

### Post by Hafswerk on 2012-02-24
> **Mark Phelps said:**
> This is an Ubuntu forum, not a Windows forum.  Nearly everyone here uses GRUB for booting and few know anything at all about EasyBCD.

Your best bet is to go to the EasyBCD forums at NeoSmart Technologies.  You can post your question there, and the EasyBCD experts there will be able to help you.

Thank you for replying. The reason I posted here is that my assumption is that this is a problem witih Grub, not the windows bootloader (easybcd simply edits the windows bootloader) I assume this since evrything works until the point where i'm referred to Grub, when the grub prompt is displayed instead of grub2. I only mentioned the windows install for context, or if i am missing something, since what i want is to run Grub off a partition. Which has worked before I replaced Mint with Ubuntu. All that is different is that i've recreated the same setup that previously worked, only this time with the ubuntu installer instead of the Mint installer.

My apologies if I'm mistaken in believing this is a problem with Grub, and is rather something to do with windows. I will pursue that lead and your link.

//Thanks again

---

### Post by oldfred on 2012-02-24
Since you have two hard drives, you have two MBRs. You can install grub2's boot loader to the MBR of the second drive without modifying anything on that drive. 

I prefer when there are multiple drives to keep each system fully on one drive and have different systems on every drive. Then if one drive fails you can at least boot the other drive.

---

### Post by darkod on 2012-02-24
Just to let you know that you are looking for trouble. Grub2 is too big to fit on the PBR (Partition Boor Record) so part of it is saved on the partition. During updates related to grub the actual location can change and this would break the grub2 boot process until you reinstall it to the PBR again.

But if you insist using a bootloader which doesn't even detect ubuntu by default, the choice is all yours. Personally I can't see the trouble is worth it. Unless you have some special situation that you didn't mention, you just said "I want windows bootloader to handle the startup".

---

### Post by Hafswerk on 2012-02-24
> **oldfred said:**
> Since you have two hard drives, you have two MBRs. You can install grub2's boot loader to the MBR of the second drive without modifying anything on that drive. 

I prefer when there are multiple drives to keep each system fully on one drive and have different systems on every drive. Then if one drive fails you can at least boot the other drive.

I see what you mean, and it certainly makes sense to me. The reason I want both Win and Ubuntu on the same drive is that it's an SSD and so for speed reasons I want all OS and program files to run off of it, while the second drive is a slower HDD that i use for storage and backup.

---

### Post by Hafswerk on 2012-02-24
> **darkod said:**
> Just to let you know that you are looking for trouble. Grub2 is too big to fit on the PBR (Partition Boor Record) so part of it is saved on the partition. During updates related to grub the actual location can change and this would break the grub2 boot process until you reinstall it to the PBR again.

But if you insist using a bootloader which doesn't even detect ubuntu by default, the choice is all yours. Personally I can't see the trouble is worth it. Unless you have some special situation that you didn't mention, you just said "I want windows bootloader to handle the startup".


Thanks for the advice!

I didn't know that there is a difference with the size of the boot record on a partition. I'm new to messing with boot records and dual booting. So apologies if my question seems silly.

I wanted to use windows boot loader to keep Grub from breaking from windows updates bulldozing over it, which is something I've been warned about. If i understand your advice correctly, I'd be better off installing GRUB directly in the MBR of the drive, since keeping it on a partition is an even bigger potential source of trouble?

---

### Post by darkod on 2012-02-24
It definitely is. The old grub1 did fit on a PBR and could have been used chainloaded to windows bootloader without any problem. But with grub2 you do have a problem.

I agree with putting both OSs on a SSD, it makes all the sense. But linux doesn't care where is / and where grub2. I agree with oldfred.

Keep your win bootloader on the SSD, install ubuntu on the SSD but it's grub2 on the HDD (you can do this with the manual partitioning step). Set in BIOS to boot from HDD, problem solved.
If at any time grub2 messes up, change to boot from SSD and you have at least win7 booting fine (not sure if you can add to EasyBCD grub2 that is on MBR of disk2, instead of PBR, try it).

And the only situations that I remember of with grub2 being "chopped off" and broken, was with some HP and Dell machines but maybe a year ago. In the latest machines we haven't seen similar threads.
And if your PC is home made, don't even worry about it. Grub2 on the MBR of the SSD would work fine too.

You have plenty of options, make a choice... :)

---

### Post by roelforg on 2012-02-24
> **Mark Phelps said:**
> This is an Ubuntu forum, not a Windows forum.  Nearly everyone here uses GRUB for booting and few know anything at all about EasyBCD.

Your best bet is to go to the EasyBCD forums at NeoSmart Technologies.  You can post your question there, and the EasyBCD experts there will be able to help you.
Although i use grub on my hd (it works, why change it?), i know how to configure/use the syslinux family of bootloaders.

---

### Post by Mark Phelps on 2012-02-25
> **roelforg said:**
> Although i use grub on my hd (it works, why change it?), i know how to configure/use the syslinux family of bootloaders.

And, what part of the syslinux family of bootloaders is EasyBCD?  I thought it was solely a Windows product ... or at least, that's the impression I got from the NeoSmart forums.

---

### Post by oldfred on 2012-02-25
It is my understanding that syslinux, lilo, MBR and maybe others are just like a Windows boot loader in that BIOS jumps to the MBR and they look for the active or boot flagged partition and jump to that. Each may have slight difference in what they check for but all are limited by size of MBR. For example lilo will boot a logical partition's PBR where Windows will not.

I think EasyBCD either takes over the PBR or just replaces the BCD which Window uses to know what partitions it can boot from.

---

### Post by Hafswerk on 2012-02-26
I've tried putting GRUB in the MBR using Ubuntu installer, and when that didn't work to put it on the windows boot partition. That had no effect either, in both cases windows bootloader is displayed. I read on EasyBCD forums that there was a bug in Ubuntu 10.04 installer that prevented the bootloader to be loaded anywhere but default. It seems to me that this boils down to something similar (though i'm trying to install 11.10). 

I eventually tried installing Mint 12 with the same partition setup, and it worked out of the box. So my conclusion at this point is that this is a bug in the installer for Ubuntu. I'm thinking I'll stick to Mint for the time being and give Precise Pangolin a whirl when it's released to see if the installer is fixed.

Big thanks to all of you for taking the time to help, I learned a lot.

---

### Post by darkod on 2012-02-26
It might sound like a stupid question, but are you taking into account which disk are you booting from?

For example, if you have windows bootloader on the ssd and put grub2 on the hdd as we suggested, if you keep booting from the ssd first windows bootloader will always be the first to boot. And that will boot windows directly.

11.10 has no problems installing grub2 where ever you want. But for greater control you need to use the manual partitioning setup, not the auto methods. I couldn't guarantee where the auto method installs grub2, whether to the same disk or the disk that is first in the boot order.
The only thing slightly changed in 11.10 is that earlier you could select during the installer not to install grub anywhere. Now that option is gone (we'll see if they put it back in 12.04) so you have to select to install it somewhere. Apart from that, it should install successfully to the location you select.

---

