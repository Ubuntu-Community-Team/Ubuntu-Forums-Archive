---
title: "Shutdown, Restart, Logout, all no longer working since upgrade to 13.10"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by lvjonathanrr on 2013-11-25
After upgrading to 13.10, ... Shutdown, Restart, and Logout... items not working.  Nothing happens at all.....No process starts.   I'm referring to shutdown etc..from the "gear" menu dropdown.  I can find nothing posted on this item except 'it may be a bug".  

Having to bring up a terminal and use "sudo shutdown -P now" command.

Any help would be appreciated...... whatever it takes

Jonathan

---

### Post by Nick_McKinnon on 2013-11-26
I have the same problem... If I find a solution, I'll post here.

---

### Post by Nick_McKinnon on 2013-11-26
Well, I found a kind-of solution:

[http://ubuntuforums.org/showthread.php?t=2181434&highlight=Can%27t+shutdown+reboot+13.10+upgrade](http://ubuntuforums.org/showthread.php?t=2181434&highlight=Can%27t+shutdown+reboot+13.10+upgrade)

If you follow the steps outlined in the first response by adec2, you will be able to shutdown Ubuntu by clicking on the cog-looking thing in the top right corner & selecting "Shut Down". You will no longer get a confirmation dialogue box, but at least Ubuntu will shutdown...

So you need to open "dconf Editor" and go to [COLOR=#000000]/apps/indicator-session[/COLOR] and tick the box next to [COLOR=#000000]/suppress-logout-restart-shutdown

[/COLOR]Hope that helps...

---

### Post by lvjonathanrr on 2013-11-26
Good quick fix....thanks very much.

---

### Post by Nick_McKinnon on 2013-11-29
No worries, glad it worked for you too. Now if I could just get Backup working...

---

