---
title: "Bootloader install (SDD, HDD, oh my)"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by Toupee on 2012-08-11
Hi all,

I've decided to get back into the linux scene what with valve's recent developments and my building a newer i5 rig.

I currently have win7 installed on a 90gb SSD.  It's not going away and I need to continue using it for video editing and such.

I'm putting ubuntu on a brand new 2TB hard drive.  Right now I have a 200gb partition and a swap partition and ... I recieve an error about the bootloader.

After a little investigation, I *THINK* my bootloader is located on the SSD on a 100mb partition that's flagged 'boot' according to gparted.  There's also another partition on another HDD that has a boot flag, which contains the win8 dev preview, but I don't think that one's actually the active boot, because I see a black-and-white text bootloader typically, not the graphical win8 one.

So what do I need to do to enable booting of win7 and ubuntu (bare miniumum)?  Is this an EFI setup or a traditional BIOS one?  How can I give more information?

Thanks for all help.  It means a lot!

---

### Post by drs305 on 2012-08-11
It sounds like EFI to me, especially since you mention a non-traditional boot menu and a small partition at the start of the disk. 

To install Ubuntu on an EFI system you need to boot the LiveCD from the EFI menu I believe. I have no experience with EFI but if you can boot the LiveCD and install Boot Repair it will either be able to sort things out or at least let you run the boot info script. The script results can help those familiar with EFI or GPT help you figure things out.

There is a link to Boot Repair in my signature line.

Note: It would be helpful to know what release you are trying to install - I doubt it's the Fiesty Fawn one listed in your profile. You said you were gone from Linux for a while, so welcome back!  ;-)

---

### Post by Toupee on 2012-08-11
Thanks :)  It's 12.04, not Feisty.

Okay, that's good to know it looks like EFI.  I was thinking the same thing.

I'll try using the automatic function of the Boot Repair (thanks!) I have been rummaging thru Rod Smith's tutorials, but frustration is setting in.

I think ultimately I might like to have ReFind installed, but we shall see how this works.

Totally loving all the new features, too.  Unity is really far better from its earlier versions.

---

### Post by Toupee on 2012-08-11
Boot Repair returns this message:

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Info: [http://paste.ubuntu.com/1142155/](http://paste.ubuntu.com/1142155/)

---

### Post by drs305 on 2012-08-11
> **Toupee said:**
> Boot Repair returns this message:

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Info: [http://paste.ubuntu.com/1142155/](http://paste.ubuntu.com/1142155/)

For GPT, you must have a bios_grub partition. It can be very small, as the message states, and you don't have to format it. Unlike an EFI partition, it can be located anywhere on the drive.

Since Boot Repair seems to know what's going on, hopefully after you create the partition it will be able to set things up for you if your Ubuntu doesn't have to be reinstalled.

(GPT is another aspect of booting with which I have no experience. You can search for posts by forum member *oldfred*, who has a lot of good links on the subject.

---

### Post by Toupee on 2012-08-11
Thank you for the leads.  You are a magician and a scholar, good sir!

---

### Post by Toupee on 2012-08-12
Well, to archive my reply...

Ultimately, I had zero luck in bootloading to my HDD.  I guess this EFI stuff is just way above me.  I eventually did create the bios_grub partition and ubuntu installed without complaint, but when I restarted, the only thing that showed up was the Windows bootloader.

I tried GAG and rEFInd, but GAG only recognized the items from the Windows MBR (I guess?) and I didn't understand the latter at all.

So instead I used wubi and everything installed in a CINCH.  Damn.  There goes six hours :)

I just hope that Ubuntu does OK with only 13 gigs and Windows doesn't need much more because there ain't much left on my SSD. :) Sure is fast as hell though!

---

### Post by darkod on 2012-08-12
Your assumption about EFI was wrong from the start. The 100MB partition of win7 is created in non-EFI boot also. It's created every time when you use the win7 installer to create the ntfs partitions. In that case, it also creates the small 100MB for the boot files.

When you say you created the bios_grub partition and it installed OK, but on reboot you only got the windows bootloader, that's perfectly normal if you are booting from a wrong disk. Don't forget, you have 4 disks and unless you tell your computer which disk you want to boot first, how should it know?

You only needed to change the disk boot order in BIOS and it would have been fine.

You can keep using wubi but personally I would avoid it. It's not a real dual boot, it's like a virtual ubuntu inside windows. And sometimes updates or an upgrade can break it, because it's not the same like working from a separate partition. Wubi is just a quick try, not a long term install.

---

### Post by oldfred on 2012-08-12
With multiple drives, multiple installs and the possibility of booting from different drives with either BIOS or UEFI,  you need to document drives with BootInfo or BootInfo script. Post link from report Boot Repair creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

