---
title: "HI, I want to install Ubuntu on my INSPIRON 6000 DELL LAPTOP, HOW TO DO IT?"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by FENNYLI on 2005-09-02
[COLOR=Navy]I'm new hand on Linux, Could any body tell me how to install Ubuntu Linux +Windows on Inspiron 6000[/COLOR]?
what should I do, Does any body have such experience?

My lap top is DELL INSPIRON 6000, 512M RAM, DVD
 CD r/w COMBBO, 40 GB Harddrive, 1.6 Ghz CPU. 

Some body told me that I should install Linux first. I hope two Operational Systems will not fight each other. 

both can run smoothly!

please send me email at [email]li63@engr.sc.edu[/email]
thanks!

---

### Post by varunus on 2005-09-02
Every piece of hardware you've listed so far will work with linux.  What video card do you have?  What wireless card?  These things can be found in device manager in windows (right click on my computer, choose properties, go to one of the tabs (i forget which) and pick "device manager.")  These are the only things left that give some people trouble.

OK, you should install windows first if you want to dual boot. (Or just install ubuntu on top of the preinstalled windows.)  Its very easy to install linux afterwards; here's some basic install instructions on how to resize your windows drive without losing your data:  [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

(This shows you how to do it in the Ubuntu installer.)

---

### Post by mcmuffy on 2005-09-02
You need to have windows installed 1st otherwise it wipes out your boot menu if you try to install windows after linux.
So long as you have created enough partition space on you hdd just boot from the ubuntu install disc and follow the prompts. When it asks where to install too tell it to use the free space you have created and it will do the rest.
Not sure about your dell but it installed fine on my ibm t21 thinkpad.

---

### Post by thieves.honor on 2005-09-03
The only thing you have to watch out for is writing over Dells MBR.  When you intsall any new OS.  If you overwrite thier MBR you loose the push ctrl-f11 to get the restore image.  You can check out this site for more information on it and how to restore it.  On the other hand I have a Dell Inspiron 6000 and had no trouble installing Ubuntu.  Just make sure to install Ubuntu second.

---

### Post by thieves.honor on 2005-09-03
Sorry forgot to link site
[http://www.goodells.net/dellrestore/fixmbr.htm](http://www.goodells.net/dellrestore/fixmbr.htm)

---

### Post by Ainvar on 2005-09-24
Any idea on how to enable all of the function keys like suspend, hibernate, battery, eject, crt/lcd buttons?

---

### Post by tritch on 2005-12-27
I've configured my 6000d to dual boot xp and ubuntu.  I previously posted a solution to this problem here:

[http://www.ubuntuforums.org/showthread.php?t=56723&page=2](http://www.ubuntuforums.org/showthread.php?t=56723&page=2)

Check out tritch's reply.

---

