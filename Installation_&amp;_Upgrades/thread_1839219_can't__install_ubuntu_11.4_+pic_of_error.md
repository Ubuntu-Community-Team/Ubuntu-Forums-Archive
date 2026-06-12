---
title: "can't  install ubuntu 11.4 +pic of error"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by SPooT25 on 2011-09-05
hello

I'm noob in Linux ....

i want install ubuntu 11.4 but i can't see the pic :

[[IMG]http://img684.imageshack.us/img684/1552/imag0005la.jpg[/IMG]]("http://imageshack.us/photo/my-images/684/imag0005la.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")



i have laptop Toshiba 

Please Help

---

### Post by YannBuntu on 2011-09-05
Hello,

- please boot on a Ubuntu CD, and backup your important data on an external drive (CD, DVD, USB disk..). The "gksu nautilus" command may help.
- then connect internet, and have a try with Boot-Repair just in case, and indicate us the URL that will appear.

Then if you are in hurry, I would just reinstall Ubuntu. (have you checked that your Ubuntu CD has no error?)

---

### Post by SPooT25 on 2011-09-05
> **YannBuntu said:**
> Hello,

- please boot on a Ubuntu CD, and backup your important data on an external drive (CD, DVD, USB disk..). The "gksu nautilus" command may help.
- then connect internet, and have a try with Boot-Repair just in case, and indicate us the URL that will appear.

Then if you are in hurry, I would just reinstall Ubuntu. (have you checked that your Ubuntu CD has no error?)


i don't know where boot repair , cuz i have windows 7 in laptop

And i test ubuntu cd with Mobalive cd programe in windows with another computer and show me same massage !!

---

### Post by YannBuntu on 2011-09-05
Since you have the problem on several computers, your Ubuntu ISO may be corrupted, I recommend you download it again and check its md5sum (if you download the ISO via bitorrent you don't need to check md5).

---

### Post by SPooT25 on 2011-09-05
> **YannBuntu said:**
> Since you have the problem on several computers, your Ubuntu ISO may be corrupted, I recommend you download it again and check its md5sum (if you download the ISO via bitorrent you don't need to check md5).


what's mean md5sum ???

I will download it again via torrent and report later..

another Q , Can i install linux from external dvd ??

---

### Post by YannBuntu on 2011-09-05
Yes, you can install Ubuntu from an external DVD-reader, there should be no difference.

md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by SPooT25 on 2011-09-05
Another messege or error check the pic:

[[IMG]http://img713.imageshack.us/img713/6169/imag0006ki.jpg[/IMG]](http://imageshack.us/photo/my-images/713/imag0006ki.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by YannBuntu on 2011-09-05
This time it may be linked to the external DVD  (the error refers to cd-rom).

You can try :
- with another Ubuntu version (e.g. Ubuntu 10.04)
- or to put Ubuntu on a USB-key (e.g. via Lili USB creator or UnetBootin), and boot your computer on this USB key (it will act like the UBuntu CD). For this you may need to set up your BIOS in order to enable boot on USB.

---

### Post by SPooT25 on 2011-09-06
> **YannBuntu said:**
> This time it may be linked to the external DVD  (the error refers to cd-rom).

You can try :
- with another Ubuntu version (e.g. Ubuntu 10.04)
- or to put Ubuntu on a USB-key (e.g. via Lili USB creator or UnetBootin), and boot your computer on this USB key (it will act like the UBuntu CD). For this you may need to set up your BIOS in order to enable boot on USB.

i install 10.4 with external dvd and everything it's ok
but i have problem with programs ,can't install or remove program
 please check this pic:

[[IMG]http://img189.imageshack.us/img189/8828/screenshottb.png[/IMG]](http://imageshack.us/photo/my-images/189/screenshottb.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by YannBuntu on 2011-09-06
Good to see you managed to install it :)

Now close all your windows (especially the Ubuntu Software Center), then open a terminal (Applications->Accessories menu) and type the following command:

```
sudo apt-get install -f
```

and type your password (nothing won't appear, it's normal)

---

### Post by SPooT25 on 2011-09-06
> **YannBuntu said:**
> Good to see you managed to install it :)

Now close all your windows (especially the Ubuntu Software Center), then open a terminal (Applications->Accessories menu) and type the following command:

```
sudo apt-get install -f
```and type your password (nothing won't appear, it's normal)


0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.


that's all??

---

### Post by SPooT25 on 2011-09-06
can't install program ... check this pic

[[IMG]http://img64.imageshack.us/img64/4268/screenshot122d.png[/IMG]](http://imageshack.us/photo/my-images/64/screenshot122d.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by YannBuntu on 2011-09-07
and what's written if you click on "Details" of this window ?

Again, please close all apps,open a terminal and type:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

Check if any error.

---

### Post by SPooT25 on 2011-09-07
> **YannBuntu said:**
> and what's written if you click on "Details" of this window ?

Again, please close all apps,open a terminal and type:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```Check if any error.


i click on Details and the message is "dooble" or " arora" like name of program i want to install

-
i type all commands , no error and try to install again with same error !!

---

### Post by YannBuntu on 2011-09-07
Sorry, I don't have any idea any more... have you deactivated all your PPAs ?

---

