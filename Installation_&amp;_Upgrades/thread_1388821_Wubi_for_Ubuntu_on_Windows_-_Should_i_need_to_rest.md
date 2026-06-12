---
title: "Wubi for Ubuntu on Windows - Should i need to restart ?"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Karthik Balaguru on 2010-01-23
Hi,
I came across wubi for having Ubuntu on Windows. 
 
'Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), as opposed to being installed within its own partition. This file is seen by Linux as a real hard disk. '
The above seem to convey that linux can be run just like any other application in windows by just clicking over the shortcut in windows . That is, it seems to convey that windows and linux co-exist. Do they co-exist ?
 
But, I came across the below line that states that 'Wubi adds an entry to the Windows boot menu which allows the user to run Linux'. 
So, should i need to restart evertime to enter into linux ?
 
Need clarifications.
 
Thx in advans,
Karthik Balaguru

---

### Post by garvinrick4 on 2010-01-23
Yes it is an option in the boot process not an App. You can get into the Windows C: drive
while in Ubuntu Wubi install it is "host" in the Ubuntu file system. Linux will accept the documents, media and such from the Windows invirement. And it does attach inself to
the dos4grub of Windows in 7 and vista you can see it by "bcdedit" from command line in windows without quotes.

---

### Post by mlentink on 2010-01-23
> **Karthik Balaguru said:**
> But, I came across the below line that states that 'Wubi adds an entry to the Windows boot menu which allows the user to run Linux'. 
So, should i need to restart evertime to enter into linux ?

Yes you do, if you want to use the Wubi installer
If you want to be able to run Ubuntu within windows, use a Virtual Machine manager like [Virtualbox]("http://www.virtualbox.org/")

---

### Post by Karthik Balaguru on 2010-01-23
Okay, i got some good links - 
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi) 
So, it seems that i need to reboot 
to switch to linux :-( :-( . It is not
an app in windows. If i want to have
it as an app, virtual machines might
be the right approach.

Wubi is a program that that allows 
you to install Ubuntu as a dual-boot 
by installing it as a huge file inside 
of Windows and then modifying the 
Windows boot loader to add an 
entry for Ubuntu. 

[http://www.lockergnome.com/blade/2007/06/22/wubi-dual-boot-windows-ub](http://www.lockergnome.com/blade/2007/06/22/wubi-dual-boot-windows-ub)... 
Wubi allows you to install and uninstall 
Ubuntu as any other application. If you 
heard about Linux and Ubuntu, if you 
wanted to try them without the fear 
of losing windows or data or partioning, 
then wubi seems to be the right choice. 

It does not provide co-existence 
of Windows and Linux at the same 
time :-( and it eases the installation
of linux for a new user from windows
environment and provides an option
to either switch to either Windows or
Linux while booting up . It is not an app.

Karthik Balaguru

---

### Post by Karthik Balaguru on 2010-01-28
Hi,
Considering the characteristics of wubi,
i have opted for virtual machines .:KS:)
 
Karthik Balaguru

---

