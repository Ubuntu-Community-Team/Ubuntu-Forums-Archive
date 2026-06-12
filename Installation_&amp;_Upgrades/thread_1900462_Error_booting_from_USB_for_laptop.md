---
title: "Error booting from USB for laptop"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by arjunajay on 2011-12-26
Hi,
I've downloaded and installed Ubuntu 11.10 in my 2gb pen drive. I'm trying to live boot on my sony vaio laptop. The installation was persistent installation and there is  a 1gb file on my pendrive with name 'casper-rw'.
when I boot (i tried switching off splash) it gives the error
9i have not typed the full thing :(
```

EXT2-fs (loop1) : error: ext2_lookup: deleted inode ...
init:/etc/init.conf: Unable to load configuration : I/O error
init:hash.c:296:assertion failed in nih_hash_search
init:caught abort, core dumped
panic-  not syncing : Atttempted to kill init

```
how do i fix it?
is there anyway to boot to some safe mode where i can attempt to repair it?
should I try re-installing without persistent install?

---

### Post by 2F4U on 2011-12-26
Looks to me as if either the download of the iso is bad (did you verify the checksum) or the installation on the flash drive failed. How did you put the iso on the usb stick?

---

### Post by arjunajay on 2011-12-26
I downloaded the iso twice now since there seems to be no way to verify if it is corrupted.
I used 'Universal-USB-Installer-1.8.7.4.exe' to install to usb.

Also, i tried installing with 0 mb persistent and removed 'persistent' from boot menu. but now the original error is gone but the boot hangs at some later time. I'll try to post the last message when i  get back home.

---

### Post by West201 on 2011-12-26
Use the MD5 to check the integrity of the ISO. Other wise try installing a more stable version of Ubuntu such as 10.10 maverick or 11.04, then upgrade using APT. May not be the best solution, but it's worked on me a few times.

---

### Post by arjunajay on 2011-12-27
> **jessejj89 said:**
> Use the MD5 to check the integrity of the ISO. Other wise try installing a more stable version of Ubuntu such as 10.10 maverick or 11.04, then upgrade using APT. May not be the best solution, but it's worked on me a few times.

tried md5. it matches. i'll try 10.04 which is the only other iso i have. i'm on a limited net connection, so up grading/downloading is not an option. i have to download from some other place and install fresh always :(
Any way i'll also try to boot to some desktop and see if it something funny with my laptop is causing the problem....

Is there a boot option which will boot step by step (in y/n steps) so that I  can see what *exactly* is not working?
thanks!

#later...
The ubuntu10.04 works. but doesn't recognise touch pad.... but why? exceept for a 'boot' (not [BOOT]) folder both iso seem to contain same organisation...
guess i'm stuck with 10.04 till i find other way...

---

### Post by West201 on 2011-12-27
> **arjunajay said:**
> tried md5. it matches. i'll try 10.04 which is the only other iso i have. i'm on a limited net connection, so up grading/downloading is not an option. i have to download from some other place and install fresh always :(
Any way i'll also try to boot to some desktop and see if it something funny with my laptop is causing the problem....

Is there a boot option which will boot step by step (in y/n steps) so that I  can see what *exactly* is not working?
thanks!

#later...
The ubuntu10.04 works. but doesn't recognise touch pad.... but why? exceept for a 'boot' (not [BOOT]) folder both iso seem to contain same organisation...
guess i'm stuck with 10.04 till i find other way...


Why type of Laptop are you using ?

---

### Post by collisionystm on 2011-12-27
> **arjunajay said:**
> Hi,
I've downloaded and installed Ubuntu 11.10 in my 2gb pen drive. I'm trying to live boot on my sony vaio laptop. The installation was persistent installation and there is  a 1gb file on my pendrive with name 'casper-rw'.
when I boot (i tried switching off splash) it gives the error
9i have not typed the full thing :(
```

EXT2-fs (loop1) : error: ext2_lookup: deleted inode ...
init:/etc/init.conf: Unable to load configuration : I/O error
init:hash.c:296:assertion failed in nih_hash_search
init:caught abort, core dumped
panic-  not syncing : Atttempted to kill init

```
how do i fix it?
is there anyway to boot to some safe mode where i can attempt to repair it?
should I try re-installing without persistent install?


It is most likely the program you are using to make the usb.

Please specify the program

---

