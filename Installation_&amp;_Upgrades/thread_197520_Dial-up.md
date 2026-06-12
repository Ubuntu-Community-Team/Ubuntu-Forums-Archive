---
title: "Dial-up"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Fittersman on 2006-06-15
Alright, 

on the previous version of ubuntu my modem would not work properly, has this been fixed on 6.06?

If i install from a cd will all of my old settings be lost? (i put alot of work into that)

and does ubuntu have a good spyware stopper and virus blocker program on it?

---

### Post by zxee on 2006-06-16
What type of modem do you have? Winmodems (modems that rely on the OS to do the contollers job-therefore called controllerless modems) don't work well with linux, with some exceptions. Having typed that I also have experianced more set up problems in dapper than with breezy. If you know you have a modem linux can recognize i.e a hardware modem or most externals have you set up internet with 'pppconfig'?

---

### Post by Fittersman on 2006-06-16
Well i have tried many things and so far none of them have worked. off the top of my head i can list a few: scanmodem, some ppp things and basically just trying to get it to work.

im pretty sure that its a winmodem, some poeple told me that i should move it to another drive but when i tried doing that i couldnt figure it out :D so i want some way to just get it to work where it is.

---

### Post by Oceola on 2006-07-21
@Fitterman - the issue might not be your modem. If your modem has serial capabilities it should be recognized and using pppconfig should help set it up. One thing to note is if you use the Modem icon which is in the Gnome panel apps it has to have the information you place in pppconfig as well. Also your /dev/ttyS? should be detected unless your computer has a manager which has changed this to a higher number. I don't know an easy way to find it but if you go into the properties for networking and to the modem tab you can try an see if your modem is detected. If not you may want to try a different /dev/ttyS? which isn't on the list, you may hve to go into double digits. Then you may have to go back to pppconfig and make sure it agrees on the /dev/ttyS?

I know this stuff and could not get Dapper on line. There's either an issue where the mailed out CD does not recognize my modem or a failure in the dial out modem setup. There were some PPP and PPP0e and pppconfig package updates after the discs were made available.

I have a US Robotics dial up modem.

---

