---
title: "Synaptic Package Manager Problem"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by hothands14 on 2007-08-09
E:Malformed line 44 in source list /etc/apt/sources.list (URI parse)
E:The list of sources could not be read
Go to repository dialog to correct the problem
E:_Cache->open() failed, please report





this is what happens when I try to run it. 

This is my 1st day with Linux so please help me!

---

### Post by kevinlyfellow on 2007-08-09
First try to go to System -> Administration -> Software Sources and click around (the problem may fix itself ;-))

If not, open your terminal [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) and then copy and paste this command
```
cat /etc/apt/source.lst
```
and post the output.

And welcome to linux, sorry a problem like that occurred off the bat lol

---

### Post by merlinus on 2007-08-09
You might also try this, in a terminal:

```

sudo aptitude update

```

-merlin

---

### Post by hothands14 on 2007-08-09
THANK YOU SO MUCH IT WORKED!!!


Linux I love so much more than windows

---

