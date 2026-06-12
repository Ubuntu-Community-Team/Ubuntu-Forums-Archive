---
title: "Need only 1 version of Ubuntu"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by orcyclist on 2008-04-18
:confused:  This is an issue I have been pondering for some time. I can install and upgrade Ubuntu with no problems. Nor any problems with any functions. 
My questions: How do I make sure that I have only the latest install version (essentially overwrite or delete the old version. (e.g. When I install 6.xx how do I make sure that 5.xx is gone.  When I installed &.xx how do I get rid of 6.xx and so on.)  AND make sure that I don't kill my files (docs, video, photo, etc.)

Thaks in advance.

---

### Post by forestpixie on 2008-04-18
You will already have a partition for the install to go onto - when you do the install use the manual partition option - pick the original partition mount as / and let the install format the disc. This way all on the partition is deleted before the install starts.

To have files kept over from install to install you need to have a partition seperate from the / and mounted as /home - this is where you have you're data in an install - when you come to install mount it to /home again but do not format the partition.

---

### Post by Jammy4041 on 2008-04-18
Welcome to the forums!

When you upgrade, every package in Ubuntu gets upgraded- and the old ones are replace with new ones. New distribution upgrades do the same. They replace almost everything, and it means software sources change, and if you go into firefox, you will notice before the distribution upgrade that it says something like "fiesty" (for 7.04 Fiesty Fawn) and after you upgrade it will say something like "Gutsy" (for Gutsy Gibbon 7.10- the version you are using).

So Ubuntu 7.xx (I think you wanted to spell) replaces 6.xx.

If you are thinking of upgrading to Hardy Heron (8.04- this version of Ubuntu gets 3 years of support) I'd wait until the stable version comes out. My experience of Stable to Beta upgrades haven't worked as well as I planned, but Hardy Heron will be great- trust me!!!!!!

---

### Post by orcyclist on 2008-04-18
Thanks. 
Yes I did mean 7 and not &. :) I will use the manual partition tools. I did use a similar tool when I used RedHat. 

I appreciate the comment about the Beta to Stable upgrade. I already decided to wait for the stable release for precisely that reason. No hurry. I probably will get some upgrades done for the system in which I will install 8.xx.  I will let you know how it goes.

---

### Post by zvacet on 2008-04-19
To be sure which version you are running 

```
lsb_release -a
```

---

