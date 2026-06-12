---
title: "Boot problem after upgrade to 10.4"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by OllieGab on 2010-05-23
This is in short my problem:
Upgraded from 9.10 to 10.4, upgrade went OK despite a /media mount problem during boot up.
In gnome I logged off and logged back in again, this time as a KDE session (as it was an option and I thought I'd try it!)
PC didn't like it, froze up and after I re-booted it entered a KDE log-on screen which disappeared before I could actually do anything. A fusion compiz logo came up, disappeared after a couple of seconds and I was back at the Ubuntu logo (with the dots underneath). Cursor is active on screen but can't do anything at all.
I can get to a command line during boot-up but nothing I've tried will sort the problem.
Bug? I mean, why give me the KDE session option when KDE isn't installed?
Any suggestions how I can get out of this?
If I boot up with a live CD all my files are available to me.
I seem to be stuck in KDE without any way of changing it...

Help!!

---

### Post by dzezz on 2010-05-23
hi,
i've go quite similar problem,
i'm using ubuntu 10.04 with gnome
and i've installed kde
and when i try to switch to the kde in logon screen i can't
there are no options at the bottom 
any ideas?

---

### Post by OllieGab on 2010-05-23
An additional problem I have is, that when I try to do something via the command line (to sort my problem out) I get a "Cannot open display" error message...and this could very well be part of my problem of not seing the screen.
Any one know what that is all about?

Cheers

---

### Post by dino99 on 2010-05-23
try to boot in recovery mode, or/and with nomodeset=0 on the boot line (without splash)

---

### Post by OllieGab on 2010-05-23
I have actually come a bit on the way....I think!
I used 'startx' on the command line which opened up the computer again. But as root!
I "daren't" log off again in case I won't get back on.
I can't open the 'Manage users' for some unknown reason. But there must be a way, now that I'm root and into the machine, that I can modify the user (I normally am, ie not root) so it will autostart in gnome again. Or at least ask me for username and session type.
Where might I find those files that need modifying?

---

