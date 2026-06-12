---
title: "messed with partitions and reinstalled windows. now have boot problems"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by mrpresident on 2006-12-26
Hi everyone.  
I installed ubuntu for first time the other day because I want to start learning how to use linux. I already had windows installed and my drive was split into quite a few partitons (see diagram). anyway so i installed ubuntu and everything was working fine...UNTIL i decided i had too many partitions and would merge some of them and reinstall windows on the newly merged partitions. anyway so i did that and reinstalled windows on sda/hd0. (for the record i havent changed anything about sdb/hd1 though.

after this computer would boot straight to windows and i realized it was the bootloader being overwritten in MBR. so i tried some commands in my ubuntu live cd, they were somethign like this: (but not exactly this)
   grub
   root (hd0,1)
   setup (hd0)
   quit.

anyway eventually i got it so that the grub options would come up again, but then it said error 22 if i tried to boot ubuntu. so i tried some other command (in which i mounted my ubuntu partition i believe (not exactly sure coz i was just copying from internet - ive only been using linux for like 2 days)).

so in the end i got it to the point where i get a grub 1.5 command line thing and neither windows will boot nor ubuntu . i have to type (root (hd0,0) chainloader +1, boot. everytime i want to get into windows. and i try to type root (hd0,5)| kernel /vmlinux root=/dev/sda6| boot. and it does start scrolling loads of lines but stops and sayd theres an error with the way ive specified the "root=" bit. then i have to restart.

i tried this super grub disk thing, but that just booted me into a different grub command prompt where it would say loading stage 1, then it would load stage 2. and then id have the grub> command prompt again but the same problems are there.

i can access my ubuntu partition from windows cause i installed some fs drive thing so if you guys need to look at my menu.lst or whatever i might be able to post them.
[IMG]http://x007.uploaderx.net/x/diagram.JPG[/IMG]
below is diagram showing how sda changed. note sdb stayed same, i didnt do anythign to it. i have a feeling i would have been able to fix it if i just reinstalled windows, but i think the fact that i merged partitions has caused more problems, but thats just a gut feeling of mine...
[IMG]http://x007.uploaderx.net/x/diagram.JPG[/IMG]
link to image because i dont think it is appearing : [http://x007.uploaderx.net/x/diagram.JPG](http://x007.uploaderx.net/x/diagram.JPG)

im sure i could fix the problem by doing fixmbr and then reinstalling ubuntu, but i started using it to learn more and i want to see this problem thru to the end (thats why i just made the longest post ive ever made at a forum).

lastly please forgive me if im not explaining this correctly or if i am failing to mention things which you need to know to help me. i will be checking this thread quite regularly and if anyone needs to know anything i will do my best to supply the info.


THANKS FOR YOUR TIME. I APPRECIATE IT.

---

