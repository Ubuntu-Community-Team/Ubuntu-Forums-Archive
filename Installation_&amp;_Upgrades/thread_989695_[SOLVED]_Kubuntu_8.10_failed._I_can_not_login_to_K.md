---
title: "[SOLVED] Kubuntu 8.10 failed. I can not login to KDE/GENOME. Please help"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by binukavumkal on 2008-11-21
I did a Kubuntu Upgrade. It upgraded the packages. System is restarted and I got the login name screen. But key board and mouse are not detected and I could not type anything and mouse is deactivated.

However I could do Alt Ctrl Del and restart the machine. I think I can login into command prompt.

How can get back my KDE/GNOME screen? 

Can I restore back my older version of KDE/GNOME

I am stuck up. Please help

Thanks

---

### Post by Skripka on 2008-11-21
Boot into recovery mode, and fix packages and X server, would be the first thing to try....

---

### Post by binukavumkal on 2008-11-21
Thanks. 
How to boot into recovery mode? 
How to fix the X window packages?

I am new to Linux. Please help

---

### Post by Skripka on 2008-11-21
> **binukavumkal said:**
> Thanks. 
How to boot into recovery mode? 
How to fix the X window packages?

I am new to Linux. Please help

As GRUB is loading, you should see a prompt to press escape to get options, or the GRUB menu to select which OS to load (if you have both Windows and Ubuntu), hit escape---you'll be given several boot options one should read "recovery mode" at the end, select it and press enter.


You should get a blue screen with some menu options, which you navigate with keyboard arrows, select "fix broken packages" and "fix X server".

---

### Post by binukavumkal on 2008-11-21
> **Skripka said:**
> As GRUB is loading, you should see a prompt to press escape to get options, or the GRUB menu to select which OS to load (if you have both Windows and Ubuntu), hit escape---you'll be given several boot options one should read "recovery mode" at the end, select it and press enter.


You should get a blue screen with some menu options, which you navigate with keyboard arrows, select "fix broken packages" and "fix X server".

I am having a dual boot desk top. It shows two options 

Ubuntu Hardy Heron... Kernel 2.6.24-21... generic...

MS Winodows XP

When I select Ubuntu / MS Windows XP, ESC option is NOT available



I can use Alt Ctrl Del and can log into  command prompt also.

But I can not use K DE or GNOME

Please help. Thanks for the quick help

---

### Post by Skripka on 2008-11-21
> **binukavumkal said:**
> I am having a dual boot desk top. It shows two options 

Ubuntu Hardy Heron... Kernel 2.6.24-21... generic...

MS Winodows XP

When I select Ubuntu / MS Windows XP, ESC option is available

I tried to edit..but it is showing

root(hda0, 6) etc.  and some more options.

This all are going to Kubuntu Loading screen and 

I get a username screen. Here I can not enter any thing.


I can use Alt Ctrl Del and can log into  command prompt also.

But I can not use K DE or GNOME

Please help. Thanks for the quick help

Hmmmm.  I'm stumped--there should be at least two or 3 linux options "normal", "recovery mode" and a 3rd....



Odds are the upgrade did several wierd things to your system....I usually advise *against* doing full "upgrade" and starting over and starting a fresh OS install--because anything can happen when upgrading between major versions.

---

### Post by binukavumkal on 2008-11-21
Can I fix this from the command prompt?
How can I edit menu.lst from the command prompt so that I can switch to previous kernel?

---

### Post by binukavumkal on 2008-11-22
This is the way it is solved

In the grub command line I edited the Kernel command line by appending a the word single at the end.

I removed the splash and quiet options also from this line

Using the 'b' booted into system

Luckily this time key board and mouse are detected. I still wonder how?

Then select fail safe gnome login

Then logged into root account

then did a sudo apt-get install.

It said  you need to run sudo dpkg --configure -a

Lots of messages came. 

Did again sudo apt-get install

once it is completed restarted. 

I could be at least login into GNOME and all applications and services are intact. 

During this process, I don't know somehow KDE (my fav desktop) is disappeared from the initial session change window

Need to get back that also. Trying to get that.

---

