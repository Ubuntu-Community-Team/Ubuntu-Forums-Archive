---
title: "&quot;The Seventh Symbol&quot; or weirdest Log-In Problem Ever?"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-02-26
I believe I have something to submit for consideration in the "award for weirdest log-in problem" category. In Lucid Alpha2 and Alpha3, I run into the following peculiar string of events:

1.) Lucid boots up fine, with some graphics "crap" in plymouth
2.) The Login Screen displays, there is only one user.
3.) I click on the user and get the password requester
4.) I type in my password: XXXXXX2
5.) As soon as I type the seventh character, the number "2", the screen blanks for a second and the gnome log-in screen restarts!
6.) I click on my username again.
7.) I type in my password and Ubuntu starts up normally.

The above is 100% reproducible on each and every boot. I use the 64bit version on a Core2 Duo notebook system (Dell Latitude D830), with nVidia Quadro NVS140 graphics. Installing or removing the proprietary nVidia driver makes no difference. It also does not matter how fast or slow I type or how long I wait before logging in. I could type in the first six characters, go for lunch, hit "2" and boom, blank screen, "log in" jingle, fresh Log-In Screen.

After that problem surfaced in Alpha2, I did a fresh install of Alpha3, just in case - but no change.

Anybody who has any idea about that weirdo glitch?

I am happy to post additional information, if you tell me what you need.

---

### Post by woodbj on 2010-02-26
I get this problem most of the time too but rarely I don't

---

### Post by cecilpierce on 2010-02-26
That's spooky!
Have you tried changing the password to see what would happen?

---

### Post by ElSlunko on 2010-02-26
I have this problem too. After you re-login the issue goes away for me.

---

### Post by VMC on 2010-02-26
> **ElSlunko said:**
> I have this problem too. After you re-login the issue goes away for me.

That's what I wold suggest. Change password to less than 6 characters and see if the "2" shows up then change it back again. You might need to use root if 6 doesn't pass password check.

---

### Post by Sub101 on 2010-03-01
Want to put in I get the same issue. Just typing a "2" causes the login screen to restart once then it works again.

Does anyone know if a bug report has been filled?

---

### Post by Nick9090 on 2010-03-01
try to uninstall plymouth?
It can be found in synaptic, just remove it..

I am using the nivida display card..plymouth causes the "re-log in" and "enter" problem..but I'm not sure about "2"...

also u can install plymouth back easily through synaptic

---

### Post by mickie.kext on 2010-03-01
> **recluce said:**
> 
1.) Lucid boots up fine, with some graphics "crap" in plymouth
2.) The Login Screen displays, there is only one user.
3.) I click on the user and get the password requester
4.) I type in my password: XXXXXX2
5.) As soon as I type the seventh character, the number "2", the screen blanks for a second and the gnome log-in screen restarts!
6.) I click on my username again.
7.) I type in my password and Ubuntu starts up normally.

Same with me. My password is 6 character, and also number 2 in end. GNOME restart is apparently triggered by "2". Is there a Launchbug filed ?

EDIT: I mean Launchpad bug:).

---

### Post by mickie.kext on 2010-03-01
I searched for bug reports, there is no any, so I filled one 
[https://bugs.launchpad.net/ubuntu/+bug/529999](https://bugs.launchpad.net/ubuntu/+bug/529999)

Please confirm this bug.

---

### Post by recluce on 2010-03-01
Thank you for all the good suggestions, folks!

I tried the following:

1.) Changing my password to something that does not contain the letter "2". Voila, no crash upon entering my password on the Login Screen! BUT: Ubuntu now crashes the first time that I hit the number "2" key - no matter where or when!!! When this happens, you are dumped at the login screen again. So changing the password is only a workaround if you disable the "2" key - kind of awkward in every day computer use... :shock:

2.) The crash scenario happens exactly once after system boot, just loging out and loging in again will not produce the error.

3.) Uninstalling plymouth (and plymouth-x11) does resolve the problem. At this point, loosing plymouth is not a big loss at all - it never worked correctly for me anyway, at least not under Lucid.

Could you guys with a similar error verify my steps and see that they are not limited to my system? Thanks!

---

### Post by JPorter on 2010-03-01
Wow, that is bizarre.  Is this a standard wired keyboard?

---

### Post by recluce on 2010-03-01
> **JPorter said:**
> Wow, that is bizarre.  Is this a standard wired keyboard?

Standard PS/2 keyboard (German layout)

The bug is actively tracked here:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/522692](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/522692)

---

