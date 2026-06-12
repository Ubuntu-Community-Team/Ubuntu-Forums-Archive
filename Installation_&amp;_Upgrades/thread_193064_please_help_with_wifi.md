---
title: "please help with wifi"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by rreyes3000 on 2006-06-09
I have posted the following on the beginner talk but have had no responses. Hope it works here.

I have an HP Pavilion dv 4000. I did an lspci command in the command console and this is what I have--Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05). I looked under device manager and my network card is detected plus in the network settings my wirelwess connection is shown as active . I am, however, unable to turn on the wifi card on the keyboard button on my laptop. I have found several sites that suggest downloding ipw2200-fw-3.0.tgz and ipw2200-1.1.2.tgz. I have used the archive manager to extract but from there I am at a loss. First, it took me forever to figure out how to extract it. then I finally figured tgz is a sort of zip file. plus I was looking for the "C" drive. And then I was looking to update the drivers for my hardware. As youi may tell I am migrating over from windows and all this command line is new for me. In some of the sites I refered too it says to extract the files--using the command shell--into directories but they did not exhist!

Please help me set up my wifi. I need a Cliffnotes for dummies with lots of pictures. I just know I cannot be this stupid for something that is probably simple.

Thanks
rreyes3000 is offline   	Reply With Quote

---

### Post by Bionic_Beefpile on 2006-06-09
[http://www.ubuntuforums.org/showthread.php?t=189074](http://www.ubuntuforums.org/showthread.php?t=189074)

---

### Post by Jason_25 on 2006-06-09
...the suggestion above is better.

---

### Post by rreyes3000 on 2006-06-10
when I go to the bash shell and type "tar . . . " I get a "cannot open: no such file or directory". I am new to changing directories and I am not sure what the problem is. The line in the window read "rreyes3000@rreyes3000-laptop:~$". The closest experience to command lines I have is DOS. I am just stuck. I downloaded the file onto the desktop. 

any ideas?

HELP

---

### Post by Bionic_Beefpile on 2006-06-11
if it's on your desktop, then
tar -xvf ~/Desktop/name_of_file should work.  It's probably easier to copy the file somewhere else first, though, because if not you will get a messy desktop in a hurry.

sudo cp ~/Desktop/name_of_file /destination_directory
then
cd /destination_directory
then sudo tar -xvf name_of_file

---

