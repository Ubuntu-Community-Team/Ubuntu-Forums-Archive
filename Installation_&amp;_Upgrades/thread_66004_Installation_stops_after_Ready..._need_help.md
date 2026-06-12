---
title: "Installation stops after Ready... need help"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by gutty on 2005-09-15
hi all,
I'm trying to install the Ubuntu on a old P4 233Mhz with 128M...

after i choose the linux installation I got the following:

Loading /install/vmlinuz
Loading /install/initrd.gz...................................
Ready

and after the ready, it stops...

any ideas?

Gutty

---

### Post by Zelut on 2005-09-15
The only time I ran into that issue was when I tried installing the x86 version on a 64bit PC.  Are you using the correct install CD?  That would be my first guess.

I'm sure it doesn't have anything to do with the age of the machine.  I've got ubuntu installed on an ANCIENT 90's IBM Thinkpad..  I'd suggest even trying another CD if you have one or can burn one.  Could be a data/burn error

---

### Post by gutty on 2005-09-16
I try already that option, i did burn a new CD and the error is the same one...

Any other idea?
Gutty

---

### Post by jervine on 2005-09-16
maybe you downloaded the wrong file... you must have downloaded the amd64 version which supports 32bit or higher cpus... try downloading i386 version... and burn it..

---

### Post by gutty on 2005-09-16
well, I know what I downloaded...

in the README.diskdefines at the root directory isays in the first line:
#define DISKNAME  Ubuntu 5.04 "Hoary Hedgehog" - Release i386 

so, now that is clear I did download the i386 version...

any ideas why it get stock there?
Gutty

---

### Post by doyzilla on 2005-09-17
hi,

im installing version 5.04 [x86] for my P4 2.4ghz with 256mb..........

my problem was this, im intalling it when if it comes in analyzing my hard disk and cdrom it stops, i dont know why,

i tryed to install the version 4.10 [x86] then its continious but when it was updating there was an error. i cannot continue....

i dont know what to do.. help me pls.

---

### Post by darkmark on 2005-09-22
I have exactly the same problem with gutty. And I am sure I have downloaded the correct file. Any ideas? TIA O:)

---

### Post by mtron on 2005-09-22
did you check the md5 checksum with the ISO, and tried some of the special boot options? (hitting f2 -f8) when the boot promt from ubuntu comes up?

---

### Post by darkmark on 2005-09-22
[QUOTE=mtron]did you check the md5 checksum with the ISO, and tried some of the special boot options? (hitting f2 -f8) when the boot promt from ubuntu comes up?[/QUOTE]
I got the CD from ubuntu ShipIt!, so I'm assuming i dont have to checksum it. As I am a total noob, I am not familiar with special boot options. :razz:  i just hit the enter key in the boot prompt (if that's what you call it :-? ), then nothing.  :roll:  Thanks dude.

---

### Post by dbott67 on 2005-09-22
[QUOTE=darkmark]I have exactly the same problem with gutty. And I am sure I have downloaded the correct file. Any ideas? TIA O:)[/QUOTE]

I've had similar issues burning ISO's.  When I burn at higher speeds (40x +), I get a lot of read errors when installing, however, when I burn at lower speeds (typically 8x) I get great results.

So, I would recommend re-burning the image at 4x or 8x --- it may take longer, but it will eliminate the "bad burn" issue.

-Dave

---

