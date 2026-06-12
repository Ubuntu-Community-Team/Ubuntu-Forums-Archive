---
title: "install xubuntu on computer without internet connection?"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by carlaJ on 2006-08-11
Hi,

I'm VERY new to linux and even with 'the other' operating system i'm not very good, so please if you know the solution to my problem, can you formulate it very simple?
I started to install xubuntu on an old pentium 3 with 128 M ram. Everything went OK, until now: I have to delete # in front of some lines after I typed 'sudo nano /etc/apt/sources.list'. But these are http lines (I expect the computer will start downloading files) and this computer is not connected to the net (it's upstairs, no modem in the house or in that computer). I have internet access on another computer (the one I'm typing this on :-)
What shall I do now?

---

### Post by Jussi Kukkonen on 2006-08-11
sources.list contains addresses used to update currently installed software  and to install new software... If you don't intend to do either, you're doing fine. 

If you do need software not found on your install CDS, things get trickier: the ubuntu software update/install procedure pretty much needs an internet connection... there are ways around this though. Tell us what you need, and we'll see.

---

### Post by dolby on 2006-08-11
maybe download the new 6.0.6.1 release from another computer which pretty much up to date...

---

### Post by Herman on 2006-08-11
> I have to delete # in front of some lines after I typed 'sudo nano /etc/apt/sources.list'. But these are http lines (I expect the computer will start downloading files) and this computer is not connected to the netcarlaJ,  Don't worry. :grin:
The sources.list file, which lives in /etc/apt directory is a file where the computer has a list of 'repositories' it can look up on the internet to download updates and software from.

A 'repository' is something like an on-line collection of software where people who write the software can send it to and make it available to users. There are several of these sites you can enable that are approved for use with Ubuntu and the software we get from those is safe and we can trust it.

You do not have to do anything to this file if your computer is never going to be plugged in to the internet.
It won't hurt anything if you do enable extra repositories though. 
Either way, it doesn't matter.
 
If you do find a way to plug your computer into the internet someday, and you want to install more software, if extra repositories are not enabled (left as they are when Xubuntu was first installed) your list of available software will be small.

If you 'uncomment' the extra repositories, (remove the '#' (hash marks), and you plug the computer into the internet someday, you will find a much larger list of software you can choose from and download for free.

Most people want the largest list of free software they can get as long as it is from 'safe' or 'trusted' sources. 

Some people even add more repositories that they find out about from freinds if they want some special software they can't get from the regular approved sources. When they do that they need to be aware that they could be taking a risk.  The software they might get may not have been checked to make sure it is safe for use with Ubuntu and clean from possible malware like rootkits and the like.

If you are not connecting to the internet and you are happy with the software that already comes with Xubuntu, (which is already pretty good), you can relax and not worry about it. 

Or do as dolby suggested in the post above this. You might be able to just run the CD in your CD drive and it might offer to update from the CD without the need to re-install. I have not had time to  try that yet.

Regards, Herman :grin:

---

