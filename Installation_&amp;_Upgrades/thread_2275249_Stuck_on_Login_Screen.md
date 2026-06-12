---
title: "Stuck on Login Screen"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2015-04-25
Hello :-)

I just upgraded to Vivid.
The first time I was asked to reboot I reached the login screen.

It is obvious it does not detect my graphics card correctly because it loads in low resolution, but that is ok.
The problem is that when I type my password I see "activity"... blank screen.. then some more "activity" and then back to login screen.

So far I have tried the following:  Loaded the Grub by holding shift.  From the advanced option I booted with the other manager (upstart).
Didn't solve the problem.

The good thing is that I have access to the terminals Alt-f1-6, and Alt f7-f12.

Can anyone point me to the right direction?
I see there are hundreds of people with problems with the upgrade.
I am sure someone must have the same problem.

So please point me to the solution, or suggest smt.

My hunch is that after I type my password it tried to load the GUI, and because there is an error (it does not detect my gfx card correctly) it sends me back to the login screen.
Any help will be greatly appreciated.

Thank you all in advance.

[Update]

After reading this :
[http://askubuntu.com/questions/612973/caught-in-loop-when-trying-to-login-after-upgrade-from-14-10-to-15-04](http://askubuntu.com/questions/612973/caught-in-loop-when-trying-to-login-after-upgrade-from-14-10-to-15-04)

I tried this :

sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop

It fixed both problems.  Now my gfx card is correctly detected and I managed to login.

---

### Post by Bucky Ball on 2015-04-25
Good news. Please mark thread as solved to help future travelers (see second link in my signature). 

Thanks and good luck. ;)

---

