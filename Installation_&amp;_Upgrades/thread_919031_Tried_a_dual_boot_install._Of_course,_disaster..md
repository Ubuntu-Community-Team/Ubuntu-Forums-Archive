---
title: "Tried a dual boot install. Of course, disaster."
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by Splicernyc on 2008-09-13
XP and Ubuntu - thought I was following the instructions correctly and thought I was creating a partition. I figured if I was overwriting the existing drive it would have given me at least one layer of warning, something like "You sure you want to do this?" For all intents and purposes, I assume that I was not in the "erase everything you have" section or it would have told me that.

I try and reboot and it automatically goes to Ubuntu - no menu of options for a Windows or Ubuntu boot. I've perused the forums looking for answers but unfortunately those answers are in a language other than one I can understand. Simply put, I don't know how a car works. I put the key in and step on the gas and I get to work and then back home again. Command line stuff confuses me because I have yet to find a place that puts it into step by step idiot language (for morons).

---

### Post by oilchangeguy on 2008-09-13
> **Splicernyc said:**
> XP and Ubuntu - thought I was following the instructions correctly and thought I was creating a partition. I figured if I was overwriting the existing drive it would have given me at least one layer of warning, something like "You sure you want to do this?" For all intents and purposes, I assume that I was not in the "erase everything you have" section or it would have told me that.

I try and reboot and it automatically goes to Ubuntu - no menu of options for a Windows or Ubuntu boot. I've perused the forums looking for answers but unfortunately those answers are in a language other than one I can understand. Simply put, I don't know how a car works. I put the key in and step on the gas and I get to work and then back home again. Command line stuff confuses me because I have yet to find a place that puts it into step by step idiot language (for morons).


first, i hope you backed up all of your data, just incase. second, if you choose the use entire disk option, then windows is no more.

---

### Post by Kumagoro on 2008-09-13
Ok but... what DO you want to do...

Just open the gnome terminal and paste what you found out to the terminal. The terminal isn't all that scary you know, it helps a lot on some things.

Eg. i want to install Abiword
I can eitherenter synaptic, search for it click it, enter password confirm and done...

OR

enter terminal and type
sudo apt-get install Abiword

What's faster? :]


But back on topic, unless ubuntu installed on your windows partition you should have access to all your filoes from within ubuntu. Otherwise, check some of these disk recovery stuff shown earlier

And for future, use some disk image software and make backups of your data. I think Gigabyte's xpress recovery can be used but i'm not sure...

---

### Post by mikewhatever on 2008-09-13
Can you open Applications->Accessories->Terminal, copy in the command below and post the output here. You'll be asked for the password. Type it in and hit enter. Sorry about the command line.:popcorn:
> sudo fdisk -l

---

### Post by Splicernyc on 2008-09-13
Consider this thread now closed although it can be a lesson for future generations. One of the replies above, stated quite simply (thanks), explained it all to me.

Let's just say that I still have Windows on my laptop along with the programs I use with it. My desktop on the other hand...

Ah well, you live and learn. I must say that I am enjoying Ubuntu for what it's worth although I am still deep in the denial phase.

---

### Post by caljohnsmith on 2008-09-13
> **Splicernyc said:**
> Consider this thread now closed although it can be a lesson for future generations. One of the replies above, stated quite simply (thanks), explained it all to me.

Let's just say that I still have Windows on my laptop along with the programs I use with it. My desktop on the other hand...

Ah well, you live and learn. I must say that I am enjoying Ubuntu for what it's worth although I am still deep in the denial phase.
Unless you specifically chose the "use entire disk" option (which you never explicitly said), you may still have Windows on your HDD. How about posting what mikewhatever suggested? Then we can be sure:
```
sudo fdisk -l
```

---

### Post by k1w1inauz on 2008-09-13
Done the same thing to get the dual boot you must load ubuntu 8.04 from inside windows just drop the disk in and select install from windows.  Then you should be asked how much space you want to allocate to ubuntu and it will install from there.  I've just started using ubuntu and love it.  I still have windows as a backup if needed...:popcorn:

---

