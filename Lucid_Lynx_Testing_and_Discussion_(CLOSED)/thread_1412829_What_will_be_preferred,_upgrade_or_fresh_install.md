---
title: "What will be preferred, upgrade or fresh install?"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by OrangeCrate on 2010-02-21
This comment by **jdong** has stuck in my mind for a long time, and it's the guidance I generally give when answering questions regarding upgrading vs a fresh install.

> Actually, **We do NOT advise a clean install** every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!

in post #96, in this thread:

[http://ubuntuforums.org/showthread.php?t=936696&page=10](http://ubuntuforums.org/showthread.php?t=936696&page=10)

We're just about there in Lucid's development, that every other question or so on the forums, will be about this topic. Particularly I suppose, from people who upgraded from Jaunty to Karmic and have ext3 as default. And of course, the 8.04 to 10.04 folks. They all might expect a conversion from ext3 to ext4 on the fly with an upgrade.

Any thoughts on what the "party line" should be, and what advice we should give going forward?

---

### Post by Marlonsm on 2010-02-21
I (and many others) have always advised a clean install. But it's a good idea to keep your home folder in a separate partition, so it will be kept intact even after the install.

---

### Post by VMC on 2010-02-21
Yes, I always do a fresh install. I did read the link and post#96, but I still prefer fresh install.

---

### Post by autocrosser on 2010-02-21
That's what I do also--Nice to have a fresh install to move my home into....That being said--I would guess that most if not all the questions will be on upgrade paths..most people want to push a couple of buttons & forget that the questions were ever asked---that with the oft-mentioned upgrade from 08.04.4 to 10.04 & we may have our hands very full in the next couple of months. I foresee lots of people jumping the gun & b0rking systems---so let's all be ready:(

---

### Post by castrojo on 2010-02-21
> **Marlonsm said:**
> I (and many others) have always advised a clean install. But it's a good idea to keep your home folder in a separate partition, so it will be kept intact even after the install.

You don't really need to have a spare partition per se, when you reinstall over an install you've broken the installer will not overwrite your user data (unless you tell it to format of course).

I personally have a separate drive for /home. I have the same install going back since at least Hardy, the way I "clean up" late in the cycle is usually blowing away ~.gconf (which ends up blowing away all my user settings). That usually clears up any weirdness that might be happening on my desktop.

---

### Post by darkstaar on 2010-02-21
For what it's worth, here's what I recommend if you _do_ have a separate /home partition:

-----

1) Make sure that you have a working bootable version of your current working version of Linux

2) Download and burn the ISO of the version that you wish to upgrade to, and burn it to your preferred bootable media (make sure that there are no defects)

3) In Synaptic Package Manager, save your markings to a file (don't forget to check "Save Full State")

-----

With these things done, you are prepared to do a fresh install if you're forced to.

At this point you can go ahead and try upgrading via the recommended upgrade path knowing that, if something goes wrong during the upgrade (and it happens), you have a couple of different means of recovery.

If you do find that something goes horribly wrong during the upgrade process (did I mention that it happens?), you can always recover by doing a fresh installation of whichever version you wish. Once this is done, you can "Read Markings" in Synaptic from your saved file to automagically reinstall all of your old applications with just a couple of mouse clicks.

I should suggest that, if you do choose the upgrade path, that you don't attempt it on the day of the version's release. The servers are extremely busy on that day and, at best, you might find it to be a very slow process.

I attempted an upgrade of Ubuntu (from 7.04 to 7.10) on upgrade day. Not only was it slow but the upgrade process aborted halfway through (after about 14 hours). Unfortunately, my laptop became unbootable after that (See? It happens.) and I was forced to do a fresh install.

With one exception, I've been doing fresh installations ever since.

Now, here's what I recommend if you _don't_ have a separate /home partition:

-----

1) Huh? What are you thinking?!? Make a separate /home partition and then start over from the beginning of this post.

---

### Post by cariboo on 2010-02-21
I have two systems that have only been upgraded, one an HP laptop that has been upgrade from Intrepid to Karmic, the other an atom powered system, that has been upgraded from Jaunty to Karmic. Both systems rarely get changed after install. On those two systems I only install packages from the repositories, which helps make the upgrade painless.

---

### Post by OrangeCrate on 2010-02-21
> **cariboo907 said:**
> I have two systems that have only been upgraded, one an HP laptop that has been upgrade from Intrepid to Karmic, the other an atom powered system, that has been upgraded from Jaunty to Karmic. Both systems rarely get changed after install. On those two systems I only install packages from the repositories, which helps make the upgrade painless.

