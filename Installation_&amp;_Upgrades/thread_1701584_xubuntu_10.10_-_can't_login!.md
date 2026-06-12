---
title: "xubuntu 10.10 - can't login!"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by xubno on 2011-03-06
It will hose your system.

You will get stuck in an endless login loop.  Reading through the forums you will see it is a common problem going back to prior versions.  However, the directions for fixing it do not apply because the system files are different.  The problem itself is the only thing that remains  the same.

Installation is not real speedy so you will put a lot of time into it and then be very sad when you can't even log in.  :-({|= Now because you can't login you can't get on the internet to look for a solution.

Beware of v10.10 xubuntu.  It does not install to a running system.  And especially don't install it on a working system because what you get when you are done is one that won't work unless you like using linux from the console.  You can type ctrl-alt-F1 and it looks just like the computer systems from the olden days then.  You can even change your login to a shell and then you get to use a nice shell terminal over a beautiful cloud background.  That's real nice too.  But if you want something a little more modern like X or maybe a nice desktop than the only thing that you will be able to do is login... over and over and over again.

Thanks.

---

### Post by mörgæs on 2011-03-06
That was quite a dramatic post. Have you tried adding boot options?

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by xubno on 2011-03-06
> **mörgæs said:**
> That was quite a dramatic post. Have you tried adding boot options?

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

It's a dramatic situation that calls for a dramatic post!  I'm not the only one with this problem.  Here's an unresolved recent thread that's been going since October of 2010.

