---
title: "help with usb install"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by MeThePeople on 2010-11-08
Trying to do a recovery of information from my broken laptop. I get to the ubuntu 10.10 screen with flashing dots, its says checking battery state then boots into the terminal instead of giving me the option to try or install. I had the same problem last week but after restarting a few times it eventually worked, now 2 days later im still trying to get it to load. Any advice?

---

### Post by dino99 on 2010-11-08
is it installed or are you trying to install it ?

maybe noacpi can help when booting: add it (F6 if i remember) when you try installation

---

### Post by MeThePeople on 2010-11-08
im just trying to try it so i can access information on the hdd

---

### Post by thegod_slayer on 2010-11-08
> **MeThePeople said:**
> Trying to do a recovery of information from my broken laptop.

first of all if your laptop is broken then who can any recovery cd recover data from it.

 > I had the same problem last week but after restarting a few times it eventually worked, now 2 days later im still trying to get it to load. Any advice?

does your restart technique not work now ??

>   I get to the ubuntu 10.10 screen with flashing dots, its says checking  battery state then boots into the terminal instead of giving me the  option to try or install


now for this problem....... try this.....
[http://ubuntuforums.org/showthread.php?t=1458355](http://ubuntuforums.org/showthread.php?t=1458355)

please google these problems first......
you surely will get your answer.

---

### Post by MeThePeople on 2010-11-08
first of all if your laptop is broken then who can any recovery cd recover data from it.


well theres lots of different types of broken so who can recover data from it? me thats who


does your restart technique not work now ??

if it worked i wouldent be asking this question. It did once, im trying to do it again.



now for this problem....... try this.....
[http://ubuntuforums.org/showthread.php?t=1458355](http://ubuntuforums.org/showthread.php?t=1458355)

please google these problems first......
you surely will get your answer.


i did google first and the link you gave me has nothing to do with my problem. i have not installed ubuntu on that computer yet. just trying to run it off of a usb so i can gain access to information on the hdd since windows decided to hang its self.

instead of going to the try ubuntu or install ubuntu screen it just goes straight into the terminal, nothing else on the screen just ubuntu@ubuntu:~$  im not trying to install it just want to run it live. the usb works just fine seeing how i installed it on all my other computers months ago and tested it on them again when it wouldnt work on the broken one.

---

### Post by sikander3786 on 2010-11-08
Hi.

You need to try the boot parameters as dino99 mentioned above? You mentioned "help with USB install" so i assume you are trying to run a Live USB. It would be handy to know how the USB was prepared. Which software was used to create it?

It would also be handy at first to check the integrity of 10.10 image to make sure the image is not corrupt itself.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums are correct, you can proceed to boot parameters.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

You need to try all of those if the first one doesn't work. I guess noapic or nomodeset should work for you.

---

### Post by uRock on 2010-11-08
> **thegod_slayer said:**
> first of all if your laptop is broken then who can any recovery cd recover data from it.

Quite obviously the OS on the laptop is broken.

To the OP, Can you boot the system with the LiveCD? If yes, then you can run the LiveCD and use it to drag and drop files to your thumb drive.

If the LiveCD is dropping to the command line, then your problem may have to do with the system's graphics hardware. What are the system's specs?

---

