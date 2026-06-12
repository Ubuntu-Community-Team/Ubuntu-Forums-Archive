---
title: "Installer delay at 82% is a paper cut?"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2009-06-23
I posted this email in response to one of the paper cut emails on the lists:

> 
Hello,

Apologies for the wide email. I'd marked an older bug (wishlist) as a papercut by adding OneHundredPaperCuts to the "affects" list and nominating it for Karmic. I understand the deadline is in a couple of days and the status is still "new" meaning nobody has looked at it?

[https://bugs.launchpad.net/hundredpapercuts/+bug/294523](https://bugs.launchpad.net/hundredpapercuts/+bug/294523)

I hope I'm not doing something wrong with the process.

The bug is about the installer attempting to "download stuff at 82 percent" which kills the install experience. What would normally be a pleasant 5 minute install now takes 15-20 min or more due to the delay at that point. I was wondering if this qualifies as a paper cut candidate and if anyone might take a look and put some sort of indication (invalid, confirmed etc) whether it qualifies to be in the 100 list or not :-)

Regards,
Vishal Rao



What do you folks think?

---

### Post by andrewabc on 2009-06-23
I've noticed a problem like this before.
I have a slow/unreliable connection. And when installing, once done, it checks server and starts downloading or doing something (loading/checking repository?).

Of course after that is done and it does cleanup (just before finishing) it says removing lots of languages. I wouldn't think it would download all languages when I already told it English. And I presume English is already installed on the CD since everything was in English when booting and all the programs were showing English when testing.

---

### Post by caryb on 2009-06-24
I find that the install works better if I drop the network connection at the time the disk partitioner starts that way it doesn't get into the 82% loop later on.:roll:


Cary

---

### Post by psyke83 on 2009-06-24
I would definitely call this a paper cut.

---

### Post by ugm6hr on 2009-06-24
> **caryb said:**
> I find that the install works better if I drop the network connection at the time the disk partitioner starts that way it doesn't get into the 82% loop later on.:roll:

Indeed.  I find the whole experience more straightforward if you install with no network connection.  Why does the install have to do anything online at all?  I actually think it would make sense to install from the ISO, and then allow you to update manually, if you wish.

But I'm not sure this is a *simple user interface issue* to qualify as a paper cut, since the installation process occurs only once, not regularly.

---

### Post by psyke83 on 2009-06-24
> **ugm6hr said:**
> Indeed.  I find the whole experience more straightforward if you install with no network connection.  Why does the install have to do anything online at all?  I actually think it would make sense to install from the ISO, and then allow you to update manually, if you wish.

But I'm not sure this is a *simple user interface issue* to qualify as a paper cut, since the installation process occurs only once, not regularly.

Perhaps. If it's rejected as a papercut, let's hope it gets fixed as a standard bug in time for Karmic's release.

---

### Post by vishalrao on 2009-06-24
Yup, I too simply pull out the network cable during install and everything appears to progress fine even post install... its only when I forget to do so that I go through the awful install experience.

If I (as a user) can work around it easily, why shouldn't it be easy (paper cut) for the developers to comment out the few lines of code to skip that step?

---

### Post by frustphil on 2009-06-24
> **vishalrao said:**
> Yup, I too simply pull out the network cable during install and everything appears to progress fine even post install...

 No, you'll still have to go through it before getting your very first update as far as I am concerned.

---

### Post by psyke83 on 2009-06-24
> **frustphil said:**
> No, you'll still have to go through it before getting your very first update as far as I am concerned.

As far as I can see, the delay is only as long as it takes for the resolution and connection of the repository addresses to time out. This timeout with no network connection is a lot faster than actually letting the updates occur (at least on a 2Mb DSL connection).

Nevertheless, this is an annoyance that could use some attention - for example, the updates could occur while the files are being copied from the CD, not afterwards.

---

### Post by zekopeko on 2009-06-24
> **ugm6hr said:**
> But I'm not sure this is a *simple user interface issue* to qualify as a paper cut, since the installation process occurs only once, not regularly.

there is a paper cut concerning timezone selection in ubiquity. i don't see why this couldn't also be a paper cut.

the user should have an easy option of skipping this step if it takes too long.

---

### Post by 23meg on 2009-06-24
[QUOTE=zekopeko]i don't see why this couldn't also be a paper cut.[/QUOTE]

From [http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/](http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/) (emphasis mine):

> 
As a reminder, a paper cut is:

    * Very easy to fix.
    * A bug that, if fixed, makes Ubuntu more usable for a significant percentage of users.
    * A bug that affects a default install of Ubuntu 9.10. A good rule of thumb: if the bug affects an application that is not in the applications menu by default, it is probably not a paper cut. We are looking for &#8220;ambient paper cuts,&#8221; little glitches a user might encounter many times during the day.

A paper cut is not:

    * A new feature. If it **requires writing more than a few lines of code, or adds any new visual elements to an interface**, it&#8217;s probably not a paper cut.


---

