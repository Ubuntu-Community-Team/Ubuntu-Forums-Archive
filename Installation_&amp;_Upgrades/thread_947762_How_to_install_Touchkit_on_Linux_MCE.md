---
title: "How to install Touchkit on Linux MCE?"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by K2002 on 2008-10-14
I am using a Shuttle D10 ([http://www.directron.com/d10.html](http://www.directron.com/d10.html)) for this exercise.

Install Kubuntu on it and Linux MCE is install. but the touch screen is not working. sometimes only work on one button the rest of the button not working.

I have downloaded a touchkit. is a touch screen driver. 

[http://www.touchkit.com/proi/drive/(K)Ubuntu5.1.tar.gz](http://www.touchkit.com/proi/drive/(K)Ubuntu5.1.tar.gz)

after untar. try to make file but the file does not exist. try to follow the steps on the pdf file below but to no avail still not working.

[http://www.touchkit.com/proi/drive/Installation%20Note.pdf](http://www.touchkit.com/proi/drive/Installation%20Note.pdf)

anyone can help me on this? because the linux MCE and Kubuntu is install properly the only thing is the touchscreen still not working. please help i am still new in linux.

Thanks
regards
-K2002-

---

### Post by Partyboi2 on 2008-10-15
When you say > after untar. try to make file but the file does not exist do you get something like this on sceen
> bash: /usr/bin/make: No such file or directory If so make sure that you have installed build-essential package. You can do this by typing in a terminal
```
sudo apt-get install build-essential
```

---

### Post by tinpalace on 2009-03-15
TouchKit.com lists drivers in 2 places
- one list is out of date - you don't mention you kubuntu version but I think the Kubuntu 5.1 driver is ancient

the other page lists drivers by 32bit/64bit and kernal and x versions and is current - you will have to check your versions and download the correct driver.

I have the touch screen working beautifully with Ubuntu 8.04

Here are some instructions I posted on Shuttle's forum:

I found the touchkit.com site and instructions confusing.
- The site lists drivers with distro specific versions that are out of date in one spot and in the other they list updated versions based on kernal and x versions.
- The instructions miss a few simple but important bits that will have you pulling your hair out. Bad translation maybe?

I WAS using Ubuntu 8.10 but had to switch back to 8.04 because the drivers are not available for the newest x version. Instructions for checking your kernal and x version are provided by TouchKit.com

Use the drivers and start follow the instructions from this page if you need to determine you kernal and x version:
[http://touchkit.com/LinuxDriver.htm](http://touchkit.com/LinuxDriver.htm)

i used the 32bit version: Kernel 2.6.x with xorg 1.4.0 only
for Unbuntu 32bit 8.04

After downloading and unzipping/unpacking the driver folder /TouchKit_x14/ - you need to also unzip/unpack the folder inside of the unpacked driver folder. (it has the same name as the driver folder ex. /TouchKit_x14/TouchKit_x14/

To install use the instructions in /TouchKit_x14/readme NOT /TouchKit/Manual_Linux v1.0.2.doc

The D10 screen controller is USB. It was ask you for this during the install. The instructions list the screen output of the setup utility - you will not have to set these yourself - the setup ultility does it for you.

The second TouchKit_x14 folder has the TouchKit panel configuration program that you will need to calibrate the screen. The instructions (/TouchKit/Manual_Linux v1.0.2.doc)  simply says (after installing the driver) to execute touchcfg to start the configuration utility. They do not tell you that the utility was not aded to any menu and that it is actually inside the second compressed folder that came with the driver ( /TouchKit_x14/TouchKit_x14/) and that it is called TouchKit not touchcfg. Go to /TouchKit_x14/TouchKit_x14/ and double click the file TouchKit.

Hope that helps you!

---

