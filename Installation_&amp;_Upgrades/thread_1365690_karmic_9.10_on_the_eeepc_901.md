---
title: "karmic 9.10 on the eeepc 901"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by brallan on 2009-12-27
NOTE: I've never liked the NBR, so everything here is just the vanilla desktop version:

After jaunty (9.04) I was pleased with the ubuntu support for the eeepc (after installing eee-control everything except hibernation worked), and I upgraded to 9.10 with little hassle. However, every fresh install of karmic koala that I've done has presented problems....

I've had 2 eeepcs, both of then 901s. Great little machines, for weight, price, and battery life. The eeepc 901 has two solid state drives, the tiny (50mm / 4GB) fast one which is next to impossible to change (it's under the mainboard) and the 16GB / 70mm drive, which is painfully slow when used for an OS install. Runcore makes a number of 70mm SSDs that have come down a great deal in price. I have also tried installing to the SD card, but it was even slower than running off a USB stick/external USB drive. Perhaps that's due to a slow SD card, though.

The first time I tried to do a fresh install of 9.10, I didn't know that it would install as ext4, or that ext4 would give me issues on an SSD. I had file system problems, io errors, and it was very slow on the 16GB phison SDD, but still more or less worked. Since then I have updated the BIOS and  installed a 64GB SSD. Having learned my lesson about ext4 being so unstable, I formatted the drive as ext3, but two install attempts completed (stating the install as a success) to reboot to a black screen with the message:

```
"Gnu Grub version 1.97~ beta 4 Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions

rescue:grub> unaligned pointer 0xb8

Aborted. Press any key to exit.
```

oops, so now I have to figure out what's wrong with grub. Come to find out 9.10 uses grub2, and many folks are having problems.

no amount of troubleshooting is getting me anywhere, so I am likely going to be reinstalling 9.04 with eee-control until 10.04 is out.

---

### Post by scubanator87 on 2009-12-27
Thats odd, i use 9.10 on y 901 with ext4 and i have noticed improved performance and none of the issues. 

Are you sure it is not the bios upgrade or the drive?

---

### Post by brallan on 2009-12-29
could be the drive i suppose. i actually had the 4GB phiso fail on me, so thats why i was running the OS on the 16GB, but it was pretty awful. I-d heard that ext4 was unstable, I assumed that was the problem. glad to hear it worked for you. many folks seem to think its faster.

in the end I installed an ext3 partition to the 64GB drive using an external USB box that the drive came with, grub installed OK.

i'll give ext4 a try and see if it speeds things up.

due to the install issues, I wound up using XP for a while. It was so unpleasantly depressing and worked so slow and unstable that all of the minor glitches I had had with running 9.04 on the phison 16gb seemed minor in comparison! Thank GNOD for Ubuntu saving me from the GATES of Hell!!!!! 

thanks for the feedback!

---

