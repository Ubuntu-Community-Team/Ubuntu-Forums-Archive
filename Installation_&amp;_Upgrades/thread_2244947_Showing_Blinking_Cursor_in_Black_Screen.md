---
title: "Showing Blinking Cursor in Black Screen"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by just_me76570 on 2014-09-19
[SIZE=3][FONT=century gothic]Hello i Try to Install Ubuntu using CD and when the Ubuntu installing maybe in percent maybe 47% the screen turn into black and i think it sleep and i try to move the  mouse and the computer awake again Ok so i try to wait and the screen turn into sleep again i wait up to 50mins and my screen turn into black the i try to move the mouse and nothing happens so i wait and again nothing happen  so i turn off the PC and try to boot into HDD but it only showing a Black Screen w/ a blinking text cursor , i try again to boot into CD/DVD using live cd and only blinking text cursor and i also try to boot from USB live usb and also[/FONT][SIZE=4][FONT=century gothic] [/FONT][/SIZE][/SIZE][SIZE=4][FONT=century gothic] blinking text cursor w/ a black screen :( showing.

like this [/FONT][/SIZE]:cry:[FONT=century gothic]

[/FONT][IMG]https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xap1/v/t1.0-9/10629659_1519828721565393_7615101139103574363_n.jpg?oh=56e00e80ecb0020be38dfd84f48955c3&oe=548AAED1&__gda__=1422548200_d4a6f87f8a9a7977210e1ae7c19982a6[/IMG]

---

### Post by yancek on 2014-09-19
Is this a computer with no other operating system installed?  If there is another operating system, what is it?  Are you changing the DVD to first boot priority in the BIOS when trying to boot it?  Are you changing the flash drive to first boot priority, the hard drive when you try to boot it?  Seeing the blinking cursor is not that unusual but seeing when trying to boot from three different types of media is.

---

### Post by just_me76570 on 2014-09-19
Hey yancek, before in counter that problem the OS installed here is Windows 7 Pro. 
i already change the Boor priority into HDD, CD/DVD and also USB boot when i boot up the pc it only show the blinking text cursor even the CD/DVD and USB is a Live CD/USB

i have here a Windows 7 Pro and i try to boot it up from DVD but nothing happens , only it's show the Blinking text cursor :(

---

### Post by just_me76570 on 2014-09-19
After i already boot the Ubuntu from DVD this what it show :( what should be the problem here? Please Help :cry:


[IMG]https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/s480x480/10647161_1519844424897156_3661310152379595972_n.jpg?oh=1ae6fec139cba27bdeb0dcc040e921b9&oe=54CC10A0&__gda__=1418862949_50b1f402f550792583e268d824ecda25[/IMG]

---

### Post by fantab on 2014-09-19
Can you boot into windows? Tell us more about your computer, hardware details, like RAM, CPU, Graphics card.... model, brand etc....
we need to look at your HDD partitions- post a screen-shot of your Disk from 'Disk management utility'.

Have you verified the integrity of your downloaded ubuntu.iso with either [MD5Sum check]("https://help.ubuntu.com/community/HowToMD5SUM") or [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM")... if the test fails then you should re-download the .iso image.

How are you writing .iso image to DVD/USB?[ https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Is your computer 32bit or 64bit? Did you choose an appropriate architecture... 64bit will not boot on 32bit systems, while 32bit can boot on 64bit... but is not recommended.

---

