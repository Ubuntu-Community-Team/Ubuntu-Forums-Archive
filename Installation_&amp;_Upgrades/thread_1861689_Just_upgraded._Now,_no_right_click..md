---
title: "Just upgraded. Now, no right click."
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by MikeVaughanG on 2011-10-15
I just upgraded from Ubuntu 11.04 to Ubuntu 11.10. 

Now; 
I can't right click. 
I can't hold down the left mouse button to drag something. 

My system info is in my signature. 

Any help is greatly appreciated.

---

### Post by BazookaAce on 2011-10-15
I had a lot of errors and bugs when i upgraded from 11.04 to 11.10, but after doing a clean install everything has worked great. I recommend you do the same.

---

### Post by wi0 on 2011-10-15
Does your right click work inside an application like firefox?

---

### Post by MikeVaughanG on 2011-10-15
> **wi0 said:**
> Does your right click work inside an application like firefox?


No, It doesn't.

---

### Post by nipunreddevil on 2011-10-16
Even i have the same problem.Waiting for the solution

---

### Post by nipunreddevil on 2011-10-16
Even the standard Win+d to show desktop isn't working

---

### Post by MikeVaughanG on 2011-10-16
> **nipunreddevil said:**
> Even the standard Win+d to show desktop isn't working

I dont have this problem...

---

### Post by viperdvman on 2011-10-16
Until a solution is found for that problem... I say, for now, go ahead and back up everything in your Ubuntu partition and do a clean install. If a number of us are having better luck with clean installs over upgrades from 11.04, then I say do the clean install. It's more work, but it might work out better for you.

Good luck, y'all :)

---

### Post by ian_balisy on 2011-10-17
I was having this problem too, but found a fix that worked for me here, posted by JulesC:

[http://ubuntuforums.org/showthread.php?t=1859938](http://ubuntuforums.org/showthread.php?t=1859938)

I simply downloaded the file he posted, created a folder in /etc/x11/ called xorg.conf.d then extracted the file in the archive to that folder. Didn't even have to refresh using command.

Hope this works for others!

---

