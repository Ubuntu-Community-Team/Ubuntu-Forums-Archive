---
title: "Cannot login"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by mostafagen2 on 2012-04-02
hi all, 
i'm not profissional in linux life specialy with ubuntu and u can say am a good normal user trying to be profissional, now my problem is after installing ubuntu 11.10 i found it awsome BUT a went to upgrade as it requested and sudenly i cannot login using my account.....why??? idont know _SO PLEASE HELP ME BROTHERS I'LL KILL MY SELF FOR IT _
 
WAITING YOU

---

### Post by zombifier25 on 2012-04-02
What do you mean you can't login? Does the system fails to boot at all, or you managed to get to the login screen but Ubuntu rejects your password?

---

### Post by mostafagen2 on 2012-04-02
no i reach the login screen and i enter the correct password but it return me to login screen again.

---

### Post by mostafagen2 on 2012-04-02
no one support, for a sysem not stable >>> so redirect to another OS should be stable

---

### Post by zombifier25 on 2012-04-03
Does the login screen rejects your password or it does but throws you back off?

---

### Post by raja.genupula on 2012-04-03
I think its a loop back of login . after installing Ubuntu 11.10 , you said you went for upgrade .is that mean of you have 12.04 now ? 

If 12.04 i heard there is a bug for login screen loop back in Ubuntu 12.04 .

[https://bugs.launchpad.net/ubuntu/precise/+source/lightdm/+bug/951404](https://bugs.launchpad.net/ubuntu/precise/+source/lightdm/+bug/951404)

---

### Post by Tass on 2012-05-31
OK - I've had the same issue as everyone else and I think I've resolved it.  I tried removing the Xauthority file and at the time I thought it had worked, with no success.

Turns out it was because I was using the guest account to try delete the file.  The guest account won't let you run any commands as sudo, but running it without sudo didn't give any indication that it hadn't succeeded.

So - here's what I did:
 - From the login, press Ctrl + Alt + F1
 - As the prompt log in with a user with admin privileges
 - Type sudo rm ~/.Xauthority
 - Reboot! (sudo shutdown -r now)

And that worked for me - hopefully it'll work for you too!

---

