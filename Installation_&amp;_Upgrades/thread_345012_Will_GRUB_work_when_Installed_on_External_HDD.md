---
title: "Will GRUB work when Installed on External HDD"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by ucsdrake on 2007-01-23
hey,

im installing Ubuntu Edgy onto my external hard drive and i had a question about GRUB.

I want to have a dual boot set up with windows (windows is on my internal hard drive and a section of my external) and i want to be able to only run windows when my external HDD ISNT attached to my laptop (so i can remain portable)

Now in my past installation I installed GRUB to hd0 (internal) which lead to an Error 21 upon computer boot up when my external hard drive wasnt attached

will installing GRUB to my external HDD (USB 2.0) work? meaning will i be able to run linux or windows when it (my external HDD) is hooked up or only windows when my external HDD is NOT hooked up 

thanks in advance

---

### Post by mandrakethepenguin on 2007-01-23
I have tried the exact same thing, and personally, couldn't get anything to work. I have tried this with SuSE and Ubuntu.

---

### Post by confused57 on 2007-01-23
> **ucsdrake said:**
> hey,

im installing Ubuntu Edgy onto my external hard drive and i had a question about GRUB.

I want to have a dual boot set up with windows (windows is on my internal hard drive and a section of my external) and i want to be able to only run windows when my external HDD ISNT attached to my laptop (so i can remain portable)

Now in my past installation I installed GRUB to hd0 (internal) which lead to an Error 21 upon computer boot up when my external hard drive wasnt attached

will installing GRUB to my external HDD (USB 2.0) work? meaning will i be able to run linux or windows when it (my external HDD) is hooked up or only windows when my external HDD is NOT hooked up 

thanks in advance
You "might" be able to get it to work if your bios is able to boot first to your USB device...you'd probably need the alternate cd, which allows you to select where to install grub(your external HD,sda?).  You'd need your boot order to be your external drive first when you're installing Ubuntu.   I haven't done this myself, so I'm not sure if it would work.
Here's a "howto" install on an external hd:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by ucsdrake on 2007-01-23
hey thanks for the link ... i searched the forums but i musta missed that one 

i read somewhere that somebody installed grub to the external and got it to run only when it was attached but there were no specifics to that installation

---

