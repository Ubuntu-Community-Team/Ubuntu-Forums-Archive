---
title: "Install 8.04 on External HardDisk"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by De_JA_Vu on 2008-06-08
[FONT="Century Gothic"][FONT="Franklin Gothic Medium"]here it goes.
 
HP Laptop
Ubuntu 8.04
Wants to install it on a External USB drive
I have done this before the following way......
 
-I have removed my laptops internal hard drive( so that installing Linux will not mess up with my windows boot loader. as i know if you try to install linux on a machine which has windows already, linux installs its own boot manager called GRUB/LILO.)
-plugged in my external usb hard drive , rebooted lappy, put the ubuntu cd in started the installation process.
-linux installation found the usb hard drive. 
-installed the linux smoothly no trouble. 
-shut down the lappy.
-put my internal hdd back in lappy.
-now when ever i boot my lappy on, i can choose either to boot from the internal hard drive or from the usb hard drive.(I dont use boot manger.i use the bios boot device choosing option(F9))
 
 
 
 
 
Now my question is...
i dont want to remove my lappy's hard drive all the time i install linux.
Can i install the linux keeping my hard drive in and do something on the linux installtion so it does not change any thing on my internal hard drive?
is it even possible.?
should i even take the risk?[/FONT][/FONT]

---

### Post by Thanoulis on 2008-06-08
In the Ubuntu installation process, at the last prompt, there is a button [i]Advanced Options[i]. From there you could install Grub in another hard disk, or not at all.

---

### Post by De_JA_Vu on 2008-06-08
> **Thanoulis said:**
> From there you could install Grub in another hard disk, or not at all.
what happens if i select to install grub on a different hard drive. i.e. the usb drive. It is not going to do any changed on my windows internal hard drive and i will still be able to select my boot device and run linux or windows without conflicting?

---

### Post by lying in bed on 2008-06-15
Hi there I am pretty much a novice to linux OS. I like the idea of booting from my external HD for a play.

Just to confirm when I choose the advanced options will ubuntu install on the external drive only? I share De Ja Vu's concern that I want to keep the window drive totally clean.

P.S.could you simply remove the hd in the bios instead of physically removing it?

P.P.S I have been very impressed with my first boot from cd

> **De_JA_Vu said:**
> [FONT="Century Gothic"][FONT="Franklin Gothic Medium"]here it goes.
 
HP Laptop
Ubuntu 8.04
Wants to install it on a External USB drive
I have done this before the following way......
 
-I have removed my laptops internal hard drive( so that installing Linux will not mess up with my windows boot loader. as i know if you try to install linux on a machine which has windows already, linux installs its own boot manager called GRUB/LILO.)
-plugged in my external usb hard drive , rebooted lappy, put the ubuntu cd in started the installation process.
-linux installation found the usb hard drive. 
-installed the linux smoothly no trouble. 
-shut down the lappy.
-put my internal hdd back in lappy.
-now when ever i boot my lappy on, i can choose either to boot from the internal hard drive or from the usb hard drive.(I dont use boot manger.i use the bios boot device choosing option(F9))
 
 
 
 
 
Now my question is...
i dont want to remove my lappy's hard drive all the time i install linux.
Can i install the linux keeping my hard drive in and do something on the linux installtion so it does not change any thing on my internal hard drive?
is it even possible.?
should i even take the risk?[/FONT][/FONT]

---

### Post by Awale on 2008-07-21
Hello there! 

I am concerned with the same issue... I have a LaCie 100Gb usb hard drive, and I would like to have ubuntu 8 installed on it... however, I am afraid of screwing up the MBR of my internal hard drive... Can somebody asure that just by choosing "install GRUB to..." and selecting the external hard drive, the MBR of the internal hard drive remains intact?

Thank you!!

---

