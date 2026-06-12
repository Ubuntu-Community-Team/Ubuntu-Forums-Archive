---
title: "stupid update from beta question"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by nutpants on 2012-02-21
is there any reason to hold off on installing ubuntu 12.04?
i am planing to do a fresh install on a computer that has very limited Internet access (as in tethered to my phone). i want to do the install as soon as possible preferably from a "alternate" install disk so full disk encryption will be easy to set up.
so what i am really asking
are there any benefits to waiting for the official release vs updating the beta in april?
i could wait if there are any big advantages to waiting.. 
but i would much rather get with 12.04 now rather than waiting..
and i dont mind a bug here or there as long its not gong to crash everything.
and is there a beta "alternate" install disk?

thank you for any info..

---

### Post by UltimateCat on 2012-02-21
I wrote about upgrading and asked members here in the past.

A few members advised me to wait until Spring; April of 2012

Hope this helps.

---

### Post by grahammechanical on 2012-02-21
Here is the place to download the iso images from:

[http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")

I do not see any mention of an alternate install CD iso image.

It is not recommended to upgrade a distribution release (such as 11.10) to a development branch (such as 12.04) because of the likelihood that something will break that requires a re-install. If you have a separate /home partition and do regular backups of your important data and documents then you can install 12.04 it that is your decision.

I have 12.04 on a separate partition and I can dual boot with 11.10. So, in this way I do not run the risk of having a computer with a broken OS. I also have a separate /home partition.

I have been running 12.04 since before it was an alpha 1 release. It is very stable. I use it every day. I do an update every day.

Sometimes I get messages that something has closed unexpectedly. It is usually due to some libraries being updated and making some other libraries obsolete. This was usually fixed by the next update.

The worse problem I have had was an update that removed the software centre because an important package was not ready to be included in 12.04 and it took about three days for that package to be downloaded and I could re-install the software centre.

It is your choice. If you want to share in testing 12.04 then please join in. Hang out at the Ubuntu+1 section. By the middle of May we will be testing 12.10 development branch.

None of the things that broke caused such problems as to prevent me from using 12.04. I just cleared the messages and went on working.

Do also install the Synaptic Package Manager. We sometimes need an alternative means of updating, or installing packages. Synaptic is not installed by default any more.

The latest 12.04 has Unity 5.4 with the Heads Up Display. There are a lot of improvements.

Regards.

---

### Post by plucky on 2012-02-22
> i am planing to do a fresh install on a computer that has very limited Internet access (as in tethered to my phone).

Distribution update today was over 100Mb and will probably continue until final release.

I would hold off until final release unless you can afford to update every day.

Good Luck

---

### Post by ivanchic on 2012-02-22
I got an advice inside some other thread in this Forum to wait until September-October and upgrade from Ubuntu 11.10 to 12.04 since it will be LTS version (5 years support). By then it should be more stable as I understood. I will listen to that advice :)

---

### Post by nutpants on 2012-02-28
> **ivanchic said:**
> I got an advice inside some other thread in this Forum to wait until September-October and upgrade from Ubuntu 11.10 to 12.04 since it will be LTS version (5 years support). By then it should be more stable as I understood. I will listen to that advice :)

why would you wait until sep-oct? it will be as solid as solid by the release date in April.

i was asking about updating from the beta or alpha to the full release in April. i know there will be some issues running a beta. i wanted to know if i install beta now (on march 1) and do a full update in April would there be any difference or issues i may encounter that may be a show stopper..

i plan on installing with tri boot winxp - win7x64 - ubuntu 12.04 full disk encryption with luks from the x64 alternate install disk.
found here ([http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/))

i can live with some bugs but i really don't want to reinstall everything all over again in April if updating trashes my system,

---

### Post by MoebusNet on 2012-02-28
@nutpants

My 2 cents: As stable as 12.04 is, the devs won't hesitate to break it if they need to fix something important; that's what it means to be in beta.

To avoid the need for a reinstallation, I concur with everyone else: wait for the release. Otherwise, understand that you are risking breakage. Best of luck!

---

### Post by grahammechanical on 2012-02-28
I would like to add that 12.04 is now at Feature Freeze where the developers are not allowed to add any more features but are to concentrate on fixing bugs.

There has also been some testing of packages before they have been put into 12.04. I have shared in testing Unity 5, Unity 5.4 and Unity 5.4+HUD. This involved running more than 170 tests with the opportunity to make comments about each test as well as recording whether things worked as they should have. A report was then sent direct to the developers of Unity. I have also tested a version of Compiz before it went into 12.04. In this way things can be fixed before they become bugs.

There have also been a lot of upgrades from the Linux kernel developers and from Gnome. 

Regards.

P.S. See this link. It illustrates the work being put into making sure that 12.04 is rock solid by release date.

[http://ubuntuforums.org/showthread.php?t=1932523]("http://ubuntuforums.org/showthread.php?t=1932523")

---

### Post by LinuxFan999 on 2012-02-28
The alternate CD requires an internet connection, just like the live CD and the mini CD, so you cannot install Ubuntu without an internet connection. The alternate CD is not likely to be able to recognize your phone, so you will need an Ethernet cable connected to your router in order to do the installation.

---

### Post by plucky on 2012-02-28
> **LinuxFan999 said:**
> The alternate CD requires an internet connection, just like the live CD and the mini CD, so you cannot install Ubuntu without an internet connection. The alternate CD is not likely to be able to recognize your phone, so you will need an Ethernet cable connected to your router in order to do the installation.

No they don't.

If you select the wired connection it will try to connect and when it fails it will take you to a menu where you can select "do not configure network at this time" and the install will continue without a network connection.

It doesn't give you this option if you select the Wireless Network Interface.

Good Luck

---

### Post by Mark Phelps on 2012-02-29
It's not so much that a Beta will "crash everything" -- that's more likely to happen with Alpha versions.  But, a Beta is still pre-release and is likely to crash "something".

Add that to the full-disk encryption your proposing to do ... and this is a recipe for disaster.

Which would not be so bad if:
1) You had readily available Internet access to troubleshoot problems
2) You had readily available Internet access to download upgrades and/or patches to fix the problems.

But given your situation, why take the risks?

---

### Post by nutpants on 2012-03-02
What life with out a little risk.
Anyway I installed and grub installed to the /boot partition and not the MBR so I'm trying to get info to boot it.
Windows still works fine but my net is only from my phone...

---

