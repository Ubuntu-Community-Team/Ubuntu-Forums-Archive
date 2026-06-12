---
title: "Tearing my hair out (n00b)"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by datassette on 2005-08-08
I'm having a problem installing Ubuntu 5.04 on my Thinkpad T20.

I've downloaded the ISO twice, once over bittorrent, and have burnt both copies twice, all four copies at 16x - so I'm pretty sure I don't have a dodgy CD.

The installation works fine up until the 'copying remaining packages' stage, where it gets to about 80-90% and I get an error message saying 'you might be out of disk space'.  I know this is untrue as I'm installing Ubuntu on a single partition across the whole 30gb of the drive.

Any idea whats happening?

I've been searching around and I've seen a lot of people mentioning MD5 checksums.
I don't really understand this, but I ran md5sum.exe on the iso on my PC (before burning) and got this:

f6b3f164c99761234858a4d2c12d0840 *ubuntu-5.04-install-i386.iso

OK, what does that tell me?

---

### Post by kosmic on 2005-08-08
Just a silly question..but when your partitioned your drive how much space did you give to the / (root) partition ?

---

### Post by Lord Illidan on 2005-08-08
Did you leave the partitioning to Ubuntu's installer or you did it yourself?

---

### Post by Martin Witte on 2005-08-08
Here [http://se.releases.ubuntu.com/5.04/MD5SUMS](http://se.releases.ubuntu.com/5.04/MD5SUMS) you can find the md5 checksums. A checksum is a unique number associated to a file, it tells you you're image is not corrupted (or if it would be different from the published number the file is corrupt). That you run a .exe program tells me you have MS Windows installed, did you create a seperate partition for Ubuntu? I would say you need minimal a 4Gb partition for a typical instalation.

---

### Post by srinath on 2005-09-07
how do I use this md5sum program?
I double clicked it after placing it along with the ISO image. A window flashed and went off. Nothing else happened. What is this?

I have no clue. I am desparate. ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by josephtura on 2005-09-07
[QUOTE=srinath]how do I use this md5sum program?
[/QUOTE]

Google is your friend...

[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)

---

### Post by srinath on 2005-09-07
Thanks.

---

