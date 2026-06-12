---
title: "audio card &quot;CS46xx&quot; seen, but no sound&quot;"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by kline on 2005-11-19
A few hours ago I completed everything to upgrade both OS and packages.  But two things; they may be related.  First, zero sound--and I really like that start-up uplifting sparking jinge when I login.  No other sound app makes a peep either.  The sound chip is a CS46xx and is builtin.  Before the upgrade to 5.10 my login splash screen was different.  Now I'm looking at a large Gnome footprint and this is the second thing:  there is an error message that says that I need to fix something in my "login". After I click OK, I can login.

Can anybody tell me how to get bck to the Ubuntu login?  And any ideas what needs fixing in my Gnome environment?  I haven't edited any files in ~/.gnome2 for months...  The only files I touched were in /etc/apt/*.

thanks.

Oh: I tried the various suggestions re getting sound working.  No luck.

---

### Post by matthewv on 2005-11-19
To fix the sound, make sure there is a line in your /etc/modules that reads "snd-cs46xx" (without quotes)
See if you can change the login screen to what it was in System --> Administration --> Login Screen Setup
What's the exact error message you get??

---

### Post by kline on 2005-11-19
[QUOTE=matthewv]To fix the sound, make sure there is a line in your /etc/modules that reads "snd-cs46xx" (without quotes)
See if you can change the login screen to what it was in System --> Administration --> Login Screen Setup
What's the exact error message you get??[/QUOTE]

Something close to the exact error message is "Cnfiguration error in login"
or something very close.  I will add the "snd-cs46xx" line to modules.  And, 
thanks much, now I see where the login or "splash" screen is set!  ...I've been
grep'ing around like crazy :-)

Done.  Now a reboot and it's time to call it a century ...

---

### Post by kline on 2005-11-19
[QUOTE=kline]Something close to the exact error message is "Cnfiguration error in login"
or something very close.  I will add the "snd-cs46xx" line to modules.  And, 
thanks much, now I see where the login or "splash" screen is set!  ...I've been
grep'ing around like crazy :-)

Done.  Now a reboot and it's time to call it a century ...[/QUOTE]


20 minutes later and I'll add this additional.  A small dialog error popped up with:
"The Configuration is not correct
The configuration file contains an invalid command in the login dialog."
It asks me to correct this---I don't understand the message.   At any rate, the line is in /etc/modules, but the speaker icon still has a tiny "x" mark beside it; so.... still broken.

---

### Post by az on 2005-11-19
A speaker with the x means that it is muted.

Double click on the speaker to get the whole display off all the meters,


Make sure that Master and PCM are notmuted (x on the bottom)

As for the login, go into System-Administration-Login screen setup and make sure everything is okay.  Just opening and closing that window should rewrite the file that is giving you problems.

---

### Post by afrifreak on 2005-11-19
Hi there,

I'e asked my question in another thread, but for 2 weeks none would dare to answer ;) . Here it is:

I have a very odd problem with my sound card, a Hercules Gamesurround Fortissimo III. It works with the cs46xx module, but only sometimes. When I boot my box the first time of day, the sound is very distorted and coming from one speaker. The other speaker produces only rubble. But, when I just reboot, the sound just works! I tried if it helps to change the settings to ALSA or OSS but no change.
Lspci shows my card, I get no error messages but still there is a problem.
Anyone an idea?

Andres

---

### Post by afrifreak on 2005-11-19
Hi there,

I'e asked my question in another thread, but for 2 weeks none would dare to answer ;) . Here it is:

I have a very odd problem with my sound card, a Hercules Gamesurround Fortissimo III. It works with the cs46xx module, but only sometimes. When I boot my box the first time of day, the sound is very distorted and coming from one speaker. The other speaker produces only rubble. But, when I just reboot, the sound just works! I tried if it helps to change the settings to ALSA or OSS but no change.
Lspci shows my card, I get no error messages but still there is a problem.
Anyone an idea?

Andres

---

### Post by afrifreak on 2005-11-19
Something went wrong in the posting process; double posting was not intended.

Andres

---

### Post by kline on 2005-11-19
[QUOTE=azz]A speaker with the x means that it is muted.

Double click on the speaker to get the whole display off all the meters,


Make sure that Master and PCM are notmuted (x on the bottom)

As for the login, go into System-Administration-Login screen setup and make sure everything is okay.  Just opening and closing that window should rewrite the file that is giving you problems.[/QUOTE]

Well, not the "x" is gone, replayed by the soundwaves emitting from the speaker, so thanks.  I hear one loud drumbeat when I mouseclick certain places, so it looks like the audio is back.   But the Login screen app is driving me up the wall.  Definitely non -intuitive.  At least I will figure this out in time.  --Meanwhile, I'm about to read up on an online help page about "support options for gnome-media".  

Lots to learn, but well worth the learning curve; IMHO, Ubuntu is way outstanding.

---

