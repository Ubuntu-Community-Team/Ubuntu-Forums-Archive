---
title: "problems with the base system"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by divinity on 2005-10-17
help me please. i can't get past the base installation. i'm totally new to all this. thank you.

---

### Post by Murgle on 2005-10-17
can you be more specific as to what you are trying to do that isn't working?  can you log in?  does you computer boot?

---

### Post by bedo on 2005-10-18
if you get "debootstrap" error; it's because the CD is not burned correctly

make sure your iso image is valid by compare it to the MD5 hash.

try to burn the CD again at 1X or 4X speed (not 16X or 24X).

I had the same problem, and I had to reburn the CD and it works now.

-B

---

### Post by discofro on 2005-10-18
I'm having a very similar problem. These are the error messages I got:

On base installation - At 79%
Failed to install kernal 'linux-386'

When I tried to 'Copy remaining packages':

Copying Package to the hard disk has failed
./pool/main/x/xorg/xserver-xorg-driver-mgon_6.8.22-77_i386.deb

And I also got this

Cannot install base system
The installer cannot figure out how to install the base system. No installable CD-ROM was found and no valid mirror was configured



So what is all this nonsense about? If we need to burn the CD's at a slow speed, PUT THAT ON THE SITE IN BIG HUGE LETTERS.

Thank you

---

### Post by Murgle on 2005-10-18
the problem could also be on the part of your system... if you fail at the exact same place twice in different installs off the cd then that is probably at fault but if you get to say 79% one time than 76% the next you could have bad ram or a bad harddrive.

---

### Post by Dylanby on 2005-10-18
Had a similar problem with Warty. None of the daily ISO's would work either.
The only way I could install was to do a net install using one of the mini.iso's (burnt to CDRW):
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-amd64/current/images/netboot/)

---

### Post by discofro on 2005-10-18
Ok, upon re-download and re-burn at a very slow speed, the install worked as I am writing this from Ubuntu now. 

Again I feel this should be documented somewhere so everyone who does this doesn't have to burn two CD's and go through pages of documentation to get a relatively simple solution.

---

### Post by Murgle on 2005-10-18
I agree that it should be noted, but I have never had such problems, perhaps it is related to only certain burners?

---

### Post by taygan on 2005-10-19
Yes, certain burners need dma enabled when installing.

alt-f3 (?) to terminal.

hdparm -d 1 /dev/sda (yours may be slightly different)

---

