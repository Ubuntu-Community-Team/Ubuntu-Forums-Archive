---
title: "Upgrade to 10.04 didn't go well, now unable to start ksmserver"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by zulaxia on 2010-04-30
Hi,

Both computers here just upgraded from Kubuntu 9.10 to 10.04 and the first issue it pretty minor in that neither of them got the two new themes installed. How do you get them and why aren't they just there?

Second issue is a lot more major, one install no longer boots into X and says that it cannot start ksmserver. This was after running nvidia-xconfig when I was told I needed to in order to use the proper driver.

Any help to get me back in? I'm having to boot Windows!

---

### Post by renatkh on 2010-05-01
Got the same problem with ksmserver!
I checked permissions of the home directory and .ICEauthority; everything is fine. :confused:

---

### Post by Neremor on 2010-05-01
Same problem here. See this for a more detailed description of our problem:

[http://ubuntuforums.org/showthread.php?p=9208331#post9208331](http://ubuntuforums.org/showthread.php?p=9208331#post9208331)

---

### Post by elcorazon on 2010-05-01
I posted a solution to the issue that worked for me:
[http://ubuntuforums.org/showpost.php?p=9209147&postcount=3](http://ubuntuforums.org/showpost.php?p=9209147&postcount=3)

---

### Post by zulaxia on 2010-05-01
Thanks guys. the rm libGL.* fix did it for me :)

---

### Post by Khopstick on 2010-05-24
Worked for me too - Thanks!
I guess NVIDIA is to blame for that...?

---

