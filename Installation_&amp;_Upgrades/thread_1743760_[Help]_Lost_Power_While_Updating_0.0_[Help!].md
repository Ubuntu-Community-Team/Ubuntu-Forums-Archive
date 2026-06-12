---
title: "[Help] Lost Power While Updating 0.0 [Help!]"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bobdotexe on 2011-04-29
So here's the short version:

I was updating to 11.04 from (last 6mo cycle {I forget the number})
and after the Downloading of all the updates, I was at the installing part I found out I was late going to {unimportant} and I needed my laptop their. So I put my laptop in suspend.

when I re opened my laptop I noticed it was still powered up. So I tried to Resume it,
but noting worked, So I left it alone for about 45 mins, and then I tried the power button, and that did not work, so I had to hold it in for 10 seconds (hard reboot) and then when I booted up again it said "the disk for ./ cannot be mounted" and said continue to wait or press 's' to Skip or 'M' to fix manually, I tried all three and all three failed. so I tried to use my Live USB and use 'chroot' but it did not work, {my flash drive has 32bit, PC 64 bit :P } when I found this out I had to find the CD I used to install it (not Ubuntu 11.04, it was the 10.XX)  and I was able to 'chroot' to it And I found some guides on line that say use 'apt-get install -a' and dpkg stuff  (I will post what I used, but I have to find the text file again...) and I got something about dev/null. I will Reboot again, and write down word for word the errors, but I decided to put this up first:

Machine:
Dell vostro 1310
processor: intel core 2 duo
OS: window7 32bit / ubuntu 64bit

(note: I also tried recovery mode But I got the same message I got from a normal boot.)
--------------
here's what i did:

sudo chroot /mnt/repair su

sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade
-----------------------
each one Failed;
I had an active internet connection,
but the "apt-get upgrade" Said
'This will take up 0kb do you want to install?'
I said 'Y'.. and it still failed, saying too many errors.

---

