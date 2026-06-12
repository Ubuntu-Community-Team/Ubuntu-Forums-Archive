---
title: "black screen when I do switch user"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2010-05-01
hello all,
yestarday I installed ubuntu 10.04, and the PC we using 3 persons, but when any user switch to the own user system, sometimes ubuntu stay on "black screen" and I need to restart.
Any solution for this???

Regards

---

### Post by weenerdog on 2010-05-01
Same here: Dell Inspiron 1100 laptop...

---

### Post by keech on 2010-05-02
I am having 10.04 ...I too am getting the error....when you switch back from another user you get a blank screen ...the system freezes...need to physically reboot. One more thing, when you switch user using 'Switch from keech'and try to login back without going to any other user the screen just freezes with the login screen. I am not sure why this happening, I have tried the following but did'nt work

Uninstalled gnome-screensaver
deleted the user,created new

Someone needs to find a solution else...its going to make people regret opting for Ubuntu

---

### Post by pernest on 2010-05-02
Hi, I'm experiencing the same problem, but I've found a way to recover without a reboot.

If you just press ctrl+alt+F7 when this happens then you can log into one of the other accounts and shut the computer down from there. Alternatively.

I really don't know what I'm doing and this is probably a very bad way of dealing with the problem, but it might be better than a reboot. IT WILL ALMOST CERTAINLY LOOSE DATA IN OPEN DOCUMENTS.

Press ctrl+alt+F3
Log into any of your accounts
type ps u -C gnome-session
Find the process id associated with the user for which logging in gives you a blank screen
then type sudo kill XXXX
enter your password
where XXXX is the process id
then press ctrl+alt+F7 and you should be able to log into one of your accounts

---

### Post by chanfle on 2010-05-02
on this moment I just use the option "Switch from <user>"
but we need the option of the user loggon

any solution..??

Regards

---

### Post by chanfle on 2010-05-02
any solutions..???
??????????
the problem still persist  :(

---

### Post by chanfle on 2010-05-02
hey guys maube I found the solution please review on my blog
[http://chanflee.com/?p=1682](http://chanflee.com/?p=1682)

---

### Post by pernest on 2010-05-03
It seems that chanfle might have a solution. After I ran the blog post through google translate I think what he's suggesting is:

use synaptic package manager to find and uninstall gnome-screensaver. After I did this, I can now switch users without the black screen appearing.

I wonder if it would be possible to just configure the screen-saver instead of removing it?

---

### Post by chanfle on 2010-05-05
hi pernest,
in my case I installed the package and uninstalled after, I not testing about configurate the screensaver mode, maybe work it, if you try this mode, please post it here...

Regards..

---

### Post by gee42 on 2010-05-31
I had the same problem with a fresh install of 10.04. As per the suggestion I uninstalled gnome-screensaver and was then able to switch users without the black screen defect. I then installed it again intending to confirm/check the results and found that the problem remained fixed: with gnome-screensaver re-installed I am now able to switch users without the black screen defect.

---

### Post by lacis_alfredo on 2010-06-06
Hi,

I have same issue - black screen after logging out.

MORE INFORMATION:

Ctrl-Alt-F1... F12 do *NOT* work.  

FYI, I've been using RedHat since 2000, now Ubuntu since 6.04, so I have some years of administering our systems at home.

---

### Post by CharlesBun on 2010-06-08
Hi,

I also have this issue. The problem started after an upgrade from Hardy Heron to Lucid Lynx.

The black screen (the screen is totally blank, no cursor or anything is seen) occurs when:
* user1 logs in
* user2 logs in through "Switch user"
* some of these user logs out.

I can "Switch user" between these accounts, but not end any user session through "Log out" or "Shut Down".
The problem also occurs if a third user logs in (through "Switch user").

Ctrl-Alt-F1...F12 and Ctrl-Alt-BackSpace do not work, and I've removed/reinstalled the gnome screen saver without any success.

---

### Post by miak on 2010-07-11
I have the same problem, 
whenever one of the users logs out, I get a blank screen and nothing works except power button.
I tried uninstalling gnome-screensaver, but no results, i still get black screen when 2nd user logs out.

---

### Post by singletrackmind on 2010-08-13
Same issue here. Anybody find a fix yet?

---

### Post by Who needs windows anyway? on 2010-08-21
The same is happening to me, although i usually have a solid cursor in the top left corner. Have tried un-installing the screen saver unfortunately it crashed the very first time i logged out afterwards!

I also have an intermittent problem whereupon the system freezes and becomes completely non-responsive after selecting Ubuntu from the Grub menu (I dual boot) and all i'm left with is the Ubuntu logo and the frozen throber.

On both occasions nothing works except hitting the power button.

This also happens to me with Linux Mint which happens to be based on Ubuntu Lucid Lynx.

---

### Post by foxxa on 2010-08-30
Same here... using nvidia drivers 173.14.22, only one screen, all defaults...

I am fairly new with playing with nvidia drivers under linux... so... no experimenting here... I love it, but this issue needs some fixing, don't you think?

---

