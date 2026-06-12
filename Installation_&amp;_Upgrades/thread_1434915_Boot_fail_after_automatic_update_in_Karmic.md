---
title: "Boot fail after automatic update in Karmic"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by maicovalcke on 2010-03-20
Hi ppl,

Yesterday, before starting my nightshift I got the update screen so i updated like I normally do.
The system asked me to reboot and I just shut down the computer.
Some hours ago, I wanted to start the computer and the system halted after the first logo showed of Ubuntu, after 15 minutes waiting, nothing happened. I tried to push keys on the keyboard, nothing helped (I even couldn't put on CAPS or num lock on the keyboard).

After a secoind reboot I didn't even saw the Ubuntu logo. When there's a black screen, it just sits there.

I have no idea if there was a kernel update (I assume there was, because the system wanted me to reboot).
Grub shows me I have the 2.6.31-20-generic-pae kernel.

What to fix this issue?

Thx

---

### Post by garvinrick4 on 2010-03-20
Do you have a Live CD. (your Burned ubuntu install disk)

Have you ever used one?

Its going to take one to fix this.

---

### Post by maicovalcke on 2010-03-21
Yep, got one in the dvd tray right now.

---

### Post by garvinrick4 on 2010-03-21
Ok boot into it.

Do you want to mount your OS and get wifi access so you can
update @ upgrade your system?

If so open gparted in Admin and see what sdax your ubuntu install is in. x being your install partition is.
What sda1, sda5.

Which ever one it is right click on it and label it. Lets say karmic and apply it. 

Then post here what your sda is.

---

### Post by maicovalcke on 2010-03-21
It's on sda1, got no wifi, it's UTP cabled

---

### Post by garvinrick4 on 2010-03-21
So you have internet access and your in your Live CD.
Make a directory:
sudo mkdir /media/karmic

Mount karmic:
sudo mount /dev/sda1 /media/karmic

Get root access:
sudo chroot /media/karmic

Do not need sudo anymore will say root: update and upgrade system 
apt-get update && apt-get upgrade

After all upgrades:
apt-get -f install

Unmount karmic: 
hit ctrl/d then Code: sudo umount /media/karmic
That is not typo umount



Make sure you labeled sda1 karmic.
If a problem let me know after any step.

---

### Post by maicovalcke on 2010-03-28
Hi [garvinrick4]("http://ubuntuforums.org/member.php?u=899097"), I finally tried to do this. 
I could make a directory called "karmic" in /media
but the chroot /dev/sda1 /media/karmic gave me an error. (sudo was not needed because it is netroot, but I tried both.)

The error with chroot I get is:

"chroot: cannot change root directory to /dev/sda1: not a directory"

Edit: I now see that you mention the Live CD as well in your last post. Should I do this all from the terminal within a running Ubuntu Live version?
If so, will this recover my broken Ubuntu and all it's settings?

---

