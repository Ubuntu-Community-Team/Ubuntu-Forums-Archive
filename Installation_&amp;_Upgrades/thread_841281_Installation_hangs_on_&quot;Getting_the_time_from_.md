---
title: "Installation hangs on &quot;Getting the time from a network time server&quot;"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Dimas on 2008-06-26
I'm trying to install Ubuntu 8.04 on a VMWare server based on Ubuntu Server 8.04.

The live ubuntu starts ok, and the install goes fine until arrive to 88% and the progress stops on ""getting the time from a network time server". The system hangs here and restarting the PC doesn't allow Ubuntu to start.

I've seen a bug open with no answers: [http://help.lockergnome.com/linux/Bug-436444-installation-reports-installation-lenny-businessc-ftopict489239.html](http://help.lockergnome.com/linux/Bug-436444-installation-reports-installation-lenny-businessc-ftopict489239.html)

Any bypass? ;(

---

### Post by PmDematagoda on 2008-06-26
Are you connected to the net during the install? If so, remove the network cable and try to install Ubuntu again.

---

### Post by djaychela on 2008-07-25
I have the exact same problem.  Acer Laptop (Celeron 1.4, 768MB RAM, all works fine in XP, etc), fresh whole-disk install, 8.04 as downloaded last night.  Always hangs on 87%, "Getting time from a network time server" - doesn't matter if the network cable is plugged in or not.  System is not bootable after, etc.

I've been using Linux for quite a while (started on Red Hat 5, been using SuSE for many years for desktop and server installs), but EVERY time I try to use Ubuntu, I have problems.  I've tried different versions on 4 different systems, and each has had deal-breakers in the installation or in the one case that did install there were problems which were fixed quickly and easily by installing OpenSUSE on it (which I still have running) - am I just unlucky, or is the Ubuntu installation process really this flaky?

---

### Post by dlowerre on 2008-07-31
Same problem for me.  I am completely hung at 87% 'Getting the time..etc.'

I have successfully installed Ubuntu on several computers.

I have also wasted countless hours on fruitless attempts to install Ubuntu on  several computers.

It is a mixed bag.  When the installer works, it is fantastic.

When it doesn't it can really suck.  What especially irks me is the advice to 'try the install again'.  You didn't mention how long it took to get to that 88% spot but in my case I have hours into this one (why is it SO nasty running linux from the CD?)  

Well, this is more of a rant.  Not much help.

---

### Post by PmDematagoda on 2008-07-31
Did you try installing Ubuntu with the Alternate CD?

---

### Post by dlowerre on 2008-07-31
No...never have tried the alternate CD.  But I will :)

---

### Post by shateiel on 2008-09-26
Bit of a late response here but I found this topic wile searching for solutions for this problem myself.
Either way the solution I found was this:

After booting from the CD start Ubuntu without installing it first. Then run the installation program from within Ubuntu. This solved the problem for me at least. Although I can not explain to you why..:)

Cheers

---

### Post by BioHaZZarD99 on 2008-11-14
anyone have anything on this problem? the thread's been here for a month and a half without any real help. o.0

---

### Post by pizpot on 2009-12-27
I just had it hang twice installing 9.04, at the "getting time" message. This is a computer that has been running ubuntu forever.

What I did different, is choosing "install" rather than "try ubuntu - and clicking the install icon."

So thanks for the tip dude, I bet I am fixed. Normally I always do it the other way, but I wanted to save time this time. LOL.

EDIT: Yes, that was my problem, and now it installed.

PS, I am using 9.04 instead of 9.10 because 9.10 is not as good, for me. I get cruddy sound in Warcraft3 in Wine. No sound for Serious Sam in Wine. Playing better than tinkering...

---

### Post by TDK800 on 2011-06-16
Ubuntu Server 11.04 32-bit - same problem! (3 years and still not fixed?)

---

### Post by trendle on 2011-08-14
Me too :confused:
11.04 server install just hangs.  Nobody seems to be able to offer any advice that makes a difference.  I've stripped the PC down to CD only, no extra cards and it still doesn't get past  this point.  I can cause a seg fault if I hit <ctrl>C several times. But that doesn't really get me anywhere.

I presume the other posters have given up by now and gone to Fedora or back to MS, but I seem to be a glutton for this type of punishment.  I must have done something bad in a previous life.

There doesn't even seem to be a way to get rid of the stupid progress bar display and to see a simple text display that might tell me something useful.

Being a 'server' version I wanted to install, there's no option to boot into the live version and do a GUI install from there (assuming that would get any  further).](*,)

---

### Post by HarvesterOfBeer on 2012-03-01
I'm also experiencing this trying to install 11.10 64-bit in ESX 5. Eventually the hang passed and the install continued.

---

