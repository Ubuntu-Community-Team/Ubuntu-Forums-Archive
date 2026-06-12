---
title: "Which updates to install...."
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by ncwalker2010 on 2010-11-10
When I start Ubuntu 10.xx it wants to periodically send me updates.  Sometimes for Ubuntu, sometimes for Firefox, whatever via the update manager.

It's nice that it (unlike Windows) actually gives me a choice as to which ones I want to install.  I am strong computer user - applications and high level code - but have little knowledge of operating systems and structure.  I sort of have an understanding of what I am seeing, but really don't know what it does.  So the list is a little daunting when it shows up.

Is there any reason why I would NOT want to install everything it offers?

What is the criteria for accepting?  Any rules of thumb of things that should be avoided?

The PC in question is the home PC.  It's used by my kids for games, schoolwork, used for internet browsing.  I do have it as the server PC in my wireless network.  The router has WPA2 security enabled so the system is secure.  But I am running Samba to let the totally aggravating Windows laptop work has forced on me :-) be able to write files to my Linux box and print over my wireless network.

I say this because I did an "accept all" and the system got REALLY sticky.  Hung up where it worked perfectly before.  We suffered through it, a few days later another batch of updates came through and everything was OK then...

(And I am not talking about packages I find on the web, or untrusted sources, I am talking the list that the Update Manager gives me when I log in...)

---

### Post by Quackers on 2010-11-10
There are 2 things which I watch for.
The first is NOT to run a partial upgrade if you are offered one! This can have serious problems. In that case I run the updates through synaptic after reading what each one does (in particular what it wants to remove - as this is where problems occur). 
Secondly I watch for what packages will be removed by an update. I am wary of ones that want to remove anything important (like ubuntu-desktop, for instance!) unless the update will replace it later.
That is the extent of my limited (bad) experiences with updates :-)

---

