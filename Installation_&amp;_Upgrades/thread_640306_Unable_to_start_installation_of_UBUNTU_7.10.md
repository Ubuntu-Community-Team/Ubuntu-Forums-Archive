---
title: "Unable to start installation of UBUNTU 7.10"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by mlb85in on 2007-12-14
:confused:

Hi evry1,

I am trying to start UBUNTU after downloading 7.10 from Ubuntu website and then burned it on to a CD.
I am trying to install it but when I boot from the CD I see various option like start installation, start installation in safe graphics mode...etc

when i select the first option or any option I am only able to see the traditional UBUNTU loading screen with a bar movie right to left and left to right. After this I go to a command prompt style (initgms..)

Thats it and nothing happens and I am trying evrything
but no help

My laptop config: Dell Inspiron 6400, Intel centrino duo 1.6GHz, 1GB ram

Please tell me what to do 

thanks n bye

---

### Post by PmDematagoda on 2007-12-14
Did you try using the Alternate CD?

It is the text-based installer for Ubuntu and can be found [here.]("http://www.ubuntu.com/getubuntu") Just check the check box near the end of the page that will allow you to download the Alternate CD image file.

---

### Post by JangMunho on 2007-12-14
Have you ever tried press Ctrl+ Alt+F2 to login through tty2?
It seems that there is not a open source driver for your graphic card.
Even you install the system successfully,you need to install the official graphic card driver, otherwise you can't run X properly.

---

### Post by Sef on 2007-12-14
1) Did you md5sum the download?  (To make sure it is good.)

2) Did you burn the iso at 4x or less? (Faster may cause corruption?)

3) Did you check the disk for errors?  (At the install/boot Live CD menu, go down to check disk or something similar.)

---

