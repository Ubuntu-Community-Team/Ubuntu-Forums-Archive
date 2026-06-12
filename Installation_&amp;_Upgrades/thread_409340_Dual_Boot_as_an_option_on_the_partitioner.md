---
title: "Dual Boot as an option on the partitioner"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Anonii on 2007-04-14
Greetings,

**[introduction]**

just yesterday my 13 years old cousin asked me why I don't have an antivirus. I explained him that I don't use Windows, and that Linux is an alternative OS. He didn't fully understand it, but due to a virus experience a week ago, he was ecstatic about it... He asked me if it's free, and I answered "as free as it gets". He asked me if he can play games, I answered "No." (I'll be back at that.). He asked me if he could chat in MSN, I told him "definately". And then he asked me why he couldn't play his favorite WoW in Linux. I tried to explain him, without complicating the issue with Wine and 3D support (he has an ATI card, so I won't even mention it.). I told him that Linux will be quite tough to manage especially in his age and with his English skills (English is not his mother tongue), but well, he wanted to try it.. I said to him, that he can dual boot Windows and Linux, and he assured me that he would try it in a week or so. Well, to tell you the truth, I'm not that happy with my 13 years old cousin trying Linux, and, obviously, me beeing his first source for support, but I'd like to see how he can manage it... Now well, I will obviously instruct him to use Ubuntu, but I have absolutely no idea about Dual Boot even tho I'm using Linux for like 4 years...  I know that I could search the wiki and find a nicely constructed guide about it, but the question is:

**[/introduction]**

[SIZE="1"]...and after this boring, full of syntax and grammar mistakes, introduction comes the...[/SIZE]

**tl;dr part:**

Why is there no option in the Feisty/Edgy install partitioner for Dual Boot? I bet that there would be no big deal... I mean, even Debian (the "even" goes because Debian is always mentioned as a non-user-friendly distro), has an option for a "compicated" partition scheme (you know, /etc /bin /usr and the rest, in their own partitions), and I bet that what I'm talking about iis even less the trouble.
I **guess** that the already installed OS's size wouldn't matter, and the user would only have to input the desired size for it, then the rest are already done. Isn't that right?



Thanks..

---

### Post by zvacet on 2007-04-14
Depends of how much free space you hae and do you want free some space from windows partition.Let´s just pretend that you have enough free space.During instalation you will came to the partition stage,and then choose manual way to partition.Next you will see win partition and your free space.In the free space you will partition like this:
1. root =5-10GB              mountpoint /
2.home =rest of  free space exept      mountpoint /home
3.swap =1GB

---

### Post by Anonii on 2007-04-16
[B]EDIT: It's okay, the guys at #ubuntu-devel cleared it up for me.

Thanks.[/B]

---