[http://ubuntuforums.org/showthread.php?t=1603117](http://ubuntuforums.org/showthread.php?t=1603117)

It sounds like an X problem.  No, I haven't tried boot options.  I just installed directly to my hard drive right after I burned & verified the CD.  Just assumed it would work.  I'm downloading Linux Mint right now.  I'll try the vga=795 option tomorrow.  I know my hardware supports 1280x1024x24.  If the vesa mode is the problem, I wonder what mode xubuntu is trying to use and why?

Thanks for the suggestion.

---

### Post by xubno on 2011-03-06
No. That didn't work. I tried the nomodeset and vga=795.  Same deal.  Screen flashes black when x tries to start and then goes back to the login screen.

very dramatic distro we got here.

---

### Post by Dutch70 on 2011-03-07
> **xubno said:**
> No. That didn't work. I tried the nomodeset and vga=795.  Same deal.  Screen flashes black when x tries to start and then goes back to the login screen.

very dramatic distro we got here.

Funny, I just installed it last week & it was a breeze. So much that I tried a diff distro, just for the fun of it, then went back to Xubuntu. Check with (anotherdrumhead) I think is his name, he just installed it also, with no problems.

Sorry to hear you're having problems, but I don't believe it's the distro. It's either your download, hardware, or process.

---

### Post by Quackers on 2011-03-07
What graphics card are you running?

---

### Post by Rubi1200 on 2011-03-07
Graphics card as Quackers asked for, but also the _full_ specifications for the computer.

And, the output of the following command:

```
sudo fdisk -lu
```

---

### Post by xubno on 2011-03-07
I have no doubt this problem has to do with my hardware.  It's an older P3 Dell machine (Dimension 4100) that I'm using for tests.  Most likely it's the video driver.  Some details:

[SIZE=2]P3 866
512MB
10GB
Nvidia TNT2 32Mb[/SIZE] (this is most likely why X is choking)

Can't do the fdisk right now, the machine is in another building.  But I set up the partitions manually and can tell you there are 3 as follows:

4.9 GB ext3 mounted as /
1 GB formatted as linux swap
3.6 GB ext4 mounted as /home

In our modern age of computing, I am surprised that xubuntu can't probe my hardware and either tell me it won't work instead of just going off into an endless loop.  I've had several other linux flavors installed, namely openSUSE and PClinuxOS and they worked albeit slow.  I've heard about xubuntu's speed and thought it was worth a try, and I can say it does the login loop impressively fast.  :D  Would like to see how it does with the desktop.

I know there are files somewhere that store the logs of x, and although I know how to work vi, the hard part is always finding these logs to check for the problem.  It's a bit frustrating because I've seen suggestions on this forum like "look in your x error log for a clue."  This suggestion is not very helpful.  And it's especially time consuming navigating the directory with ls & cd commands.  It's not like I can launch an explorer to hunt for the files.

Thanks

---

### Post by Linux_junkie on 2011-03-07
With only 10MB hard disk you have very limited disk space. A typical Linux system using X server and desktop requires roughly this amount of space.  So I think you'll need to install Linux without X server to enable it to run  without problems.

---

### Post by xubno on 2011-03-07
That's 10GB not 10MB.  I should be able to easily fit linux with X into 5GB unless there's something I don't know about xubuntu's requierments.  Last I checked, there was plenty of free space on my root partition.  I don't believe small disk is the problem in this case.  But I'm willing to check the appropriate log file to see if there's a disk full message.  Could you please tell me where that file is located and what is its name?

Thanks

---

### Post by Linux_junkie on 2011-03-07
oops I meant to type 10GB.  bloody fingers let me down again!

---

### Post by Rubi1200 on 2011-03-07
If Xubuntu is not working on your hardware, try Lubuntu.

Other options here too:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by xubno on 2011-03-07
I don't know which xubuntu you're working with, but this is the one I'm trying to install:

**Minimum system requirements**

 You need 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.
 To install Xubuntu, you need 2.0 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by xubno on 2011-03-07
> **Rubi1200 said:**
> If Xubuntu is not working on your hardware, try Lubuntu.

Other options here too:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

Please tell me more.  What makes lubuntu special and is it as light-weight as xubuntu?

---

### Post by xubno on 2011-03-07
I've been reading about lubuntu. That may be more of what I want on this machine anyway.  I'll give it a shot.

---

### Post by xubno on 2011-03-07
OK, that fixed it.  The solution was pretty straightforward...  simply install lubuntu and pitch the xubuntu 10.10 distro.

I can say lubuntu is pretty nice.  Very clean desktop, fast, synaptic works well.  I installed firefox and office, no problems.

Just one question, where is the setting to make my monitor resolution permanent?  I can set it per session, but after a reboot it goes back to the default.

thanks

---

### Post by Dutch70 on 2011-03-07
How ironic, I had the same trouble with Lubuntu, that you had with Xubuntu, but as I said in an earlier post. Xubuntu worked great for me. I was then able to add 'lubuntu-desktop" from synaptic. Which also added an LXDE desktop which I like above all. 

Glad you got it worked out. :D

> Just one question, where is the setting to make my monitor resolution permanent? I can set it per session, but after a reboot it goes back to the default.

Sorry, I don't have the answer for that.

---

### Post by ivanovnegro on 2011-03-07
Could someone change the title of this thread, its horrible. :)
Its confusing to write such nonsense because that it did not work was individually.

---

### Post by Dutch70 on 2011-03-07
> **ivanovnegro said:**
> Could someone change the title of this thread, its horrible. :)
Its confusing to write such nonsense because that it did not work was individually.

Hahaa, I don't think so. However they may be able to put it in thread jail, because it is misleading & deceptive. :lolflag:

---

### Post by xubno on 2011-03-07
> **Dutch70 said:**
> How ironic, I had the same trouble with Lubuntu, that you had with Xubuntu, but as I said in an earlier post. Xubuntu worked great for me. I was then able to add 'lubuntu-desktop" from synaptic. Which also added an LXDE desktop which I like above all. 

Glad you got it worked out. :D



Sorry, I don't have the answer for that.

Yeah, that is pretty funny.  I think I know what might have happened to you in lubuntu.  If you select one of the desktops that it doesn't have in the login screen that's how lubuntu behaves.  I tried all of the xubuntu desktop choices though and the only one I could login to was the command shell.  X was unable to start.

---

### Post by xubno on 2011-03-07
> **ivanovnegro said:**
> Could someone change the title of this thread, its horrible. :)
Its confusing to write such nonsense because that it did not work was individually.

I don't think it was individual.  I think these problems are ongoing, others have reported it and are still unable to login.  See the link above that dates back to 10/10.

Maybe my title was a bit harsh, but not totally misleading.  There is a problem, and no solution has yet been reported.

---

