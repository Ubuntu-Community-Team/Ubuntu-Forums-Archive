---
title: "reinstall hoary without losing data?"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by 12twelve12 on 2005-08-07
i know everyone says you shouldn't ever have to reinstall linux to fix something, but i'm a total newb and all that mess. i'm just wondering how i could reinstall ubuntu without losing my files already on there. my system is screwed i can't even boot to a gui or anything. something about syslogd hanging and never starting. i was able to start in rescue mode, the type quit or exit and it would start "x", but now it just hangs at syslogd, (i hope that's what it's called.) anyway if this doesn't make sense it's because i have no idea what i'm talkin about. so, is it possible to reinsall ubuntu from the rescue cd?  thanks

---

### Post by Teroedni on 2005-08-07
Yea you could use a rescue cd to create an extra partition, 
and then you could use a Ubuntu live cd to copy your file over to that extra partition.

Then you only need to reinstall on main partiton and then copy over your files afterward

Should work;)

---

### Post by Teroedni on 2005-08-07
BY the way im losed files plenty of times due to reinstall(I mesh with my system pretty badly:P

As i have started to use Openoffice and html coding more recently i have foundm out i need to protect my data from getting deleted.

Therefore i have created
1 Home Partition
and 
2 Ubuntu partition also Dual Boot;)

So if the one goes down(Which will happend) all i need is boot into the other and fix it from there

May be an Idea for you to;)

---

### Post by 12twelve12 on 2005-08-07
[QUOTE=Teroedni]BY the way im losed files plenty of times due to reinstall(I mesh with my system pretty badly:P

As i have started to use Openoffice and html coding more recently i have foundm out i need to protect my data from getting deleted.

Therefore i have created
1 Home Partition
and 
2 Ubuntu partition also Dual Boot;)

So if the one goes down(Which will happend) all i need is boot into the other and fix it from there

May be an Idea for you to;)[/QUOTE]
 err, i don't have room for another partition :/

---

### Post by Teroedni on 2005-08-07
ohh too bad:(

What are yur machine specs?
How big Hard drive?

---

### Post by artinla on 2005-08-07
do you have a /home partition?

just reinstall, use custom partitioning and select to NOT format the /home partition.  Format all the others that Ubuntu uses.

make sure that any data that you want to save is located there.  When you reinstall, use a different username than before.

Works for me.

Art

---

### Post by Pablo El Vagabundo on 2005-08-08
I have a similar issue.

If I manually delete all dirs except the home dir, which i can rename, can I ask the installation not to format the root drive?

Will it delete the renamed directory or just install a fresh ubuntu?

Pablo

---

