---
title: "Keyring Asked at Startup"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by belkinsa on 2010-04-25
Is it me or is your Ubuntu 10.04 RC always asking for your password when you start it up?  It happening to me.  Should I make a big report or fix it on Ubuntu 10.04 RC?

---

### Post by cariboo on 2010-04-25
You are more than likely being asked for a keyring password because you are using auto login. 

This has been covered so often, it should be a recurring discussion. 

Just create a blank password for the keyring, and you won't be asked for a password anymore.

---

### Post by randomizer101 on 2010-04-25
Well it would be nice if this discussion didn't *need* to keep being brought up ;) If you log out and log back in with yor password I find it will prevent this from recurring. I usually enable auto-login only after having manually logged in at least once so as to never need to worry about it.

---

### Post by kaffemonster on 2010-04-26
Using autologin on a clean install of the RC, it kept asking for a keyring password. Blank password did nothing, it just kept asking. This wasn't a problem in Beta 2.

Fortuneatley, manually logging out & back in fixed it :)

---

### Post by cariboo on 2010-04-26
If you have to log out and back in again, you could just as well disable auto login.

---

### Post by kaffemonster on 2010-04-26
> **cariboo907 said:**
> If you have to log out and back in again, you could just as well disable auto login.

Sorry if my first post wasn't clear - I meant that after logging out and back in, my keyring was opened without any problems. 

But after a reboot, I am asked for my password to unlock my keyring - even though my keyring has a blank password. This was not the case in Beta 2 where autologin would log me in and unlock my keyring, no questions asked. I guess it's less secure, but it's not like I keep government secrets on my laptop anyway. I'd like to go back to the old, insecure, easy and fast way of doing it.

---

### Post by cariboo on 2010-04-26
Did you create a blank password, or just remove the one that was there? Just right click Password and and select change password, then enter your login password and leave the rest blank. I hope I'm not being to obtuse, but the solution as worked for many other people.

---

### Post by Queue29 on 2010-04-26
> **cariboo907 said:**
> Did you create a blank password, or just remove the one that was there? Just right click Password and and select change password, then enter your login password and leave the rest blank. I hope I'm not being to obtuse, but the solution as worked for many other people.

Setting an explicitly blank password is extremely hack-ish. Don't you think it would be better to have a check box or something that says, "don't use keyring"?

---

