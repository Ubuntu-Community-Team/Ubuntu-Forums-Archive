---
title: "Trying Ubuntu 12.04 without installing gets a black screen"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by reychun on 2012-07-23
Hello, I did a clean installation of Ubuntu 10.04 today (because my computer has always been stuck on tty1 for every Ubuntu 12.04 boot). I have burned both Ubuntu 10.04 and 12.04 into LiveCDs. 

**So here's the question:** should I install Ubuntu 12.04 if I see a black/blank screen from just trying to test Ubuntu 12.04 without installing? I have enabled [PAE ]("https://help.ubuntu.com/community/EnablingPAE/")and tried to test Ubuntu 12.04 again but I still get a blank screen.

My computer is Acer Aspire AX5900 and with the nvidia card. Note: not sure if nvidia-current has anything to do with it because I purged it before I freshly installed Ubuntu 10.10.

Feel free to ask me anything or for command outputs because I do want to use the latest version of Ubuntu. Thanks.

---

### Post by JeffThePCGeek on 2012-07-23
Have you tried enabling "Nomodeset" in Grub when booting?  I had an issue similar to this with a previous Nvidia Card.  Nvidia 5200FX

---

### Post by confused57 on 2012-07-23
See this link:
[http://askubuntu.com/questions/127180/12-04-boots-to-blackscreen](http://askubuntu.com/questions/127180/12-04-boots-to-blackscreen)

I believe it's a problem with backlight on some Acer Aspires.

---

### Post by reychun on 2012-07-24
> **JeffThePCGeek said:**
> Have you tried enabling "Nomodeset" in Grub when booting?  I had an issue similar to this with a previous Nvidia Card.  Nvidia 5200FX

I changed the option to nomodeset but this is what I get:

[http://img829.imageshack.us/img829/6813/a6cc14e83679155e7d6c453.jpg](http://img829.imageshack.us/img829/6813/a6cc14e83679155e7d6c453.jpg)
[http://img818.imageshack.us/img818/705/279746ba8c6441e54ee7110.jpg](http://img818.imageshack.us/img818/705/279746ba8c6441e54ee7110.jpg)
[http://img267.imageshack.us/img267/3788/c33c7b9a567bbddc8ff0175.jpg](http://img267.imageshack.us/img267/3788/c33c7b9a567bbddc8ff0175.jpg)

And after all the loading, I ended up having the same tty1 screen I had when I installed Ubuntu 12.04 (before I re-installed Ubuntu 10.04 again)

[http://img98.imageshack.us/img98/9118/50e51855224dab119489031.jpg](http://img98.imageshack.us/img98/9118/50e51855224dab119489031.jpg)

If I used quiet splash, the screen would flicker and  then go blank/black (the monitor switches off) but the CPU is still switched on. 

I have upgraded to Ubuntu 11.10 via LiveCD according to one of the suggestions in [http://askubuntu.com/questions/12718...to-blackscreen]("http://askubuntu.com/questions/127180/12-04-boots-to-blackscreen"), but **have not installed Ubuntu 12.04**. Considering my previous experience, there was no need to type Ctrl+Alt+F1 because the computer boots in tty1. And the command prompt

> sudo service lightdm restart

does not work. So what should I do?

---

### Post by sid0972 on 2012-07-24
this black screen hangup occurs in my case too
not always, but frequently
usually during startup

any idead why?
system specs 
amd 1090t
4 gig ram
asus mobo
ati 5850 cf (using onboard atm)

also, dual boot with w7

---

### Post by sid0972 on 2012-07-27
i solved my issue
bad, half dead motherboard

---

