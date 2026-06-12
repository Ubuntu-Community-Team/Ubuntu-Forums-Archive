---
title: "reinstall as last resort, advice requested"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by danzinho on 2007-03-02
Hi

Somehow my python is corrupted so that all the usual maintenance tools (apt-get, aptitude, synaptic) are unable to resolve other broken packages.

[http://www.ubuntuforums.org/showthread.php?t=372528](http://www.ubuntuforums.org/showthread.php?t=372528)

It seems to be a very intractable problem and I'm reduced to contemplating reinstallation from CD.  A few queries

- with the same Ubuntu version should my files in theory/in practice be conserved?
- I'll obviously back them all up just in case.  Are there any particular system files I'd be well advised to have a copy of - things like my xorg.conf and the cron files for backups.

Many thanks for your advice

Daniel

---

### Post by Herman on 2007-03-02
Hello danzinho,
I don't know the answer to your apt-get problem either.
>  - with the same Ubuntu version should my files in theory/in practice be conserved?No, whenever we format our partition to re-install we lose the access to all the files. So you will need all your files backed up, definitely. 

It's too late this time,  but when you do have your system working well again, there are ways to back up your entire operating system with all its files and settings. I like to keep my files somewhere else, backed up separately. A program called 'partimage' is probably the most popular, you can run it from a live cd or another operating system on the same hard disk with your partition-to-be-copied ummounted. Aysiu has an excellent web-page about how to use partimage, here, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")
Partimage is one of the programs featured in the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") which is free and only a small download. Aysiu describes apt-getting it in Ubuntu and running it from RAM either way would be good.

> - I'll obviously back them all up just in case. Are there any particular system files I'd be well advised to have a copy of - things like my xorg.conf and the cron files for backups.
 Yes, it wouldn't hurt to back up any files that were specially customized. Anything you think might be useful, maybe menu.lst if you have put a little work into customizing it. Probably a list of all your installed software so you can easily re-install it again.

Regards, Herman :)

---

### Post by danzinho on 2007-03-05
Hi Herman

Thanks for all the helpful advice.

Daniel

---

