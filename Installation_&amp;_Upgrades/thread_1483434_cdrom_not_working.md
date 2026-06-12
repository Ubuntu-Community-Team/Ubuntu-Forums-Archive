---
title: "cdrom not working"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by ezens on 2010-05-14
i'm using ubuntu 8.04 on hp dv6600 laptop 
today i wanted to upgrade it to 8.10 
downloaded alternate .iso and realised cdrom IS NOT working i have so many cd's but none works 
no errors no nothing like there is no cd in drive 
so hove can i upgrade ??????
i seted up usb boot stick and what a surprise installer looks for cd (but hove can there be cd if it's USB ) 
so what to do now ????
btw. this is my last call for help since every time i ask i just get ignored 
p.s. if i woud wrote review on ubuntu today it woud sound WORSE than Windows VISTA what was a total fail, so thanks for nothing as usual

---

### Post by davidmohammed on 2010-05-14
duplicate - please don't post questions twice.

---

### Post by ezens on 2010-05-14
doesn't matter people who can help just won't

---

### Post by jclements73 on 2010-05-14
I had this problem with Ubuntu 9.10.  For my case it was permissions on the CD and DVD drives.  Fixed it by typing in the terminal window.

sudo chown yourname:yourname /media/cdrom

yourname is your login name.  /media/cdrom is where my CD drive is located.  What this does is changes the owner and group to your login.  By default Ubuntu does not login as root.  CD and DVD were owned by root and group was root.  

For example:  your login name is bob.  (Can find by typing in terminal 'whoami')
then in terminal window:

sudo chown bob:bob /media/cdrom

Happy CD'ing

JCC

---

