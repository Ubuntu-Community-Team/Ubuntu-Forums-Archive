---
title: "Installation Input/Output Error"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by Chuckymong on 2012-07-15
Hey people. I have just got a hold of 2 copies of the lubuntu 12.04 installation disc, one is on a cd-r and was downloaded by a friend and the other was downloaded and burned by me onto a dvd-rw. I have tried both installation discs the dvd-rw doesn't even find the OS.

The cd-r finds the OS and the try lubuntu works to perfection but unfortunately the installation of it seems to fail due to a Input/Output error.

Can anybody help me figure out what might be causing this and how i would go about solving it?

Thanks a lot - Marcus.

---

### Post by ajgreeny on 2012-07-15
Try using the CD again, (and after checking that the CD is a good copy from the first menu) boot to the desktop, and run the command ```
sudo apt-get remove ubiquity-slideshow-lubuntu
``` This removes the slideshow which will normally display during installation and which seems to crash and stop the whole installation on some hardware.

If you have a different problem I am sorry but I can not help further, but this may solve your current problem.  It certainly did mine when I tried (and failed) installing Lubuntu 12.04.

---

### Post by Chuckymong on 2012-07-15
Hi and thanks for the reply. I have just tried what you have stated above and unfortunately I got the exact same error, so I figured that I should reboot and check the disc again only to find that it contains 1 error. My next question is - is there anyway I can download lubuntu onto the try-it lubuntu desktop and install from there with no need for a cd/dvd?

Thanks again - Marcus.

---

### Post by jmfal on 2012-07-15
Welcome to Ubuntu

A quick search says that ther may be faulty ram.

Boot the live cd and run memtest, at least two passes,
if errors , remove one stick and try again, till no errors
The stick your removed before no errors is bad.

---

### Post by Chuckymong on 2012-07-15
Thanks for the reply, I also have just this second seen that information myself and was planning on trying it so i shall run a memtest now and see what happens.

Thanks guys - Marcus.

---

### Post by Chuckymong on 2012-07-15
Ok, by the looks of things its not due to the sticks of ram. 2 test came back with no errors so im begining to think i should pick up some more blank cds tomorow and download another iso to burn. Is there anyway to check its a good download before burning it because i dont fancy using multiple cds if their going to be no good?

Thanks in advance - Marcus.

EDIT: Repetition of a group of words due to loss of attention whilst writing and a few spellings.

---

### Post by Rex Bouwense on 2012-07-16
Sure enough.  Check the MD5Sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS](https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS)

---

### Post by ajgreeny on 2012-07-16
If your CD disk check at boot showed even a single error as you mentioned above, you need to burn again as slow as possible after making sure the md5sum of the .iso file is correct.

See links in post from Rex above.

---

