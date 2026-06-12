---
title: "How can I install Hoary over Warty?"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by redwing on 2005-05-04
Hi, I'm a brand-new user to Linux, and would appreciate any help that can be offered for the following questions:

**Question 1:**  Is it possible to install Hoary OVER Warty, via the cd? I have Warty installed from an original disk, and an ISO burned to disk of Hoary, which a friend downloaded/burned for me, from the 'net.  I am running a laptop, Pentium 4, 20GB hd, with a single cd/burner/dvd player combo drive, 384  of SIMM memory.

**Question 2:**  I have been unable to set up an internet connection. I have a dialup ISP. I have tried to put in just the phone # [7 #s with no area code], and either I am not using the proper file to do this or I have put in the wrong info. I have always used, under Windows, a simple dialup connection which I set up myself, and its always worked, putting in my user name/password and the proper phone #. What other things do I need to find out about my ISP, and in which place should I enter all of these things? I am a single home-user, so have no network [even between my desktop....which I am using now...and my laptop] or other users to consider.

Thank you, Redwing

---

### Post by bored2k on 2005-05-05
1) Yes. Just make apt-get use that disc as a repository, then do sudo apt-get dist-upgrade.
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

---

### Post by jodef on 2005-05-05
[QUOTE=redwing]Hi, I'm a brand-new user to Linux, and would appreciate any help that can be offered for the following questions:

**Question 2:**  I have been unable to set up an internet connection. I have a dialup ISP. I have tried to put in just the phone # [7 #s with no area code], and either I am not using the proper file to do this or I have put in the wrong info. I have always used, under Windows, a simple dialup connection which I set up myself, and its always worked, putting in my user name/password and the proper phone #. What other things do I need to find out about my ISP, and in which place should I enter all of these things? I am a single home-user, so have no network [even between my desktop....which I am using now...and my laptop] or other users to consider.

Thank you, Redwing[/QUOTE]
How are you trying to setup your ISP connection? What are the steps you did? Have you tried pppconfig? I know it can be tedious at times but helps if you outline the exact steps you have performed so far and the error messages you get.

---

### Post by redwing on 2005-05-05
[QUOTE=bored2k]1) Yes. Just make apt-get use that disc as a repository, then do sudo apt-get dist-upgrade.
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)[/QUOTE]
 Thank you very much!  I will try that this evening when I get home from work, and see how I do with that.       ~~Redwing~~

---

### Post by redwing on 2005-05-05
[QUOTE=jodef]How are you trying to setup your ISP connection? What are the steps you did? Have you tried pppconfig? I know it can be tedious at times but helps if you outline the exact steps you have performed so far and the error messages you get.[/QUOTE]
 Thank you, Johann! I will try the pppconfig this evening, and see what happens. Haven't actually received any error messages....just couldn't get past putting in the phone number with only 7 numbers....didn't want to move on to the next field.  ~~Redwing~~

---

