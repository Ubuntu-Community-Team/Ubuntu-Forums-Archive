---
title: "Unity 3D fail for main user after upgrade"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Retor on 2011-10-14
I've upgraded from 11.04 to 11.10. Unity 3D works for one account, but not for my primary. 

When I try unity --reset, I get this: [http://pastebin.com/8SbwYVff](http://pastebin.com/8SbwYVff)

Then it runs both 3D and 2D (so hitting win-key gives me 3D, if I hit win-key again, 3D hides and 2D pops up).

I've tried everything in this thread: [http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)

Only difference is that I can no longer open compiz config.

Anything else I should try, or is it simply easier to create a new account?

---

### Post by Retor on 2011-10-15
So new account it is?

---

### Post by Retor on 2011-10-15
This is sooo buggy. 

I opened CCSM in a user where unity 3d was working and tried to export configuration. That caused unity to stop working in that user as well. 

When I tried to run "unity --reset" it caused an error that said "This should never happen. You should file a bug" or something. I don't remeber the exact word since X froze, and I had to kill it from another terminal with "sudo service lightdm stop" then "(..) start"

Now neither of the unity versions work in that account and I can't reset it. And only Unity 2d in the other account. 

So I'm thinking perhaps 11.10 was released premature. Maybe I should roll back to 11.04. Or perhaps this is a good time to try Gnome 3.

---

### Post by Retor on 2011-10-15
Reinstalled compiz-stuff and deleted compiz profile settings. Noe the user that didn't have any effects, got Unity 3D back. Still Unity 2d for the main user.

---

