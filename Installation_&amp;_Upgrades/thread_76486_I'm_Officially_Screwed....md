---
title: "I'm Officially Screwed..."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Mazza558 on 2005-10-15
Is there any way out of this mess i've put myself in?

I created a partition for Ubuntu 5.10 yesterday so I could dual-boot with XP Home. It went well and I had Ubuntu installed very quickly. For some reason It wouldn't let me increase my resolution to the native one (1280x1024) and It wouldn't detect my wireless card so I attempted to "uninstall" it. Knowing that the MBR was overwritten with GRUB 1.5 I deleted the partition with Ubuntu on it (instead of formatting the partition in the setup). I restarted and got an "Error 22" message on the GRUB loader. Fair enough I thought, so I re-installed Linux and GRUB loader to gain access to XP Home. I was happy then because I could get back on XP again. There was a small problem though. GRUB loader kept loading Ubuntu by default instead of XP, and I wanted XP to be default. I read about the commands to set XP to default but I couldn't do it. So I tried various FDISK bootdisks to try to use the "FDISK /MBR" command. none of them worked.  I burned the same Ubuntu ISO onto the same disk that previously had the FDISK program and the Ubuntu Iso on it before to see If there was any way of fixing the resolution and wireless problem I had in the first place since I couldn't find any feasable way of restoring the MBR (my PC is a HP one so It has a separate partition dedicated to restoring XP on it - no XP Home Setup disks). I used the Ubuntu setup disk again and deleted any partitions that I had created previously so my PC was back to normal. I then tried to install linux AGAIN but this time it said that some files were missing from the CD. I rebooted and I got another "Error 22" message. So my situation now is:

-Can't access XP because Ubuntu isn't installed
-Can't Install Ubuntu because there's something wrong with the CD

:???: :confused: :( 


I've tried various XP boot disks but I'm not sure if the boot.ini on the boot disk is right:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect

When I try that It just goes onto a blank screen with a flashing _ on it. 

I'm currently downloading Ubuntu again so I can try again with a different CD.
Any help would be greatly appreciated, and sorrry for the wall of text ;)

---

### Post by Mazza558 on 2005-10-15
I managed to re-install Ubuntu and the GRUB loader but It now comes down to:

How do I set XP as the default OS?

---

### Post by codejunkie on 2005-10-15
[quote=Mazza558]Is there any way out of this mess i've put myself in?

I created a partition for Ubuntu 5.10 yesterday so I could dual-boot with XP Home. It went well and I had Ubuntu installed very quickly. For some reason It wouldn't let me increase my resolution to the native one (1280x1024) and It wouldn't detect my wireless card so I attempted to "uninstall" it. Knowing that the MBR was overwritten with GRUB 1.5 I deleted the partition with Ubuntu on it (instead of formatting the partition in the setup). I restarted and got an "Error 22" message on the GRUB loader. Fair enough I thought, so I re-installed Linux and GRUB loader to gain access to XP Home. I was happy then because I could get back on XP again. There was a small problem though. GRUB loader kept loading Ubuntu by default instead of XP, and I wanted XP to be default. I read about the commands to set XP to default but I couldn't do it. So I tried various FDISK bootdisks to try to use the "FDISK /MBR" command. none of them worked. I burned the same Ubuntu ISO onto the same disk that previously had the FDISK program and the Ubuntu Iso on it before to see If there was any way of fixing the resolution and wireless problem I had in the first place since I couldn't find any feasable way of restoring the MBR (my PC is a HP one so It has a separate partition dedicated to restoring XP on it - no XP Home Setup disks). I used the Ubuntu setup disk again and deleted any partitions that I had created previously so my PC was back to normal. I then tried to install linux AGAIN but this time it said that some files were missing from the CD. I rebooted and I got another "Error 22" message. So my situation now is:

-Can't access XP because Ubuntu isn't installed
-Can't Install Ubuntu because there's something wrong with the CD

:???: :confused: :( 


I've tried various XP boot disks but I'm not sure if the boot.ini on the boot disk is right:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect

When I try that It just goes onto a blank screen with a flashing _ on it. 

I'm currently downloading Ubuntu again so I can try again with a different CD.
Any help would be greatly appreciated, and sorrry for the wall of text ;)[/quote] if you have your windows xp cd you can put that in and choose recovery console from there type fixmbr and that will restore the windows xp boot loader. if you don't have the windows xp cd, because most pc manufactures seem to cut cost's by not providing reinstall cd's, you still have a couple of other choices. if you have a windows 98 boot floppy you can put that boot to dos and do ```
fdisk /mbr
``` or you could have a look at ultimatebootcd at [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/") it has tools for restoring the mbr. i also found a windows xp boot floppy set here at [http://support.microsoft.com/?kbid=310994]("http://support.microsoft.com/?kbid=310994") i haven't tested it myself so i have no idea if it has the tools to restore the mbr or not but it might not hurt to look at just in case.

---

### Post by codejunkie on 2005-10-15
[quote=Mazza558]I managed to re-install Ubuntu and the GRUB loader but It now comes down to:

How do I set XP as the default OS?[/quote] [http://ubuntuguide.org/#changedefaultosgrub]("http://ubuntuguide.org/#changedefaultosgrub") this guide shows how to choose a different os in grub.
edit: i just tried that in breezy and it dosen't seem to be working sorry about that i've been known to mess up every once in a while ;)

---

### Post by SilentCacophony on 2005-10-15
> [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub) this guide shows how to choose a different os in grub.
edit: i just tried that in breezy and it dosen't seem to be working sorry about that i've been known to mess up every once in a while 

I looked at that link, and haven't got any idea how or why putting *X_sequence* in the default line would work.

There are a couple of other ways to set the default. The easiest for me is as in the above guide, but chage it to the *number* of the choice you want, counting the selctable entries from zero.

---

### Post by Lord Illidan on 2005-10-15
[QUOTE=SilentCacophony]I looked at that link, and haven't got any idea how or why putting *X_sequence* in the default line would work.

There are a couple of other ways to set the default. The easiest for me is as in the above guide, but chage it to the *number* of the choice you want, counting the selctable entries from zero.[/QUOTE]

Indeed, for example...I have:

1. Ubuntu 686
2. Ubuntu Failsafe
3. Memtest
4. Other OSes - separator
5. Windows Xp

Therefore, I would do the default 5. No problem there..

---

### Post by codejunkie on 2005-10-15
[quote=SilentCacophony]I looked at that link, and haven't got any idea how or why putting *X_sequence* in the default line would work.

There are a couple of other ways to set the default. The easiest for me is as in the above guide, but chage it to the *number* of the choice you want, counting the selctable entries from zero.[/quote]
after looking at that a little closer i think that might have been what he ment, it's a little confusing the way it's worded, he could have said change it to the menu item number of your choice with the first entry being counted as zero that would have been easier for me to understand thanks for the help that was confusing me a little.

---

### Post by llamakc on 2005-10-15
[quote=Lord Illidan]Indeed, for example...I have:

1. Ubuntu 686
2. Ubuntu Failsafe
3. Memtest
4. Other OSes - separator
5. Windows Xp

Therefore, I would do the default 5. No problem there..[/quote]

In the example above you would put 4 as the default in menu.lst because Grub starts counting from 0.

---

