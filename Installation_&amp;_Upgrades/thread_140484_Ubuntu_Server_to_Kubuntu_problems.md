---
title: "Ubuntu Server to Kubuntu problems"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by kmonihen on 2006-03-06
Hello,
  This weekend I decided to re-install ubuntu because it was residing on a measly 7GB partition on my 80 GB hard-drive, and with no more need for Windows, I decided to dedicate the whole 80GB to Ubuntu.

So I backed up all the important stuff onto a 200GB external HD and started up the re-install, only to find out that my CD-ROM no longer works.  Well, it works just enough to get half-way through installing packages before it "craps out."  I know it is the CD-ROM because I have tried all 5 installation disks that I have an they all fail at the same point in the installation, and I had used the same disks on my previous install.

Alright, so at this point I'm desperate because I have no operating system on my computer and my computer can't boot from a USB drive (because it is an older Dell), nor can it boot from a floppy drive because it doesn't have one.  At this point I decided to try to install Ubuntu Server from the disks... and it worked! =]

After I logged into Ubuntu server I immediatly apt-got kubuntu-desktop.  All went well with this installation, but when I restart it takes me to the Ubuntu Server log-in instead of the KDM graphical login.  This seems like it would be an easy fix, but I'm not sure how to do it.

Any help would be appreciated, and thanks for listening to my long tale of woe and malfunctioning hardware.

-Keith

---

### Post by Aewheros on 2006-03-06
Does the login screen load? Have you checked CTRL+ALT+F7?

If not: Can you still start the login screen manually by typing "sudo kdm"?

---

### Post by kmonihen on 2006-03-06
Oh yeah, I tried switching using ALT-FX, but I could only get to the other "normal" login screens, never to the KDM screen.  I also tried running KDM using "sudo kdm", but it gives the error that "only root wants to run KDM."

I should also mention that KDM is started during boot and stopped during shutdown, so it seems to be running.  I also tried "startx" but it doesn't work either.


-Keith

---

### Post by kmonihen on 2006-03-06
I figured this out...  I just needed to set-up my graphics card.

-Keith

---

