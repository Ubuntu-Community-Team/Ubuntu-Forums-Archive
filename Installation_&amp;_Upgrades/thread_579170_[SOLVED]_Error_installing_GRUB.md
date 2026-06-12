---
title: "[SOLVED] Error installing GRUB"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2007-10-18
When I was installing Xubuntu (Feisty Fawn, alternate CD), I had problems installing GRUB. The installer told me that installing GRUB had failed, and suggested me to try again. When I did this, it failed again. So I decided to try and install LILO instead. It didn't work as well.

So I went into recovery mode, opened a shell in my Xubuntu installation and entered:
```

sudo apt-get install GRUB

```

It then gives me an error (I don't remember it exactly, but I will have a look later, have to go in a few minutes at the moment).

Does anyone know a way to get GRUB installed?

---

### Post by forestpixie on 2007-10-18
I used [supergrub]("http://supergrub.forjamari.linex.org/") - download it and burn as an iso

but you can use the livecd - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

hermans page is a good place to start for fixing grub - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ScriptDevil on 2007-10-18
Well.. does apt-get itself fail?? or are you not able to install it to your master boot record?

If it is the second, run 
```

sudo grub-install /dev/sda (or whatever your hard disk is named)

```

Be sure to check if your **/boot/grub/menu.lst** contains something like this at the least

```


default        0
timeout         10
title           Ubuntu, kernel 2.6.20-15-generic #any name
root            (hd1,5) #Can change
kernel          /vmlinuz-2.6.20-15-generic root=UUID=2e1d4cca-e576-4604-82a7-38$ #will differ
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault



```




--------------------------------------------------------------------------------------------------------------------------
:guitar:
ScriptDevil

---

### Post by Bliepo32 on 2007-10-18
> **ScriptDevil said:**
> Well.. does apt-get itself fail?? or are you not able to install it to your master boot record?

If it is the second, run 
```

sudo grub-install /dev/sda (or whatever your hard disk is named)

```

Be sure to check if your **/boot/grub/menu.lst** contains something like this at the least

```


default        0
timeout         10
title           Ubuntu, kernel 2.6.20-15-generic #any name
root            (hd1,5) #Can change
kernel          /vmlinuz-2.6.20-15-generic root=UUID=2e1d4cca-e576-4604-82a7-38$ #will differ
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault



```




--------------------------------------------------------------------------------------------------------------------------
:guitar:
ScriptDevil
Nah, Grub is not installed at all (so /boot/grub doesn't even exist). Running sudo apt-get install grub gives me the following:

[QUOTE=My laptop]
Reading package list... Done
Building dependency tree
Reading state information... Done
Package grub is not available, but is referred to by another package.
This may mean that the package is missing, had been obsoleted, or is only available from another source
E: Package grub has no installation candidate
[/QUOTE]

I have yet to try the SuperGRUB cd. I will edit this post once I have done so.

---

### Post by Bliepo32 on 2007-10-19
Allright, an update on the topic. I downloaded and used SuperGRUB. It too, failed at installing Grub. It could however boot Ubuntu directly. The X-server failed however (but I already found how to fix this).

So, I still have the same problem. I do not have GRUB installed, and installing it fails.

EDIT:
I have finally found time to post the system specifications. Here they come:

Processor
Processor: Intel Pentium MMX 233 MHz
Data Bus Speed: 66 MHz

Ram
Installed Size: 32 MB / 96 MB (max)
Technology: EDO RAM
Form Factor: SO DIMM 144-PIN

Hard Drive: 3.2 GB (2 GB for Ubuntu, 1.2 Fro Windows, and a 2GB USB-stick as swap)

Optical storage
Type: 1 x CD-ROM - internal
Read Speed: 20x
Compliant Standards: 2nd generation, Kodak PhotoCD, CD-DA, CD-XA, CDi

Display
Display Type: 12.1" TFT active matrix integrated
Max Resolution: 800 x 600 ( SVGA )
Widescreen Display: No
Colour support: 24-bit (16.7 million colours)

Video
Video Memory: EDO RAM - 2 MB
Supported Display Graphics: VGA (640x480), XGA (1024x768), SVGA (800x600), SXGA (1280x1024)

---

### Post by greenlegacy on 2007-10-20
I seem to be having a similar issue.  

I was trying to install Ubuntu 7.04 (was going to update to 7.10 afterwards) on a newer laptop that has Vista on the other partition.  I tried twice and both times the grub install failed.  I've used this same disk on other machines without issue.

---

