---
title: "Problems after Phase-1 of installation::::::::: :("
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by sahibvirk on 2006-04-11
Cannot boot ubuntu at all after installation phase-1 ............

I use the Acronis OS-Loader to boot all the operating systems. I wanna uae it as my main boot loader. I installed ubuntu and put the LILO boot loader in the new ubuntu partition. Acronis detected the OS. When I click on its icon, it LILO boot loader is initiated. It starts loading ubuntu. But now is where the problem starts. Certain kinds of problems start showing up. These 2 are some of them:-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off

I repeated the installation twice, but faced the same problem.
Please tell me what to do.

And yeah, I dont want any other boot loader in my MBR. Because I bought the Acronis Disk Director Suite for a very costly price. And I use it to boot many other OS's(Windows xp[2-versions], FreeBSD, Fedora).

I even tried to check the typo, in my /etc/lilo.conf ,and tried to copy it.
Well guess what ??????????????????
There is no lilo.conf inside the /etc/ :-

This is what actually happens when the ubuntu tries to boot. First the system shows some errors like these :-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off
Then it by itself logins as root into the shell. No XWindows, no graphics, no nothing......................................

Please help me. I have the original ubuntu installation CD's, so there cant be any problem with the installattion media. I just cannot understand whats going wrong here.

I tried to provide you the output of:
mount
cat /etc/fstab
fdisk -l /dev/hda
But both the commands are not working.


Please help.............................................. ...

Any help will be appreciated.

Thanks in advance........................................... ...


YAO-YAO-YAO
KEEP SEEDING
KEEP SHARING
AS YOU HELP
SO SHALL YOOU REEP

---

### Post by afonic on 2006-04-11
Hi,

1) Seems like that Acronis messed things up.
2) Ubuntu uses grub, not lilo.
3) What does the poll have to do with the topic?

I voted for the last option. Windows95 is the best OS in the world.

---

### Post by angkor on 2006-04-12
[QUOTE=sahibvirk]I even tried to check the typo, in my /etc/lilo.conf ,and tried to copy it.
Well guess what ??????????????????
There is no lilo.conf inside the /etc/ :-
[/QUOTE]

Have you tried running lilo again by booting the install cd using the 'rescue' option?

Also check this thread, if you haven't already:

[http://ubuntuforums.org/showthread.php?t=94250&](http://ubuntuforums.org/showthread.php?t=94250&)

Maybe there's some useful info in there.

I'm no expert on lilo and don't even know acronis so can't help you there.

[quote=afonic]2) Ubuntu uses grub, not lilo.[/quote]

You can choose to install lilo in stead of grub in the ubuntu installer.

Edit: I chose the first option on the 'useless but an interesting attempt to attract attention to your problem poll'...;) Ubuntu's got everything I need. (OS-wise that is :))

---

### Post by dbd on 2006-04-13
It might be worth trying to install grub (or lilo, doesn't really matter) to a floppy disk (that will be /dev/fd0), then you can boot that boot loader with the floppy, and otherwise boot your normal boot loader.
This isn't really the best long term fix, becuase it can be annoying, but at least if it works it might help to show you where the problem is. I think you can do this with the install cd's resuce option, and just chose to install lilo/grub to /dev/fd0.

Good luck

BTW: I voted for the heavy graphics one. Even though some games work fine with wine (World of Warcraft, Warcraft 3, Counter Strike) there are many others which simply don't work.

---

### Post by sahibvirk on 2006-04-14
Fine I will give this one a try........

And yeah.... :
You dont get much of the truth if you ask one person. And I needed to know wheather ubuntu is worth an install or not.
That is the reason the poll was included..

Thanks..........

---

