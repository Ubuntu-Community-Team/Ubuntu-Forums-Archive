---
title: "can't install on elonex dfy30 laptop"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by gobbledigook on 2010-07-08
Hi there!

i recently purchased an elonex dfy30, never heard of the brand or model before but it has a fair spec and was cheap :) I have been trying to install 10.04 on it, but cannot even get the live CD to work :( i have tried several options all with the dame result, after selecting install/try without changes i get a screen of text and it freezes, i have to ctr-alt-del to reboot... the last line is:

```
[  0.947053] sr 1:0:0:0: attached scsi generic sg1 type 5
```

i have tried installing inside windows, and on reboot i get the option for ubuntu, but when i select it i get:

```
error: couldn't read file
error: you need to load the kernel first.
```

i have also tried the alternate cd and get the same result!

also i am finding it tough to get any info on my laptop... here is what i have from belarc advisor and what i could find on the web:

[**_belarc_**]("http://gobbledigook.homelinux.net/BelarcAdvisorCurrentProfile.htm")

[**_hardware info_**]("http://smolt.fedoraproject.org/client/show/pub_6e227290-bf8b-47e0-8401-d2ce62535db6")

sorry for the lack of info, any ideas?

thanx

---

### Post by davidmohammed on 2010-07-08
it looks like you've got a graphics card called "SIS" - never heard of it myself.

Anyway - when you boot the live CD - press F6

at the bottom is your boot string.

before quiet splash --

can you add

video=sisfb

or possibly

video=sisfb:mode:1024x768x32,rate:70,mem:4096

e.g.

... ro video=sisfb quiet splash --
and then choose "try without booting"

does this work?

---

### Post by gobbledigook on 2010-07-09
thanx for you reply! 

I will try this evening when i get home from work and let you know how i get on.

i sucessfully installed mandriva spring 2009 from a disc i got off a magazine (spring 2009 obviously ;) ) just to see if another distro worked... but i really want to get ubuntu working as i'm simply used to it!

now i know it is an issue with the SiS M661FX display adapter i have found some more info about this - more for my own ref here are some links to info about it including a bug where you need to reduce the shared memory in bios - something which i have increased!!

[**_Bug_**]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/291294") about #11

[**_graphic info_**]("http://www.winischhofer.net/linuxsispart1.shtml#12")

---

### Post by gobbledigook on 2010-07-09
ok i have now tried both:

video=sisfb:mode:1024x768x32,rate:70,mem:4096

video=sisfb

and reduced the shared memory from 64 to 32mb in bios (32 being the default) 

all with no effect :(

i will try and battle with mandriva over the w/e to see if i cannot simply install from that or at least find out what drivers IT is using for my graphics :) But for now... its friday so i'm gonna chill :)

feel free to chime in with any ideas ;)

thanx!

---

