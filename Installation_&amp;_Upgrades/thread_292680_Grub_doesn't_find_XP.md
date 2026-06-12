---
title: "Grub doesn't find XP"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by gibbylinks on 2006-11-04
I'm having a major headache. I can't get grub to see my Win XP. I've been having major problems since I upgraded to Edgy  using the live cd and it hosed grub.

This morning I booted from the Win XP cd did a FIXMBR, followed by FIXBOOT and re-booted my PC. Windows XP came up fine and ran OK.

I then booted from my alternate Edgy cd and did a rescue system > re-install grub option.

I can now boot into Edgy but grub doesn't see my Win XP !!

I have 3 hard drives

Drive 1 - SATA - BOOT Drive
/dev/sda1  NTFS Win XP Pro (flagged as boot in gparted)
/dev/sda2  Ext3 Edgy (root)
/dev/sda3  SWAP

Drive 2 - SATA
/dev/sdb1 NTFS Music (flagged as boot in gparted)

Drive 3 - IDE
/dev/hdh1 NTFS Docs Etc (flagged as boot in gparted)
/dev/hdh2 VFAT E-Mail (Shared Edgy & XP)

I have grub installed on (hd0), with Edgy on (hd0,1) & XP should be on (hd0,0) but grub just doesn't install an option for it in menu.lst

Does anyone have any ideas pointers ? 

Thanks

---

### Post by dpm on 2006-11-04
This might be an obvious question, but did you try to add the XP entry in **/boot/grub/menu.lst** yourself? I do not know what the rescue option of the alternate edgy livecd does, but I suspect that it might not add it to the menu configuration file.

Also you are saying that you've got grub installed on (**hd0**). That would be /dev/hda, but you have no such device. Your first hard drive is a serial ATA drive, so if I'm not mistaken you've got grub installed on (**[COLOR=Red]s[/COLOR]d0**)

Adding something like this to /boot/grub/menu.lst might work:

```
title        Windows NT/2000/XP (loader)
root        (sd0,0)
savedefault
makeactive
chainloader    +1
```But I think the best thing would be if you can attach the file **/boot/grub/menu.lst** and paste the output of ```
sudo fdisk -l
``` to a new post.

Cheers.

---

### Post by gn2 on 2006-11-04
As you have three hard drives, I would suggest this method: [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

---

### Post by gn2 on 2006-11-04
OOPS! Operator Error !!!

---

### Post by gibbylinks on 2006-11-09
OK, I bottled it. I sorted out my XP and re-installed using the alternate CD and the text installer. :) 

I've never had a problem with GRUB using the text version, and only experienced problems when using the live CD.

I think I'll burn both versions and keep them to hand in future. Anyway thanks for the help, and as I've said in the past I only keep windows because I've paid for some of the software, Tag & Rename, Nero, Xara Xtreme (yes it's a tad annoying that it's now free on Linux) and Oxygen Phone Manager. If I could get EAC and these to run on Linux, windows may well be kissed goodbye !!

Cheers

---

### Post by dpm on 2006-11-09
> **gibbylinks said:**
> Tag & Rename, Nero, Xara Xtreme (yes it's a tad annoying that it's now free on Linux) and Oxygen Phone Manager. If I could get EAC and these to run on Linux, windows may well be kissed goodbye !!

A replacement for Tag & Rename might be EasyTag, available from the repos. It is a bit strange to use the first time, but it is actually very powerful, I just love it.

Nero: there is a commercial version for Linux. If not, you can also try k3b or GnomeBaker (k3b will run also fine on Gnome and it is currently a lot better and more stable IMHO). Both of these two are also in the repos.

About the others I don't know.

And as a last option, there is always wine or crossover office, although I do not know how good is the support for those apps.


Cheers.

---

