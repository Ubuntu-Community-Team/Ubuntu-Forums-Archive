---
title: "Upgrade to UNE Lucid gone bad on eee pc 1005PE"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by lbravo on 2010-05-01
Help!

I upgraded (or attempted to) my 9.10 perfectly stable install on my eee pc 1005PE to 10.04 and all has gone awry.  It seems to boot into 10.04, but now get a blinking screen (every four seconds, the screen blinks - unusual).  I can't seem to boot from a USB to start all over again... in fact, I can't get the my little notebook to start with the standard start up screen -- it goes straight to grub, and only gives me options to boot into the broken 10.04.  I don't know why this is... I've removed direct power and battery, and tried to reboot, but it won't reboot starting with the bios - it just goes straight to grub.  I'm feelin' really stupid right now... missing something.

Also, if I try to create a new startup USB, on a different system running desktop 9.10, the "Make Startup Disk" utility tells me I need to format the USB -- fine (I've tried two different manufacturers) -- and it does nothing.  I'm totally stymied and I want my eee pc back... dang it!

If anyone has clues on what I should do, PLEASE respond, I'll consider you a rock star! :guitar:

Huge Advance THANK YOU's for any clues you can provide.

Lori

---

### Post by iovis9 on 2010-05-04
Same issue here :(

---

### Post by pandemix on 2010-06-24
I had similar problems, but with the original install of Windows.  Perhaps you have already tried holding down F2 while powering the machine on?  That should cause the BIOS to pop up before GRUB shows.

I found it useful to turn off the faster-booting features of the BIOS until after I had everything working.  If you turn off 'Quiet Booting', the AMI BIOS will show its splash screen, allowing you to hit ESC and tell the BIOS explicitly to boot off your USB or SD drive.  (This is what I had to do to get it to boot in the first place.)

I hope this is helpful.

- Caleb

---

