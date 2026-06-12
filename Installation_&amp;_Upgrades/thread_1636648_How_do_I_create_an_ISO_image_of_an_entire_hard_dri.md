---
title: "How do I create an ISO image of an entire hard drive running a Linux OS?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by nerdybrunette on 2010-12-03
Hello all!
 
Does anybody know how to or even if it's possible to create an ISO image (a snapshot, if you will) of an entire volume on a Linux box so that I can use that ISO to burn to a CD use in the future for creating an identical configuation on another box (which would have the same exact hardware)?   

It is to my understanding that I'd have to first create the ISO file of the entire system and then burn it to a CD and somehow mount it onto the hard drive of the identical-system-to-be. 
 
I'm thinking that I'd have to use the "mkisofs" command but I'm not sure exactly how to do this. 
 
**P.S. I do not want to use any 3rd party applications.**
 
Thanks in advance for all of your help :)

---

### Post by luca.cappelletta on 2010-12-03
quick answer: dd ;)

---

### Post by endotherm on 2010-12-03
if the system is cd sized, then dd/partimg/clonezilla/etc will all work, but it won;t result in a bootable CD. it is an image, but it's not a CD image. if you use dd to create your image, and burn off the disk, you will have to boot the new machine off a livecd and use dd again to copy the image from the disk to your target partition.

---

### Post by nerdybrunette on 2010-12-03
Okay, thanks for all of the input! Clonezilla is a little confusing to me so I'll just use dd to create the image.
 
Another question: 
What if I wanted to be able to pop in a CD on the identical-system-to-be and grab that image I just made from a server? Could I simply just make a bootable Ubuntu CD with a script on the desktop that ran a command like:
 
```
(somehow grab the image from the server) | dd of=/dev/sda
```
 
:confused:

---

### Post by Megaptera on 2010-12-03
I like to make a CD/DVD backup of my setup using Remastersys. Guide here: [http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043) I can then re-install as reqd.

---

### Post by endotherm on 2010-12-03
> **nicolemarie said:**
> Okay, thanks for all of the input! Clonezilla is a little confusing to me so I'll just use dd to create the image.
 
Another question: 
What if I wanted to be able to pop in a CD on the identical-system-to-be and grab that image I just made from a server? Could I simply just make a bootable Ubuntu CD with a script on the desktop that ran a command like:
 
```
(somehow grab the image from the server) | dd of=/dev/sda
```:confused:
well all you woudl have to do is map the server share locally. then run 
```
dd if=/path/to/share/mount/img.iso of=/dev/sda
```

---

### Post by nerdybrunette on 2011-01-14
Thanks for all of the help, everyone.
 
FYI, I ended up using Ghost 4 Linux ([G4L]("http://sourceforge.net/projects/g4l/")). It was very easy to use!

---

