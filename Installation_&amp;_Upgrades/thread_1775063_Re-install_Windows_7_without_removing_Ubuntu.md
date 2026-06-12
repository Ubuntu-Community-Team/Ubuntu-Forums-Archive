---
title: "Re-install Windows 7 without removing Ubuntu?"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by a1exander on 2011-06-04
Hi!

Recently when I booted Windows 7, a "check filesystem" thing got up, so I let it do its thing. And now when I start Windows 7 my computer reboots right after "Windows 7" logo pops up.

Is there any way I can re-install/repair my Windows 7 without losing my Ubuntu partition and all my stuff on it?

Veery thankful for a fast reply. :)

---

### Post by cbowman57 on 2011-06-04
> **a1exander said:**
> Hi!

Recently when I booted Windows 7, a "check filesystem" thing got up, so I let it do its thing. And now when I start Windows 7 my computer reboots right after "Windows 7" logo pops up.

Is there any way I can re-install/repair my Windows 7 without losing my Ubuntu partition and all my stuff on it?

Veery thankful for a fast reply. :)

You can restore your grub with the liveCD, but I've found it much similar to use an iso called rescatux.  It's just a google away. :)

---

### Post by a1exander on 2011-06-04
> **cbowman57 said:**
> You can restore your grub with the liveCD, but I've found it much similar to use an iso called rescatux.  It's just a google away. :)

So I CAN reinstall windows 7 on its partition its on now, without affecting Ubuntu? And after that I restore GRUB with its live cd to be able to boot into my old Ubuntu?

---

### Post by cbowman57 on 2011-06-04
The simple answer is yes you can. :)

---

### Post by a1exander on 2011-06-04
> **cbowman57 said:**
> The simple answer is yes you can. :)

Can you give me a little guide on how to do that? :D

---

### Post by cbowman57 on 2011-06-04
My guide is to download & create a bootable usb or cd of rescatux.  There are numerous threads on using the livecd to restore grub.  Use the search feature or google "restoring grub from livecd".  It's much easier to use rescatux than it is to use the livecd process, but there are plenty of people willing to walk you through the steps if that is how you want to do it.  I'm on my way to bed. :)

---

### Post by a1exander on 2011-06-04
> **cbowman57 said:**
> My guide is to download & create a bootable usb or cd of rescatux.  There are numerous threads on using the livecd to restore grub.  Use the search feature or google "restoring grub from livecd".  It's much easier to use rescatux than it is to use the livecd process, but there are plenty of people willing to walk you through the steps if that is how you want to do it.  I'm on my way to bed. :)

But I mean, how do I re-install Windows 7 without losing my Ubuntu partition? ^ This is just for restoring Ubuntu bootloader right?

---

### Post by cbowman57 on 2011-06-04
When you install Win7 just don't have it overwrite or format your ubuntu partition. I can't remember at what step Win7 gives you the options about what partition to install to, just make sure you don't use anything like "Use entire disk", or something like that.

---

### Post by YesWeCan on 2011-06-04
> **a1exander said:**
> Is there any way I can re-install/repair my Windows 7 without losing my Ubuntu partition and all my stuff on it?
Not if your Grub MBR is on the same disk as Windows. If you have more than one disk or a USB disk, you can install Grub's MBR to it instead.

When you reinstall Windows or Windows decides to repair its boot process (in order to help you) it will restore its own disks MBR to the standard one, thus eliminating Grub's non-standard MBR. This does nothing to your Ubuntu installation, it just breaks Grub. But if Grub's MBR is on a different disk then Windows will not touch it.

The other thing you can do is to install Grub's MBR to the Ubuntu partition instead of the disk's MBR. Then in Windows install EasyBCD (free) and use it to add Ubuntu to Window's bootloader menu. I have done this and it works fine but is prone to possible future failure because of a detail of the way Grub and the linux filesystem work and the grub-install command refuses to do it unless you choose the --force option.

---

### Post by oldfred on 2011-06-04
Have you tried repairing your windows install? Sometimes chkdsk does not fix everything on one pass. Or other repairs may be needed.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by linuxinstalledfromhdd on 2011-06-04
The best order of operation is to install windows first and then Ubuntu.  It will take care of stuff like this automatically for you. :)

---

