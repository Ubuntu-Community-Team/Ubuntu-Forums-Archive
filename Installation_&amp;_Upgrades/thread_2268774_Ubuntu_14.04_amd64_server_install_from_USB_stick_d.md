---
title: "Ubuntu 14.04 amd64 server install from USB stick drive fails on busybox"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by wxadkin on 2015-03-11
I am a newbie to Ubuntu, so far not real happy with the experience sorry to say, here is why.

I am attempting to install the 14.04 server on a new Dell insperion box with a 64-bit Celeron processor, 4gb of RAM and 500g drive. I have repeatedly tried to install and each time the install fails when it gets to busybox-initramfs and stops. I can install the desktop, as a test, but I don't need this at the box is intended for a postgres server. 
:cry:
I have a deadline for this week to get the server stood up for testing and it looks like that is not going to happen

---

### Post by coldraven on 2015-03-11
Check the md5sum of the file you downloaded, see here: (scroll down a bit) [http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)
```
md5sum the_file_that you_downloaded.iso
```

If it does not match then download it again from that link.
Then I would delete everything from the USB stick and burn the image again. Make sure to select any hidden files and use Shift+Delete to skip the trash can.
I use Unetbootin to make my bootable sticks. It runs on Mac, Linux and Windows. Tip: it's faster if you don't select any "Space to preserve across re-boots"
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wxadkin on 2015-03-11
That did it thanks

---

### Post by coldraven on 2015-03-12
I'm glad that helped. You can mark the thread as solved using the thread tools at the top right of your original post.

---

