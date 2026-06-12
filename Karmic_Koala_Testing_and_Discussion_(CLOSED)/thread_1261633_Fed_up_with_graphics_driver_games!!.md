---
title: "Fed up with graphics driver games!!"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-09-09
Ok, so yesterday I was able to install 'fglrx' and had all the 'goodies that go along with it. Desktop Effects were enabled and all was good. I did an update and bam!! All quit working but 'Hardware Drivers' said 'fglrx' was installed. So I gave up on all that and reinstalled Karmic 64 bit all over again about an hour ago. Ran all updates and rebooted. Went to 'Hardware Drivers' and clicked 'Activate', it ask for password and then nada. For some reason it won't install it now.
ATI Radeon HD3200. I do not understand and I am at the point where I am ready to just give up. But I am hoping some one here can help me pin point the problem.
Thanks to any one who can take the time to help me

---

### Post by simmeson on 2009-09-09
> **DougieFresh4U said:**
> Ok, so yesterday I was able to install 'fglrx' and had all the 'goodies that go along with it. Desktop Effects were enabled and all was good. I did an update and bam!! All quit working but 'Hardware Drivers' said 'fglrx' was installed. So I gave up on all that and reinstalled Karmic 64 bit all over again about an hour ago. Ran all updates and rebooted. Went to 'Hardware Drivers' and clicked 'Activate', it ask for password and then nada. For some reason it won't install it now.
ATI Radeon HD3200. I do not understand and I am at the point where I am ready to just give up. But I am hoping some one here can help me pin point the problem.
Thanks to any one who can take the time to help me

That's why you should stick with Jaunty until Karmic's released. Sad but true ;)

---

### Post by alphacrucis2 on 2009-09-09
> **DougieFresh4U said:**
> Ok, so yesterday I was able to install 'fglrx' and had all the 'goodies that go along with it. Desktop Effects were enabled and all was good. I did an update and bam!! All quit working but 'Hardware Drivers' said 'fglrx' was installed. So I gave up on all that and reinstalled Karmic 64 bit all over again about an hour ago. Ran all updates and rebooted. Went to 'Hardware Drivers' and clicked 'Activate', it ask for password and then nada. For some reason it won't install it now.
ATI Radeon HD3200. I do not understand and I am at the point where I am ready to just give up. But I am hoping some one here can help me pin point the problem.
Thanks to any one who can take the time to help me

Maybe using test versions isn't for you?

---

### Post by DougieFresh4U on 2009-09-09
> **simmeson said:**
> That's why you should stick with Jaunty until Karmic's released. Sad but true ;)

I do love the challenge :P
Running a 32 & 64 bit Karmic and I do have a Jaunty partition as well.
One thing that's really great about Ubuntu is that I can whip out a DVD and be up and running 'fresh' in about 15 or 20 minutes
Now the problem that I started about, got 'fglrx' going using the .31.10 kernel. But yesterday it was the .31.9 kernel that I first had 'fglrx' running on then it 'borked' some how (operator error).

---

### Post by dinxter on 2009-09-09
[EDIT] Doh! glad its resolved now :)

you could try
$ lsmod | grep fglrx
if this is empty then,
$ modprobe fglrx
$ dmesg
dmesg will show you if theres a problem inserting the module.
if all is well after that and the fglrx module is installed then you probably need to look at the X log, which is
/var/log/gdm/\:0.log 
if your using gdm
if that all looks fine then you might want to run 
$compiz --replace 
at the command line in the desktop to see if any errors show up

---

### Post by DougieFresh4U on 2009-09-09
> **dinxter said:**
> [EDIT] Doh! glad its resolved now :)

you could try
$ lsmod | grep fglrx
if this is empty then,
$ modprobe fglrx
$ dmesg
dmesg will show you if theres a problem inserting the module.
if all is well after that and the fglrx module is installed then you probably need to look at the X log, which is
/var/log/gdm/\:0.log 
if your using gdm
if that all looks fine then you might want to run 
$compiz --replace 
at the command line in the desktop to see if any errors show up

Thanks dinxter
Yeah, all is good for the most part. Will have a look using your tips.

---

### Post by waspbr on 2009-09-09
Finally some progress, don't know if this applies to the OP, though I have a radeon HD 3300, and after the last update to kernel *-10 the drivers [v6.60 installed through jockey] finally worked [as they should].

It's nice to see the full 3d again in my main machine.Now the only issue I have is getting pulse audio to behave

---

