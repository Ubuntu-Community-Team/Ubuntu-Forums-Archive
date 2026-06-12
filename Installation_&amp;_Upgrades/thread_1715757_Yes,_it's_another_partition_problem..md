---
title: "Yes, it's another partition problem."
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by Krypten on 2011-03-27
Yeah. I got fed up with Windows 7 being so freakishly slow, lagging and freezing all the time. I had nearly forgotten the existence of Ubuntu. Well, I got the idea from my brother, and have now installed Ubuntu 10.10 on my laptop.

Now then, I have a huge partition problem. I would actually enjoy kicking 7 out of my computer. But there are so many files I would like to keep, like movies, music, documents and so on. All located in my home folder on the Windows side.
[INDENT]So, basically I would like to transfer all my personal data from Windows to Ubuntu, and uninstall Windows after the process.[/INDENT] The size of the home folder is apprx 100gb, and the hard drive is around 320gb. The partitions on it now are
|105mb System Reserved|250gb NTFS|Free 31gb|Extended 21gb(Ubuntu)|Recover 12 gb NTFS|

All in all, what do I do? I hope I was clear enough, and am happy the give more details, and information.

---

### Post by Megaptera on 2011-03-27
How much of the 250gb (Windows 7) is used and how much is free?

---

### Post by Krypten on 2011-04-02
> **Megaptera said:**
> How much of the 250gb (Windows 7) is used and how much is free?

I just logged into Ubuntu, and am too lazy to restart the computer. Anyhows, I was remembering, that the used size is a little bit over 100 gb, which would make the free space to be around 150 gb. How come?

---

### Post by 23dornot23d on 2011-04-02
If I asked that question it would probably be to determine whether to just shrink the Windows drive down and leave the files where they are as you can still get to them from Linux .....

The question is how much of it is useful Data that you need to move - a USB 500 Gig hard drive would be handy for this  ..... 

Windows takes up such a lot of room  ......

You are limited to 4 Primary partitions one needs to be an extended one .... you probably have this if you are running linux already ...... there is a [script file that can be run from linux]("http://bootinfoscript.sourceforge.net/") to find exactly how your drive is layed out .....

I would run this .... and post the results ...... you may be able to get more help then .......

Hope this helps in some way .....

---

### Post by Megaptera on 2011-04-02
> **Krypten said:**
> I just logged into Ubuntu, and am too lazy to restart the computer. Anyhows, I was remembering, that the used size is a little bit over 100 gb, which would make the free space to be around 150 gb. How come?

I was wondering if there was space to shrink 7, install Ubuntu alongside as a dual boot and then transfer all your docs etc to a shared data partition as explained here. [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)
That way you've still got 7 just in case, Ubuntu 'cos that's what you want, and data accessible from both.

---

### Post by Krypten on 2011-04-02
My brother suggested to do the same. Shrink down the Windows 7, and keep it for 'just in case' -situations. I could, however, do it. I guess I can't partition the 7 from Ubuntu, or can I? Should I just download some partition program from internet on the 7? Geez :D

---

### Post by Dutch70 on 2011-04-02
No, windows does not like to be messed with from other systems. Defragment windows once or maybe even twice before you start & shrink your windows partition from within windows. You may want to run check disk & make sure you can still boot into windows just to be on the safe side. After that, I'ts all Ubuntu.

[[COLOR="Red"]http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

or this one...
[[COLOR="Red"]http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/[/COLOR]]("http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/")

and just in case you need this one.
[[COLOR="Red"]https://help.ubuntu.com/community/WindowsDualBoot[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Krypten on 2011-04-02
> **Dutch70 said:**
> No, windows does not like to be messed with from other systems. Defragment windows once or maybe even twice before you start& shrink your windows partition from within windows. You may want to run check disk & make sure you can still boot into windows just to be on the safe side. After that, I'ts all Ubuntu.

[[COLOR="Red"]http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

or this one...
[[COLOR="Red"]http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/[/COLOR]]("http://pcsplace.com/tutorial/how-to-dual-boot-windows-7-ubuntu-linux-install-run-ubuntu-on-windows/")

and just in case you need this one.
[[COLOR="Red"]https://help.ubuntu.com/community/WindowsDualBoot[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot")
 
Thanks, I'll try this out and see what happens. :)

---

