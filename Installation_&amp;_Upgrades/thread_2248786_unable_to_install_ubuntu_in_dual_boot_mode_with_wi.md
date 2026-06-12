---
title: "unable to install ubuntu in dual boot mode with windows 7"
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by ramadavid on 2014-10-17
Dear Friends, 
    I have sony vaio laptop with i3 processor, 3 gb ram, nvidea graohic card, windows 7 OS.
I want to install ubuntu 14.04 LTS. but when I put bootable usb or CD,  its not
recognise any such device. it directly boot into the windows ( i also press F12). 
I checked the integrity of OS cd/usb, it was perfect.
 I also changed the boot priority with respective devices.
I previously installed ubuntu 12.04 lts 32 bit and also updates it to 14.04 LTS. I unistalled ubuntu
with easyBCD. As my system is 64 bit I want to install 64 bit ubuntu.

I search a lot of post but not find any such problem and solution by any one.
I will be thankful for your cooperation. 


With Best regards,
RamaDavid

---

### Post by fantab on 2014-10-17
Try to install Ubuntu from a USB drive (pen drive)... 
Make sure Windows is NOT hibernating...
Can you "Try Ubuntu" without installing?

---

### Post by ramadavid on 2014-10-17
Dear Friend,
    Thank you for giving time from your busy scheduled.

      Make sure Windows is NOT hibernating...

How to check it 

and I not getting any option of booting . Windows directly getting started as Normal window PC so 
there is no way to go " TRY UBUNTU ".

I am confused a lot. I also check with other OS like Linuxmint. 
laptop easily get booted with pendrive USB when Linuxmint is OS. but with Ubuntu  its not showing 
any sign of booting. It just start as normal window 7.


 With regards,
RamaDavid.

---

### Post by yancek on 2014-10-17
When you click the Main Menu key (lower left of Desktop) you should have several options such as restart, hibernate, shutdown.
EasyBCD can't "uninstall" Ubuntu as it is just a graphical interface to modify windows boot files so you likely just deleted the menu entry for ubuntu from windows boot menu.
Have you tried the Ubuntu usb or CD/DVD on another computer to verify it is working?

---

### Post by Vladlenin5000 on 2014-10-17
> **yancek said:**
> Have you tried the Ubuntu usb or CD/DVD on another computer to verify it is working?

^^^^
This. And because you just mentioned that a USB pendrive with Mint boots then it doesn't take a "rocket scientist" to conclude something is wrong with the one with Ubuntu.

---

### Post by ramadavid on 2014-10-20
Dear Friends,
    Thank you for replies and giving your valuable time.
As per your suggestions, I check the bootable device on
another computer and I installed ubuntu there. 
  I think problem is as bellow :

I had the previously installed Ubuntu 12.04 LTS.
I deleted the partiion and with easyBCD I chage the boot option. 
I didn't delete the grubloader. When I am using ubuntu 12.04 LTS 
for boot it shows me one option of repairing the ubuntu  that may be the reason ???
  Is it right or wrong ???
      
      Was I used the process to remove the LINUX was good or I should need another 
way to remove the grubloader ???


I will thankful for your suggestions.

With best Regards,
 RamaDavid.

---

