---
title: "Ubuntu hangs on startup"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by gaberiele on 2011-03-14
The computer was turned off while installing the updates and after you are no longer starts

Freezes at the point in image:
[http://gaberiele.files.wordpress.com/2011/03/g-003.jpg?w=470](http://gaberiele.files.wordpress.com/2011/03/g-003.jpg?w=470)

Ubuntu is 10.4

---

### Post by tommcd on 2011-03-14
Are you able to boot to recovery mode? If so, then try running:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then reboot. If that does not help, try:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```
Then reboot.
If that does not work, then try:
```
sudo dpkg --clear-avail && sudo apt-get update
sudo apt-get dist-upgrade
```
Then reboot. If still no success, then try:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade
```
If none of that fixes it, then post what errors you get if you can.
Just out of curiosity, why was the computer turned off while updating the system?
Did this happen from a running 10.04 system? Or did it happen while trying to upgrade from Ubuntu 9.10 to 10.04?

And welcome to the Ubuntu forums!

---

