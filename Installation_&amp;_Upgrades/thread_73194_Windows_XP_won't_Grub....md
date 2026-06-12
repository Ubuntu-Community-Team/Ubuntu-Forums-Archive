---
title: "Windows XP won't Grub..."
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by Cad-Monkey on 2005-10-08
Hey all,

I have been experimenting a little bit, and it has gotten me into trouble. I am hoping someone on here will be able to help me fix this.

Last night I tried to install Gentoo Linux. After all, a week ago, I had to reformat my hard drive again (it is a new computer, and the university hard drive image has been very uncooperative for me, so I have had chances to try Ubuntu, Red Hat, and this time -without much luck- Gentoo.) Anyhow, I ran fdisk, and tried to make an extended partition with a swap and a root partition in it for Gentoo. When I wrote the changes, I got this error :

The Partition table has been altered!


Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

So I rebooted, thinking that that would prepare my hard drive to write on the new partitions. Well, surely enough, the hard drive simply wouldn't boot anymore. No Windows. Just a blinking underscore. Windows died.

Here is the good news. I installed trusty old Ubuntu Hoary, and was able to get the hard drive to grub. From there, I was able to rescue files from my windows partition and move them to my mac. YAY! I haven't lost any of my work!

But, Windows will not grub. It shows up in Grub, but if you try to load it from grub, it shows you this text :

root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

Screwy, huh?

Does anyone know what is going on here? Can anyone tell me how to get Windows to load properly again? I should mention that this computer is a month old IBM Thinkpad T43p. It would be a nice machine, if I could keep it running properly in windows for more than 2 weeks...

I will be your best friend forever if you can tell me how to get this computer to boot from windows again.

-------------Cad-Monkey

---

### Post by mlomker on 2005-10-08
> I will be your best friend forever if you can tell me how to get this computer to boot from windows again.


The easiest thing would be to boot a WinXP CD into the recovery console and do a **fixmbr**.  Once you get Windows booting then put grub back on.

---

### Post by aysiu on 2005-10-08
[QUOTE=mlomker]The easiest thing would be to boot a WinXP CD into the recovery console and do a **fixmbr**.  Once you get Windows booting then put grub back on.[/QUOTE] Microsoft has [instructions](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp) for how to do this, too.

---

### Post by mlomker on 2005-10-08
> You don't need to boot to Windows in order to save your files.

They already did that according to the post.  They need Windows to boot now.

---

### Post by aysiu on 2005-10-08
[QUOTE=mlomker]They already did that according to the post.  They need Windows to boot now.[/QUOTE] Yeah, I just realized that--so I edited my post accordingly.

---

### Post by Cad-Monkey on 2005-10-08
Hmm,

This looks promising... My computer didn't come with a Windows XP Install cd though. That's one problem. I might be able to get one, however.

So if I understand this correctly, my partition table is damaged, and I need to somehow restore it, without wrecking the partitions in my hard drive... The site you guys showed me gives instructions on using diskprobe to restore from a bootloader backup and a partition table backup. I have never used diskprobe. Does this mean that I can't actually restore my partition table?

Well, the first thing I will try is fixmbr. Thanks a bunch for your helpful responses!

-----------Cad-Monkey

---

### Post by mlomker on 2005-10-08
> So if I understand this correctly, my partition table is damaged, and I need to somehow restore it, without wrecking the partitions in my hard drive... 

We don't know that.  The Microsoft page is just a long explanation of how to get into the recovery console to type 'fixmbr'.  :D 

That will replace grub with the regular Windows boot loader.  If that works then you can put grub back on.  If you can't get into Windows afterward then you have other problems with your XP install...maybe have to run checkdisk or reinstall...who knows at this point.

---

### Post by Cad-Monkey on 2005-10-09
Ok, I've got your answers. I will have to try them as it becomes possible for me to do so.

In the mean time, does anyone know how I can get ahold of a Windows XP installer cd? Can one be burned off the net? I have a valid key on a sticker right on the bottom of my laptop, so I would think it would be legal to take this approach.

And then is there some other way to load a Windows XP Master Boot Record.

I thought I might have access to a commercial disk, but apparently not... and I am just not comfortable with using an iso off the net that has the word "crack" somewhere in the title for an operating system...

Thanks for your help...

----------Cad-Monkey

---

### Post by mlomker on 2005-10-09
> In the mean time, does anyone know how I can get ahold of a Windows XP installer cd?

Undoubtedly, but not from Microsoft.

> And then is there some other way to load a Windows XP Master Boot Record.

Yes, that's what the 'fixmbr' command does.

---

### Post by codejunkie on 2005-10-09
you could download a windows 98 bootfloppy from [www.bootdisk.com](www.bootdisk.com) and do ```
fdisk /mbr
``` or if your computer dosen't have a floppy drive there is the ultimatebootcd at 
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) it has tools for restoring the mbr.

---

### Post by mlomker on 2005-10-09
[QUOTE=codejunkie]you could download a windows 98 bootfloppy from [/QUOTE]

You've tried that to recover a WinXP box?  I always assumed that they were different because Win9x doesn't have a menu.

---

### Post by codejunkie on 2005-10-09
[QUOTE=mlomker]You've tried that to recover a WinXP box?  I always assumed that they were different because Win9x doesn't have a menu.[/QUOTE]
the win 98 boot floppy worked for me i'd assume it would work for them also, but i've learned with linux and pc's in general what works for one might not work for all. that is if there pc has a floppy drive most newer ones don't but if not the ultimatebootcd will and i have also used it on my other computer that dosen't have a floppy.

---

### Post by Cad-Monkey on 2005-10-09
Hey all,

So the problem has more or less been solved. The Ultimate BootCD had a great deal of trouble reading the hard drive, unfortunately.

My school's computer help desk had a copy of WinXP that they lent me. Turns out that fdisk had read my partitions table completely wrong... A restore from a Windows XP install cd cleaned up the bootloader, and the master boot record, and voila, Windows works again, at least as well as it did before (Thank God I didn't have to reinstall all my software). The new partitions table showed only one partition for windows (instead of 3), interestingly enough, and recognized it not as unknown, but as ntfs.

This, unfortunately, deleted Ubuntu... but at least I didn't have to reinstall Windows. I do still have ubuntu on my mac, however, so I'm not completely out of the loop...

Thanks for your all your help. Hopefully my problems will shed light on someone else's troubles sometime.

----------Cad-Monkey

---

