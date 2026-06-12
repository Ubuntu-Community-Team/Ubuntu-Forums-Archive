---
title: "Persistent Install problem with Lubuntu 10.10"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2010-12-28
Hi there!

I'm keen on a persistent install of Xubuntu 10.10 on a USB flahs drive.

But there was a snag.  My persistent install ***mostly*** worked; with the notable exception of the wireless Internet connections.  Whenever I selected a wireless network to sign in on, the sign-in window would close immediately, making it impossible for me to sign in.  The wireless connection works fine with the Live Install CD, but not the resulting persistent install on my USB flash drive.

Does anyone know a way around this one?  A friend of mine told me it might be a drive issue of some sort, but I wouldn't know where to look for that...

Thanks!

---

### Post by ranm on 2010-12-29
I am having a similar problem. After setting up a persistent Lubuntu (10.10) on a 4GB SD with Universal-USB-Installer-1.8.1.8 , I started changing the passwd of the original user ubuntu , but after rebooting, I can't log in. So I resorted to hitting Ctrl+the function key that gives you a CLI, and created a new user with a password, and managed to log in with this user.

Now, with the new user I am experiencing the exact same problems with wifi sign in and also my "start menu" only contains two elements, Run and Logout.

Did you create a new user or are you simply using the "live" user ?

---

### Post by C.S.Cameron on 2010-12-29
With my persistent install of 10.10 I click the network thingy on the top of the screen and choose the wireless network and it just works.

---

### Post by M_Mynaardt on 2010-12-29
> **ranm said:**
> I am having a similar problem. After setting up a persistent Lubuntu (10.10) on a 4GB SD with Universal-USB-Installer-1.8.1.8 , I started changing the passwd of the original user ubuntu , but after rebooting, I can't log in. So I resorted to hitting Ctrl+the function key that gives you a CLI, and created a new user with a password, and managed to log in with this user.

Now, with the new user I am experiencing the exact same problems with wifi sign in and also my "start menu" only contains two elements, Run and Logout.

Did you create a new user or are you simply using the "live" user ?

I created a new user myself.  At least I'm not the only one experiencing problems with Lubuntu 10.10 as a persistent install!  Sounds like there's something not quite right with the ISO if the problems are this consistent!

What I'm trying now is making a Lubuntu 10.04 install (it works just fine) and seeing if ***maybe*** I upgrade it to 10.10 from within 10.04 it might not have the same problems.  Of course that'll be slow as hell; so I will try the upgrade to 10.10 sometime in the next couple of days and will see what happens.

---

### Post by M_Mynaardt on 2010-12-29
> **C.S.Cameron said:**
> With my persistent install of 10.10 I click the network thingy on the top of the screen and choose the wireless network and it just works.

Are you talking about plain Ubuntu 10.10 or Lubuntu 10.10?  Lubuntu 10.10 seems to be the fussy one...  :???:

---

### Post by C.S.Cameron on 2010-12-29
You can not upgrade persistent 10.04 to 10.10.
It will fill the drive and you won't be able to boot.

I was talking 10.10.
Instead of creating new user, try changing name and password of existing user in Users and Groups.

---

### Post by M_Mynaardt on 2010-12-30
> **C.S.Cameron said:**
> You can not upgrade persistent 10.04 to 10.10.
It will fill the drive and you won't be able to boot.

I was talking 10.10.
Instead of creating new user, try changing name and password of existing user in Users and Groups.

I was just wondering because I saw you said the upper panel and Lubuntu has only the lower one.

I wouldn't have thought of changing the name and password of the user in User and Groups.  I'll try to give that a go and see what happens...

---

### Post by C.S.Cameron on 2010-12-30
Oops, now that I recall, I did not change the existing user, I made a new user, changed the Account type to Administrator and added a password.
The next time I logged on I was the only user listed in Users and Groups.

---

### Post by M_Mynaardt on 2010-12-30
> **C.S.Cameron said:**
> Oops, now that I recall, I did not change the existing user, I made a new user, changed the Account type to Administrator and added a password.
The next time I logged on I was the only user listed in Users and Groups.

I'll try giving that a go in the next day or two...

***HOWEVER*** ... if the menu doesn't come up at all when I make a Lubuntu 10.10 Persistent install;what then?  :confused:

---

