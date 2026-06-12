---
title: "Ubuntu 13.10 installer does not offer upgrade option"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by PeopleUnite on 2014-02-15
I am trying to upgrading from 12.10 to 13.10 from a USB drive.  Something went wrong with the installer.    I kept getting error  messages.  It couldn't set my time zone.  It couldn't set my keyboard  settings.  The error message said "ubi-console-setup failed with exit  code 1.  Further information may be found in /var/log/syslog."  I had to  skip connecting to UbuntuOne, but then, at the end of a slideshow about  Ubuntu's features, I got an endless spinning wheel.

 					So I've tried re-downloading ubuntu 13.10 twice now.  But each time  I run the installer, I  don't get an upgrade option anymore.  I did the first time when it  failed.  Now my choices are "Install Ubuntu  alongside Ubuntu 12.10" (it  doesn't even say 13.10 anymore, it looks like there is a double space  and it's just missing) or "Erase Ubuntu 12.10 and reinstall" then two  options that are greyed out and "Something Else."  I really don't want  to create a partition and lose a big chunk of my disk space, but that's  better than losing all my data.  Did I download the wrong .iso file?   This is such a bizarre problem!  Please help!

Thanks!

---

### Post by fantab on 2014-02-16
First of all you can't upgrade from Ubuntu version 12.10 directly to 13.10. From 12.10 you must first upgrade to 13.04 and then to 13.10.
Secondly the Installer will give the choice to upgrade only if you have 13.04 installed.

It would be easier if you just Install 13.10 replacing 12.10, that is, "Erase Ubuntu 12.10 and reinstall" or you can do it with "Something Else" option.
Its always a goot idea to have good 'BACKUP(s)" for your important data.

---

### Post by PeopleUnite on 2014-02-16
I am upgrading from a USB drive, which I was told would allow me to jump from 12.04 to 13.10.  In any case, the installer believes I have 12.10 installed (because I tried to do that, and it looked fine at the time, but when I reboot it only goes to Memtest86+).  So that's why I'm trying to do it from a USB drive.  I put 13.04 on my USB drive and I'm still having the same problem.  I am given the option of installing alongside 12.10, or else deleting 12.10 and losing all my data.

I could back up my files, but I'm afraid of losing years of archived email and browser bookmarks.  Since I can't boot from the hard drive anymore, I'm not sure how to back these up.

---

### Post by frank18 on 2014-02-16
> **PeopleUnite said:**
> I am upgrading from a USB drive, which I was told would allow me to jump from 12.04 to 13.10.  In any case, the installer believes I have 12.10 installed (because I tried to do that, and it looked fine at the time, but when I reboot it only goes to Memtest86+).  So that's why I'm trying to do it from a USB drive.  I put 13.04 on my USB drive and I'm still having the same problem.  I am given the option of installing alongside 12.10, or else deleting 12.10 and losing all my data.

I could back up my files, but I'm afraid of losing years of archived email and browser bookmarks.  Since I can't boot from the hard drive anymore, I'm not sure how to back these up.

Use Ubuntu 1 to backup your files.

---

### Post by fantab on 2014-02-16
> **PeopleUnite said:**
> I am upgrading from a USB drive, which I was told would allow me to jump from 12.04 to 13.10.  In any case, the installer believes I have 12.10 installed (because I tried to do that, and it looked fine at the time, but when I reboot it only goes to Memtest86+).  So that's why I'm trying to do it from a USB drive.  I put 13.04 on my USB drive and I'm still having the same problem.  I am given the option of installing alongside 12.10, or else deleting 12.10 and losing all my data.

I could back up my files, but I'm afraid of losing years of archived email and browser bookmarks.  Since I can't boot from the hard drive anymore, I'm not sure how to back these up.

We can upgrade from LTS to LTS, that is you can easily upgrade from 12.04 to 14.04 (when it is released in April 2014). But since you tried unsuccessful upgrade from 12.04 to 12.10 you probably have mixed up install. Clean and Fresh Ubuntu 13.10 is the best option.
If you can boot Ubuntu DVD/USB with "Try ubuntu without installing" option, which will run Ubuntu from RAM. You can then access your Partitions from Live Ubuntu and backup as needed.

---

### Post by mastablasta on 2014-02-17
you can install over the previous install without first formating the disk. that should keep the data there. you might need to change a few settings and read some PPA's if you have any.

---

