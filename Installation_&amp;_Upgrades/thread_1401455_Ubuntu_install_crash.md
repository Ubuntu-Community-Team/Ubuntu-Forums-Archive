---
title: "Ubuntu install crash"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by lord0fshred on 2010-02-08
I've been using Ubuntu for about a year or so and have never had any problems installing it up until now. 

I can boot from live CD for 9.10, but if at any point I attempt to install it to my hardrive, it either locks up or the screen goes black. Sometimes I'm able to start the installer, but the screen will go blank. The most progress I've been able to make on the install was up to 98% before it locked up, every other time I've gotten a blank screen or a lock up around 40-60%. After a hard reboot I get an error that reads "DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER"

This problem doesn't only occur with 9.10, but with every other linux distro I've tried on it. My first attempt was with Ubuntu Studio, but I got similar errors. I've searched literally for hours and have found nary a solution that even comes close to solving my problem. 

any help? :/


using HP Pavilion a404x desktop

---

### Post by shriramrs31 on 2010-02-08
> **lord0fshred said:**
> 
any help? :/
using HP Pavilion a404x desktop

Initial guess is a faulty hard drive. Use gparted to completely format the disk and make a superficial error check. If nothing is found, then download the tool from the hard-drive manufacturer to perform more detailed error checks and if possible do a zero fill. If something's wrong with the HDD, you will definitely catch it in these steps.

Sometimes a messed up partition table/MBR might also behave like this.

Since you have tried with different linux distros(different kernels), I dont think it must be something to do with missing hardware drivers. If you cant find anything with HDD, try a distro with an older linux kernel.

---

### Post by golusweet on 2010-02-08
It's hard drive problem.

1. Check your BIOS sequence. 

2. Make sure hard drive is properly plugged in.

---

### Post by shriramrs31 on 2010-02-08
> **lord0fshred said:**
>  

any help? :/

using HP Pavilion a404x desktop

Did you try seeing the messages in the alternate screens by pressing ALT+F1, upto F6. ALT+F7 is the GUI screen and from F1 till F6 you have different console screens giving some kind of info. you can even log into one of these consoles and  look for system log or dmesg.

One of these screens must give you an error message regarding why its hanging up.

---

### Post by lord0fshred on 2010-02-08
It could be a partition error, I created/deleted partitions like no tomorrow earlier. Since there's no OS currently installed on the hdd as of now, I'll try a complete format, thanks for the help, I'll let ya know how it goes :P

---

### Post by lord0fshred on 2010-02-08
I finally got it working. All it needed was a vigorous and thorough manual formatting. Thanks for the help, you guys :D

---