### Post by zekopeko on 2009-06-24
> **23meg said:**
> From [http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/](http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/) (emphasis mine):

> As a reminder, a paper cut is:

* Very easy to fix.
* A bug that, if fixed, makes Ubuntu more usable for a significant percentage of users.
* A bug that affects a default install of Ubuntu 9.10. A good rule of thumb: if the bug affects an application that is not in the applications menu by default, it is probably not a paper cut. We are looking for &#8220;ambient paper cuts,&#8221; little glitches a user might encounter many times during the day.

A paper cut is not:

* A new feature. If it requires writing more than a few lines of code, or adds any new visual elements to an interface,** it&#8217;s probably not a paper cut.**

emphasis mine ;)

---

### Post by caryb on 2009-06-24
Paper cut or no paper cut I install a lot of *buntu's in a week & I find this idiosyncrasy really annoying it has been around a long time.


Cary

---

### Post by frustphil on 2009-06-24
> **psyke83 said:**
> 
nevertheless, this is an annoyance that could use some attention - for example, the updates could occur while the files are being copied from the cd, not afterwards.

+1

---

### Post by Col-1023 on 2009-06-25
When I first encountered this bug, I thought my system had hung, since it doesn't tell you how the download is progressing.

Fixing this would definitely be worthwhile for first time users.

---

### Post by vishalrao on 2009-07-07
Since its not likely a papercut (didnt make the cut :P) I sent this email out: [http://www.mail-archive.com/ayatana@lists.launchpad.net/msg00489.html](http://www.mail-archive.com/ayatana@lists.launchpad.net/msg00489.html)

---

### Post by caryb on 2009-07-08
I had a play & it seems the timeout might be the fact that the resolv.conf file is empty on install. No DNS server = no updates during install.


Cary

---

### Post by vishalrao on 2009-07-08
From what the devs have been saying its more likely due to mirrors being overloaded whenever a fresh release is made...

But really spoils the installation experience, I hope they do something to "fix" it...

---

### Post by caryb on 2009-07-08
> **vishalrao said:**
> From what the devs have been saying its more likely due to mirrors being overloaded whenever a fresh release is made...

But really spoils the installation experience, I hope they do something to "fix" it...

I find this hard to believe for 2 reasons 
1) I installed a Hardy server yesterday & it did the 20 min wait (Hardy is not exactly a fresh release

2) I'm in Aust & 12 hours behind the US, I imagine there wouldn't be that many folks this side of the planet doing install/upgrades.

Cary

---

### Post by scheuri on 2009-07-09
> **ugm6hr said:**
> Indeed.  I find the whole experience more straightforward if you install with no network connection.  Why does the install have to do anything online at all?  I actually think it would make sense to install from the ISO, and then allow you to update manually, if you wish[...]

Hi there
I must admit that I do not completly agree there.
It is a rather good idea to let give the choice to upgrade the system right after or actually during installation to make sure you start out with a system which should be (security wise) up to date.
It may be an issue if that should be done automatically (I personally prefer this, but I see the trouble if you have a slow internet connection) of if it should ask you after installing the ISO-files if you want to upgrade right away.

But with that method you dont risk that the average user starts out with an old ISO installation and no security fixes.

But well, that is just me...:)
cheers
scheuri

---

### Post by scheuri on 2009-07-09
> **psyke83 said:**
> 
Nevertheless, this is an annoyance that could use some attention - for example, the updates could occur while the files are being copied from the CD, not afterwards.

Good idea, however I am not sure if that (as a default behaviour) might lead into other potential problems.
As far as I know (please tell me if I am wrong) the packages are copied from the CD/ISO to the disk and then installed and AFTER all that they will be deleted (as in housekeeping/freeing space from unnecessary stuff).
If you download updates (which may be worth a couple of megs or even a couple of hundred megs depending on the ISO you use) at the same time you MIGHT get into trouble if your /-partition is too small.
So you probably need to check the size of the partition first.

On the other hand, the stuff from the ISO must be installed first anyway to determine what can be upated. That again might be solved by downloading just the "default" stuff.
But it must be made sure that the insatllation of the ISO packages and the updates are not interfering with each other.

Well...as I said...good idea, but I guess it might be easier just to "avoid" the misinterpretation of the wait for updates by displaying some sort of progress bar of the downloads...

cheers
scheuri

---

### Post by ELD on 2009-07-09
> **scheuri said:**
> 

Well...as I said...good idea, but I guess it might be easier just to "avoid" the misinterpretation of the wait for updates by displaying some sort of progress bar of the downloads...


Makes me wonder why this wasn't put in - in the first place?!

---

### Post by vishalrao on 2009-07-24
same problem with alpha 3. someone added a usability tag to the bug at [lpbug]294523[/lpbug] so i hope the DX team considers this as a regular bug/wishlist for karmic and is able to find resources to fix it.

---

### Post by vishalrao on 2009-08-15
some hope in the form of recent activity for bugs:

[lpbug]172879[/lpbug]
[lpbug]294523[/lpbug]

---

