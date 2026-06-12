---
title: "Ubuntu 10.10 64 bit installing problem"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by mertergun on 2011-03-04
After pressing "Install Ubuntu", nothing happens, just a black screen and a cursor is blinking. I've waited 20 minutes and nothing. Then, I tried this DVD on an another computer. It worked totally, so what do you think what's wrong with my computer?

---

### Post by Skaperen on 2011-03-04
I don't know if this is still a problem at 10.10, but it has been in the past, causing a problem like this for SOME computers.  See my post #4 in this thread ... [http://ubuntuforums.org/showthread.php?t=1699945](http://ubuntuforums.org/showthread.php?t=1699945)

---

### Post by sikander3786 on 2011-03-04
Welcome to the forums :-)

This type of problem is sometimes reported on some hardware while using DVD as an installation media. Can you please try from a CD or a USB drive?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

And before burning the image to disc or USB, it is recommended to check the health of your image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mertergun on 2011-03-04
Maybe my problem is a bit different.. I'll tell you what i did respectively. At the beginning, I had just windows 7 64 bit.

1. I installed ubuntu 10.04 32 bit on my computer. I install ubuntu with windows 7. Everything went well except, at the end of installation when i pressed "Restart Now" nothing happend, there was just ubuntu's purple screen. 

2. I waited about 10 minutes and then shuted down the computer and restarted, ubuntu o.s. opened but there was a problem with the internet. I could open just few small web sites ( for example google ). Update manager also didn't update. I couldn't install any application neither.

3. Then i decided to reinstall ubuntu. This time I choosed the advanced part of setup. I deleted manually ubuntu and created a space for it then ubuntu was installed.

4. Again, at the end of the setup, (after pressing "Restart Now") i got lots of error messages in black screen. And I had to restart the computer. Again ubuntu worked but there was the same internet problem. 

5. Then I thought that maybe its a contradiction with 32 bit and 64 bit. I downloaded ubuntu 10.10 64 bit version burned it into a dvd and tried to install but couldn't do it. 
( the problem that I mentioned in the first message ) 

6. And then I tried reinstalling windows. After erasing windows and ubuntu (by windows 7 installer )  An extended partition appeared ( empty ) and it was separated with avaliable free space.

7. Then I created C: disk for windows 7 with avaliable space and installed windows 7 without a problem. In windows 7, I runned Disk Manager to see what's wrong with that "extended partition" and saw these ( in the img below ). Then tried to install ubuntu again but there was the same black screen, i couldn't start installing.

What do you think then?

How can I delete that "extended partition" without erasing D: part?

[IMG]http://img576.imageshack.us/img576/3935/ekranalntszw.png[/IMG]

---

### Post by mertergun on 2011-03-04
> **sikander3786 said:**
> Welcome to the forums :-)

This type of problem is sometimes reported on some hardware while using DVD as an installation media. Can you please try from a CD or a USB drive?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

And before burning the image to disc or USB, it is recommended to check the health of your image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thank you:)
I forgot to write it. I tried installing ubuntu with USB but the installation didn't started again. And this DVD and USB worked with another PC. There is a problem with my computer.

edit: I did it between 4 and 5. step

---

### Post by mertergun on 2011-03-04
[INDENT]I think if I format all harddisk, my problem'll be solved.. :/ I need to back up my files..
[/INDENT]

---

### Post by sikander3786 on 2011-03-05
> **mertergun said:**
> [INDENT]I think if I format all harddisk, my problem'll be solved.. :/ I need to back up my files..
[/INDENT]
That is the easiest possible solution. Otherwise it can be done but needs a lot of work to do and I can't be of much help there.

Hope your problems you will solve the problems soon.

---

### Post by mertergun on 2011-03-05
> **sikander3786 said:**
> That is the easiest possible solution. Otherwise it can be done but needs a lot of work to do and I can't be of much help there.

Hope your problems you will solve the problems soon.


I formated entire harddisk ( except the recovery part ) it didn't work :/. I'll ask this assistance of my dept.

---

### Post by mertergun on 2011-03-07
The installation problem is fixed but there is still a problem with the internet. Despite I edit the DNS cong. (my dormitory ip adresses) I can access few websites only, google, youtube etc. Update manager isn't working. I have a [*SiS191 Ethernet* *Device*]("http://download.cnet.com/SiS191-Ethernet-Device/3000-2112_4-96829.html"). Can it be a problem about Hardware-driver issue? 
[]("http://download.cnet.com/SiS191-Ethernet-Device/3000-2112_4-96829.html")

---

