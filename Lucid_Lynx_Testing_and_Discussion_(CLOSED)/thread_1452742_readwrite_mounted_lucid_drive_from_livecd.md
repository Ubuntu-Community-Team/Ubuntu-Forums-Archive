---
title: "read/write mounted lucid drive from livecd"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wademus on 2010-04-12
Hello!

The other night i updated my Lucid Lynx beta from .32-19 to .32-20 and it said it required a reboot, I did not reboot right away. An hour or so later I ran update again before I reboot it.

Upon reboot the system stops loading after grub and displays a screen that seems to be lots of jumbled text and numbers (?detecting devices?) and quits loading with the last line being

0060/serio0
[34.575032] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known

whatever that means right? i cant type to respond or anything

Being the genius that I am I edited my menu.lst file to only display the most recent version, so I cannot simply select .32-19 and avoid this whole mess

So I busted out the live CD thinking I'd edit the menu.lst to reinclude all previous versions on my drive, however I apparently dont have permission to do so on my mounted drive

Please Help!! How can I change permission to allow me to edit files on mounted drive /dev/sda2

Thanx!

any other insight to the problem is also welcome!!

---

### Post by dannyboy79 on 2010-04-12
well, how did you mount the drive? all you should have to do within the livecd is mount the drive to some location that you have editing capabilities, veen if you dont have write priveleges to say /media/ or /mnt/, then all you have to do is use sudo gedit menu.lst.

---

### Post by wademus on 2010-04-12
sudo mount blah/blah

is all I have been doing.

I am unmounting and awaiting instruction right now, how would you approach this?

---

### Post by sisco311 on 2010-04-12
At the grub menu press e & edit manually the linux & initrd lines, press Ctrl+x to boot.

---

### Post by wademus on 2010-04-12
that does work and I can boot, however it doesnt take me to a gui, just a command line interface

---

### Post by wademus on 2010-04-12
nevermind, upon a second reboot I am back in business!!

Thank you so much! I feel a hug is in order, or perhaps a beer.....

---

### Post by sisco311 on 2010-04-12
You're welcome!

Just mark this thread as [SOLVED]. :)

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

---

### Post by dannyboy79 on 2010-04-12
> **wademus said:**
> nevermind, upon a second reboot I am back in business!!

Thank you so much! I feel a hug is in order, or perhaps a beer.....editing a grub line while in grub is NOT permenant just so you know. you'll have to edit your menu.lst like you were trying before. i haev already told you, after you mount it, you can edit ANYTHING with sudo

---

### Post by wademus on 2010-04-12
yessir, but no while on the live cd a simple "sudo gedit" wouldnt allow me to edit the menu.lst file on the mounted drive, unless i did something wrong

---

### Post by dannyboy79 on 2010-04-12
> **wademus said:**
> yessir, but no while on the live cd a simple "sudo gedit" wouldnt allow me to edit the menu.lst file on the mounted drive, unless i did something wrong

you must have mounted the disk read only then. everytime i have been in a live cd, i see my disks on the desktop, i just double click it and it mounts itself. not sure which what options but I know I can edit the files with sudo gedit foo. so I am not sure how you were mounting the disk or why it appears to be mounting read only

---

