---
title: "Ubuntu 14.04 User rights confusion-errors"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2014-09-27
The problem is that when I login in ubuntu 14.04 as a guest user that was created during the initial installation  unity desktop look fine.
But when I change to the user I normally login into  unity side bar is visible, and I when I launch ubuntu software center it it start then close automatically.
but when I login as a guest user I an launch ubuntu softare center, and all unity bars are are in place.

---

### Post by fly-by-night on 2014-09-27
If I understand correctly, the problem relates to the Unity Launcher. 
Check System Settings/Appearance under Behavior tab. Set to Off.

Edit: Ubuntu Software Centre opening and closing, sorry can't help

---

### Post by hoboy on 2014-09-27
> **fly-by-night said:**
> If I understand correctly, the problem relates to the Unity Launcher. 
Check System Settings/Appearance under Behavior tab. Set to Off.

Edit: Ubuntu Software Centre opening and closing, sorry can't help

Tks very much any suggestion is welcomed I am desperated now I have used 2 days on it.
the suggestion did not helped.
I don't understand when I log in as Guest everything works

---

### Post by hoboy on 2014-09-28
no answer ???

---

### Post by echotech2 on 2014-09-28
It's the weekend.  Wait for a day or two.

---

### Post by yancek on 2014-09-28
Each time I have installed Ubuntu I have been prompted to create a user (one user) and that user is the primary user and will have root/admin privileges.  I have never seen a guest user on an installed system so I'm wondering where that came from.  I suppose it would be easy enough to do.  Was the user you created during the install 'guest' and you later created another user?   I guess that would explain your situation in part at least.  Maybe you could clarify these points.  Or maybe I'm not understanding the problem?

---

### Post by Vladlenin5000 on 2014-09-28
Actually, by default, there's always a guest account in standard Ubuntu, at least. You can explicitly disable it but the default is with guest account. And no, it isn't part of the problem here. As a matter of fact it helps a lot in understanding where the problem must be: Whenever the desktop is fine in the guest account but it isn't in the main or other users' accounts then something is wrong in that/those profile(s). What's wrong is what you need to find out.

Have you installed themes or in any way tweaked the desktop environment?

---

### Post by hoboy on 2014-09-28
Have you installed themes or in any way tweaked the desktop environment? 
I have installed Gnome

---

### Post by Vladlenin5000 on 2014-09-28
> **hoboy said:**
> I have installed Gnome

There's your problem.

---

