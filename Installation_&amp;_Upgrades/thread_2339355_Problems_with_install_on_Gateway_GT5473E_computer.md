---
title: "Problems with install on Gateway GT5473E computer"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by tx836519 on 2016-10-07
I tried to install by booting Ubuntu 14.04 Live DVD.  All went fine up to the point of starting the gnome display system when the screen went black, all stopped and the machine no longer responded to keyboard.  After several attempts, I searched the forums and thought I found the answer that the video chip set was the problem.  I installed a replacement video driver board, ASUS HD 6450.  I still get the same response.

Again, I searched the forums and tried using the 'nomodeset' approach.  The disk boots and displays the first screen to display Examples and Install icons.  The menu drop downs work for a bit as it finishes reading from the DVD and then it reboots to repeat this process.

I don't have much hair already, but I'm pulling it out again over this.

---

### Post by RobGoss on 2016-10-07
Hello and welcome, Have you tried installing **16.04** you may have better luck with this distribution seeing it's the latest. What are the specs for your machine it will help others provide the help needed to solve the problem your having

---

### Post by tx836519 on 2016-10-07
Thanks for the reply.  The computer is running an Athalon AMD 64, dual core, 2 GB memory,  I am wanting to upgrade the machine used as my file server, an old Pentium box.  For this machine I want to run an LTS version and upgrade to a new version about every two years.

The machine was shipped originally with Windows Vista and came to me with no OS installed.  I have tried various distributions of Debian and Ubuntu and have yet to find one that will run.  On receipt, I installed Windows XP to see if it was working OK.  It boots and runs this with no problem.  Once I get it where I can install Linux, I will install a server version.

---

### Post by RobGoss on 2016-10-08
Have you tried Ubuntu 16.04 on that machine to see if it loads correctly it's the latest LTS version of Ubuntu and runs really well give it a try and report back here with the results

How are you trying to install Ubuntu **USB** or** DVD ?** I find **USB** to be the easiest method in my option is might be a problem on the really old machine that don't recognize **USB** thumb drive but on newer machines they work the best.

---

### Post by tx836519 on 2016-10-08
Ok, I downloaded 16.04-1 DVD iso, burned the image, and then tried to boot the DVD.  (I don't believe this computer will boot from the USB stick based on what I see in the bios.)

This disk behaves quite similarly to the 14.04-3 system disk -- booted to the point of actually starting the Gnome display and stopped.  It did one thing that was new -- Running with 'nomodeset', it reported 'No UMS Support in Radeon Video.

I removed the new video card and connected back to the Nvidia chip set.  Just booting it hung just like with the ASUS card installed.  Restarting and running with 'nomodeset', it reported 'MP-Bios bug:  8254 timer not connected, no APIC'.  Otherwise, it responded the save as with the 14.04-3 disk.

---

### Post by howefield on 2016-10-08
> **tx836519 said:**
> ....  Once I get it where I can install Linux, I will install a server version.

Why not start with the Server install in the first place ?

---

