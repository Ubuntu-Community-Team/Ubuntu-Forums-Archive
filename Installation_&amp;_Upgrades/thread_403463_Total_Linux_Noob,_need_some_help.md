---
title: "Total Linux Noob, need some help"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by Joshkdmw on 2007-04-07
Hey, everybody. I just started running Ubuntu, and I have a problem I need help with.

I'm using 6.10 (edgy). I'm trying to add applications via the add/remove applications program (very nifty, by the way), but I'm having trouble beginning the download. When It's about to start, I get this error message:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



I tried searching for "dpkg--config -a", but returned no helpful results.

My computing background is both in Windows, and OSX. If you're able to make any helpful references, let me know.

---

### Post by raja on 2007-04-07
What you are being asked to do is to type in a terminal ```
sudo dpkg --configure -a
``` Note the space after dpkg.

---

### Post by Joshkdmw on 2007-04-07
Okay, that makes sense. How do I open up the terminal?

---

### Post by aysiu on 2007-04-07
> **Joshkdmw said:**
> Okay, that makes sense. How do I open up the terminal?
This should help:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by Joshkdmw on 2007-04-07
Awesome! Thanks, aysiyu. You too, raja. I'll try this out and see if I'm back on track.

---

### Post by Joshkdmw on 2007-04-08
Hmm. Well, I ran the command. I tried to use add/remove, but now ehen I tell it to download something, the app freezes. It just keeps on loading, for hours and hours. No loading bar shows, and it won't listen when I tell it to quit.

Any suggestions?

---

