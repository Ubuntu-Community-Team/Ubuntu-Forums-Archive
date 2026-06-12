---
title: "Karmic not booting"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by umby24 on 2009-10-03
After a recent update, i took some time to be on windows, because I could not hear sound on linux ( the level was very very low, and yet it was all the way up )

so I simply used windows instead.

But, when I had watched my video and tryed to return to Ubuntu karmic, it would not boot.

Just a blank screen, not even a LCD backlight.

a few boots later it displayed some things on the screen,

including a bunch of I/O Errors, (on the recovery mode as well)

and something saying there was disk errors, and a check would be forced... but then it just froze.

and stayed there.


can you offer any insight?


(Karmic Alpha 7, btw)

---

### Post by stephana on 2009-10-03
is thera a console? can you specify the error messages?

greetz from germany, stephana

---

### Post by umby24 on 2009-10-03
No console that I know of, but I can type and it shows up. Let me write them down real quick

---

### Post by stephana on 2009-10-03
i'm not sure but i think this might be helpfull.

just type in: 

#: e2fsck /dev/hdaX (the X stands for the number of your volume)

---

### Post by umby24 on 2009-10-03
Grub has serverel differernt boot kernals, so heres what i got for 2 of them..


Kernal version 2.6.31 - 10 - Generic

Buffer I/O Error on Src0 Logical Block 0
Buffer I/O Error on Src0 Logical Block 1
Buffer I/O Error on Src0 Logical Block 2
Buffer I/O Error on Src0 Logical Block 3
Buffer I/O Error on Src0 Logical Block 4
Buffer I/O Error on Src0 Logical Block 5
Buffer I/O Error on Src0 Logical Block 6
Buffer I/O Error on Src0 Logical Block 7
Buffer I/O Error on Src0 Logical Block 8
Buffer I/O Error on Src0 Logical Block 9

Kernal Version 2.6.24-23

Blank Screen

Kernal Version 2.6.24-24

Starting up....

Mountall:/Proc: unable to mount: Device or resource busy
init: mountall main process (1353) killed by SEGV signal

---

### Post by stephana on 2009-10-03
sounds like a hard disk error, but i'm not sure. is your windows system installed on same drive? my only idea is to format the drive and reinstall, but maybe there is a better solution...

---

### Post by umby24 on 2009-10-03
hm.. i see.  its on the same drive, different partition.

---

### Post by kansasnoob on 2009-10-03
> **umby24 said:**
> Grub has serverel differernt boot kernals, so heres what i got for 2 of them..


Kernal version 2.6.31 - 10 - Generic

Buffer I/O Error on Src0 Logical Block 0
Buffer I/O Error on Src0 Logical Block 1
Buffer I/O Error on Src0 Logical Block 2
Buffer I/O Error on Src0 Logical Block 3
Buffer I/O Error on Src0 Logical Block 4
Buffer I/O Error on Src0 Logical Block 5
Buffer I/O Error on Src0 Logical Block 6
Buffer I/O Error on Src0 Logical Block 7
Buffer I/O Error on Src0 Logical Block 8
Buffer I/O Error on Src0 Logical Block 9

Kernal Version 2.6.24-23

Blank Screen

Kernal Version 2.6.24-24

Starting up....

Mountall:/Proc: unable to mount: Device or resource busy
init: mountall main process (1353) killed by SEGV signal

Was this an upgrade? If so from what to what?

The old 2.6.24-xx kernels have me at a loss, even Jaunty is currently on 2.6.28-15. Karmic is currently on 2.6.31-11.

---

### Post by VMC on 2009-10-03
> **umby24 said:**
> hm.. i see.  its on the same drive, different partition.

Lets start at the beginning. Output this ```
sudo fdisk -l
```. Also What hardware do you have; ATI, nVidia?

---

### Post by kansasnoob on 2009-10-03
If you boot into Recovery mode does it complete and drop you to a menu with several choices?

If so I'd choose the dpkg option and see what errors it spits back at you.

Or possibly choose the "shell w/networking" option and try some simple commands like sudo apt-get update, sudo apt-get upgrade, or sudo apt-get -f install.

---

### Post by umby24 on 2009-10-04
> **VMC said:**
> Lets start at the beginning. Output this ```
sudo fdisk -l
```. Also What hardware do you have; ATI, nVidia?

@ the above, I don't have a console, just a blank screen, so I am horribly doubtful that any linux terminal commands would work..

and I don't have ATI or NVidia...

I really have no clue what it is, but its neither.

My computer is a Compaq Presario C571NR Laptop, Original OS: Windows Vista


Was this an upgrade? If so from what to what?

The old 2.6.24-xx kernels have me at a loss, even Jaunty is currently on 2.6.28-15. Karmic is currently on 2.6.31-11. 	


It was after an upgrade, and those kernals are just different boot options I have, I could get pictures and video if needed, the upgrade was Alpha 6 to alpha 7

---

### Post by ranch hand on 2009-10-04
The 2.6.24 kernal series is from Hardy.  If you updated directoy from Hardy to 9.10 I can see why you are having problems.

---

