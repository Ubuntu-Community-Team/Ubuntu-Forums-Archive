---
title: "Password changed by upgrade"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by customearl on 2012-07-12
I installed Ubuntu on a Dell Optiplex GS.
I used wubi to install Ubuntu.
I then proceeded to update, and after update the administrator password was changed after reboot.  
The original password was 8 letter password and now the password is a 5 letter password.
I found this out by going user accounts.
My experience is medium level with windows, and beginner in Ubuntu.
HELP!
Thank you.
 .

---

### Post by coffeecat on 2012-07-12
Upgrades do **not** change your password.

> **customearl said:**
> 
The original password was 8 letter password and now the password is a 5 letter password.
I found this out by going user accounts.

User accounts simply shows five dots as a symbolic representation of a hidden password. There is nothing implied about the length of the password. My password is 12 characters long but I see the five dots as well. Are you still able to log into your account with your 8 character password?

---

### Post by cynicalcylon on 2013-04-12
My password seems to have changed after an upgrade too.
My old one won't let me do any admin-y stuff now & all I've done recently was a few upgrades.
Any way I can find out what the new/current password is?

---

### Post by kostkon on 2013-04-12
> **cynicalcylon said:**
> My password seems to have changed after an upgrade too.
My old one won't let me do any admin-y stuff now & all I've done recently was a few upgrades.
Any way I can find out what the new/current password is?
You can reset your password by following [these instructions]("http://www.psychocats.net/ubuntu/resetpassword").

Hope that helps.

---

### Post by cynicalcylon on 2013-04-12
It didn't, until I found elsewhere that it should be **mount -o remount,rw /**
You put **mount -o rw,remount /** which didn't work for me - may have been my system, so might be worth putting it as an option too...

A fab little walkthrough though. Ta :)

---

### Post by bcbc on 2013-04-12
There used to be an option on the recovery menu to remount drives as read-write. I don't know why they took it away because **mount -o rw,remount /** is hardly intuitive.

If I start getting weird behaviour on login after an update (especially with Wubi) I go defensive. Run chkdsk /f on windows partition (for wubi partition), then fsck the root.disk. Never heard of passwords changing... seems unlikely. More likely some corruption (but that's all speculation).

---

