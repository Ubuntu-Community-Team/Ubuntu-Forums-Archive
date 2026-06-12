---
title: "Ubuntu login does not start after upgrade"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by blwegrzyn on 2011-03-16
I have dell d630- 64bit version
So i upgraded to the latest alpha and my system gets stuck at:
as far as "Checking battery state" and hangs,

i can login to the separate console and run startx
but then no window manager is comming up

so again, another ubuntu upgrade and another failure
i love ubuntu , but i hate the fact that it never works without troubleshooting !!!

---

### Post by tommcd on 2011-03-16
> **blwegrzyn said:**
> 
So i upgraded to the latest alpha ...

... so again, another ubuntu upgrade and another failure
i love ubuntu , but i hate the fact that it never works without troubleshooting !!!
If you hate troubleshooting problems, then you should stay away from alpha builds of anything. Alpha builds of Ubuntu, or anything else, are intended for people who don't mind, and even enjoy, trying to solve bugs with early development builds.

I always do clean installs of the stable releases, and I never have problems; and I have used every version of Ubuntu since the inaugural 4.10.

---

### Post by Aovalles on 2011-03-22
This also happened to me. I installed Kubuntu desktop on Ubuntu... Then I removed Kubuntu with a script I found somewhere and the "Checking battery state" problem appeared.

This is how I finally solved it:

1) Booted into restore mode... and also hanged
2) Then I pressed ALT-CTRL-F1... for a new console interface
3) Logged in
4) Started X  (startx)... X started and could see my desktop
5) Then I removed gdm...  the Gnome display manager?
6) Reinstalled gdm and Ubuntu Desktop
7) I also changed back to open source video drivers... I suspected because I had recently installed Intel drivers.

Done... never saw the problem again

Hope this work for someone.

---

