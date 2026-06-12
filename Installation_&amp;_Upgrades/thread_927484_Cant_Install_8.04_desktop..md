---
title: "Cant Install 8.04 desktop."
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by daGeneral on 2008-09-23
I've downloaded the installer and burned it to a cd. when I boot from the cd and try to install, installer does not start. I get the following error codes when i try to start ubuntu from the cd.

[92.435152] ata2.00: revalidation falied (errno=-5);
[92.530816] ata2: COMRESET failed (errno=-16);
[92.563881] ata2: exception Emask 0x1 SAct SErr 0x0 action 0x0 t4;
[92.563933] ata2: irq_stat 0x40000008;

wats happenin? how do i fix it?

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
sudo fdisk -l
```

---

### Post by Sef on 2008-09-23
Have you run 'Check Disk for Errors'?  Instead of booting into the live cd or installing, go down the list.

---

### Post by daGeneral on 2008-09-23
tried sudo fdisk -1

says that bin/sh/ sudo: does not exit


and btw cant check for error on cd too. goes to command line and gives the first 4 errors i stated


im big time noob to linux. so dont know wat the heck is hapenin

---

### Post by coffeecat on 2008-09-23
It's possible you've got a corrupted download of the iso, or a faulty burn. First, check the md5sum of your download - [instructions here]("https://help.ubuntu.com/community/HowToMD5SUM"). If your download passes that, try reburning at a lower speed. Full speed burning, even with good-quality media, sometimes results in a faulty burn. I use x4 and rarely have problems. The Ubuntu [Burning iso howto]("https://help.ubuntu.com/community/BurningIsoHowto") is useful, but it sounds as though you already have software for burning isos.

By the way, is that the Desktop (live) CD or alternate (text-based) CD you're using?

---

### Post by nerdjgua on 2008-09-23
Hi, 
I have the same issue.

On the last week, I just installed 8.04 release on my notebook and everything worked fine. But some things was not working to me, and I saw on Dell Wiki a release with some customizations and pre-built drivers. 

First of all, I downloaded the last 8.04.1 ISO from Dell Wiki website, burned the DVD media, start install and a custom menu from Dell tell me that it will ERASE all my information - OK. But at 82% of the copy of files, the ERRORNO 5 appeared. I tried to download again, from other mirror, burned with another brand of DVD-media and the problem still occuring.

Right... with the white flag on hands, yesterday I just downloaded the 8.04.1 release from Ubuntu Mirror (the original CD, not Dell Release), and voilla, the same error occurs!

I suspect the 8.04.1 release has a problem, because I've tried to download and burn several times the media (with several brands of cd-media) and returns the same error code to me.

I have a Dell 1525.

With pure 8.04 the system installs normally.

Does anyone with Dell 1525 could do a fresh install to see what happens?

Thanks in advance to all community.

---

### Post by augoldfinger on 2008-09-23
> **daGeneral said:**
> I've downloaded the installer and burned it to a cd....

What Program did you use to burn this?

Burning .iso with a Windows computer I like [Alcohol 120%.]("http://www.alcohol-soft.com/") You can try it before you buy it. I liked it so much, I bought it. It's a great program for burning iso's

---

### Post by daGeneral on 2008-09-23
I used nero7 to burn it. and md5 checksum is the same.

am gonna try to burn x4 burn and c wat happens.

thanx for the help guys

---

### Post by daGeneral on 2008-09-24
the checksum is identical to wants stated in ubuntu site.

tried burnin with alcohol at lowest speed setting. but still keep gettin the same error messages.

so wat do i do now?

---

### Post by robert shearer on 2008-09-24
[QUOTE=daGeneral;5839309]tried sudo fdisk -1

says that bin/sh/ sudo: does not exit


the command is sudo fdisk -l  (thats a lower case L not the number one)

---

### Post by pieknymarian on 2008-09-26
Hello,

This is not an problem with your image. I am having the same problem on my Dell Vostro 200 tower.

See here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

Regards,

Tikky

---

### Post by nerdjgua on 2008-10-01
> **pieknymarian said:**
> Hello,

This is not an problem with your image. I am having the same problem on my Dell Vostro 200 tower.

See here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

Regards,

Tikky

No, it's not a problem with HD SATA in IDE MODE.
I'm only get this error with 8.04.1 Release, but 8.04 works fine.

---

