---
title: "dual-booting ubuntu and suse"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by shax on 2006-11-01
Hello,

I've recently switched from windows to Linux (cold turkey, no dual boot after I tested out Ubuntu from LiveCD) and I'm loving it. I've already learned a lot and I groan every time I have to use my buggy windows system at work. 

Anyway, now that I've gotten my feet wet with Ubuntu (which I love), I want to try out Suse. My questions are:

1- After googling around, it seems that installing Suse first is easier, and that there are some things I have to manually change if I have Ubuntu installed first. Does anyone know the procedure exactly?

2- I have one main partition on a 30 gig harddrive, with a 1.2 gig swap. I assume I need to repartition before the Suse install, but will I need to create another swap partition? And what size would be recommended if I want to keep Ubuntu as my primary distro, or does it not matter since I heard that two linux distros share the same /home (akin to having ubuntu-gnome and kubuntu, maybe)?

3- Is there an issue with using the same username for both distros or will that mess things up?

4- Is there anything I need to do in particular when partitioning for Suse, or is it just a regular partition?

Thanks!

---

### Post by Joe_CoT on 2006-11-01
Running both Suse and Ubunu should be relatively painless. Answering your questions in a completely random order:

1) You can use the same swap partition for both. Shouldn't make any difference.
2) From my experience, it doesn't matter whether your linux partitions are primary or logical
3) You can use the same username in both, as they're both completely different installs of linux with their own file systems. This would only be an issue if you made a separate partition for your home directory and used it for both, which I don't recommend. If you do share the same /home partition for both, yes, you'd want separate usernames so that the user's home directory isn't overridden.

Basically, I'd recommend installing Suse first and Ubuntu second, simply because I want ubuntu's grub to be the one used. Odds are the procedure is similar if you use Suse's grub

Install suse. Then look at the suse /boot/grub/menu.lst . you'll want to copy the sections involving booting into suse.

Install ubuntu. After installing ubuntu, add the Suse boot options to Ubuntu's menu.lst . Then reinstall grub with
```
sudo update-grub
```

And you should be good to go.

---

