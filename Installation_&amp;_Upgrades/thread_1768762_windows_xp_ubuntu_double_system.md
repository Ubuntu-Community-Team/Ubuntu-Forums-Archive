---
title: "windows xp ubuntu double system"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by alex_goacross on 2011-05-27
Hi!

I am going to install the ubuntu 10.0.4LTS to my hard disk under windows XP,
here is what i tried

1.down the iso:ubuntu-10.04.2-desktop-i386.iso file from ubuntun.com
2.down the unetbootin-win-549.exe and write the iso file to my USB disk
3.reboot my system to boot from usb disk
4.as i expect, every thing goes well util i got the err like this:
---------------------------------
[B]Installation Failed
The following file did not match its source copy on the CD/DVD:
/target/use/lib/openoffice/basis3.2/program/lib/plug_genli.so

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.
It may help to clean the CD/DVD, to burn the CD/DVD at o lower speed, to clean the CD/DVD drive lens(cleaning kits are often available from electronics supplier),to check whether the hard disk is old and in need of replacement, or to move the system to a cooler enviroment.[/B]

After this err, another err pop-ups

[B]The installer encountered an error copying files to the hard disk:
[error 5] input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.
It may help to clean the CD/DVD, to burn the CD/DVD at o lower speed, to clean the CD/DVD drive lens(cleaning kits are often available from electronics supplier),to check whether the hard disk is old and in need of replacement, or to move the system to a cooler enviroment. 
[/B]

---------------------------------

I do not know what is going on!
Any information will be appreciated!
Alex

---

### Post by Rubi1200 on 2011-05-27
Hi and welcome to the forums :-)

These are the steps I advise to troubleshoot this:

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

post the specifications especially RAM and graphics card.

it would also help to know the make and model of the computer.

Thanks.

---

### Post by alex_goacross on 2011-05-27
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

These are the steps I advise to troubleshoot this:

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

post the specifications especially RAM and graphics card.

it would also help to know the make and model of the computer.

Thanks.
Thanks for your response!:D
>check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
I did check it, the MD5 code comparing is OK

>burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Maybe i should use CD install instead of USB disk

I'm stuck by this installation err a couple of weeks, i managed to install with many approaches,but it is still NG.:(
Maybe I'll have a try follow what you show me..


Message was edited by alex at 09:00 am on 05/28/11.

---

### Post by Rubi1200 on 2011-05-28
Have you checked whether your CD drive is okay?

Is the hard-drive healthy?

These are also things to check.

---

### Post by alex_goacross on 2011-05-28
> **Rubi1200 said:**
> Have you checked whether your CD drive is okay?

Is the hard-drive healthy?

These are also things to check.

Hi!Rubi1200!
Thanks again!

>Have you checked whether your CD drive is okay?
>Is the hard-drive healthy?
It does work well in windows Xp!
I'm sure it's ok, but i do not know how to ensure that it is absolutely ok during the ubuntu installation.
By the way, my installation boots from USB disk.

Message was edited by alex at 16:00 pm on 05/28/11

---

### Post by kansasnoob on 2011-05-28
When you first boot the USB drive, right after the system/BIOS screen passes, you'll see a purple screen with two small emblems at the bottom. 

At that point you have about 3 seconds to press a key which will allow you to select language and then a boot option screen. On that screen select "Check disc for defects".

It takes a few minutes to complete, so be patient and see if it reports any errors found.

---

### Post by alex_goacross on 2011-05-28
> **kansasnoob said:**
> When you first boot the USB drive, right after the system/BIOS screen passes, you'll see a purple screen with two small emblems at the bottom. 

At that point you have about 3 seconds to press a key which will allow you to select language and then a boot option screen. On that screen select "Check disc for defects".

It takes a few minutes to complete, so be patient and see if it reports any errors found.
Thanks for your reply!
I did have a try for "Check disc for defects".
But the installation is still NG.

Message was edited by alex at 19:57 on 05/28/11.

---

### Post by alex_goacross on 2011-05-28
Thanks for all who takes a glance on it!

Finally, ubuntu is installed successfully.
What I did is just follow what Rubi1200 advice me to do:
I burn the iso file in WinXp with the system-package tools,

I use the cd to boot,install, and it did work for me!
I donot know why the ubs disk installation does not work, but at least, i'm using the ubuntu os to post right now.;)

Message was edited by alex at 20:07 on 05/28/11.

---

### Post by Rubi1200 on 2011-05-28
Excellent, I am really pleased you got this sorted out in the end.

Enjoy :-)

---

### Post by alex_goacross on 2011-05-28
I'm so interested in open-source project!
Ubuntu is just amazing!:p

---

