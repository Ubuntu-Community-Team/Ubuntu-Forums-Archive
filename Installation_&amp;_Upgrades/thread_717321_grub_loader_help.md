---
title: "grub loader help"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by hydroparasite on 2008-03-06
**hello**

i was just keen to use the ubuntu linux on my ibm t43 laptop, so i installed the os onto my usb hdd with swap and / mounted partitions . i wanted to install it on my laptop but due to Rescue n Recovery issues i didnt do it . this is because i wanted to save my predesktop area for recovery , but now after installin ubuntu on my usb hdd, n my bios set to usb boot , i can't boot n get a grub loader error , i guess this is because the grub loader was setup on my laptop hdd . i went to the whole recovery setup n restored my xp back 

the question is that i still have ubuntu on my usb hdd , and i want to separately put the grub on the usb hdd without reinstalling it . i know i loaded the grub loader on my laptop hdd which caused the errors !!! 

so is there a way around without installing ubunto again on usb (already there) , boot from it by jus installing the grub boot loader on the external usb hdd !!! 

thanks in advance !! please help :(

---

### Post by confused57 on 2008-03-07
> **hydroparasite said:**
> **hello**

i was just keen to use the ubuntu linux on my ibm t43 laptop, so i installed the os onto my usb hdd with swap and / mounted partitions . i wanted to install it on my laptop but due to Rescue n Recovery issues i didnt do it . this is because i wanted to save my predesktop area for recovery , but now after installin ubuntu on my usb hdd, n my bios set to usb boot , i can't boot n get a grub loader error , i guess this is because the grub loader was setup on my laptop hdd . i went to the whole recovery setup n restored my xp back 

the question is that i still have ubuntu on my usb hdd , and i want to separately put the grub on the usb hdd without reinstalling it . i know i loaded the grub loader on my laptop hdd which caused the errors !!! 

so is there a way around without installing ubunto again on usb (already there) , boot from it by jus installing the grub boot loader on the external usb hdd !!! 

thanks in advance !! please help :(
If your bios can boot first to USB, then you could install grub's IPL(Initial Program Loader) to the external hard drives mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
for example:
root (hd1,0)
setup (hd1)

Boot to your external drive, select your first Ubuntu entry, press "e", select the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter" then "b" to boot...x means leave this value as it is.  This is temporary(if it works)...you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
also, make the change in the line with groot...leave the # in front of groot

---

### Post by hydroparasite on 2008-03-07
thanks for the help , just some clarity needed regarding this.. i have the ubuntu n swap on my external hdd , my laptopn can detect the usb drive for boot , and i get grub entries , that is two of the each . so if i try to boot i cant boot , get error 22 . i TRIED fiddling around by usin root > n changing hd(0,x) and i have the ubuntu on one partition , but cant boot 


how to go about ti

---

### Post by hydroparasite on 2008-03-07
question : folowing the steps using grub , i get to terminal screen with lots of errors 
sudo grub gives me grub loacaion dat is hd(1,6)
if i setup it for (hd0)
wouldn't it wrte grub to my internall hdd and disable the rescue n recovery feature of my ibm laptop
 thanks

---

### Post by confused57 on 2008-03-07
> **hydroparasite said:**
> question : folowing the steps using grub , i get to terminal screen with lots of errors 
sudo grub gives me grub loacaion dat is hd(1,6)
if i setup it for (hd0)
wouldn't it wrte grub to my internall hdd and disable the rescue n recovery feature of my ibm laptop
 thanks
Yes, setup (hd0) would set up grub on your internal drive's mbr..."setup (hd1)" would set up grub on the external hard drive's mbr(which is what you want to do).   Were you able to install grub to (hd1), using the instructions I gave you in my other reply, then using "e", changing root from (hd1,6) to (hd0,6), then pressing "b" gave you grub error 22?

---

### Post by hydroparasite on 2008-03-08
**hello**


thanks for the help extended , but i finally removed the ubuntui os from my externall HDD . Now i would like to do a fresh install on the external HDD , and would require foolprrof method to make it work and not  tincker with the internal drives MBR ... i . e  . i would like to boot to ubuntu only if external hdd is connected ...with usb boot enabled in BIOS . 

please help me and by the way i am gonna use the alternate CD this time to check the installation the notorious GRUB loader .....

Thanks waiting for suggestions !!! :):popcorn:

---

### Post by confused57 on 2008-03-08
> **hydroparasite said:**
> **hello**


thanks for the help extended , but i finally removed the ubuntui os from my externall HDD . Now i would like to do a fresh install on the external HDD , and would require foolprrof method to make it work and not  tincker with the internal drives MBR ... i . e  . i would like to boot to ubuntu only if external hdd is connected ...with usb boot enabled in BIOS . 

please help me and by the way i am gonna use the alternate CD this time to check the installation the notorious GRUB loader .....

Thanks waiting for suggestions !!! :):popcorn:
I would recommend making a Super Grub Disk, before you try installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is a very small download(5-7 Mb), which you could burn to a cd-rw or cd-r, and is an excellent utility to boot different OS or repair booting problems.

As far as installing to your external hard drive, set your external hard drive to boot before your internal hard drive in bios before you boot up the Ubuntu install cd.  On the alternate cd, the very last step asks if you want to install grub to the mbr, select "No", then another screen appears where you can type in where you want grub installed...type in /dev/sdb(or however your external drive is recognized during the partitioning steps).  You "shouldn't" have to do anything else, just  boot first to your external drive into Ubuntu.  Your internal drive should boot with the external drive disconnected.

Here's an excellent guide for installing with the alternate cd, you may want to check out the screenshots:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by hydroparasite on 2008-03-08
thank you very much i ll look into it and get back to you if i have any problems !!! :guitar:



> **confused57 said:**
> I would recommend making a Super Grub Disk, before you try installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is a very small download(5-7 Mb), which you could burn to a cd-rw or cd-r, and is an excellent utility to boot different OS or repair booting problems.

As far as installing to your external hard drive, set your external hard drive to boot before your internal hard drive in bios before you boot up the Ubuntu install cd.  On the alternate cd, the very last step asks if you want to install grub to the mbr, select "No", then another screen appears where you can type in where you want grub installed...type in /dev/sdb(or however your external drive is recognized during the partitioning steps).  You "shouldn't" have to do anything else, just  boot first to your external drive into Ubuntu.  Your internal drive should boot with the external drive disconnected.

Here's an excellent guide for installing with the alternate cd, you may want to check out the screenshots:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

