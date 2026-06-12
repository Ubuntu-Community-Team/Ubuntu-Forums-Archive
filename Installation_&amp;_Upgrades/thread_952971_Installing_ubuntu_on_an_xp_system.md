---
title: "Installing ubuntu on an xp system"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by rush_fan on 2008-10-19
Hi y'all,

I have an old Dell desktop with a P4 processor and a 20gb drive.

I want to install ubuntu on the drive.

I can't get windows to recognize the iso file so I can install ubuntu.

What do I need to do to get this installed?

I know NOTHING about Linux.

Thanks!!

---

### Post by AMESSIER on 2008-10-19
Windows will not know what a .iso file is unless you have the software necassary to burn an iso image to a CD/DVD. The main stream ones are Roxio and Nero. But you can also do a web-search for free ones. Here's a link that I found after a quick search: [http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html](http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html). XP has built in support for drag-drop to CD, but I think ISO to DVD will not work without some kind of burning app.

---

### Post by ginestre on 2008-10-19
> **rush_fan said:**
> Hi y'all,


I can't get windows to recognize the iso file so I can install ubuntu.


You don't need windows to recognise the iso file; the iso file is a special kind of file that 'replicates' a CD. What you need to do is 
1) put the iso file on a CD with any burner program (you can do this under windows) making sure that you choose the option to 'make a disk image' AND NOT the option to 'just copy the files over to the CD for storage' 
2) reboot your PC (therefore you will NOT be in windows) with the CD in your drive. If windows comes up, and not ubuntu, you need to change a BIOS setting. Just reset the computer again, and push DEL while it is booting. You'll get into the BIOS set up menu, and one of the options available is to define the boot sequence. Just change this value so that your PC looks for an operating system on the CD before it looks on the HD. It'll be clear to you when you see the menus.

And that's it.

---

