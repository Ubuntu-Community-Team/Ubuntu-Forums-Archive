---
title: "[SOLVED] Installing Kubuntu on x86-64"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by t3h_g3n3r4l on 2008-06-13
Maybe I'm just missing something here,  but is there no way to select the software that gets installed on Kubuntu 8.04?  I am doing a clean install as an upgrade from 7.10, which had no problems with disk space, but with my partition setup, I over run the disk space set aside for my root filesystem.  

I'm dual booting with Win XP Home, so my partition table looks something like this:
--------------------------------------------------------------
sda1 : fat 32: 16088 MB  : /windows/D
sda2 : ntfs  : 136695 MB : /windows/C
sda5 : swap  : 512 MB
sda6 : ext3  : 5371 MB   : /      }  <-- expanding to 8570 MB
sda7 : ext3  : 5247 MB   : /home  }  <-- shrinking to 2048 MB
--------------------------------------------------------------

Even though I'm thinking expanding the disk space might solve the problem,  does the install really need to be *that* bloated for a standard system?

---

### Post by t3h_g3n3r4l on 2008-06-13
Okay, so I solved the problem by just expanding the root partition as I mentioned I might do.

It seemed that the installer copied everything over before installing the packages and deleting the rest.  Am I right about this?

---

