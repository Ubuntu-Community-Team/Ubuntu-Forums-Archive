---
title: "desktop installation shutdown"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by smokeyone2 on 2015-12-23
After a successful Ubuntu installation on my laptop I thought I would try a desktop installation - compared to the laptop the installation took a long time and then the screen frooze. Switched off power - re started okay but then would not shutdown - switched off power again and restarted - tried again and this time the PC bleeped once and a screen error message 927 non fatal error on front side bus 1 - switched off power again.
Search Ubuntu forums/google mentioned it might be a video card driver problem so went through all the settings and changed the driver to a Nvidia one - all seems fine now but the PC now shuts down almost instantly - words go across the screen - white on black in a flash and the PC is off - all in about one second - is this normal -

Thanks

---

### Post by Vladlenin5000 on 2015-12-23
Yes, it is normal.

---

### Post by smokeyone2 on 2015-12-23
Thanks for the confirmation - after years of Windows where you could make coffee in the shutdown time to virtually instant -
Just for info changed driver from X.Org X server - Nouveau to Nvidia legacy bibary version 173.14.39

---

### Post by Vladlenin5000 on 2015-12-23
It must be a very old card for having such driver being offered but if it works and meets your needs than by all means use it until it breaks.
The shutdown time is typically fast but it depends a lot on how much services are running at the moment just like any other OS. It won't be always like this.

---

### Post by smokeyone2 on 2015-12-23
Thanks again for the help - anything in seconds is fine - it's when it gets to minutes I start to wonder -
Now if only I could solve my login problem ...

---

### Post by Vladlenin5000 on 2015-12-23
> **smokeyone2 said:**
> Now if only I could solve my login problem ...

What login problem? I believe you haven't mentioned it yet.

---

### Post by smokeyone2 on 2015-12-24
On another post another forum member is trying to assist but my system keeps asking for a password upon start up even though I ticked automatically login -

---

### Post by Vladlenin5000 on 2015-12-24
If you're using WiFi then all the passwords of the networks you use or used in the past are stored in a keyring that must be opened thus triggering the request. It wouldn't have to do that if you already entered your (admin) user's password.

Don't use automatic login is my advice. There are plenty of reasons for logging in with a password whereas the only reason not to is laziness.
FYI, password at login is now the default behavior in Windows also. 'nough said.

---

### Post by smokeyone2 on 2015-12-24
Okay then, one less problem to solve - thanks

---

### Post by MAFoElffen on 2015-12-24
But he had asked in both threads, the where that is changed ... and was trying but unclear on that, so was trying to chnage by manually editing the text file. Where he should have tried that was to go to Settings > Users > Unlock > Passwords > check the autlogon checkbox.

Not sure, but I think that the keyring is tied to the userID and not necessarily the password of that userID. I could be wrong, but I believe when you check the autologon, the userid is still tied to the user session, but the system then passes the users password for that session login... Now that you know where to change that, you could test that.

Also-- If that corrects that, then you now have 2 threads that you need to use the Thread tools, to mark those 1 or 2 threads as "Solved."

---

