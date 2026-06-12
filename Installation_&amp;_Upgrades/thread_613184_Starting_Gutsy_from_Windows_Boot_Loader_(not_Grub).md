---
title: "Starting Gutsy from Windows Boot Loader (not Grub)"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by MRCuadra on 2007-11-14
Okay, I've searched, read, and perused, and I cannot find what I'm looking for. So here is my question:

What is the proper string for the boot loader (boot.ini in WinXP) to boot Ubuntu (7.10)?

This is the situation: Have WinXP Pro installed; installed Ubuntu from the LiveCD to new partition(s), but specifically DID NOT install Grub as the boot loader. I did this because I already setup the boot loader in Windows with an entry for Ubuntu (since I was planning on installing Ubuntu). Now that I did the install, I cannot find (what I now realize I should have found before starting this, which is) the proper string to boot Ubuntu.

Here is the boot.ini:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\="Ubuntu Linux 7.10" 
```

Obviously, this last line needs more, but what? I've tried some stuff I've seen in threads/posts/pages about Grub, but nothing is working (just re-boots my machine), which is to be expected since they're just shots in the dark...

I'll entertain the installation of Grub since I found, in my travels, how to rearrange the boot order; but I'd rather see if I can do it this way before going down that road, or re-installing Ubuntu.

---

### Post by meierfra on 2007-11-14
It can be done but it takes a little bit of work:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

But it would be  easier to just install Grub to the MBR.

---

### Post by logos34 on 2007-11-14
You really should use Grub like meierfra said.  You can hide grub and make it default to windows so other users won't even know ubuntu is there, if that is the issue.  

To boot using NTLDR you need to copy 'grldr' and a menu.lst files (avail in grub4dos pkg) to the C: root directory.  It's easiest to use Wingrub (follow [this guide]("http://users.bigpond.net.au/hermanzone/p9.html") and make sure to get the configuration right the first time).

Or try this method:
[How to Boot Ubuntu from the Windows Bootloader]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to")

---

### Post by MRCuadra on 2007-11-14
> **meierfra said:**
> It can be done but it takes a little bit of work:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

But it would be  easier to just install Grub to the MBR.

I'm afraid I have to agree with you, meierfra... That looks to be like a little more effort than I want to take on right now. I haven't even determined yet if the Ubuntu installation worked!

Since I'm starting fresh anyway, I'll just re-install, include Grub, and figure out how to tweak Grub to my liking; after all, I've found a **whole lot** of Grub resources in my travels...  :grin:

Thanks anyway for the link!

---

### Post by bliffle on 2007-11-15
GRUB is very confusing, partly because the menus are difficult and partly because people who recommend GRUB make it sound too easy.

One would think that GRUB would be capable of identifying all the OSs and bootable partitions on a computer and give you an opportunity to boot, or fixMBR or construct new MBR, ntldr, etc.

But it seldom seems to work right and it's not straightforward to use

I have GRUB, Super Grub, Ultra GRUB (and some others) yet I was unable to boot a new Gutsy this morning (after I installed from the LiveCD to a fresh HDD after cloning my old XP with Gparted)

I suppose I'll figure this out eventually, but I always dread using GRUB.

---

