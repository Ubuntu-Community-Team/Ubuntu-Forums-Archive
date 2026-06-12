---
title: "DD install?"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by ubuntu.daemon on 2007-08-19
My current install is having some issues, but anyways point is when i try to do a new install on this laptop it goes awry, is there a way to like make an install inside of my own?  or dd an install i make on another computer?

---

### Post by GarlicFish on 2007-08-19
I've not used DD to install Linux, but I have used it for imaging and installing Windows.

Things to watch out for are Partition Tables and the boot sector.
When I was doing it, I had to make a separate DD image of each partition (/dev/sda1, /dev/sda2 etc) + the first 460ish (can't remember exact figure) bytes of /dev/sda which contains the boot sector but excludes the partition table.

Then find a live CD which includes the networking tools you need to transfer the image from your server/external disk.  I used Netcat.

Frankly, there are easier ways to transfer a linux system such as Rsync.

It's probably going to be easier to figure out why your install is failing in the first place.  You may go through all the hassle of re-imaging your laptop only to have it still not work right.

What is going wrong with the install that has you looking at DD in the first place?

---

### Post by ubuntu.daemon on 2007-08-20
like idk it just lags, i have xubuntu and it gives me issues, though when i had gnome on the same laptop there was no problem.......

---

