---
title: "Dual-booting Windows + Ubuntu on a SATA drive?"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by forevereating on 2007-05-26
I already had windows previously installed and now want to do a clean install of both windows and ubuntu (I'm upgrading from an older computer). I know how to do a dual boot environment using grub, but I don't know much about SATA drives. My old computer used PATA and it was very simple, you didn't have to do anything. But for SATA I think you need to install drivers. I have a 250GB Western Digital SATA drive and I'm not sure if I need to install the drivers once more for doing a fresh install of windows then ubuntu. I'm quite confused right now so guidance would be great.

---

### Post by JAPrufrock on 2007-05-27
> **forevereating said:**
> I already had windows previously installed and now want to do a clean install of both windows and ubuntu (I'm upgrading from an older computer). I know how to do a dual boot environment using grub, but I don't know much about SATA drives. My old computer used PATA and it was very simple, you didn't have to do anything. But for SATA I think you need to install drivers. I have a 250GB Western Digital SATA drive and I'm not sure if I need to install the drivers once more for doing a fresh install of windows then ubuntu. I'm quite confused right now so guidance would be great.

Install windows first, using the floppy that came with your SATA drive to set it up.  Don't worry- when you later install Ubuntu you don't have to do anything- it will see the SATA drive.

---

### Post by forevereating on 2007-05-27
Oh, but the problem is that I didn't build the computer myself. You think Western Digital would have the drivers on theit website? I suppose I should check it out myself. Thx, for the reply btw.

---

### Post by ryanVickers on 2007-05-27
I would just install windows, then ubuntu.  It will automaticly set up grub and probably detect your drive just fine - I have a SeaGate 300Gb SATA II harddrive and it's bean great with ubuntu and windows, although there's a limit on what you can call great with windows :)

---

### Post by forevereating on 2007-05-27
Alright, thanks everybody, you've all been helpful, I think I got it. I'll report back what happens tomorrow.

---

### Post by hakimaki on 2007-05-27
I had the same issue on my sisters laptop when I was setting it up for a dual boot.  Being that I had no floppy, and no external one to hook up I was at a bump.  2 solutions I came across: 

1.  Disable SATA "something" in the BIOS (twas long ago so I cant recall...)

2.  Found a XP install with SATA drivers already included

Both worked fine, however I chose the latter.

---

### Post by forevereating on 2007-05-28
Ok, right now I'm typing from my freshly installed XP, so I guess it works. But this computer also doesn't have a floppy, and I don't want to install grub to the mbr, so I was thinking of installing it temporary to a usb stick. Here is the thread I already created before: [Installing Grub]("http://ubuntuforums.org/showthread.php?t=455691").

---

