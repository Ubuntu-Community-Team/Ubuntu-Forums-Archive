---
title: "Desktop appears, but nothing responds"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2011-01-10
After making a new install of Maverick, it lets me login but then drops me on a desktop that is empty apart from the menu and taskbar. That's not a problem in itself, but nothing responds when I click it. The mouse pointer moves, but I can't click anything. Before logging in, I can click stuff on the login screen, so the mouse as such works.

---

### Post by karthick87 on 2011-01-10
Create a new user and see if that user has the same problem?This will  help us to  find the problem.

---

### Post by pinkunicorn on 2011-01-10
> **karthick87 said:**
> Create a new user and see if that user has the same problem?This will  help us to  find the problem.

My personal user (which has a home directory mounted via nfs and krb5) was the one that doesn't work.

A regular user local to the machine works fine, as does root.

Of course, when I try again to verify the problem with my own user, it fails in a different way, even though the only change from my last try is a reboot and then the logins by the local user and root. This time, I get past the login dialog but then get stopped by a dialog that I don't remember the wording of, but the cause of it is that my home directory isn'&#7831; available (which isn't immediately obvious from the dialog). I've seen this problem a lot before when dealing with the combination of Ubuntu/nfs/krb5. I have gotten it to work in the past, but I haven't gotten to the bottom of the exact cause. This combination doesn't seem entirely good.

After a reboot I try to login as myself again (without trying the local user and/or root first), and then I get the desktop where nothing can be clicked again. I didn't note it last time, but that desktop also shows the "waiting" mouse pointer.

Actually, this seems repeatable:

 - Log in with my user first:
   My user ends up with a desktop where nothing can be clicked 
   (but the desktop in itself indicates that my home directory is 
   available)

 - Log in with local user, and then my user:
   My user gets stopped by a dialog, since my home directory
   isn't available. 

This just gets weirder...

---

