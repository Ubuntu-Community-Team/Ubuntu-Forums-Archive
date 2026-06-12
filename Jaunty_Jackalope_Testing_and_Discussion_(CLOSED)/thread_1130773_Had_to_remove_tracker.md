---
title: "Had to remove tracker"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-04-20
After updating a couple of days ago, I have had to remove tracker from my system. Every couple of seconds it says that the index is broke and want to re-index the machine, this goes in a continuous loop. So the only way to stop it was to remove tracker. Is this a problem only on my machine, or are others having the same issues??

---

### Post by Lunx on 2009-04-20
> **celticbhoy said:**
> After updating a couple of days ago, I have had to remove tracker from my system. Every couple of seconds it says that the index is broke and want to re-index the machine, this goes in a continuous loop. So the only way to stop it was to remove tracker. Is this a problem only on my machine, or are others having the same issues??

Just did a fresh install of Jaunty and installed all updates a little earlier today. I installed Tracker a few minutes ago to see if there were any problems, indexed my system and it all seems to be working fine so far. Perhaps try reinstalling and see if you still have troubles.

---

### Post by jethro10 on 2009-04-20
> **celticbhoy said:**
> After updating a couple of days ago, I have had to remove tracker from my system. Every couple of seconds it says that the index is broke and want to re-index the machine, this goes in a continuous loop. So the only way to stop it was to remove tracker. Is this a problem only on my machine, or are others having the same issues??

Same Here, I did an upgrade also, rather than a clean install, just 3 days ago. Thought I was safe as it's nearly release time!

J

---

### Post by celticbhoy on 2009-04-20
Just tried a complete removal -> reboot -> re-install -> reboot

Still the same.

---

### Post by Polygon on 2009-04-20
did you delete the .config/tracker folder (or wherever it stores its files)?

---

### Post by lean on 2009-04-20
I can confirm this. Had to remove tracker. Actually the popup disappeared after clicking on it multiple times. The reason I uninstalled it was because of memory-leak, it took more than a gig of ram, and seriosly slowed my system.
It is really a shame it happens so late in the game, but at least it is not in the default install anymore, so new users don't get **crap.

I really hope it will get fixed, since I actually use tracker for work.

---

### Post by celticbhoy on 2009-04-20
Yes I deleted the folder in config & just the same, I do think if you select for complete removal in synaptic it should do this for you.

---

### Post by wsonar on 2009-04-20
What is tracker?

---

### Post by Lunx on 2009-04-20
> **wsonar said:**
> What is tracker?


It's a search and system indexing application, you can find it listed in synaptic

These are the details Synaptic mentions

> metadata database, indexer and search tool

Tracker is an advanced framework for first class objects with associated
metadata and tags. It provides a one stop solution for all metadata, tags,
shared object databases, search tools and indexing.

---

### Post by billyShears on 2009-04-20
You can try to reset the databases with the command "tracker-processes --hard-reset".
Deleting the folders ~/.cache/tracker and ~/.local/share/tracker should have the same effect

---

### Post by celticbhoy on 2009-04-20
Thanx BillyShears that has done the trick on my system.

I deleted the folders you mentioned and the one in .config, and re-installed.
After a reboot it seems to be fine.

---

