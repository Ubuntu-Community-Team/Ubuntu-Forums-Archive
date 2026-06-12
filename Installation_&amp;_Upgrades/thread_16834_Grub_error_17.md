---
title: "Grub error 17"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by egg on 2005-02-24
After trying to install a new hard drive, on reboot I now get Grub error 17. So it's having problems reading the partition on my main drive.

How can I fix this?

I've got the live CD.. so i can gain access to the files on the drive.

What exactly is the problem here? 

Confused  :neutral: 

thanks!

---

### Post by Buffalo Soldier on 2005-02-24
First, welcome to Ubuntu and GNU/Linux.

Error 17 is described here [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

With more information and your installation maybe others in here can know/guess what's the problem and easier to suggest solutions.

---

### Post by egg on 2005-02-24
hi! thanks... after some hacking... i now get the message No boot Sector found.

I'm just browsing to see how to fix that!  :???:

---

### Post by m4ng0 on 2005-02-24
If you post your /boot/grub/menu.lst and the output of
dmesg | grep hd
(you said you have the live CD, so you can boot) probably we can see where is the problem.

---

### Post by egg on 2005-02-24
well.. i actually got it work now! thanks anyhow.

For the record.. if someone has the same issue I did the following:

run fdisk /dev/hda and choose options a, 1, and w. 

(no idea how it became UNactive)

then, run grub and make a new install:
root (hd0,0)
and
setup (hd0,0)

followed by reboot and all is well!

---

