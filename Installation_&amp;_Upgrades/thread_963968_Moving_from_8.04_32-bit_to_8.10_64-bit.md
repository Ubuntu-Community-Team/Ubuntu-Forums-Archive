---
title: "Moving from 8.04 32-bit to 8.10 64-bit"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by freak42 on 2008-10-30
Hello all,

the title says it all.
I have a new laptop on which I installed Ubuntu 8.10 64-bit today and I have an old laptop from which I would like to copy as much as possible (read settings, customizations,.. etc).

What is the best way to go about this move?

Shall I just copy my home folder to the new computer and manually install all software and redo tweaks that aren't saved in the home folder. 

Should I upgrade the old box to 8.10 first before copying the home folder?

Are there any better methods?

(And by the way IF I copy over the home-folder (via external HD) how do I handle the ownerships correctly?)

Many thanks in advance for your time!

---

### Post by martrn on 2008-10-30
I am probably not the best person to answer.

The 32-bit version are kept separate from the 64-bit versions therefore the version upgrade will be quite hard.  It would be best to to reinstall, the version of ubuntu/kubuntu you want over the top of your current installations.  If you are moving to a complete new laptop/workstation/computer you would be best totally to install from scratch and copy your home folder across.

If you would like to copy your home folder across to your new laptop/workstation/computer just gzip it and it will keep all the file permissions as the were if any have changed.  

```
tar -czvf my_archive.tgz /home/myname/
```

or 

```
cd /home
tar -czvf archive.tgz myname/files/
```

---

