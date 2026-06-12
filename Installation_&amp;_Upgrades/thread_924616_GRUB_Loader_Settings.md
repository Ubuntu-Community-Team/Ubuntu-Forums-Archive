---
title: "GRUB Loader Settings?"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by CyberPrime on 2008-09-19
Well, I intsalled Ubuntu on a 10 GB drive just to do something with the drive, but it installed badly, when I went to boot it thru GRUB (Windows XP Pro / Ubuntu) it gave me this error:
"Find --set-root --ignorefloppies /ubuntu/install/boot/vmlinux

Error 15: File not found"

Fine, not a problem. So, I went and booted off a 8.04 Live CD, partitioned the 500GB windows drive 35/75 or so with room for swap (7.5 something by default). So, it installed well and asked me to reboot, I did and I removed the 10GB drive. when I went to boot into Ubuntu via the GRUB loader that came up, it gave me the same error 15 as if the drive was still in. I booted into windows to find that I had partitioned fine.

Any ideas as to what my problem is? Thanks.

---

### Post by Pumalite on 2008-09-19
Replace your small drive and make it first in the boot order.

---

### Post by caljohnsmith on 2008-09-19
> **CyberPrime said:**
> 
"Find --set-root --ignorefloppies /ubuntu/install/boot/vmlinux

That syntax you are using above is for Grub4DOS, so I assume you did a Wubi install? In other words, did you install Ubuntu within Windows using Wubi? As long as you have a separate partition for Ubuntu, I think you should ditch Wubi and just use the Ubuntu installer from the Ubuntu Live CD to install Ubuntu to the partition you allocated for it. Wubi only adds another layer of complexity that can only mean more problems, so it is usually better when you can give Ubuntu its own partition like you plan to do. Let me know how it goes or if you need more info/details.

---

### Post by Pumalite on 2008-09-19
I'm learning about Wubi.

---

### Post by caljohnsmith on 2008-09-19
> **Pumalite said:**
> I'm learning about Wubi.
You're braver than I am then; I finally gave up on Ubuntu + Wubi because I never could get it working on my computer. :)

---

### Post by Pumalite on 2008-09-19
I meant learning so I would know what I'm talking about. I know nothing about wubi and I've never used it.

---

### Post by CyberPrime on 2008-09-19
Aye, that's what I meant. I thought i put it down.

Anyway, I don't have a floppy if that makes any difference.

Isn't there a way I can remove that drive from the boot?

> **caljohnsmith said:**
> That syntax you are using above is for Grub4DOS, so I assume you did a Wubi install? In other words, did you install Ubuntu within Windows using Wubi? As long as you have a separate partition for Ubuntu, I think you should ditch Wubi and just use the Ubuntu installer from the Ubuntu Live CD to install Ubuntu to the partition you allocated for it. Wubi only adds another layer of complexity that can only mean more problems, so it is usually better when you can give Ubuntu its own partition like you plan to do. Let me know how it goes or if you need more info/details.

---

### Post by caljohnsmith on 2008-09-20
> **CyberPrime said:**
> Aye, that's what I meant. I thought i put it down.

Anyway, I don't have a floppy if that makes any difference.

Isn't there a way I can remove that drive from the boot?
If you uninstall your Wubi Ubuntu through the "Add/Remove Programs" in Windows' Control Panel, it should remove the reference to Ubuntu in your Windows boot loader so you won't get it at start up. You can also do it manually by opening up your C:\boot.ini file and removing the line at the bottom that says something like:
```
C:\wubildr.mbr="Ubuntu"
```
It is easy to modify that file in Linux (like from your Live CD) if you are just going to remove that line, but if you want to do it from Windows, I would suggest reading "[A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")" at Herman's website.
Let me know how it goes. Let me know how it goes.

---

### Post by CyberPrime on 2008-09-20
Well, I deleted the string for the boot.ini, and reinstalled ubuntu, it work's great! I am pleased to say I am (almost completely) off windoze on this machine. Sadly some games won't run in WINE so I was forced to leave windoze on. :'(

---

### Post by red_team316 on 2008-09-20
It sounds great that you got it working, but it sounds pretty odd that you could delete boot.ini and still be able to boot into windows. I'm curious, could you post what your boot.ini(was?) and/or your GRUB menu.lst. As I've always had GRUB chainload windows which requires an intact ntldr and boot.ini...

I'm familiar with wubi but have no use for it so I'm not sure what modifications it makes to the windows and GRUB bootloaders.

---

### Post by caljohnsmith on 2008-09-20
> **red_team316 said:**
> It sounds great that you got it working, but it sounds pretty odd that you could delete boot.ini and still be able to boot into windows. I'm curious, could you post what your boot.ini(was?) and/or your GRUB menu.lst. As I've always had GRUB chainload windows which requires an intact ntldr and boot.ini...

I'm familiar with wubi but have no use for it so I'm not sure what modifications it makes to the windows and GRUB bootloaders.
I think you might be misunderstanding; as you say, you can't boot Windows without a boot.ini. Wubi merely adds an extra line at the end of boot.ini (see my previous post) so that Ubuntu becomes an option in the Windows boot menu. So all CyberPrime did was delete that line in boot.ini, not the file itself. :)

---

