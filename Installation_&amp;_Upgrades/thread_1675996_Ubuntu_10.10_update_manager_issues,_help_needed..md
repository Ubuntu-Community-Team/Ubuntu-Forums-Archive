---
title: "Ubuntu 10.10 update manager issues, help needed."
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Jazzmaster94 on 2011-01-26
I have noticed today after running Update Manager (I have two Daily PPA's that I have to update constantly) that it is telling me to do a "Partial Upgrade" since "a previous upgrade may have failed, or one or more programs conflict with a full upgrade".  I'm not entirely sure why this is coming up, since I was not attempting to do an upgrade (even though the Terminal command is technically sudo apt-get upgrade).  I do realize that my experimental PPA Builds of Chromium-Developer and Docky-Developer (maybe AlephOne PPA as well) could potentially be causing these issues, but I have not had this dialog box come up before today. I can still hit cancel and do a normal update.  Any ideas and/or solutions?  To anyone who can help me with this issue: thanks for your time.

---

### Post by NetForce1 on 2011-01-26
I have the same issues, be it with other PPAs though. When I choose to do a partial upgrade it wants to replace wine1.3 with wine1.2, so maybe the problem is related to wine. (I am using wine's PPA, not the official ubuntu wine version)

---

### Post by Jazzmaster94 on 2011-01-26
> **NetForce1 said:**
> I have the same issues, be it with other PPAs though. When I choose to do a partial upgrade it wants to replace wine1.3 with wine1.2, so maybe the problem is related to wine. (I am using wine's PPA, not the official ubuntu wine version)

I also have the Wine 1.3 PPA.  How long have you been having these issues? It started this morning for me.

---

### Post by NetForce1 on 2011-01-27
It started just before I posted my message, for me that's yesterday evening.

---

### Post by Ddes on 2011-01-27
Exactly the same issue. I didn't want to run the "Partial Upgrade" before, not being able to see what was partial about it. But now I gather we all had it wanting to remove Wine 1.3 I risked it, and it is all ok. But what was "partial" about it? As far as it tells you, it went above and beyond the normal update and downgraded your packages.

Anyway, surprisingly my Wine hacks and apps continue to work ok on this updated 1.2 so I'll stick with it for now, to avoid any update clashes.

---

### Post by Jazzmaster94 on 2011-01-27
I ignored the partial upgrade and I just went along with a normal update.  After that was done I restarted update manager and I did not get any more messages.  However, I did not try it this morning to see if a new round of updates would trigger the messages again.

---

### Post by BigSilly on 2011-01-27
I'm getting this too. Just started my update manager to find it, and not seen it before. I'm going to run a normal update and see how it goes.

Odd...

---

### Post by mordhel on 2011-01-27
I had this message this morning as well.  I am using the PPAs for Docky, Wine and several other apps as well.  I went ahead and did the partial upgrade since I was in a hurry to get out the door this morning.  In my case however, I cannot get past the boot screen so I am having to do a reinstall and restoring my home folder.

First time I have ever seen that. o_O

---

### Post by BigSilly on 2011-01-27
Bloody hell mate. I'd be very annoyed!

Luckily it seems just running a normal update rather than clicking the "Partial Upgrade" box is fine. After it installed one round of updates, it then did a check and found a set of kernel updates too. But on rebooting all seems fine. I was *this* close to running the partial upgrade too. Phew!

Maverick for me has just gone from an initial strong and stable impression at release and sunk into a buggy nightmare in recent weeks. Loads of crazy bugs, the like of which I've never encountered before in my use of Ubuntu since 7.04. Have I just been lucky?

---

### Post by Jazzmaster94 on 2011-01-27
> **BigSilly said:**
> Bloody hell mate. I'd be very annoyed!

Luckily it seems just running a normal update rather than clicking the "Partial Upgrade" box is fine. After it installed one round of updates, it then did a check and found a set of kernel updates too. But on rebooting all seems fine. I was *this* close to running the partial upgrade too. Phew!

Maverick for me has just gone from an initial strong and stable impression at release and sunk into a buggy nightmare in recent weeks. Loads of crazy bugs, the like of which I've never encountered before in my use of Ubuntu since 7.04. Have I just been lucky?
I also found that doing a regular update fixes it.  What other issues have you been encountering?  I have had an issue with Rhythmbox for a while, that when I have any music store enabled half of the time I start Rhythmbox it just crashes after about a minute.  Other than that, I have had few issues.

---