### Post by Dutch70 on 2011-03-07
> **xubno said:**
> I don't think it was individual.  I think these problems are ongoing, others have reported it and are still unable to login.  See the link above that dates back to 10/10.

Maybe my title was a bit harsh, but not totally misleading.  There is a problem, and no solution has yet been reported.

There will always be a problem with some distro's on some machines. They simply can't make every single distro work on every single computer in the world. Expecting such a thing is quite unreasonable.

It was absolutely "individual". As I said, Xubuntu worked great on my old computer & many, many others.

Lubuntu on the other hand did not. Should I tell the world that Lubuntu will "hose your computer"

---

### Post by xubno on 2011-03-07
I just saw your computer specs.  You consider that an old computer?  Here are my computer specs:

[http://support.dell.com/support/edocs/systems/dzuul/specs.htm](http://support.dell.com/support/edocs/systems/dzuul/specs.htm)

I did upgrade it to 512MB RAM, though. :)

---

### Post by Dutch70 on 2011-03-07
> **xubno said:**
> I just saw your computer specs.  You consider that an old computer?  Here are my computer specs:

[http://support.dell.com/support/edocs/systems/dzuul/specs.htm](http://support.dell.com/support/edocs/systems/dzuul/specs.htm)

I did upgrade it to 512MB RAM, though. :)

Wrong computer ;)

I'm talking about this one.
[[COLOR="Blue"]Compaq Presario SR1303WM[/COLOR]]("http://www.dealtime.com/Hewlett-Packard-HP-Compaq-Presario-SR1303WM-AMD-Sempron-3000-256MB-DDR-40GB-HDD-DVD-ROM-CD-RW-Combo-Window/prices")

As you can tell by the screenshots, this computer has neither Xubuntu or Lubuntu on it.

 It does appear that Lubuntu is much better suited for your pc though. Thats why there are so many linux distro's. If one doesn't work for your "individual" needs, there is one that almost certainly will. Glad you found yours.

---

### Post by Nicky.. on 2011-03-07
Totally agree xubno your system is by far older.

Thanks for the headsup on this issue ill inform friends with older PCs to give this a miss.

---

### Post by Dutch70 on 2011-03-07
> **Nicky.. said:**
> Totally agree xubno your system is by far older.

Thanks for the headsup on this issue ill inform friends with older PCs to give this a miss.

Be sure & give them this video as well...
[[COLOR="Blue"]Xubuntu Compiz Fusion VERY OLD computer / Better than Vista[/COLOR] ]("http://www.youtube.com/watch?v=_qddueXkD8E&feature=related")

---

### Post by xubno on 2011-03-07
> **Dutch70 said:**
> Be sure & give them this video as well...
[[COLOR=Blue]Xubuntu Compiz Fusion VERY OLD computer / Better than Vista[/COLOR] ]("http://www.youtube.com/watch?v=_qddueXkD8E&feature=related")

That's a pretty cool video.  He was able to do that because the non-free nvidia drivers (96.43.xx) for his nvidia GeForce 2 MX are in the repository and provide 3D support.  The free drivers in the repo don't support 3D for my video card, nvidia TNT.  To get 3D I would need to install the 71.86.xx non-free drivers, but those are not in the repository.  I guess my machine is even older than his.

---

### Post by Dutch70 on 2011-03-08
> **xubno said:**
> That's a pretty cool video.  He was able to do that because the non-free nvidia drivers (96.43.xx) for his nvidia GeForce 2 MX are in the repository and provide 3D support.  The free drivers in the repo don't support 3D for my video card, nvidia TNT.  To get 3D I would need to install the 71.86.xx non-free drivers, but those are not in the repository.  I guess my machine is even older than his.

Yes, yours is older than I would have thought. Let me explain something that may help you to understand the difference. That is if you don't already.

Xubuntu uses an XFCE desktop environment, much lighter than Ubuntu, which uses Gnome. or Kubuntu which uses KDE.

Lubuntu uses LXDE, which is lighter than Xubuntu's XFCE. That doesn't mean that there is anything wrong with Xubuntu, just that it's still a  little too heavy (payload) for your hardware. 

