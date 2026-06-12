---
title: "Windows won't boot in dual boot setup, blining cursor"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by DiGiTY on 2012-02-11
I installed Windows XP and then installed Ubuntu Desktop 11.10 and chose the default options for dual booting during installation. I can boot into Ubuntu when selecting it in the GRUB boot menu but when selecting Windows it goes black with a blinking cursor.

How do I fix this?

---

### Post by oldfred on 2012-02-11
Windows may need chkdsk from the XP disk. 

Best to post boot info script output to see details of your install.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by DiGiTY on 2012-06-20
I tried the "recommended repair" option of Boot Repair and it still doesn't boot Windows XP (still getting blinking cursor). Here's the output of Boot Repair: [http://paste.ubuntu.com/1050441/](http://paste.ubuntu.com/1050441/)

---

### Post by YannBuntu on 2012-06-20
Hi
you seem to have correct XP boot files (/boot.ini /ntldr /NTDETECT.COM), so Boot-Repair can't do better.
Please try to fix XP by booting on a XP CD, choose "repair" (or recover), then type the following commands:
```
fixmbr
```
```
fixboot
```
```
exit
```
Reboot. 
- If you have access to XP, use Boot-Repair again to recover the GRUB menu. 
- If not, I have no other idea than reinstalling XP.

---

### Post by DiGiTY on 2012-06-20
Tried that and no luck. It actually knocked out Linux too (cursor blinks, goes down two lines then stays there continuously blinking).

Frak it! There wasn't anything in particular I wanted to test/play/use Ubuntu Desktop for anyway. Guess I'll try dual booting Windows 8 and XP instead

Thanks everyone for your help!

---

### Post by darkod on 2012-06-20
That sounds like you have grub2 installed on a partition, maybe on the windows partition.

If you posted the link with the boot info results like oldfred suggested we could have looked into the details. Without details, it's hard to know what to do.

I am not sure whether boot-repair can remove grub2 from partitions, Yann can answer that better.

---

### Post by DiGiTY on 2012-06-21
Its okay, I don't have a need for Ubuntu Desktop at the moment. Thanks anyway.

---

### Post by YannBuntu on 2012-06-21
> **DiGiTY said:**
> Tried that and no luck. It actually knocked out Linux too (cursor blinks, goes down two lines then stays there continuously blinking).

That means your XP system is deeply broken, if i were you i would simply reinstall XP, then Ubuntu. If this breaks XP again, this would mean that this is a bug of Ubiquity/GRUB, so I would retry using the XP bootloader instead of GRUB.

**@darkod:** DiGiTY indicated his BootInfo URL yesterday (post#3). There is no GRUB in PBR. (for information Boot-Repair can remove GRUB from MBR, but to remove it from PBR i recommend [this]("http://ubuntuforums.org/showpost.php?p=11693662&postcount=1")).

---

