---
title: "Installation Error"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by MavKato on 2005-03-30
I am trying to install Hoary to an older computer before i put it on my main computer.  I am running into problems with the installation.  It tries to start the actual installation, then I get an error saying:
"No installable kernel was found in the defined APT sources

"The current default kernel package is 'kernel-image'

"You may try to continue though this rather strange error is probably fatal"

The system I am trying to install on is a Pentium Pro 200MHz, 128 MB RAM, 13 GB HDD

I have had nothing but bad luck trying to install Ubuntu so far.  I ordered the CDs through the mail before I had internet at home, all 5 CDs were bad.  Now that I have high speed internet, i downloaded the Warty release, and that doesnt work.  I burned it to a CD, and it fails the integrity check.  Now this.  I don't want to give up on it, but I don't know what to do.

---

### Post by MavKato on 2005-03-30
i tried installing again, this time I got an error saying "The installer cannot figure out how to install Ubuntu.  No installable CD-ROM was found and no valid mirror was configured."

---

### Post by sophomERIC on 2005-04-10
I am having this exact same problem. This is an old Pentium 3 with 512 SDRAM. The other hardware is unknown to me for the most part. I am using the same disc that worked for an install on my laptop though.

---

### Post by MavKato on 2005-04-10
I took the hard disk out of that computer and put it into my pentium 4 dell, and the installation worked fine with the same cd.  I then formatted the hard disk, put it back into the old computer, and it gave me the error again.

---

### Post by sophomERIC on 2005-04-10
I have been playing with it all day and I got around it two ways.

1.) do the install as expert, but after loading the necessary hardware item froms the disc, I switched to a terminal (Alt + Right), unmounted and ejected the CD so that when it went to install the base system it actually downloaded it (and gave me far more kernel choices anyways) from one of the mirrors. You have to enable the extra download module if you do this though, it will be on one of the option screens, I just forget which one.

2.) later in the day it just worked as standard install. I saw a post on another forum where someone had the same problem and it just worked the next day they said

I have installed Ubunutu about 8 different times today just messing with it. I highly recommend you get it to work with the standard install if possible, because every time I did the expert install, it asked to make a root password, which I think messed up the whole no root/use sudo idea they have going here. Any time I tried to open their package manager, add/remove programs or update applications, it would not take either my root or user password. I could also not use sudo with the user account I made during setup. It's just funny that the install worked better on my laptop than the desktop because it is usually the other way around. 

Once you get this installed, it is a really nice OS though IMO.

---

