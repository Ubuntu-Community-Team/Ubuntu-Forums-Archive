---
title: "Install App packages in Multiple Systems"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by pnrkumar on 2011-09-25
Hi,
 
I'm new to Ubuntu. Recently decided to use Ubuntu intead of Windows. It's great experience learning & using Ubuntu. I've few questions regarding installation of app packafes in multiple systems.
 
We have to install ubuntu in about 10-12 Systems. All with different hardware. What I learned installing Ubuntu is, we need internet to get packages to install. There are offline option also available (But at this stage it's bit confusing for me).
 
Usually in Windows we used to download all the essential software like Flash, Java, Browsers, Games etc. & install the same in all the machines. Even in case of system crash we install the downloaded software.
 
But downloading the packages in Ubuntu in all the machines is time & bandwidth consuming process. My question is : "Is there a method where we can download all the essential packages once and install the same in all the machines, even the one without networking feature"?
 
I am looking for a solution as simple as possible and any suggestions are greatly welcome! 

Thank you to the all Ubuntu Community for providing such great software, and the Open Source Community as well for creating so many great apps!

---

### Post by pnrkumar on 2011-09-25
Thanks for the reply. Could you please help me with steps.

---

### Post by ajgreeny on 2011-09-25
Assuming you have one main machine, and all the machines are running the same OS version, simply update and install everything on the main one, then copy all the .deb files from /var/cache/apt/archives on that machine to the same place on the other machines using a USB flash drive.  It needs just two commands
```
cp /var/cache/apt/archives/*.deb /media/*USBname/*
``` then on the new machine ```
sudo cp /media/*USBname*/*.deb /var/cache/apt/archives/
```

You can then install everything and update the other machines, one by one.  There is also an application called **aptoncd** which will do all this for you but I don't think it is worth it for the sake of two commands.

---

### Post by pnrkumar on 2011-09-30
Thanks for the tip. Do we need to manually install the apps after copying?

Is there any method to create a list of commands & execute them in one go?

---

### Post by pnrkumar on 2011-10-08
I've copied the packages as mentioned but some packages are showing x mark on the folder & not able to install as well. Any solutions?

---

### Post by collisionystm on 2011-10-08
you could always sign up for a trial of ubuntu landscape. You can manage all your systems at once from there.

---

