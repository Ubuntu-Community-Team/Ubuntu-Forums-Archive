---
title: "Where has Synaptic put it??"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2010-07-06
This is driving me nuts.](*,)

I installed "Thinkfinger" on a newly acquired laptop using Synaptic Package Manager & now I can't find any of the files (not the first time this has happened to me).

I've tried searching through various directories/folders and was only able to find one of them.  Where do they get put?

I know this is a bit of a "newbie" problem, but I haven't been able to get anywhere working this out on my own.  Normally, I have no probs installing apps on my Ubuntu systems but, I haven't even been able to find the documentation file (that I installed with the other files) that goes with this particular app.

---

### Post by Yarui on 2010-07-06
Well, I'm not sure where the files would have been put, but if you happen to know what they are called you can do a command line file search:

```
sudo find / -name filename
```replacing filename with the name of the file, of course.

EDIT: Oh yeah, it's been a while since I have used this feature so I kind of forgot about it.  You can use Synaptic Package Manager to find the files.  Right click on the installed package's name and go to properties > Installed Files.  This should solve your problem.

---

### Post by netsurfau on 2010-07-06
Thanks.

Used the right-click/properties method.  So much easier when you know how.
Prob solved.

---

### Post by Yarui on 2010-07-06
Glad to be of help, it's always good when a problem has a simple solution.

---

