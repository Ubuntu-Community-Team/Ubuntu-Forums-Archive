---
title: "When will the gui installer auto detect other os's?"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by McQuaid on 2006-07-23
I have ordered 10 discs and got them recently.  I plan to just keep one for myself and give the rest out. I've already given out a few, and have received some questions from would be installers.  

My question is the default of format the harddrive.  Why can't the installer do a quick check, and if there are any existing fat32/ntfs partitions say something like: 

'There are other filesystems detected on this drive that may contain other operating systems.  Would you like to keep these os's and use remaining space for ubuntu?'  

Grub detects them and puts them in the boot loader, why can't there be a detection routine right before doing the partitioning?

To go further, I think someone installing ubuntu on a fresh drive are people in the minority.  A huge chunk of people already have an existing operating system (windows) and would, in most circumstances, to keep it while they get their feet went with linux.  To have a default when the vast majority have something different is a mistake imho.

It's just in handing these out, I'm almost afraid one of them is going to call me and scream 'What happened to my windows install!?'

I just think it would be nice if I could confidently say 'don't worry about it, the default is to not touch any detected operating systems'.  Instead I have to warn them that the default is format so be careful, and I say they have to make a seperate partition for linux and then I get 'what's a partition?'

Btw, here are some great vids on doing the install that some other user created:
[http://www.linux.com/article.pl?sid=06/07/20/1654251](http://www.linux.com/article.pl?sid=06/07/20/1654251)

[http://enterprise.linux.com/article.pl?sid=06/07/05/1533204&tid=23](http://enterprise.linux.com/article.pl?sid=06/07/05/1533204&tid=23)

But he mentions he doesn't like using gparted included with the ubuntu installer and instead opts for the parted live cd.  I didn't really understand his reasoning.  Is the parted live cd more up to date on some bug fix or something?

I post this as installing/partitioning is something we rarely do but is so crucial.

---

### Post by confused57 on 2006-07-23
Have you seen this guide:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Qrk on 2006-07-23
The great thing about a LiveCD installer is that all of the system documentation is right there to help you along. It would be increadibly easy to have a partitioning guide linked right to the desktop. Even something like that might be better... and increadibly easy to put into edgy.

---

### Post by Sef on 2006-07-23
> There are other filesystems detected on this drive that may contain other operating systems. Would you like to keep these os's and use remaining space for ubuntu?'

You have to do it manually, but I have never heard of being able to do it automatically.  It would be nice to have it done automatically, but whether it would be feasible to do is another question.

An excellent tutorial on [Dual Booting]("http://users.bigpond.net.au/hermanzone/") is this one.

---

### Post by McQuaid on 2006-07-24
I can't see why it could not be done automatically, at least to some extent.  Surely any installer can check any/all drives for available harddrive space and what partitions currently exist.  Once they are detected (esp if they are other filesystems like fat32/ntfs) ask the user if these other filesystems should remain intact.  

Because face it, as I stated eariler, a huge amount of users trying out ubuntu or any other linux distro are first timers (yes there are a fair amount who have played with numerous distros but you get my point).

And being first time users, they probably already had an OS on their drive and if you asked the majority, they aren't going to say, ya I'm ready to try out linux for the first time, ya go ahead toast my existing windows install, no prob.

So if I am correct and a huge amount of new users trying ubuntu (and probably linux) for the first time, are definitely not going to want to use the default 'format entire contents of drive'

A default the majority will not want to use is not a sane default.


And sef, thanks for the dual booting link.  But my friends are windows users that have never installed any os in their lives.  For most of them I installed windows.   I guess taking that into account, I should babysit the install of linux as well, but it would be nice if I didn't have to.  

As I said wouldn't it be great to say, 'don't worry the installer checks for existing OS's and assumes you want to keep em.'

---

