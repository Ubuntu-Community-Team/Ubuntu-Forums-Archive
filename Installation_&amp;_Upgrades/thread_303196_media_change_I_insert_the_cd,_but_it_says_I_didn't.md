---
title: "media change: I insert the cd, but it says I didn't"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by djcaston on 2006-11-19
Im trying to install vmware server onto by toshiba protege, and when im downloading one particular file, it says:

Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

So I put the cd in the drive (i've tried both the livecd and the alternate) and press enter. No matter how many times I press enter, it says the cd isn't in the drive. Please help! its driving me crazy!

---

### Post by deanlinkous on 2006-11-19
comment the disk out of your sources.list file and just download everything
OR
manually mount your cd at /cdrom
OR
make /cdrom a symlink to the actual location the disk is being mounted at
OR
all I can think of :)

---

### Post by djcaston on 2006-11-19
how do i do the first one?

---

### Post by deanlinkous on 2006-11-19
open up the file /etc/apt/sources.list
place a # sign in front of the line that lists the CD
save it, close it

You need root privys for this so whichever way you want to accomplish that!

---

### Post by djcaston on 2006-11-19
how do i get the permissions to change that file? it's read only.

---

### Post by deanlinkous on 2006-11-19
sudo gedit
or a hundred other ways :)

---

### Post by djcaston on 2006-11-19
Thanks so much. You've been a lot of help!

---

### Post by deanlinkous on 2006-11-19
Did you get it!
cool beans!

---

