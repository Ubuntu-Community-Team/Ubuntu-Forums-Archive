---
title: "Burning Feisty .iso produces blank CD"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2007-05-19
Hey, I have a weird problem when trying to install Feisty on my parents Dapper system. I want to make a fresh install rather than upgrade as that usually gives a better result in my opinion.

I have downloaded the ubuntu-7.04-desktop-i386.iso from the Swedish mirror. I have checked it with md5sum and it checks out correctly (e296e3468358789904097fc8df29609a). 

This system is Dapper Drake i386 with everything up to date. I have tried two times to burn the .iso; first with GnomeBaker and then with K3b. Both of the tries produces the same result.

After burning the CD I rebooted my computer. The installation menu comes up. No problem so far. But no matter what I choose in the menu (except "Boot from first hard drive") I get an error, something like "Can't read from CD". So when I start Dapper again I try to access the CD and it reports it as a blank CD, opening the CD Creator. 

The one thing I noticed is that both GnomeBaker and K3b produced some warnings, but I never wrote them down and I'm reluctant to waste another CD just trying to find out what the warnings were. I do know that I noticed that both apps use an external burning software like "cdcreator" or something similar (again, I don't remember exactly) instead of what I am used to: dd or builtindd.

So, can anyone give me a simple tip on how to fix this without wasting lots of CD's on half-tries that only semi-work?

---

### Post by xodeus on 2007-05-20
> **Garyu said:**
> Hey, I have a weird problem when trying to install Feisty on my parents Dapper system. I want to make a fresh install rather than upgrade as that usually gives a better result in my opinion.

I have downloaded the ubuntu-7.04-desktop-i386.iso from the Swedish mirror. I have checked it with md5sum and it checks out correctly (e296e3468358789904097fc8df29609a). 

This system is Dapper Drake i386 with everything up to date. I have tried two times to burn the .iso; first with GnomeBaker and then with K3b. Both of the tries produces the same result.

After burning the CD I rebooted my computer. The installation menu comes up. No problem so far. But no matter what I choose in the menu (except "Boot from first hard drive") I get an error, something like "Can't read from CD". So when I start Dapper again I try to access the CD and it reports it as a blank CD, opening the CD Creator. 

The one thing I noticed is that both GnomeBaker and K3b produced some warnings, but I never wrote them down and I'm reluctant to waste another CD just trying to find out what the warnings were. I do know that I noticed that both apps use an external burning software like "cdcreator" or something similar (again, I don't remember exactly) instead of what I am used to: dd or builtindd.

So, can anyone give me a simple tip on how to fix this without wasting lots of CD's on half-tries that only semi-work?

then let's try the classic way of burning an iso.
Insert a blank CD-R in your drive.
Fire up your terminal.
Then make sure that you have the latest cdrecord
```
sudo apt-get update && sudo apt-get install cdrecord
```
Then execute a script to find your burning device
```
cdrecord -scanbus
```
You should see some info about your SCSI/IDE drives here like that:
```
mariusz@ubuntu:~$ cdrecord -scanbus 
scsibus0:
        0,0,0     0) 'LITE-ON ' 'DVDRW SHW-16H5S ' 'LS0W' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
mariusz@ubuntu:~$ 

```
In my case my burner is located at 0,0,0 we are going to use it now...
Then it's time to bake the CD.
```
cdrecord -v dev=0,0,0 /path/to/the/file.iso
```
Now press ENTER watch the process.

---

### Post by xodeus on 2007-05-23
Did it help?

---

### Post by bigken on 2007-05-23
all ever have to do is right clickhe iso  tand select burn to disc

---

### Post by wpshooter on 2007-05-23
I would get a CD-RW and go into k3b and FIRST do a **complete erase **on the CD-RW and then try the burn.

I never use CD-R media.

---

### Post by bigken on 2007-05-23
just a though could be a bad iso regardless of what checks say

---

### Post by mate on 2007-06-03
There is a REAL problem between Feisty iso and cd-rw drives. i have a ibm thinkpad r50e has a cd-rw drive. tried to burn feisty iso to a blank cd media several times. all of my tries caused same result: nothing. burned cd still appears as blank or can't readable. Additional, tried to burn using approx thinkpad machines ( r50p or something else ) and result was same.

BUT when a friend who has a ibm thinkpad with dvd-rw; burning and checking cd and then installing feisty is absolutely succesfull and smooth with no problems.

Is there something to fix this cd writer problem ? Is it about .iso file or burner drive ?

---

