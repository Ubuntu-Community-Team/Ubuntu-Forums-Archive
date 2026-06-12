---
title: "Upgrade to 15.10 frozen mid process with error"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by reswob on 2015-11-02
I have this error during my upgrade from 15.04 to 15.10 (see attached screenshot) which seems to be what is going on with this active thread:  [http://ubuntuforums.org/showthread.php?t=2299724](http://ubuntuforums.org/showthread.php?t=2299724)

I don't mind trying the solutions that are being suggested there, but my first question is this: should I quit the upgrade process before before running the commands suggested?  When I focus on that window and type control-c, it tells me that aborting the operation may leave the system in a broken state.  

Should I do that and then try the suggested solutions or first try the suggested solutions.

BTW, here are a couple of responses from my efforts without closing said window:

user@machine:~$ sudo apt-get update
[sudo] password for user: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

and 

user@machine:~$ sudo dpkg --configure -a
user@machine:~$ 

seems like nothing happened after this command...

Thanks

---

### Post by reswob on 2015-11-04
So after not hearing anything, I just went ahead and canceled the upgrade and rebooted.  After some weird boots where the screens stayed black for a long time before showing the login screen, everything seems to be working OK.

No errors, no broken apps... yet.

Sooo..... whatever.

---

