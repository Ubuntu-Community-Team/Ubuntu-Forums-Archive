---
title: "Revert to 8.04 from 9.10"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by cfirpo99 on 2009-12-18
Hi. im new to Linux.
 
Im trying to go back to 8.04 from 9.10 because I may be in over my head.  So I boot up with the new ISO i burned for 8.04 and it boots straight to GRUB naturally.  I understand GRUB deosnt boot CD's, and im assuming it gets called because it sees the Kernel from 9.10.
 
How can I just do a clean install with the tools I have?  Im still loading into 9.10 without a problem, but i have no idea how to format the drive or run the install from within the OS if at all possible.
 
Thanks in advance.. 
 
C

---

### Post by jerrrys on 2009-12-18
sounds like to me that your bios is not set to boot from cd

---

### Post by cfirpo99 on 2009-12-19
it sure is.  if i boot with the 9.10 CD it works just fine.  For some reason the GRUB shell (1.97 beta) loads when i use the 8.04 LTS CD, then im stuck.  Obviously it sees the previous install because the boot loader is asking me to choose from the menu or go to prompt.

I just want to start fresh with 8.04

Thanks

---

### Post by phillw on 2009-12-19
> **cfirpo99 said:**
> it sure is.  if i boot with the 9.10 CD it works just fine.  For some reason the GRUB shell (1.97 beta) loads when i use the 8.04 LTS CD, then im stuck.  Obviously it sees the previous install because the boot loader is asking me to choose from the menu or go to prompt.

I just want to start fresh with 8.04

Thanks

Boot from 8.04, the CD Boots - not your 9.10 install. Tell 8.04 to use the entire disk.

***NOTE*** You will lose EVERYTHING on your computer if you do this.

If you want dual booting or keeping data etc. post back with what you have on your computer & what you want to keep.

May I ask what problems you're having with 9.10 that makes you want to back to 8.04 ?

Phill.

---

### Post by cfirpo99 on 2009-12-19
Hi.  Im just testing with a gateway mx3210 laptop.  No sensitive data.  I was reading the beginner guide and it said that 804 was more stable, more drivers available etc.  Im unable to load drivers for Video and wifi in 910.

I have a broadcom chipset for built in wifi, and a linksys300N pcmcia card id "like" to use.

back to 804, when i use the boot cd, it goes straight to GRUB, not sure what command to use to have it wipe the disk and load the ISO from CD. 

Thanks for your help.

I would stay in 910 if it wasnt such a pain to get/load drivers.  I know people are doing it, Im just new at linux.

---

### Post by jerrrys on 2009-12-19
not to distract you from your goal for i am a true blue 804er, but Envy makes it fairly painless to load drivers.  you can find it in the 910 software store

---

### Post by cheesefry on 2009-12-19
I'm new to linux myself and am starting to get discouraged as 9.10 is my first ever distro of linux. In 2 days, I have had the hardest time to get things to work. Still no wireless, difficult time booting system, etc.... any suggestions as to what distro I should move to before hanging my head in shame and going back to win XP?? I have a Gateway LT20 netbook that is really great, but am ready to toss it out the window. 

Should I try 8.04??

---

### Post by jerrrys on 2009-12-19
Should I try 8.04??

yes and you find a better response by starting your own thread with that in the title :)

---

### Post by cfirpo99 on 2009-12-19
> **jerrrys said:**
> not to distract you from your goal for i am a true blue 804er, but Envy makes it fairly painless to load drivers.  you can find it in the 910 software store


Thanks but i have an S3 Video chip.  Dont think its supported by Envy.

---

### Post by jerrrys on 2009-12-19
interesting

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=s3+video+chip+support&as_qdr=all&sa=Google+Search&lang=en#1081](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=s3+video+chip+support&as_qdr=all&sa=Google+Search&lang=en#1081)

---

### Post by cfirpo99 on 2009-12-19
> **jerrrys said:**
> interesting

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=s3+video+chip+support&as_qdr=all&sa=Google+Search&lang=en#1081](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=s3+video+chip+support&as_qdr=all&sa=Google+Search&lang=en#1081)


doesnt look so good i suppose, my VIA/S3 board doesnt have a good history with linux.  No matter which version i run...

I guess i ll just have to keep reading..  BUT compatible hardware would be nice before installing...  On me i suppose. 

Thanks

---

### Post by jerrrys on 2009-12-19
opensuse has limited support

S3 
[LIST]
[*]ViRGE 2MB/4MB
[*]ViRGE/DX  2MB/4MB
[*]ViRGE/GX  2MB/4MB
[*]ViRGE/GX /2 2MB/4MB
[*]ViRGE/VX  2MB/4MB
[*]Trio32 1MB/2MB
[*]Trio64 1MB/2MB
[*]Trio64V+ 1MB/2MB
[*]Trio64V2/DX 1MB/2MB
[*]Trio64V2/GX 1MB/2MB
[*]801 1MB/2MB
[*]805 1MB/2MB
[*]Vision864 1MB/2MB
[*]Vision866 1MB/2MB
[*]Vision868 1MB/2MB
[*]911 1MB
[*]924 1MB
[*]928 1MB
[*]928 2MB/
[/LIST]

[http://128.194.106.6/~baum/linux/LDP/HOWTO/Hardware-HOWTO-6.html](http://128.194.106.6/~baum/linux/LDP/HOWTO/Hardware-HOWTO-6.html)

---

### Post by jerrrys on 2009-12-19
dose this apply to you?

[http://packages.ubuntu.com/hardy/xserver-xorg-video-s3](http://packages.ubuntu.com/hardy/xserver-xorg-video-s3)

---

### Post by cfirpo99 on 2009-12-19
my chip is S3 unichrome pro.  I found some other comments on this.  an I will try your link as well.  many thanks.  

I think ill try to get back to 8.04 first before i drive myself crazy.  then start loading some drivers..

---

### Post by cfirpo99 on 2011-08-08
Natty is good to me so far!

---

