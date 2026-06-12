---
title: "Athlon64 question: can i install the non-64 bit version?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by alexweber15 on 2005-10-17
hi all!
this might seem like a dumb question but here goes:

i recently tried to install the 5.10 preview release and it screwed up my boot record and partition tables beyond repair (tried everything but eventually gave up) and therefore rendered my windows installation unusable.

but its all good i've formatted and now that 5.10 is an official release i'd like to try it again... i'm just wondering: i have an athlon64 processor but i run WXP 32-bit at the moment and i wanted to get a dual-boot going with breezy badger... **which version should i install?  the "normal" one or the 64-bit one?**  what will the differences be?  thanks! :)

---

### Post by Dr. Nick on 2005-10-17
Either, I run the 64bit but you can use the 32bit and it will have more software support, The 64bit version is a bit harder to use since a few applications are missing right now but the 32bit should be just fine. The K7 kernel would probably be best so install it if it doesnt by default

---

### Post by alexweber15 on 2005-10-17
thanks!  that's what i wanted to hear!
32-bit it is!

---

### Post by chaok on 2005-10-18
Will installing the 32 bit cause any problems later with files or compiling your own stuff?  

I really don't like my 64bit because i can't do a lot of stuff I want.

Just curious.

---

### Post by Dr. Nick on 2005-10-18
oops read below

---

### Post by Dr. Nick on 2005-10-18
[QUOTE=chaok]Will installing the 32 bit cause any problems later with files or compiling your own stuff?  

I really don't like my 64bit because i can't do a lot of stuff I want.

Just curious.[/QUOTE]

Shouldnt be any problem compiling as the amd64 will run 32bit operating systems just fine, example windows. But if you have the 64bit Ubuntu I am really not sure if you could install 32bit over it or not. It may be better to erase all of your 64bit Ubuntu partitions and start with a fresh hard drive to install a 32bit, but I seriously doubt you will encounter any problems by running a 32bit version

---

### Post by chaok on 2005-10-18
Do I have to use expert install or regular?

---

### Post by tseliot on 2005-10-18
[QUOTE=chaok]Do I have to use expert install or regular?[/QUOTE]
Use the regular install

---

### Post by Biased turkey on 2005-10-18
If you ar an adventurous brave soul, go with the AMD64 bits version.
If you just want to run Ubuntu on your AMD64, install the x86 version  ( that's what I'm using now ).
Imho i'll just wait for the next release ( 6 months from now ? ) to go the 64 bits way.
P.S. I'm running Gentoo 2005 64 bits too on my AMD64 and I suspect the situation is the same with Ububtu 5.10 64 bits: The basic distro runs fine: KDe ( or Gnome ),  Gimp, Gcc, Alsa, Nvidia drivers , tect editor etc..
The problem is with specific 32 bits application and stuff like Mplayer.
Conclusion: the 32 bits ( x86 ) version will run just fine because the AMD64 is 100 % compatible for running 32 bits version of Linux or Windows.

---

### Post by Dr. Nick on 2005-10-18
Your pretty much right Biased_turkey the core OS and gnome plus gnomes system tools work, Mplayer runs, just not will all the w32codecs, Ive heard it can be done but havent had the need. 64bit Ubuntu and Gentoo I assume are similar in what can/cant run. The only thing I cant use that I want/need is flash, though i've heard that may change soon either by macromedia or by a 3rd party cleaning up the crashes in their version (forgot the name of the 3rd party flash app )

---

