---
title: "upgraded to 12.04, unable to log in"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by Ansible on 2012-04-22
I upgraded to 12.04 a few weeks ago, from 11.10.  

All was well for a while, but a few days ago I was unable to log in - I got to the login screen and typed in my password, and it hung on 'logging in'.  I rebooted a couple of times and tried again and was able to log in.  Today that solution isn't working.  

Any suggestions?  I mean, besides reinstalling with 12.04.

---

### Post by darkod on 2012-04-22
Not really. 12.04 is still in development so you shouldn't upgrade your main system yet. Things will keep breaking down.

If you think this is a bug you can file a bug report at launchpad to help the developers.

---

### Post by jerrrys on 2012-04-22
I wonder if its the password or your desktop thats getting hung up.

Maybe try another desktop to see.  For gnome classic you could:

sudo apt-get install gnome-session-fallback

---

### Post by Ansible on 2012-04-22
> **jerrrys said:**
> I wonder if its the password or your desktop thats getting hung up.

Maybe try another desktop to see.  For gnome classic you could:

sudo apt-get install gnome-session-fallback

Ok good call.  was able to log in with xmonad.  did apt-get upgrade and now I can log in with unity again.

---

