---
title: "Partitioning and encryption"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by SZF2001 on 2008-03-08
Alright, so my main Ubuntu drive is encrypted. Which I freakin' love.

Here's the deal though - right now, I want to make a partition and install Xubuntu on it's own space. I know it'd be easier to just run 'sudo aptitude install xubuntu-desktop', but I don't want ANY gnome or kde libraries, or ANYTHING influencing or being influenced by my Ubuntu desktop other than being a question as to which I boot from.

I have GParted installed through the repositories, and I just don't know where to even partition.

You can see the options of drives in the attachments for better view of what I'm dealing with.

Under '/dev/mapper/colecomp-root', it's locked so I can't even mess with it.

Under '/dev/mapper/colecomp-swap_1', that's the ONLY place I can resize ANYTHING, as it seems, and I can only free 3024 MB's. So... Is that gigs? Sorry it's been a while. And that'd be kind of dangerous to have a swap partition of 8 MB's anyway... Xubuntu requires at least 3 gigs (2 for installation, and I'll just give it another gig).

Under '/dev/mapper/sda5_crypt', of course I can't move anything, and there's nothing to really move around.

Under '/dev/sda', I have '/dev/sda1' and '/dev/sda2/', and '/dev/sda5' (which is under /dev/sda2). Can't do anything with sda1, I "can" resize sda2 - it says I can, but won't allow me, and yes I'm under root - and can only delete sda5.

I'm somewhat new to partitioning, but I really need to keep the configuration of my Ubuntu desktop and try and see if Xubuntu is easier to set up my WUSB11v4 card with. It was a freaking miracle to get it working under Ubuntu in the first place and I'll be damned if I have to do THAT all over again.

---

### Post by SZF2001 on 2008-03-08
Wow, this forum moves fast...

Anyway, I'm also using LVM. I think I screwed myself over in this. AUGH. If anyone out there can help, PALEASE DO SO

---

