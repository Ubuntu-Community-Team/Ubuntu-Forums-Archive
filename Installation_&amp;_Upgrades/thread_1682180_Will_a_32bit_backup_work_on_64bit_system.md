---
title: "Will a 32bit backup work on 64bit system"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by SgtMunky on 2011-02-05
I am thinking about upgrading to 64bit Ubuntu 10.10 because I have heard it's good for gaming and makes things run smoother.  Also, I know it's the new thing and I'm going to have to switch eventually.  Point is I don't want to loose my data with the clean install and I was wondering if I backup my current system, which is 32bit (assuming there is a backup utility, I thought I saw one) will I be able to load that on my new 64bit install?

---

### Post by dino99 on 2011-02-05
ia32-libs have to be installed

---

### Post by oldos2er on 2011-02-05
Do you have /home on a separate partition?

---

### Post by SgtMunky on 2011-02-06
What's the command for the 32 libs? And I assume I do that after the upgrade.  As for the /home folder, no, same partition.  Nothing fancy here, I just did a standard install and realized I might be better off with 64bit so here I am lol.

---

### Post by dino99 on 2011-02-06
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

install the needed package with synaptic, if you need

---

### Post by apmcd47 on 2011-02-06
It entirely depends on what you want to back up and how you do it. If it is only your home directory and you have only data then no problem. If you have programs that need to be compiled and you have the source code (ie C, C++) you can simply recompile them. Programs written in for example python or perl are considered interpreted and don't need anything. For programs that you don't have the source code, perhaps you do need the ia 32-libs, assuming you can't get 64 bit versions. As you are talking about gaming I assume you are running games under wine?

As far as backing up is concerned, how you do it depends on what you have available. If your data will fit on a CD or DVD and you have a DVD writer it's probably easier to copy onto a disc with your favourite authoring tool.

Andrew

---

### Post by SgtMunky on 2011-02-06
apmcd: I do play the games under wine, but I also have a few of those freeware games built natively for linux.  And honestly if I loose my programs then it's no big deal, installing them again isn't that hard, I would prefer not to have to though.  The data is the big issue.  But is it possible to back up on a HDD, I have a terabyte HDD I could use (assuming it wouldn't require any reformatting though)?  

dino:  Currently, I am taking Computer Science classes at my college and I intend to continue with them, so the developer aspect of the 64bit machines is appealing to me.

---

### Post by apmcd47 on 2011-02-06
If it's a USB device you should be able to just plug it in and copy the data over, either using rsync or the drag & drop function of your favourite file manager, or just using tar or zip to create an archive file on the external drive. I would imagine that the installed verion of Linux will cope with whatever filesystem is in use. If it can't cope use 10.10 live CD to mount the file systems and copy, or download  and burn [Parted Magic]("http://partedmagic.com/doku.php") or [Insert Recovery CD]("http://www.inside-security.de/insert_en.html"). Both of these will allow you to find and mount file systems easily.

Andrew

---

### Post by SgtMunky on 2011-02-06
Great news, thanks for the help, this is one of the many reasons to love Ubuntu, massive support community.

---

