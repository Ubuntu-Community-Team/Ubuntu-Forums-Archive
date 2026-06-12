---
title: "Back to 10.04...  The crash of 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Nylo on 2010-10-14
Luckily I have a testing (dirty) laptop to try new OS's.  With every new issue of Ubuntu I have had issues which usually take about a week to stabilize.  As was with 10.04 which I had running perfectly in no time.  But, as of date, 10.10 has been the worst.  This time it simply crashed.

After updating I ran 10.10 through some paces which looked OK.  Then I went to settings manager, appearance, style, and tried a few new looks when after choosing a particular style the screen went black, and I wound up at my login.  After I logged in it simply went black again, and back to login.

So for now I'm going back to 10.4 and just sit it out till things get more stable.

---

### Post by rikxik on 2010-10-14
You can do Ctrl+Alt+F1 and get the login prompt. After that you can backup your home directory (to say another partition), empty your home directory by removing all files (include hidden . files) and do Ctrl+Alt+F7 (or F6 or F8 - can't remember) and get back the login prompt. Then login and let XFCE create the config etc. from the scratch.

This will ensure that whatever setting is causing you to go into a login loop is removed and you start from a fresh base.

There are probably nicer ways to handle this but this is how I would trouble shoot.

---

### Post by Nylo on 2010-10-16
> **rikxik said:**
> You can do Ctrl+Alt+F1 and get the login prompt. After that you can backup your home directory (to say another partition), empty your home directory by removing all files (include hidden . files) and do Ctrl+Alt+F7 (or F6 or F8 - can't remember) and get back the login prompt. Then login and let XFCE create the config etc. from the scratch.

This will ensure that whatever setting is causing you to go into a login loop is removed and you start from a fresh base.

There are probably nicer ways to handle this but this is how I would trouble shoot.

Thanks, Ill give it a shot.

---

### Post by franklamoureux on 2010-10-17
Hi Nilo,

I get similar crashes, but the crash happens randomly within 5 minutes (or less) of working on the desktop. Most the time the crash seems to happen when a new window gets opened, when there is some kind of X activity. Can't find any crash references in dmesg, syslogs or X server logs...

---

### Post by zeating on 2010-10-17
I'm also back to 10.04 because of stability issues, i'll wait until they fix it up more

---

### Post by TBABill on 2010-10-17
+1 on waiting for stability. Reverted both my machines because of wireless issues that seem widespread. Not quite ready for me yet.

---

### Post by franklamoureux on 2010-10-18
Silly question, but what is the best way to revert? Save your Home on another disk and full reinstall?

---

### Post by eddier on 2010-10-18
If you have a separate /home partition (A Very Good Idea!) then boot up puppy Linux from a cd, open your home folder,expose all the 'dot' files in the browser.Delete everything other than your music-video-pictures folders.

You can keep 'dot' folders such as .icons,.themes,.mozilla etc. But all the various config files should go.

When doing the re-install make sure you do not re-format the home folder,existing folders/files will not be overwritten.

If you dont have separate /home folder then its the hard way--but do create one on the re-install!

You should be able to use the Ubuntu Live cd to do this,but WTH,Puppy looks so nice!

eddie

---

### Post by Simian Man on 2010-10-18
> **Nylo said:**
> After updating I ran 10.10 through some paces which looked OK.  Then I went to settings manager, appearance, style, and tried a few new looks when after choosing a particular style the screen went black, and I wound up at my login.  After I logged in it imply went black again and back to login.

I believe I know EXACTLY what the problem is.  Xfce comes with a couple themes which crash the window manager.  Choosing one of those will make it crash right away and make it impossible to fix the problem graphically.  This has happened to me and I went to another VT and changed the default theme directly in the Xfce config files.  Making a new user and copying your data is an easier way to do it.

Really bad QA for this to happen though.

---

### Post by franklamoureux on 2010-10-18
I was using the ClearLooks theme when I upgraded, and if I recall, it was still this theme the first time I logged in after the upgrade. I *of course* tried a long time ago to only switch it back to Ambiance, the default theme (*Hold on, is it really the default theme? The window icons in the example shows icons on the right a-la-windows while the default theme puts them on the left side, a-la-OSX)*, but still, even with Ambiance the crash occurs. 

But I'll give creating a new user a try for sure.

***Update***

Hi Simian Man, reading twice your post, I realized you were replying to Nylo using xubuntu. I'm not, I'm on the vanilla Ubuntu desktop 10.10 64bit. But I realized it after creating that new user, and X is not crashing with this new user. So there is definitely something wrong in an X config somewhere...

---

### Post by Simian Man on 2010-10-18
> **franklamoureux said:**
> I was using the ClearLooks theme when I upgraded, and if I recall, it was still this theme the first time I logged in after the upgrade. I *of course* tried a long time ago to only switch it back to Ambiance, the default theme (*Hold on, is it really the default theme? The window icons in the example shows icons on the right a-la-windows while the default theme puts them on the left side, a-la-OSX)*, but still, even with Ambiance the crash occurs. 

But I'll give creating a new user a try for sure.

Sorry, I thought you were using Xfce since you have the [xubuntu] tag.

---

### Post by franklamoureux on 2010-10-27
I "fixed" my problem for those interested. Details at [http://ubuntuforums.org/showpost.php?p=10032343&postcount=3](http://ubuntuforums.org/showpost.php?p=10032343&postcount=3).

---

