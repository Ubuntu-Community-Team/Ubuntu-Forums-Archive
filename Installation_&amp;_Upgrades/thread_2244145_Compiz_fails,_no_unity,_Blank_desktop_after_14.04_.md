---
title: "Compiz fails, no unity, Blank desktop after 14.04 update"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-09-14
Okay, I put together my second Intel i7-4770K processor-based PC.  I used an SSD with 12.04 64-bit on it.  I upgraded to 14.04 everthing was fine.  Since my scientific consulting business has several mission-critical programs that work under wine or crossover, I attempted an install of Crossover 13.2.0 (note was already working under 14.04 64-bit on my Dell Vosrto 3500 desktop) (also note that wine will not install under 14.04).  Installation of crossover failed, and it also took down unity, etc.  So, I have a PC with no unity desktop, no launch bar, etc.  Remember, the Intel graphics drivers are built into the 14.04 kernel and are supported by Canonical.

Now, I could wait until Monday morning, and let my Canonical support engineer fix this problem.  However, it appears that there is a serious problem with unity and 14.04 64-bit that no one wants to address in a way that provides all users with an accurate set of instructions to recover from this apparently wide-spread problem with numerous inaccurate solutions posted in Ubuntu-related websites.

If there is a true and accurate fix, it should be posted as a separate sticky under installation and upgrades.

John

---

### Post by cigtoxdoc on 2014-09-14
You will numerous solutions to the subject problem by doing Google searches on Ubuntu 14.04 and compiz fails, no unity, blank desktop, and cannot do Ctrl-Alt-t.  None of them has worked for me.

Here is what has worked:

sudo apt-get install gnome

After numerous programs install and you reboot, you will get a logon screen that will include the choice of Gnime Compiz Flashback.  Select that one and then make any changes in compiz or reset it using procedures described at [http://roziq.com/how-to-repair-unity-and-compiz-in-ubuntu-14-04-13-10-or-13-04/](http://roziq.com/how-to-repair-unity-and-compiz-in-ubuntu-14-04-13-10-or-13-04/) .

Next reboot, and go for the Ubuntu Unity logon option.  Problem should be solved.  I have had this work on two PCs, one with nVidia graphics and the other with the Intel graphics built into the i7-4770K processor.

John

---

### Post by ibjsb4 on 2014-09-14
```
I could wait until Monday morning, and let my Canonical support engineer fix this problem.
```

Me wonders what other support you got going on at this early morning hour.

---

### Post by cigtoxdoc on 2014-09-16
My "other support" was my own memory.  I remembered that between sessions with the Canonical engineer on the problems with my Dell laptop, I had created the same problem when I was evaluating the nouveau and video drivers other than the current nVidia.  I got myself out of the problem (by shear luck) byh loading gnome, fixing compiz, and getting back to the full Unity desktop.

John

---

