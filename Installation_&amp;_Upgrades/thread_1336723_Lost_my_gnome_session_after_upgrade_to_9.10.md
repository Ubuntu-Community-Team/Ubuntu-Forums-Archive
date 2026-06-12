---
title: "Lost my gnome session after upgrade to 9.10"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by RRK on 2009-11-24
I upgraded from 9.4 to 9.10 the other day.  Seemed to work okay other than the loss of sound which I expected since I lost it on the last few upgrades.  Then, I could no longer get into my gnome session.  I login and get the Karmic reddish-brownish screen. Nothing else. I can log in under failsafe-gnome and have tried many of the home-remedies found in the forum. 
I can log on with the other two accounts on the PC but not mine.  Any ideas?
I have deleted .gconf* .gnome* .metacity several times. I have run gdmsetup, sudo gdmsetup. I have installed kdm but can't get it to be an option.  
Please help.

SOLVED.

Thanks jjcv. That did it.  I had to re-establish my evolution connection but nothing lost.  Now on to the lack of sound.

---

### Post by jjcv on 2009-11-24
It sounds like a problem with one of the config files if you can login with another account okay.

I suggest you recreate your /home/<username> directory and then see if you can login.  It should create new config files for you.

Best way to do this is to login as someone else.  The start a terminal and do the following:

sudo mv /home/<username> /home/<username>.old

sudo mkdir /home/username

sudo chown <username> /home/<username>

Replace <username> with whaterver your one is.

The login back into your account and you should see a gnome session.

You can then move your files from /home/<username.old> to your new directory.

---

