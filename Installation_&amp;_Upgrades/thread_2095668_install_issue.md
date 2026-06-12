---
title: "install issue"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by disturbed13 on 2012-12-17
[IMG]http://i107.photobucket.com/albums/m294/hedoe/IMAG0201_zpsffe028b2.jpg[/IMG]

it doesnt matter how i try to install it
i get this no matter what

i have gone into the BIOS and made a RAID1 array from 2 160 GB HDD's
i have want to partition off the space like so
4GB swap
60GB for /
and the rest of the HDD for /home

but it wont install
what has happened?
im trying to use Ubuntu 12.04(?) the LTS distro

system specs
Core2 Quad
6GB DDR3 RAM

thanks for any help

---

### Post by sandyd on 2012-12-17
> **disturbed13 said:**
> [IMG]http://i107.photobucket.com/albums/m294/hedoe/IMAG0201_zpsffe028b2.jpg[/IMG]

it doesnt matter how i try to install it
i get this no matter what

i have gone into the BIOS and made a RAID1 array from 2 160 GB HDD's
i have want to partition off the space like so
4GB swap
60GB for /
and the rest of the HDD for /home

but it wont install
what has happened?
im trying to use Ubuntu 12.04(?) the LTS distro

system specs
Core2 Quad
6GB DDR3 RAM

thanks for any help
I would guess that that isn't really RAID 1 but fakeraid.

You probably want to use software raid, as it is easier to recover than fakeraid. See [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) for setup details

---

### Post by disturbed13 on 2012-12-17
?????
how could it be a fakeraid when i go into the BIOs and set it up from there?


oh
nvm

---

### Post by ronparent on 2012-12-18
By definition a RAID set up in BIOS is what the Linux community refers to as a fakeRAID (it is a Windows software RAID implementation). Ubuntu 12.10 currently doesn't install automatically on a RAID set. There are ways to do it but it is not straight forward. If you want to setup with a linux software RAID, as suggested, you will need to beforehand erase the fakeRAID metadata written to your drives. Also you will not be able to use Windows on a RAID setup on a Linux software RAID set. There it is in a nutshell - how you proceed is your choice.

---

