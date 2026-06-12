---
title: "yet another one of those &quot;job control&quot; errors"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by dracomordag on 2007-07-25
alright, i've searched through about 20 threads all relating to the common "job control" error message (/bin/sh: can't acces tty; job control turned off) and none of them seem to really address my specific problem. ie, theyre insalling on older computers, its after an upgrade, etc.

I am attempting to install Ubuntu on a partition of my new laptop. It has the new santa rosa Intel Dualcore 2.4 GHz processor, a 200 GB HD, nVidia GeForce 8400, 2 GB RAM,  DVD RW +/- whatever drive, etc. 

It came loaded with Vista (which still functions properly despite my attempts with the LiveCD so far), and i've used up about 100 GB so far of its HD.

any ideas? ctrl+alt+F1 just gets me ```
[    0.368247] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:0 1:00.0
```


i've gotten Feisty loaded perfectly on my desktop (see my signature), but i cant seem to get it on this one.

---

### Post by nichipet on 2007-07-25
Which model laptop is it?

---

### Post by dracomordag on 2007-07-25
sony vaio fz (no blu-ray, though)

---

### Post by dracomordag on 2007-07-25
your post made me think to add the words "vaio fz" to my search, and i found [this thread](http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off), which gets me a lot farther. i get an x server error (odd, normally nVidia cards work fine)

i'll come back if i encounter more problems

---

### Post by dracomordag on 2007-07-25
alright, my typical approach "sudo dpkg-reconfigure xserver-xorg" does not work at all. it leaves me with the following errors:
```
(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server: ":0.0"
     after 0 requests (0 known processed) with 0 events remaining
```

---

### Post by nichipet on 2007-07-25
When and how do you receive those errors? Are they after a reboot? Did you accept the defaults or enter values that you know apply to your computer? If you accepted defaults, that may be the problem.

---

### Post by zach382 on 2007-07-25
Im having this same problem. I have an error ```
 [    0.368247] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:0 1:00.0I
```  Then i get ```
/bin/sh: can't access tty; job control turned off
``` Can anyone suggest any ideas?. I have close to the same specs, 2.0ghz santa rosa, 8400 video card, 2 gig ram, its a brand new hp dv 6500t. The ubuntu live cd doesnt load for me, neither does xubuntu, kubuntu, sabyon, the only one i found that works is the fedora 6 live cd.

---

### Post by nichipet on 2007-07-25
zach382:

Have you looked at [http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off) ? It is a thread that dracomordag posted earlier and if you are using a Sony Vaio, it may be of some help.

---

### Post by zach382 on 2007-07-25
No im using an HP dv6500t, but ill look at it. Thanks for the link.

---

### Post by dracomordag on 2007-07-25
when i boot and hit "run/install ubuntu" or whatever, i get
```
/bin/sh: can't acces tty; job control turned off
```

to fix it, on boot up (before hitting run/install) i hit F6 for "more options" and add ```
break=top
``` to the line. after it starts running linux, i get an different error and then a command line, into which i type ```
modprobe piix
exit
```
this lets it boot up more, but then i get
[img]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0044.jpg[/img]

now, when this happened on my old computer (which is where i got that picture from) (also, the "job control error" didnt happen to my old computer), i just ignored the error so it would give me a command line, into which i would type ```
sudo dpkg-reconfigure xserver-xorg
``` and then let it auto-detect everything (aka hit enter over and over again) and then it would start up fine.

now when i let it autodetect (it tries the NV driver, btw), it still doesn't work, giving me an error of ```
(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server: ":0.0"
     after 0 requests (0 known processed) with 0 events remaining
```


i have no idea what to do now.

remember, my processor is a 2.4 GHz santa rosa intel, and my video card is a nVidia GeForce 8400M GT

---

### Post by zach382 on 2007-07-25
> **dracomordag said:**
> when i boot and hit "run/install ubuntu" or whatever, i get
```
/bin/sh: can't acces tty; job control turned off
```

to fix it, on boot up (before hitting run/install) i hit F6 for "more options" and add ```
break=top
``` to the line. after it starts running linux, i get an different error and then a command line, into which i type ```
modprobe piix
exit
```
this lets it boot up more, but then i get
[img]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0044.jpg[/img]

now, when this happened on my old computer (which is where i got that picture from) (also, the "job control error" didnt happen to my old computer), i just ignored the error so it would give me a command line, into which i would type ```
sudo dpkg-reconfigure xserver-xorg
``` and then let it auto-detect everything (aka hit enter over and over again) and then it would start up fine.

now when i let it autodetect (it tries the NV driver, btw), it still doesn't work, giving me an error of ```
(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server: ":0.0"
     after 0 requests (0 known processed) with 0 events remaining
```


i have no idea what to do now.

remember, my processor is a 2.4 GHz santa rosa intel, and my video card is a nVidia GeForce 8400M GT
This is exactly the same thing that happened to me. I did the same exact thing (the break=top and modprobe piix thing) and i got that same exact screen. Could it be my video card doesn have proper drivers by default in ubuntu? I have an 8400M GS. I am really frusterated that I cant run ubuntu. I really wanna try out Compiz Fusion on my shiny new laptop.

---

### Post by dracomordag on 2007-07-26
anyone?

i guess there goes any hope i had of using ubuntu.

---

### Post by nichipet on 2007-07-26
Based on this thread: [https://lists.ubuntu.com/archives/ubuntu-users/2007-June/115689.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/115689.html)

I would suggest trying an alternate CD, if you were using a Live CD.

---

### Post by dracomordag on 2007-07-26
im very worried about partitioning using the alternate CD, though.

i may give it a shot.

---

### Post by nichipet on 2007-07-26
> **dracomordag said:**
> im very worried about partitioning using the alternate CD, though.


Why?

---

### Post by dracomordag on 2007-07-27
no idea how, basically. i've been trying to read up, but i cant find any halfway-decent instructions.

plus, if i can't get it to install visually, what are the chances that it'll work when i install it text based? the text-based install won't change anything.

---

### Post by dracomordag on 2007-07-27
alright, well it turns out the nVidia GeForce 8400 is too new to use the nv driver included on the live CD, so i just gotta use vesa and then install the new driver once Ubuntu is installed

will update if any more errors pop up

---

### Post by Cavalier1723 on 2007-07-27
i have an fz190 as well
this thread covers similar problems:

[http://ubuntuforums.org/showthread.php?t=486861&highlight=vaio](http://ubuntuforums.org/showthread.php?t=486861&highlight=vaio)

I've been messing with patch_sigmatel.c all day trying to get headphone jack sensing with not much luck

let me know if u get it

also, i installed nvidia drivers with no problems using envy

---

