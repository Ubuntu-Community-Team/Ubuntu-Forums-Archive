---
title: "First Impressions Jaunty Jackalope"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ramjet_1953 on 2009-02-27
Hi, Guys!

Just a few comments on this alpha release.

Firstly I was impressed that for an alpha release the install on my Acer TravelMate 4101 went without a hitch.

I manually partitioned and set up partitioning using /, /home and swap.
I also used ext4, because I could.

Everything seems to run well and fast.

The only complaints that I have are not particular to Jaunty, but have existed with every release since Dapper.

1. Even though the installation sees that I have a HP printer connected during install, HPLIP is not installed automatically.
Surely, common sense dictates that you need this package, to be able to control and maintain the printer?

2. Even though wireless networking is enabled for my hardware, the installation does not enable the LED on my laptop to indicate that it is working.
It is not a big deal to make a file [COLOR="Blue"]/etc/modprobe.d/ipw2200[/COLOR] and put the line [COLOR="Red"]options ipw2200 led=1[/COLOR] into that file.
However, for the new user this can be quite beyond them.
Other distributions that I have tried do this automatically during installation, so there is no reason why it cannot be automated in Ubuntu.

3. Since 7.10 the installer no longer recognizes that I have a WinModem on-board.
Again, this is no biggie, as I can install the Smart Link [COLOR="Red"]sl-modem-daemon[/COLOR] manually.
Again, however, for the new user this can be daunting.

I realize that the above difficulties are specific to my hardware, but other distributions out there handle these issues with aplomb.

Overall, I think that Jaunty is going to be another big success.

Regards,
Roger :D

---

### Post by fut21 on 2009-02-28
Why not make a bug repport about these issuses?

---

### Post by ubuntu27 on 2009-03-01
File a bug report at [LaunchPad]("https://launchpad.net/")

also, here is a thread on how to [Contribute to Ubuntu Jaunty Jackalo]("http://ubuntuforums.org/showthread.php?t=996538")pe

---

### Post by bvanaerde on 2009-03-03
I've got an Acer Travelmate 4001WLMi, and I'm glad that the [freeze bug at logon]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220345") is no more in Jaunty :D
I haven't tested much, but everything seems to be working out of the box.

I'm using Ext4, without any problems.

---

### Post by nyarnon on 2009-03-03
Hardy was my first cup and I entered intrepid at beta level. The experience was great and I couldn't resist going alpha with Jaunty.

I have a distinct impression that the development team is even more involved then with intrepid. It's raining updates and even though, the system remains fairly stable.

I think this is a great achievement of the development team and I think this thread is an excellent occasion to thank them for their effort.

So lets give them them as much feedback as they give us updates. Jaunty is going great.

---

### Post by Nullack on 2009-03-03
Thats right mate, let Fedora be broken with kernel mode setting, the FOSS nvidia driver, the .29 kernel and all the other things arent ready and arent robust. Ubuntu should not and does not need to be bleeding edge.

Especially when fixes from SVN or GIT or whatever are cherry picked into Debian packages.

---

