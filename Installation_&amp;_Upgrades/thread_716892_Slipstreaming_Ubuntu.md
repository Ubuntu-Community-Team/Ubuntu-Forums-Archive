---
title: "Slipstreaming Ubuntu"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by BobSongs on 2008-03-06
[FONT=Verdana]I've done a search in the forum for the concept of slipstreaming updates into the latest setup CD, but to no avail.

So, since the question has been asked a few times in the past without being answered I figured I'd give it a try. The forum members are now older, wiser and better informed.

[FONT=Trebuchet MS][SIZE=3]**slipstreaming updates**[/SIZE][/FONT]
Is there a method for slipstreaming updates into an Ubuntu setup CD? Coming from the Windows world this was a nice feature.

[FONT=Trebuchet MS][SIZE=3]**my guess**[/SIZE][/FONT]
Now, it is likely that "slipstreaming" is not going to be easy simply because we're not working with a single service pack executable that's designed to scatter its various files all over the place. At best the only way to accomplish this, at present, is to manually replace 200 odd files in their various folder and somehow re-create a bootable ISO.

[FONT=Trebuchet MS][SIZE=3]**downloadable ISOs?**[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3][**This link**]("http://cdimages.ubuntu.com/")[/SIZE][/FONT] shows were one can download an ISO that's updated regularly. It's similar to what I'm looking for. But I'm not currently interested in Hardy Heron. A link to a set of ISOs for Gutsy Gibbon, etc., that are reasonably maintained (old packages replace so that an install results in very few updates required), that would be cool.

:-)
[/FONT]

---

### Post by wolfen69 on 2008-03-06
Remastersys [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/) may be what your looking for.

---

### Post by justin whitaker on 2008-03-06
> **BobSongs said:**
> [FONT=Trebuchet MS][SIZE=3]**slipstreaming updates**[/SIZE][/FONT]
Is there a method for slipstreaming updates into an Ubuntu setup CD? Coming from the Windows world this was a nice feature.

As noted, remastersys can allow you to create a modified setup CD. 

> [FONT=Trebuchet MS][SIZE=3]**my guess**[/SIZE][/FONT]
Now, it is likely that "slipstreaming" is not going to be easy simply because we're not working with a single service pack executable that's designed to scatter its various files all over the place. At best the only way to accomplish this, at present, is to manually replace 200 odd files in their various folder and somehow re-create a bootable ISO.

Actually, what you could do is:

1. Set up a default desktop install.
2. Update it.
3. Install whatever you want.
4. Use remastersys to create a backup image of that install. 

I make it sound easy, but it really isn't. :)

> [FONT=Trebuchet MS][SIZE=3]**downloadable ISOs?**[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3][**This link**]("http://cdimages.ubuntu.com/")[/SIZE][/FONT] shows were one can download an ISO that's updated regularly. It's similar to what I'm looking for. But I'm not currently interested in Hardy Heron. A link to a set of ISOs for Gutsy Gibbon, etc., that are reasonably maintained (old packages replace so that an install results in very few updates required), that would be cool. [/FONT]

The dailies from Hardy are there because there are new fixes and features each day for people to test...once it goes into Release status, there is one set of ISOs, and people are expected to update from there. 

The exception is the LTS releases, which have been known to get updated ISOs over the course of their life. 

I would say wait for Hardy, because once it is released, Gutsy will only get security fixes.

---

### Post by BobSongs on 2008-03-06
[FONT=Trebuchet MS]Thanks, guys.

I'll give your suggestions a try. My /home folder is on another hard drive. Trashing Ubuntu's a small inconvenience compared to what trashing XP was.  So I have no difficulty with the idea of being experimental.

:-)

Here's an oddball solution that is probably more painful, but it came to mind when answering someone else's question.

Install Linux to a PenDrive using PenDrive Linux's method, update it from there and install it from that USB PenDrive. It may or may not work. It's only theoretical at the moment. But [**Remastersys**]("http://www.remastersys.klikit.org/") sounds like the solution. I'll investigate it now.

Thanks again! (I'll click your thanks tags).[/FONT]

---

