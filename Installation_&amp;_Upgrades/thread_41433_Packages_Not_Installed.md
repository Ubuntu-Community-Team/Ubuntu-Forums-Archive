---
title: "Packages Not Installed?"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by neotope on 2005-06-13
I tried Unbuntu from the LiveDVD and I liked what I saw so I decided to install it.  I went through the install as normal and then it ejected the CD-ROM and rebooted.  After it rebooted Ubuntu loaded a shell login and did not complete the installation.  I reformatted the partition I installed Ubuntu on and tried again and the same thing happened.

I know it is not the DVD because I gave it to a friend at work to try and it loaded fine on his machine.

Any ideas?

---

### Post by bored2k on 2005-06-13
[QUOTE=neotope]I tried Unbuntu from the LiveDVD and I liked what I saw so I decided to install it.  I went through the install as normal and then it ejected the CD-ROM and rebooted.  After it rebooted Ubuntu loaded a shell login and did not complete the installation.  I reformatted the partition I installed Ubuntu on and tried again and the same thing happened.

I know it is not the DVD because I gave it to a friend at work to try and it loaded fine on his machine.

Any ideas?[/QUOTE]
 Everthing is probably installed. You just have a xorg problem (graphics). If you're doubtful, try running (After login in) sudo apt-get install ubuntu-desktop.

---

### Post by trivialpackets on 2005-06-13
[QUOTE=neotope]I tried Unbuntu from the LiveDVD and I liked what I saw so I decided to install it.  I went through the install as normal and then it ejected the CD-ROM and rebooted.  After it rebooted Ubuntu loaded a shell login and did not complete the installation.  I reformatted the partition I installed Ubuntu on and tried again and the same thing happened.

I know it is not the DVD because I gave it to a friend at work to try and it loaded fine on his machine.

Any ideas?[/QUOTE]
 After the reboot, did it go through the process of unpacking the data?  If not, then there may be another issue than what was already stated.  If it did all this, then just got the shell prompt, a simple cd /  and ls would tell you if the system was installed properly as well once you login.

---

