---
title: "&quot;Missing Operating System&quot;"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by Akilou on 2013-06-15
I'm trying to install Ubuntu via a live USB. This isn't my first rodeo, I've had a dual-booting system for a while (+ Windows 7), and after experimenting a little, I ended up breaking Ubuntu. No worries, I uninstalled it. Now I'm trying to get back in the game, but things aren't working.

Let me start with what I've tried:

[LIST]
[*]creating the bootable usb drive with both unetbootin and Linux Live usb creator
[*]both 32 bit and 64 bit versions of both 12.04 and 13.04
[*]Even used checksum, and everything checked out.
[*]Also tried every iteration on all (4) usb ports.
[*]Tried running it in virtual box (after using Linux Live usb creator) and I get the same result (see below)
[/LIST]

This is what happens with every attempt above
[LIST]
[*] When booting, i hit escape, get to the boot menu, and Sandisk usb key is an option from which to boot. I choose it and I get a message 'missing operating system' before it goes to the Windows splash screen and Windows boots like normal.
[/LIST]


Any ideas? 

If you need any more info about my system, I'd be happy to tell you; just let me know what you need.

Thanks in advance!

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by Akilou on 2013-06-15
My USB drive is formatted at FAT32, and in windows, I can open up the drive and  see all of the files and folders inside. At first it was formatted at NTFS, but Linux Live USB Creator alerted me; so I reformatted as FAT32.

Let me see if I can boot from the same USB on another computer. I'll get back to you.

---

### Post by Akilou on 2013-06-15
So I got an error message on a different computer, but a different one. SanDisk show up as an option to boot from, but I get "no boot disk detected or boot disk has failed" after I select it.

I assume this means I screwed up when creating the USB drive, but I don't know what could have gone wrong. I downloaded 13.04 as an ISO, ran unetbootin, pointed the iso to the usb drive, and let it roll.

Any suggestions on what I should try next?

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by Mark Phelps on 2013-06-16
An alternative, which I personally use, is the Universal Installer from PendriveLinux.com.  When you run it, choose the bottom-most option -- generic Linux.

---

### Post by Akilou on 2013-06-16
I figured it out!

It must have been something with the flash drive that I was using. I tried a few others, and the third one worked without any problems.

I guess I'll never know, specifically, what the problem was past 'use a different flash drive', but oh well. I'm posting this from 13.04. Yay!

---

