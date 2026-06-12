---
title: "ubuntu-server 12.04 LTS _Precise Pangolin_ 20120424.1"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by fastzombie on 2012-05-26
I am in the middle of installing the 32b i386 server and it is asking to insert disk labeled 'ubuntu-server 12.04 LTS _Precise Pangolin_ 20120424.1'.  WTF?  I can't give a disk a label that long.  I tried using a burner that let me use ISO9660 but that still only gives me 32 characters and I get the same message.  I am really afraid of hosing up the whole disk if I can't solve this.  Any suggestions?

---

### Post by VMC on 2012-05-26
Edit: I miss understood your first statement. Sorry.

I haven't installed a server disk before. Are you sure you downloaded the correct disk?

What is the name of the ISO you downloaded. I assume your installing from a cd/usb.

---

### Post by fastzombie on 2012-05-26
I'm not sure how to use that info in the middle of an install.  It's asking for a disk with that label and I don't understand why and more importantly how to rescue it.

---

### Post by fastzombie on 2012-05-27
well i tried using desktop thinking the server disk might be corrupted and the install completely failed.  not sure why i can't have an install of ubuntu go cleanly, there is always some catastrophic failure.

---

### Post by Bucky Ball on 2012-05-27
> **fastzombie said:**
> well i tried using desktop thinking the server disk might be corrupted and the install completely failed.  not sure why i can't have an install of ubuntu go cleanly, there is always some catastrophic failure.

Yea, strange. I'm not sure either.

* What machine are you using? (i.e. RAM, processor)
* With the desktop install, does it run ok when you boot from the disk and 'Try Ubuntu' rather than attempt to install?
* Have you tried the most stable release, 10.04 LTS (or any others), to see if you get the same results? That might give other clues.
* Have you tried the alternate install ISO? If it is a graphics issue this will (should) bypass as it is a text-based installer.

Please provide more details about exactly how these installs have failed, i.e. any error messages you might remember. ;)

---

### Post by fastzombie on 2012-05-27
Thanks for reply.

On the "Install Base System" step it was asking for volume 'ubuntu-server 12.04 LTS _Precise Pangolin_ 20120424.1', literally that whole quote.  I could not continue, I could not go back, I was stuck.  As I clicked either option it seemed to be looking for a file but it flashed too quickly to read.

I tried sneaking in desktop but then the install totally failed.  I'm pretty concerned my partitions are hosed and I've lost Windows.

- I am using an IBM T60 with Centrino Dual core 2G ram.
- I did not try desktop on this machine, but I tried it on another machine and it was a disaster.  It screwed up my partitions and I still cannot boot up windows.  Made me very paranoid about partitioning.
- Have not tried 10.04, but considered it.  I suppose with server it won't make much difference.
- Server 32 has no graphics, it's like it is the alt disk.  Most server instructions are for 64.

I am going to try Kubuntu desktop, I had luck with that.  I can install any server stuff I need later.  I prefer KDE anyway.

Thanks for the help.

---

### Post by fastzombie on 2012-05-30
Well my greatest partitioning fears came true it wiped my windows.  Just freakin great.  I really thought Ubuntu would be better than this but so far every install I try is a new disaster.

I'll just install Kubuntu desktop and add/remove as necessary.

---

