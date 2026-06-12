---
title: "forensic analysis"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by gpredrag on 2005-09-23
I don't have all the data about the case, but I wonder if anyone has any idea what might have happened:
friend of mine recently installed Ubuntu 5.10. According to what he said, he was installing updates via update manager, when his internet connection broke up. He can't tell me what was being updated at the moment, but I suspect it could be at the time mount package was to be updated, couple a days ago. 
Later, his connection came up, and he ran Update manager again and finished, apparently regulary. Problem is, that something, and he beleives it's this interrupted update, left his system unbootable.
Apparently ther was nothing important on the machine, and he has probably reinstalled Ubuntu by now, but I was wondering if it is really possible that failed download can break package?
Aren't all the packages signed, and that partially downloaded packages go to /var/cache/apt/archives/partial?

---

### Post by az on 2005-09-23
[QUOTE=gpredrag]I don't have all the data about the case, but I wonder if anyone has any idea what might have happened:
friend of mine recently installed Ubuntu 5.10. According to what he said, he was installing updates via update manager, when his internet connection broke up. He can't tell me what was being updated at the moment, but I suspect it could be at the time mount package was to be updated, couple a days ago. 
Later, his connection came up, and he ran Update manager again and finished, apparently regulary. Problem is, that something, and he beleives it's this interrupted update, left his system unbootable.
Apparently ther was nothing important on the machine, and he has probably reinstalled Ubuntu by now, but I was wondering if it is really possible that failed download can break package?
Aren't all the packages signed, and that partially downloaded packages go to /var/cache/apt/archives/partial?[/QUOTE]

The kernel is packaged in such a way as to not leave your system unbootable.  You have to jump through a lot of hoops to leave your system unbootable.  In an upgrade, your new kernel is installed beside the old one, so that if the new one does not boot your machine, you can always pick the onld one in the grub menu.

What do you mean by unbootable?  What is the last thing that happens?

---

### Post by gpredrag on 2005-09-24
Sorry, my mistake, it's more like unusable than unbootable.
Just like one time I recompiled kernel under RedHat, the old, traditional way, and forgot to compile ReiserFS suport.Couldn't mount root partition. Now I appreciate Debian way of dealing with kernel packages, and you have a point there.
My question really was about how apt/dpkg deals with failed downloads of packages. As I have understood, thing like that should not happen. All packages are to supposed to be signed, and corrupted package should not go unnoticed, and incoplete downloads should go to partial folder.
In case of my friend, he's a newbee to linux in general, contrary to my advise he has enabled root account, and that update may not be the only thing he did with his computer that day. He couldn't tell me what exactly was the problem, just a lot of messages he could not understand, and after that he could not get to the console login. It's just that when he told me about that episode I actually agreed with him, but now I think it makes no sence.

---

