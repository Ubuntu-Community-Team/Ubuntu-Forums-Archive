---
title: "is it safe to use the same /home folder for multiple installations?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-04-06
Like the title says, is it safe (as in no major problems) to use the same /home folder (or partition)  across different versions of ubuntu and maybe other linux distros? I'm thinking that it WILL cause problems because different versions of programs trying to read different versions of config files and various other things...


anyway...anyone have any experience with doing this?

---

### Post by mmcmonster on 2009-04-06
You will likely get the dot files (ie: ~/.kde/*, etc.) read between multiple incompatible versions of the same application.  You wont get data corruption, but applications may act a little funny or the UI of the desktop may be a little funny.

My advice, create a new username for each OS installation.  Then, in the ~/ folder create a symbolic link to your true documents folder.  That way each OS can adjust your ~/ folder but you keep all your documents in the same location.

Similarly, when I upgrade from one version of Ubuntu to the next, I selectively delete most of the dot files in my ~/ folder so I can see how the vanilla OS installation is supposed to be.

---

### Post by kerry_s on 2009-04-06
> **Polygon said:**
> Like the title says, is it safe (as in no major problems) to use the same /home folder (or partition)  across different versions of ubuntu and maybe other linux distros? I'm thinking that it WILL cause problems because different versions of programs trying to read different versions of config files and various other things...


anyway...anyone have any experience with doing this?

your right, you'll bone it for sure. :lolflag:
you can though use different users on the same home, that way each user folder can have the different configs, you'll just have to remember which is which. ;)

---

### Post by KhaaL on 2009-04-06
I haven't tried it myself, but just like the other blokes that have already told you its not advisable since it might get majorly borked up.

---

### Post by FuturePilot on 2009-04-06
I wouldn't recommend it. Newer versions of programs can change their config files around which can cause incompatibility with the older version of the program. And then when you try to run the older version it either won't start at all or it will crash. I've seen this happen before.

---

### Post by kansasnoob on 2009-04-06
Generally NO!

It is possible if you create different profiles when installing, but why would you?

It's much better to create a separate data partition:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

I'll grant you that that uses the Alternate CD which we'll seldom do now, and also FAT 32 which we'd also seldom use now, but the same general principles apply!

I personally use external USB drives for most storage, mostly formatted in NTFS, and they're easily mounted by adding ntfsprogs and pmount to my Ubuntu installation. But I'm paranoid about data loss having lost data to fire, flood and a vindictive ex-wife!

My drives go in tupperware, then the fireproof gun-safe!

---

### Post by hexion on 2009-04-06
I've been using the same /home partition for the developer and the stable version at the same time during the whole developing process since Dapper. Not a single problem.

I'd like to know whether people here are talking by experience or only 'in theory'. In theory yes, incompatibility can happen. In practice, never happened here.

That doesn't mean I would recommend it. However what's the worst you can loose? The config file for an application?

---

### Post by FuturePilot on 2009-04-06
> **hexion said:**
> I've been using the same /home partition for the developer and the stable version at the same time during the whole developing process since Dapper. Not a single problem.

I'd like to know whether people here are talking by experience or only 'in theory'. In theory yes, incompatibility can happen. In practice, never happened here.

That doesn't mean I would recommend it. However what's the worst you can loose? The config file for an application?

I speak from experience. For example, once I upgraded liferea to a newer version and it changed some of its config around. Later I decided to go back to the older version for some reason. Then the older version didn't even start. It just segfaulted. I then realized it was because it modified its config files and it wasn't compatible with the older version.

Another example is Firefox. If you went from Firefox 2 to Firefox 3, you couldn't go back to Firefox 2 without deleting your profile because of all the changes it made.

---

### Post by kerry_s on 2009-04-06
> I'd like to know whether people here are talking by experience or only 'in theory'.

from experience, i know it works with different users, even across several distros. i've tried lot's of things, linux is a playground. :lolflag:
if in doubt back it up, then go for it, best way to learn is through experience, don't listen just do it.

---

### Post by mmcmonster on 2009-04-06
From experience.

I was using Ubuntu for quite some time.  Then decided to try Mandriva or a similar OS.  The desktop was a pretty screwy combination of the Ubuntu and Mandriva desktops.  I deleted all the dot files and logged in again and it was all good. (Without a reinstall of the OS)

---

### Post by rbmorse on 2009-04-06
> **hexion said:**
> I've been using the same /home partition for the developer and the stable version at the same time during the whole developing process since Dapper. Not a single problem.

I'd like to know whether people here are talking by experience or only 'in theory'. In theory yes, incompatibility can happen. In practice, never happened here.

That doesn't mean I would recommend it. However what's the worst you can loose? The config file for an application?

Evolution has proven to not be particularly backwards compatible at times.  When that happens you lose all your accumulated mail and settings.  This isn't all that serious if you have good backups, but it is inconvenient. 

I've also had various gnome elements go bad when faced with version inconsistencies (panels are bad in this regard).

---

### Post by dirtylobster on 2009-04-07
> **mmcmonster said:**
> You will likely get the dot files (ie: ~/.kde/*, etc.) read between multiple incompatible versions of the same application.  You wont get data corruption, but applications may act a little funny or the UI of the desktop may be a little funny.

My advice, create a new username for each OS installation.  Then, in the ~/ folder create a symbolic link to your true documents folder.  That way each OS can adjust your ~/ folder but you keep all your documents in the same location.

Similarly, when I upgrade from one version of Ubuntu to the next, I selectively delete most of the dot files in my ~/ folder so I can see how the vanilla OS installation is supposed to be.

This is good advice, hadn't even thought about symlinking!

---

### Post by Flag on 2009-04-07
Using same home partition for various OSs' for years now, no prob.

---

### Post by Polygon on 2009-04-07
hmm....i guess i will try using the same home folder for jaunty once i upgrade from intrepid and see how that works.

---

### Post by RIchard James13 on 2009-04-07
I've done it between Slackware and Ubuntu. And also between different versions of Ubuntu.

---

### Post by hexion on 2009-04-07
It seems that our experiences differ. Probably a bit of analysis of the different installations before sharing the home partition would help avoid problems.

Here it's been fine so far. If I ran into problems (probably I suffered from the firefox issue too, I can't recall) they weren't that difficult to solve and I had backups just in case anyway. That's probably the best advice in this thread.. sharing /home may or may not be problematic but a backup is highly encouraged.

---

