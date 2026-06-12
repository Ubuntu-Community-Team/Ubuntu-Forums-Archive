---
title: "Missing Applications Icon"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by Sandman62 on 2011-12-19
I recently upgraded from 11.04 to 11.10.  I no longer have the applications icon on my desktop.  How do I get to my applications?  When I go to the software center it shows that I have the applications installed but I have no way of getting to the applications.

---

### Post by hackb0y294 on 2011-12-19
The location should be /usr/share/applications.

---

### Post by mbuell on 2011-12-19
I have not gone to 11.10 yet. In part, because I am extremely wary of Unity. Downright scared. The desktop developers are shooting themselves in the foot, left and right. 

Ok - here is why I replied - I think that your difficulty is the Unity desktop. Look up how to restore classic Gnome desktop - it should be in your boot options. But google it to get good instructions on how to get classic Gnome back. Get back to the classic Gnome desktop and I think your problems will be over.

---

### Post by hackb0y294 on 2011-12-19
> **mbuell said:**
> I have not gone to 11.10 yet. In part, because I am extremely wary of Unity. Downright scared. The desktop developers are shooting themselves in the foot, left and right. 

Ok - here is why I replied - I think that your difficulty is the Unity desktop. Look up how to restore classic Gnome desktop - it should be in your boot options. But google it to get good instructions on how to get classic Gnome back. Get back to the classic Gnome desktop and I think your problems will be over.

I totally agree with the Unity part. It's hard to believe the Ubuntu devs could release something so buggy, then basically force people to use it by not including GNOME.

Regarding the GNOME shell install, just run this in a terminal window:

```
sudo apt-get install gnome-shell
```

Then, after it's done, log out, click the little gear icon next to your username, and click GNOME. You should be good to go.

---

### Post by Sandman62 on 2011-12-19
Thanks for the replies and help.  The desktop is a little confusing in the new upgrade.  I am a beginner and was just getting used to 11.04 when a friend of mine said I needed to do the upgrade to 11.10.

---

### Post by hackb0y294 on 2011-12-19
You're welcome. Contrary to what your friend said, quite a few people (myself included) have no intention of **ever **upgrading to 11.10.

---

### Post by fast_ian on 2012-12-17
> **hackb0y294 said:**
> You're welcome. Contrary to what your friend said, quite a few people (myself included) have no intention of **ever **upgrading to 11.10.

I was of the same opinion. Trouble is, a buddy got the "11.04 is no longer supported" message. He upgraded to 11.10 and it broke *everything*.

I cannot believe that a so called "minor release" made such a huge change - Going to 12, maybe, but this *sucks*.....

Hopefully reinstalling Gnome as above will fix it..... I'll report back after the revoot.

Cheers,
Ian

---