That's nice, any comment on my original post in this thread?

---

### Post by darkstaar on 2010-02-21
To address the OP's original post: The upgrade process works nicely...when it does work, and it usually does...apparently. But I've had just a 67% success rate with it so I know first hand that it isn't always flawless.

In addition, I've had more than one occasion where a newer version of a distro simply didn't work and I've been forced to revert to the older, working version (Ubuntu 8.10 was one example for me).

My point is, be prepared to do a clean installation. It may become necessary.

> **whiprush said:**
> You don't really need to have a spare partition per se, when you reinstall over an install you've broken the installer will not overwrite your user data (unless you tell it to format of course).

True, but I recall the documentation for RedHat 6.0 (my first non-Slackware Linux distro), circa 1999, which strongly recommended separate partitions for many system directories in addition to /home and /boot. I never did quite figure out why I should have a partition for /var, another one for /etc, and so on, but I could clearly understand why a separate /home partition was important. Throughout my many years of running RH, S.U.S.E., Mandrake, and Ubuntu, I've always maintained a separate /home partition or drive. I even practiced this with Windows back in my dual-booting days. It just makes things so much easier and safer.

So, unless a user has a very small hard drive and can't afford to lose a gigabyte or two to slack space, I strongly recommend a separate /home partition.

---

### Post by ikt on 2010-02-22
I upgrade and if there's any weirdness then clean install.

---

### Post by cariboo on 2010-02-22
@OrangeCrate

There really is no party line, All the releases have had instruction on the main page on how to do a proper upgrade, I've found that most users don't even check out the release notes, let alone instructions on how to upgrade. Starting with Karmic the upgrade manager disables all ppa's, so that is a big plus as far as I'm concerned, and should make upgrades a lot more doable for the average user.

---

### Post by ranch hand on 2010-02-22
My main "business" OS is 8.04.  I will be doing a clean install for the simple reason that I want ext4 and grub (not grub-legacy)

I will do a clean install and transfer the files I want to keep.

On upgrades, if you watch, there are a bunch of old files that can't, for one reason or another, be removed if no longer needed.  Why keep the crap?

We are talking about a LTS here.  If you are planning, like me, on keeping it for your most secure OS then it seems to me that it needs a clean install.

