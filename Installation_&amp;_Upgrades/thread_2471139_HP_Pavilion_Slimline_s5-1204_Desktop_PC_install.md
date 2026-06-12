---
title: "HP Pavilion Slimline s5-1204 Desktop PC install"
date: 2022-01-21
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-01-21
I was given a HP Pavilion Slimline s5-1204 Desktop PC.  This is a little single drive machine.  What I wanted to do was to convert this machine from Microsoft v7 to ubuntu 20.04.3   To that end I downloaded ubuntu-20.04.3-desktop-amd64.iso and put that on a cd.  I then tried to boot from that cd and install ubuntu.  I got noplace.  I think one of my problems is that I didn't set the bios to boot from the CD because I have absolutely no idea how to get to the bios on this machine.  I tried; del, f11, esc and got absolutely nothing.  Oh, I also put another drive into the machine as well.  The drive I used was a 1tb drive that I had.  I have no idea what might have been on that drive but thought that would make no difference as the installer, on the cd, would deal with the partition, format and file system (this might be what screwed it all up).   

I could also put the original drive back in this machine and try it that way.  My problem with that one is that I really wanted to give the drive back to the person who gave it to me in case there is anything on that drive that they might want.  

Anyway, any thoughts would be appreciated ....

---

### Post by jimmy-frydkaer on 2022-01-21
On my HP Pavilion I have to hit F2 to enter BIOS and F9 to get the boot menu.

---

### Post by jgw on 2022-01-21
Thank you for the reply

I tried both of them and neither worked.  I think that it is expecting something on the hard drive but am not sure as I see nothing on the screen.  I know that was working with the original drive (which had microsoft on it).  My other thought is to take that drive out, install it on another machine, disconnect the drive(s) on the other machine and then put ubuntu onto that drive then remove that drive from that machine and put it back on the pavilion and see what happens.  I might even able to tell that machine that I want to install ubuntu onto the external drive (suspect I would be wise to just disconnect the existing drives until I get it installed)

---

### Post by jgw on 2022-01-24
I solved this one by moving to a different system, disabled all drives, hooked up a new drive.  The system is one I was familiar with and knew I could tell it to start with the cd.   I then took my ubuntu 20.04.3 cd and put it into the cd drive and rebooted into the installation disk.  Told it to install and it did just that.  After it was done I went back to the offending machine, installed the disk with the installation and booted up.  Worked off the bat.  I then found out that my HP system was setup to goto the bios (and other stuff) was the ESCape key.  The problem, I think, was the blank disk that confused everything.

Oh, I also put the drive I used to create a new ubuntu on back together (hooked the drives backup) and its working fine too.  

Thanks again for the help.

---

