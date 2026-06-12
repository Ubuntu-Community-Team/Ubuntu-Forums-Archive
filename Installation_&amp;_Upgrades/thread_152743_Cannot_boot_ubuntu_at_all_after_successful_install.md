---
title: "Cannot boot ubuntu at all after successful installation ............"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by sahibvirk on 2006-03-30
HAIL LINUX!!!!!!!

I use the Acronis OS-Loader to boot all the operating systems. I wanna uae it as my main boot loader. I installed ubuntu and put the LILO boot loader in the new ubuntu partition. I even mounted ubuntu some swap-space. Acronis detected the OS. When I click on its icon, it LILO boot loader is initiated. It starts loading ubuntu. But now is where the problem starts. Certain kinds of problems start showing up. These 2 are some of them:-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off

I repeated the installation twice, but faced the same problem.
Please tell me what to do.

And yeah, I dont want any other boot loader in my MBR. Because I bought the Acronis Disk Director Suite for a very costly price. And I use it to boot many other OS's(Windows xp[2-versions], FreeBSD, Fedora).


I thought maybe there is something wrong, typo, in my /etc/lilo.conf so I tried to post a copy of it.

Well guess what ??????????????????
There is no lilo.conf inside the /etc/ :-
Well let me tell you what actually happens when the ubuntu tries to boot. First the system shows some errors like these :-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off
Then it by itself logins as root into the shell. No XWindows, no graphics, no nothing......................................

Please help me. I have the original ubuntu installation CD's, so there cant be any problem with the installattion media. I just cannot understand whats going wrong here.
Please help.............................................. ....

I tried provide you people with the output of :
mount
cat /etc/fstab
fdisk -l /dev/hda
BUT:- both the commands are nopt working.

FOR ACRONIS OS LOADER:- It's a great software. Works perfectly with any other OS in the whole damn world. That is why I spent so much money on it..

Note: I dont want to use grub cause I am already multi booting too many OS's for it.



Any help will be appreciated.

Thanks in advance........................................... ...

YAO-YAO-YAO
KEEP SEEDING
KEEP SHARING
AS YOU HELP
SO SHALL YOOU REEP

---

