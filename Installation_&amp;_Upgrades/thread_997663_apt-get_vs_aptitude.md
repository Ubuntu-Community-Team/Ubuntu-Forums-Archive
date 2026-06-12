---
title: "apt-get vs aptitude?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by scottmac112 on 2008-11-30
Hey All:

I was wondering what the difference is between apt-get and aptitude. I use aptitude and it works alright. Same for apt-get. But I'm just wondering what the difference is between the two commands.:confused:

---

### Post by blackened on 2008-11-30
Decent thread on the subject here: [http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/]("http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/").

---

### Post by forkandles on 2008-11-30
This article is worth a read as well.

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by xadder on 2008-11-30
Interesting points in that link, and I wouldn't like to remember all the apt-xxx variants. Still, I just use synaptic - and that's great!

---

### Post by unutbu on 2008-11-30
In [http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html) the author of aptitude, Daniel Burrows, wrote 

> aptitude shouldn't wipe out packages installed with apt-get, period
full stop.

Let's think about what this implies. Suppose package A depends on package B.
Suppose you install B with aptitude, and A with apt-get.

If you try to remove B using aptitude, then it will either

1) refuse to remove B because by policy it can not remove A, or
2) will remove B but leave A alone. A is now a broken package.

Either case is undesirable.

The conclusion, it seems to me, is that you can use aptitude, or you can use apt-get, but you should not mix the two.

Here are some more interesting threads on this topic. 

[http://ubuntuforums.org/showthread.php?t=379804](http://ubuntuforums.org/showthread.php?t=379804)
[http://ubuntuforums.org/showthread.php?t=727077](http://ubuntuforums.org/showthread.php?t=727077)

Be aware of the dates of posts that your read. apt-get used to be criticized because it did not have an autoremove feature. Now it does. aptitude has been criticized for autoremoving too much. See [http://ubuntuforums.org/showpost.php?p=4533599&postcount=14](http://ubuntuforums.org/showpost.php?p=4533599&postcount=14).
I don't know if this is still a problem. For what it's worth, I use apt-get.

---

