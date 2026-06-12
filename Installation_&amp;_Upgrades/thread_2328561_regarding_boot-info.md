---
title: "regarding boot-info"
date: 2016-06-22
forum: Installation &amp; Upgrades
---

### Post by vijaya3 on 2016-06-22
I did run boot-info and I got a report Please write on a paper the following URL:
[http://paste2.org/4XsxUd74](http://paste2.org/4XsxUd74)
pleasse help me...

---

### Post by westie457 on 2016-06-22
Hi and welcome to you.

Some more information about the problem will be helpful. 

What boots and what does not?

Having had a quick look at the report there are several issues and trying to sort them by guess work could make matters worse.

---

### Post by oldfred on 2016-06-22
You show you have installed Ubuntu both in BIOS & UEFI boot mode.
Since Windows is always UEFI on gpt partitioned drives, you want Ubuntu in UEFI boot mode.
And then need to boot Boot-Repair in UEFI boot mode and make UEFI repairs.

And be sure tick/check to include this option.
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 

But HP are not UEFI friendly. After Boot-Repair's fixes, see if you can boot in UEFI mode and choose the use standard efi or similar words boot option. (not Ubuntu entry)

Other HP, they manually copied files, that Boot-Repair will do for you.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