I have no problem with upgrades, my best behaved Lizard (10.04 is Lounge Lizard isn't it?) was upgraded to the tool chain from 9.10.  My favorite is a 9.04>910>10.04 upgrade.

My new "business" OS will be as clean as I can make it.

---

### Post by 23meg on 2010-02-22
jdong is right: there's no reason to recommend a clean install over an upgrade, *in the case of a reasonably well-maintained system, whose configuration isn't prone to possible known upgrade showstoppers*. To expand on that catch, there are some points to remember which you should actively remind people of when the question of "Upgrade vs. clean install" comes up:

[list] [*] Many users still think of "modify sources.list and issue *sudo apt-get dist-upgrade*" when it comes to upgrades, which is an unsupported method. Advise people to use Update Manager, or "*do-release-upgrade*" when upgrading.


[*] Advise people to **read the release notes**, and check if there are known problems with upgrades, or in general, that apply to their systems.


[*] If the system is messed up with unsupportable replacements to key components, casual use of package installation scripts and the like, it's more likely for an upgrade to fail (though Update Manager has improved things in that regard). It may be a good idea to recommend a clean install to a user who has such a system.[/list]
The notion that upgrades are inherently problematic is a carryover from the Warty-Feisty era (approximately), where the use of package installation scripts that made upgrades problematic was widespread, and the upgrade tools didn't do a very good job at coping with such problems. The situation has changed a lot today: people use PPAs maintained by trusted community members for the most part, which usually have good packaging, installation scripts are less common, and the cases for the most common customizations (adding restricted codecs, Flash etc.) are covered by Ubuntu itself securely, and the upgrade paths are tested much more extensively, so the advice should change accordingly.

---

### Post by Merk42 on 2010-02-22
I do a fresh install because on release day downloading the iso via torrent is quicker than update manager when the servers are hammered :P

---

### Post by 23meg on 2010-02-22
A reminder: this thread isn't about which of the two methods you prefer, but about which of the two methods should be recommended, and how and why.

---

### Post by ranch hand on 2010-02-22
Until there is the a way to format to ext4 on the fly there is no reason to upgrade.

I have one install of 10.04 on ext3.  It does not run as well as ones on ext4 (this is 64bit - 32 may be different).  There is more lag in apps opening, and it seems (just seems) more fragile.

I do need to make sure that things are fully open on one workstation before going to another.

Firefox will slow thing on it to a crawl with 6 or more tabs open.

Now I will admit that performance may well improve as teh OS matures but, except for testing fun, I do not want an ext3 installation and that is what you will have with an upgrade.

---

### Post by OrangeCrate on 2010-02-22
> **23meg said:**
> A reminder: this thread isn't about which of the two methods you prefer, but about which of the two methods should be recommended, and how and why.

Thanks, the drive by post count chasers get in the way sometimes to what's really being discussed.

Personally, I've always been of the school, to upgrade rather than do a new install, and to do a new install only when all else fails.

This time however, the upgrade path will ignore both grub2 and ext4, so I for one will suggest to backup, and do a fresh install. Or, at least know what you'll get in the finished product, if you go the easier route and upgrade.

Once a user is on Grub2 and ext4, IMO, the upgrade path then continues to be the preferred install method per jdong, you, and others. When I have the opportunity to respond in the forums, this will be the advice I will give (along with a link to this thread for reference).

---

### Post by zika on 2010-02-22
> **OrangeCrate said:**
> Thanks, the drive by post count chasers get in the way sometimes to what's really being discussed.

Personally, I've always been of the school, to upgrade rather than do a new install, and to do a new install only when all else fails.

This time however, the upgrade path will ignore both grub2 and ext4, so I for one will suggest to backup, and do a fresh install. Or, at least know what you'll get in the finished product, if you go the easier route and upgrade.

Once a user is on Grub2 and ext4, IMO, the upgrade path then continues to be the preferred install method per jdong and others. When I have the opportunity to respond in the forums, this will be the advice I will give (along with a link to this thread for reference).Risking that I'll be counted as a post chaser, which I'm not, I agree with all said. I stll have enough fingers on my hand(s) to count all the {re,clean}installs I did after I embarked on Ubuntu ship, with GG... Even though, I must admit, I'm always, since JJ, on development release... It is, somewhat, easier, now, when I can do reinstall with keeping my /home (almost) intact, not having it as a separate partition. I tried that, a month ago, with LL and it is a nice experience...

Update: Just to clear one point. I prefer upgrade, but in case of switching from ext3 to ext4 clean install is preferred option... I did switch on-the-fly but was eagerly waiting for a moment that clean re-install was needed so that I have clean ext4 newly re-formated partition for Ubuntu... I've edited this post in order not to be accused of being post count chaser ...

---

### Post by jppr on 2010-02-22
I do a fresh install almost every week, last yesterday.

---

### Post by philinux on 2010-02-22
I prefer a clean install. I have home on its own partition, formatted ext4. I had to do a backup and restore to get ext4 as people will know.

Personally I've had the worst experience with upgrades. I dont use ppa's or have a modified system either.

Therefore I would recommend a clean install. This is a personal choice only.

---

### Post by Merk42 on 2010-02-22
> **OrangeCrate said:**
> Thanks, the drive by post count chasers get in the way sometimes to what's really being discussed.

Yea okay I only posted because I wanted to increase my count :roll:


On topic:
My brother has a Dell Vostro A90 with the lpia "Dellbuntu" 8.04.  Is the upgrade path even possible for him?

---

### Post by ranch hand on 2010-02-22
> **Merk42 said:**
> Yea okay I only posted because I wanted to increase my count :roll:


On topic:
My brother has a Dell Vostro A90 with the lpia "Dellbuntu" 8.04.  Is the upgrade path even possible for him?
I run a Dell that was not preinstalled with Ubuntu but I do belong to the Dell mailing list for those boxes.  

[https://lists.us.dell.com/mailman/listinfo/linux-desktops](https://lists.us.dell.com/mailman/listinfo/linux-desktops)

I would check with the guys on the list before doing anything.

Dell has a repo of their own and the upgrade may work.  It will maybe be a little after the release by Ubuntu.

There has been no chatter about this on the list yet.

---

### Post by wojox on 2010-02-22
I upgraded from 8.10 to 9.04 no problem. I only did a fresh install of 9.10 the take advantage of Grub2 and ext4. I'll more than likely just go back to upgrading on 10.04. ;)

---

### Post by slakkie on 2010-02-22
I prefer [upgrades over clean installs any day](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/). 

However, if you want native ext4 support on your root slice, I would suggest a clean install. That for me is the only reason why one would do a clean install. If you want ext4 on other slices, go with the upgrade.

---

### Post by darkstaar on 2010-02-22
> **OrangeCrate said:**
> Thanks, the drive by post count chasers get in the way sometimes to what's really being discussed.

Just wanted to say that this "drive by post chaser" makes no apologies for achieving a staggering 100 posts in the 26 short months that I've been a member of UF.

---

### Post by OrangeCrate on 2010-02-22
> **darkstaar said:**
> Just wanted to say that this "drive by post chaser" makes no apologies for achieving a staggering 100 posts in the 26 short months that I've been a member of UF.

I'm sure you recognized, that my comment wasn't aimed at anyone in particular, it's just a common problem on forums of all types.

Some people just don't read a thread for content, but either assume the topic, or just don't care, as long as their post count goes up (that's why they're called drive-by posters). If there's a lot of them in a thread, in total, they can end up hijacking a thread away from it's initial subject.

BTW, how many keyboards have you worn out getting to that 100 posts? (Inquiring minds want to know...)

:)

---

### Post by snowpine on 2010-02-22
> **Merk42 said:**
> Yea okay I only posted because I wanted to increase my count :roll:


On topic:
My brother has a Dell Vostro A90 with the lpia "Dellbuntu" 8.04.  Is the upgrade path even possible for him?

Canonical has dropped support for lpia, so your brother will probably not be able to upgrade to 10.04. 

ps to stay on topic, I recommend recommending a fresh reinstall.

---

### Post by biomedtech on 2010-02-23
I pulled the trigger on a fresh install, because Update Manager was slowly choking my netbook to death. With the small partition of an Eee PC, I need all the free space possible, and Lucid Lynx left me with over 1.2GB of my 3.8 volume, something Karmic never came close to. 

 I don't know why I was fighting a losting battle with Update Manager, but so far this fresh install has been worth it.

---

### Post by slakkie on 2010-02-23
> **biomedtech said:**
> I pulled the trigger on a fresh install, because Update Manager was slowly choking my netbook to death. With the small partition of an Eee PC, I need all the free space possible, and Lucid Lynx left me with over 1.2GB of my 3.8 volume, something Karmic never came close to. 


Perhaps run aptitude clean or the apt-get equivalent. Will remove your cache which is huge after an upgrade.

---

### Post by OrangeCrate on 2010-02-23
> **slakkie said:**
> Perhaps run aptitude clean or the apt-get equivalent. Will remove your cache which is huge after an upgrade.

Adding...

**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by ranch hand on 2010-02-23
So, basically what we need to do is do an upgrade which takes longer, leaves us in ext3 with an unsupported version of grub and a bunch of junk files.

Then send time and effort to clean the sucker up and convert the format and install a modern boot loader.  All this, apparently, because this is the macho way to do things.

All this to avoid backing up the files, get the ISO, install, dump the files in.  All on a nice clean system formatted to ext4 and already has a supported version of grub.  Also taking about 70% of the time and not having the inherent risk of changing from ext3 to ext4 with data in place.

I guess I just do not understand the reason for this question.

---

### Post by OrangeCrate on 2010-02-23
> **ranch hand said:**
> My main "business" OS is 8.04.  **I will be doing a clean install** for the simple reason that I want ext4 and grub (not grub-legacy)

**I will do a clean install** and transfer the files I want to keep.

On upgrades, if you watch, there are a bunch of old files that can't, for one reason or another, be removed if no longer needed.  Why keep the crap?

We are talking about a LTS here.  If you are planning, like me, on keeping it for your most secure OS then it seems to me that** it needs a clean install**.

I have no problem with upgrades, my best behaved Lizard (10.04 is Lounge Lizard isn't it?) was upgraded to the tool chain from 9.10.  My favorite is a 9.04>910>10.04 upgrade.

My new "business" OS will be **as clean as I can make it**.

> **ranch hand said:**
> Until there is the a way to format to ext4 on the fly **there is no reason to upgrade**.

I have one install of 10.04 on ext3.  It does not run as well as ones on ext4 (this is 64bit - 32 may be different).  There is more lag in apps opening, and it seems (just seems) more fragile.

I do need to make sure that things are fully open on one workstation before going to another.

Firefox will slow thing on it to a crawl with 6 or more tabs open.

Now I will admit that performance may well improve as teh OS matures but, except for testing fun, **I do not want an ext3 installation and that is what you will have with an upgrade**.

> **ranch hand said:**
> I run a Dell that was not preinstalled with Ubuntu but I do belong to the Dell mailing list for those boxes.  

[https://lists.us.dell.com/mailman/listinfo/linux-desktops](https://lists.us.dell.com/mailman/listinfo/linux-desktops)

I would check with the guys on the list before doing anything.

Dell has a repo of their own and the upgrade may work.  It will maybe be a little after the release by Ubuntu.

There has been no chatter about this on the list yet.

> **ranch hand said:**
> So, basically what we need to do is do **an upgrade which takes longer, leaves us in ext3 with an unsupported version of grub and a bunch of junk files**.

Then send time and effort to clean the sucker up and convert the format and install a modern boot loader.  All this, apparently, because this is the macho way to do things.

**All this to avoid backing up the files, get the ISO, install, dump the files in.  All on a nice clean system formatted to ext4 and already has a supported version of grub.**  Also taking about 70% of the time and not having the inherent risk of changing from ext3 to ext4 with data in place.

**I guess I just do not understand the reason for this question**.

O.K., we get your point, thanks for playing.

:)

---

### Post by OrangeCrate on 2010-02-23
Enough. Marking the thread as solved.

---

### Post by slakkie on 2010-02-23
> **ranch hand said:**
> So, basically what we need to do is do an upgrade which takes longer, leaves us in ext3 with an unsupported version of grub and a bunch of junk files.


You can upgrade grub in Karmic to grub2, same thing on Lucid. Junk files.. A default install creates "junk".

> 
All this to avoid backing up the files, get the ISO, install, dump the files in.  All on a nice clean system formatted to ext4 and already has a supported version of grub.  Also taking about 70% of the time and not having the inherent risk of changing from ext3 to ext4 with data in place.


ext4 on non-root slices do not warrant a reinstall, you can do that any day of the week. And upgrading also requires a backup, just like your reinstall does. 

> 
I guess I just do not understand the reason for this question.

Luckely, I don't follow your reasoning as well :)

---

### Post by VMC on 2010-02-23
> **slakkie said:**
> You can upgrade grub in Karmic to grub2, same thing on Lucid. Junk files.. A default install creates "junk".
 Yes, a new install does leave unneeded files behind.

> **OrangeCrate said:**
> 
**HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Thanks for this link. Its been around almost 4 years! Lots of good information in those 11+ pages.

---

### Post by biomedtech on 2010-02-23
Are those 4 yr old tips still valid with an Alpha release? or with the ext4 file system?

---

### Post by OrangeCrate on 2010-02-23
> **biomedtech said:**
> Are those 4 yr old tips still valid with an Alpha release? or with the ext4 file system?

Absolutely.

---

### Post by nanog on 2010-02-23
**What 23meg said.**

I have had far more problems with fresh installs than upgrades. At least with an upgrade you can revert to the original working kernel and drivers if the new install fails to recognize your NIC or PCI bus. In my experience upgrades typically fail because users have installed dubious debs or binaries.

---

### Post by nanog on 2010-02-23
> All on a nice clean system formatted to ext4 and already has a supported version of grub. 

Recent phoronix bench marks show ext4 performance is now markedly worse than ext3.

---

### Post by MCVenom on 2010-02-23
Post chaser here: So the official party line for those with a ***clean Karmic install*** is that upgrading has no significant disadvantage over a clean install? It hasn't been discussed much and Karmic has ext4 as the default filesystem, as well as the new GRUB.

---

### Post by tekstr1der on 2010-02-23
> **slakkie said:**
> Luckely, I don't follow your reasoning as well :)

Ditto, if you have a functional well-established system, it's easy enough to update grub, create a new ext4 partition or two and move your existing /root & /home over. Did this months ago right after grub2 went into Karmic alpha. My current system began with Intrepid and has made its way through Jaunty, the full Karmic dev cycle and now into Lucid.

It's all matter of fixing whatever you break and cleaning up after yourself.

---

### Post by OrangeCrate on 2010-02-23
> **BlackOtaku said:**
> Post chaser here: **So the official party line for those with a clean Karmic install, is that upgrading has no significant disadvantage over a clean install?** It hasn't been discussed much and Karmic has ext4 as the default filesystem, as well as the new GRUB.

That's correct.

---

