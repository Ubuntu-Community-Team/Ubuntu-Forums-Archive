---
title: "KDM/GDM conflicts"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by lello1776 on 2007-05-04
Hi all,
I am a new user, although I have been using ubuntu for 2 years.
I am facing the following problem: I installed the KDE desktop manager kdm then I switchem to gdm
and all went fine. Then I switched back to sm and voila...I lost the graphical login and was prompt
with a text login. dpkg-reconfigure kdm which didn't work,  and after a while I found the reason which 
can possibly be a bug but I am not sure.
I basically found that the init scripts for gdm had a link S13gdm in /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d
while kdm had only one link /etc/rc5.d/S99kdm.
I created the other link with the proper number, that is S13kdm, in all the directories and then I got the kdm
graphical login back.

Why dpkg-reconfigure didn't create the link?

lello.

---

