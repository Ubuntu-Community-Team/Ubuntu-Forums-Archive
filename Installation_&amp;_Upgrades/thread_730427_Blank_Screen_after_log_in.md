---
title: "Blank Screen after log in"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Kawa800 on 2008-03-20
Last night I realized that I had not set my laptop to get updates.  I set it for updates and there were a little over 200 of them. I kicked them off and went upstairs to put the kids to bed.  I never made it back to check it.  When I came home from work kids said they tried to log in but nothing happened.  I confirmed, user name and password screens come up,  but screen goes beige with arrow curser, but gets no further than that.  Tried hitting escape at boot and selected the option that said recovery mode.  same result.  Any ideas?  I am going to try to boot with the CD and see what I can do.  Has anyone seen this before?  I also tried typing my password wrong on purpose and it told me i had a bad username and password, so that part is working.  Just nothing after that.

---

### Post by Kawa800 on 2008-03-20
I booted to the CD.  First I tried safe graphics mode.  This brought me to the same beige screen.  Just a little more pixilated, I assume from the lower resolution. Powered down and tried again.  This time Run or Install.  The desktop came up.  I was able to browse to the hard drive and see the files.  Just couldn't seem to find anything useful.  I am a recent convert from Windows so I guess I am looking for a System Restore, Last Known Good Configuration, Safe Mode, etc equivilant.  Is there such a thing or am I looking at a re-image?

---

### Post by PmDematagoda on 2008-03-20
Go to Options on the login screen and select Select Session, when you do that select Fail-safe GNOME on the menu. Then try logging in again and see if you can access the desktop.

If that works then we can go on in trying to solve your problem, if it does not work then we may have to look to other ways.

---

### Post by Kawa800 on 2008-03-21
I am in!  Thanks.  But now what?  I get an error - "The panel encountered a problem while loading "OAFIID: Deskbar_Applet".  Do you want to delete the applet from your configuration?      I selected "Don't Delete".  Also, I was showing I had updates to run.  I am suspecting something went wrong when I ran the updates the other night so I figured I would try and run the remaining ones.  I get an error  - "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."  I am using the laptop right now.  So I am connected to the wireless internet.  I will try rebooting and logging in normally.

---

### Post by PmDematagoda on 2008-03-21
I think it would have been better if you had just removed the deskbar applet for the time being, but anyway.

Run:-
```
sudo dpkg --configure -a
```
as suggested by the error message and then see if that fixes your problem.

---

### Post by Kawa800 on 2008-03-21
Rebooting did not work.  I was thinking it might, like in Windows sometimes just logging into Safe Mode and rebooting will clear a problem.  I guess if I stick with Ubuntu long enough I will start thinking Ubuntu instead of Windows. I went back into Fail-safe Gnome.  Deleted the problem applet and ran the suggested code.  Now I was down to 38 updates.  I ran these successfully and was prompted to restart.  Restarted and logged in normally.  Thank you so much for your help!!!

---

### Post by PmDematagoda on 2008-03-21
I trust that everything is working for you now?

---

### Post by Kawa800 on 2008-03-21
Yes! Thanks again!

---

### Post by PmDematagoda on 2008-03-21
> **Kawa800 said:**
> Yes! Thanks again!
No problem, could you please mark this thread as Solved so that it can help others with your same problem?

---