LXDE will even run on an android phone. Have a look...
[[COLOR="Blue"]LXDE on Android[/COLOR]]("http://blog.lxde.org/?p=248")
And this is the (very nice) OS that's on the Android. Which is probably in your repositories. 
[[COLOR="Blue"]http://en.wikipedia.org/wiki/File:LXDE_desktop_full.png[/COLOR]]("http://en.wikipedia.org/wiki/File:LXDE_desktop_full.png")

Another interesting site...
[[COLOR="Blue"]distrowatch.com[/COLOR]]("http://distrowatch.com/")

Anyway, like I said. I'm glad you didn't give up & found one that works for you. Not only that, but you learned a lot & will probably be a big help to other people that encounter similar situations.

Best regards

---

### Post by mörgæs on 2011-03-08
> **xubno said:**
> Maybe my title was a bit harsh, but not totally misleading.

It was harsh and totally misleading. Please ask the moderators to change it.

---

### Post by col48 on 2011-03-08
Yes, IMHO the title need softening, but please bear in mind that
(1) if xubuntu 10.10 were that bad it would never have got as far as release
(2) as has been pointed out in the thread, no OS will run on every combination of hardware that can be called a computer
(3) it is helpful to warn people to be wary.
(4) no doubt, as issues are resolved, 10.10 will improve but [assuming it follows the ubuntu LTS scheme] 10.10 is not LTS so is already obsolescent.

It would be interesting to have, somewhere a continuous census where people could record (in tick-box form) their experience of installing each release or upgrade - this would give a broad idea of user-friendliness, but it would be too ambitious to aim to collect statistics for every combination of hardware.
A) went like a breeze
B) no reinstall needed but issues took < 1 day to resolve
C) issues took a longer time to resolve or one or more reinstalls
D) install failed but possible to revert to status quo
E) disaster

---

### Post by ivanovnegro on 2011-03-08
> **Dutch70 said:**
> There will always be a problem with some distro's on some machines. They simply can't make every single distro work on every single computer in the world. Expecting such a thing is quite unreasonable.

It was absolutely "individual". As I said, Xubuntu worked great on my old computer & many, many others.

Lubuntu on the other hand did not. Should I tell the world that Lubuntu will "hose your computer"

Exactly. I can understand that people have trouble but please use other titles if you want serious help, I think you can read this on the forum guidance, such titles are misleading.

---

### Post by Dutch70 on 2011-03-08
> **ivanovnegro said:**
> Exactly. I can understand that people have trouble but please use other titles if you want serious help, I think you can read this on the forum guidance, such titles are misleading.

LOL, I'm not the OP!!! #-o

---

### Post by mörgæs on 2011-03-08
> **col48 said:**
> 
It would be interesting to have, somewhere a continuous census where people could record (in tick-box form) their experience of installing each release or upgrade - this would give a broad idea of user-friendliness, but it would be too ambitious to aim to collect statistics for every combination of hardware.
A) went like a breeze
B) no reinstall needed but issues took < 1 day to resolve
C) issues took a longer time to resolve or one or more reinstalls
D) install failed but possible to revert to status quo
E) disaster

A good idea, but such a census will be skewed since the majority of users, who never encounter a problem, will not even read this forum.

---

### Post by Dutch70 on 2011-03-08
> **mörgæs said:**
> A good idea, but such a census will be skewed since the majority of users, who never encounter a problem, will not even read this forum.

There is such a thing with upgrading to a new version, and you are absolutely right. Most of the people that post are the ones that had trouble. The happy people are doing something else.

---

### Post by ivanovnegro on 2011-03-08
> **Dutch70 said:**
> LOL, I'm not the OP!!! #-o

Sorry, I agreed with your comment but then talked more in general and referred me to the OP.

---

### Post by ivanovnegro on 2011-03-08
> **Dutch70 said:**
> There is such a thing with upgrading to a new version, and you are absolutely right. Most of the people that post are the ones that had trouble. The happy people are doing something else.

Yes, for example trying to find problems or to help others here. :)

---

### Post by Dutch70 on 2011-03-08
> **ivanovnegro said:**
> Yes, for example trying to find problems or to help others here. :)

Exactly!!!

---

