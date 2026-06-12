---
title: "Corrupt install files"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Lee71 on 2008-03-05
Hi I'm trying to install a linux OS for the first time

Specs
vista 64/xp pro32
 intel Core 2 Quad Q6600 Kentsfield 2.4GHz
8800GTX
G.SKILL 4GB(2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 5-5-5-15
2 160gb hd's not in raid xppro on one, installing ubuntu on the other
ASUS P5K DELUXE/WIFI-AP LGA 775 Intel P35
Xfi XTREME MUSIC
Gateway 24' 1920 1200*

I tested each downloads md5hash, i never got a corrupt file.  

On vista64, First I downloaded the amd64bit from georgia tech server, burned it twice to dvd+rw disks, I got blank screens after selecting install from boot menu, switched to cd-r disk, same result.  Downloaded amd64bit alternative download text based installer from georgia tech, same result.  Gave up on 64bit downloaded x86 standard, got all the way to the orange loading screen with the block moving back and forth, it froze after a minute or two, tried 3 times with different burning apps including the 2 on BurningIsoHowto documentation.  This time went with the x86 alternate text based installer got the farthest so far, got to the install menu, failed at verifying cd contents (didn't write down what file sorry) tried this a couple times never got past it.  

So I was thinking that my optical drive went bad even though I haven't had any problems with it before, got a sony one from walmart.  Got home decided to reformat/install xp pro fresh, and nero essentials came with my sony dvd burner.  

With a fresh xp install, new dvd burner, I downloaded the x86 text based installer from University of Utah server.  Mounted it with nero with the option for bit by bit comparison of the data burned onto the disk and the original data, this burn passed without error and verified correct.  After booting to disk it actually passed cd verification and allowed me to start the install process, soon after starting base install I got corrupt file message this time I wrote it down;

Corrupt file
///cdrom/pool/main/d/pkg/dpkg/_1.14.5ubuntu16_i386.deb

Another error window popped up after that one

Failure trying to run: chroot/target dpkg--force-depends--install
var/cache/apt/archives/base-files_4.0.0ubuntu5_i386.deb
var/cache/apt/archives/base-passwd_3.5.11build1_i386.deb

one more window after that one

debootstrap program exited with an error (return value 1).
Check /var/log/syslog



So what am I doing wrong?


Edit: I was downloading 7.10 each time.

---

### Post by louieb on 2008-03-05
Doesn't look like your doing anything wrong.  That pretty much the way I always do it. 
If it passed the media check I  am a loss. The only thing I can suggest is to use CD-R and burn at the slowest speed possible. I normally use 2x when burning an iso image. Good Luck.

---

### Post by Lee71 on 2008-03-05
/bump

I tried to install fedora, I get the same corrupt file errors with that too.  So I think this points to my dvd burners, cable and mobo, that is unless its a software issue.

I think I ruled out memory problems, I turned off all OCs and took one of the two sticks out, didn't work, and switched it, still didn't work.

---

### Post by Pumalite on 2008-03-05
Clean the lens in your burner or change it. If you have a good md5sun and then you get a corrupted CD, that is pointing to your burner. I agree with louieb; use good quality CD-R media and burn at the slowest possible speed.

---

### Post by Lee71 on 2008-03-05
> **Pumalite said:**
> Clean the lens in your burner or change it. If you have a good md5sun and then you get a corrupted CD, that is pointing to your burner. I agree with louieb; use good quality CD-R media and burn at the slowest possible speed.

Ok, I checked the md5sum again and it was perfect, also burned a new cd-r with Iso recorder v2, everything seemed fine, booted to disk used the verify cd contents button and got an error that a file was corrupt cause it failed md5sum check.  

I'm going to take this burner back to walmart tomorrow in the mean time any ideas are appreciated!

---

