---
title: "Unetbootin persistent login problems"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by onebir on 2012-06-13
I just used Unetbootin to create a persistent Xubuntu 11.10 install on a USB drive (FAT32). This worked fine the first time, but then required a password. I tried these combinations of logins and passwords:
```
ubuntu -
ubuntu ubuntu
xubuntu -
xubuntu xubuntu
root -
root root
root pass
root password
```
None worked. I reinstalled. Same thing. I mounted the casper file system:
```
mkdir /media/casper
mount /media/KITE/casper-rw /media/casper -o loop
```
And edited (/media/casper)/etc/passwd to delete the 'x' in the root line. Login fails, and the 'x' miraculously found its way back into the passwd line..

Has anyone come across this, or similar, or have any ideas about how to resolve it?

---

### Post by onebir on 2012-06-14
It looks like there's some fault on the USB drive that makes it incompatible with unetbootin's install; it often hangs up while it's writing the casper-rw file.

After I downloaded the xubuntu 11.10 iso again (despite the md5sum checking out) the 'Startup Disk Creator' managed to create a persistent xubuntu 11.10 install on the problematic USB drive. And I was just able to make one with unetbootin on a different USB drive. Neither has the login problem described above.

Both of these installs function normally in casual testing, with one oddity: it's impossible to delete files in the GUI. rm works in the terminal, but it'd be nice to be able to delete as normal in the GUI...

---

### Post by irv on 2012-06-14
There was some issues with 11.xx.
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

> Known Issues
Natty Narwhal 11.04 is having issues with USB flash drives from SanDisk that have U3 Launchpad. You can either use another brand or use either u3-tool from Ubuntu Repositories or SanDisk's U3 Launchpad Removal Tool to remove U3.

---

### Post by onebir on 2012-06-14
Thanks irv - couldn't see anything obviously relevant to this trash problem in 11.10 tho...

I mainly need a USB install for fallback purposes, so working round it with rm isn't too bad.

---

