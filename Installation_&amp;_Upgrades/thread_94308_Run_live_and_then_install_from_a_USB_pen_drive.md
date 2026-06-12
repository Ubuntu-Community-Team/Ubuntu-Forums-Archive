---
title: "Run live and then install from a USB pen drive"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by brianlparkinson on 2005-11-23
Hi
I have an IBM X24 Thinkpad running W98 on which I want to run ubuntu (removing w98 altogether). This machine has no CD drive (either internal or external). I do have a 1gb usb 2.0 pen drive which works with the laptop.
I would like to run 'live' from this device to check out the pc and network connections before installing (again from this drive). 
Just copying the cd contents across did not work, neither did making the pen drive bootable (from a fdd created from my Windows xp desktop) and running start.
Can any kind sole out their offer me any help firstly with 'live' then with installation? As you may gather I am new to Linux although not to pcs
Kind Regards
Brian

---

### Post by Arktis on 2005-11-23
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

---

### Post by brianlparkinson on 2005-11-27
Thanks for the pointer - I now have a secondary problem in that having got syslinux onto the stick and the other files plus the contents of the install file I am now recieving a "missing operating system" message. 
There is a suggestion that the mbr may be corrupt but whilst I have downloaded the debian mbr package I cannot find a way to install it as and so run mbr.
Linux Format instructs me to 'make install' from root but I get a missing command late last night (early this morning) I posted for a copy of mbr - currently I am wading in syrup :-) still at least I am exploring the swamp. Can anyone help?
KInd REgards
Brian

---

### Post by brianlparkinson on 2005-11-27
Well, I have returned to my Windows machine and found PeToUSB. [http://codebeetle.com/page.php?al=petousb](http://codebeetle.com/page.php?al=petousb)
This has successfully formatted and created a new mbr on my stick. Hurray. Now I have 
         could not find kernal image: vmlinux.cfg
Still I live and learn

Brian

---

### Post by brianlparkinson on 2005-11-28
Ok now it is all going! Not the way I intended but what the heck. Will post to another thread to explain what I had to do to get my setup working.

---

