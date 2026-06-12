---
title: "do-release-upgrade: No new release found. Upgrading 16.04 to 18.04.1"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by eduardo74 on 2018-08-02
Hello im trying to upgrade from 16.04.5 to 18.04.1 and i meet this:

eduardo@MiPcLinux:~$ sudo do-release-upgrade
[sudo] password for eduardo: 
Comprobar si hay una nueva versión de Ubuntu
No new release found.

In Ubuntu wiki says that in a few days from 18.04.1 release it would work. Its been almost a week since release and i dont know if its a bug or ubuntu is working on it...

Thanks in advance

---

### Post by jonbjoseph on 2018-08-02
I also encountered the same problem when trying to upgrade from Ubuntu 16.04.5 to 18.04.1,  when running do-release-upgrade.  I don't have any useful information at this point.

Jonathan

---

### Post by monkeybrain20122 on 2018-08-02
Forget about "upgrade" and stop puzzling why it doesn't work or why it breaks after it appears to work etc. Just back up your data and do a fresh install, much faster and safer. If you did that  you would have 18.04 up and running long before I replied to this thread (43 minutes since the previous post and 7 hours after OP) :)

---

### Post by symbiosix on 2018-08-02
I'm also encountering this problem. I originally installed 14.04 and upgraded it to 16.04 two years ago.

---

### Post by wjbmd48 on 2018-08-02
Well, yes, it just might be easier to do a fresh install. But if you're using the system for multiple native linux apps as well as running them under WINE, and customizing a lot of scripts, that's several hours of work.

Is the problem just that the new upgrade is not yet available? If so, it's worth waiting for.

Also, I've heard that doing the upgrade is not recommended with an encrypted LVM. Is this true?  (And if it is, then I'll happily do the fresh install. But would be nice to avoid, if possible.)

Thanks!  You guys are the best.

Bill

---

### Post by monkeybrain20122 on 2018-08-02
> **wjbmd48 said:**
> Well, yes, it just might be easier to do a fresh install. But if you're using the system for multiple native linux apps as well as running them under WINE, and customizing a lot of scripts, that's several hours of work.


Well if you customize a lot it is more the reason to do a fresh install because the further your system deviates from factory condition the more likely that upgrade will fail. Upgrade works best when you have a pristine system,--where there are least reasons to upgrade instead of doing a clean install. You are advised to restore the system to its standard configuration (i.e reversing all your customizations, removing all proprietary drivers, purge all ppas,--not just disabling but restoring packages to their default versions by downgrading,--etc) before you do the upgrade. That ALONE would take you longer than doing a clean install.

So "upgrade" is neither here nor there and just contributes to a lot of hard to diagnose problems. A large number of threads here are upgrade related every time there is a new release. I customize a lot too, so here is what I do. When a new release comes I install it in an external hard drive and take a few months to test and customize it to make sure everything works, then I just make a clone and restore to my internal hard drive.

---

### Post by Impavidus on 2018-08-03
For me, upgrades tend to work. Click the button, read a book, reboot and ready. And I'm sure that the upgrade will be offered soon (provided you have enabled upgrades to LTS releases). If you're in a hurry to get away from 16.04 and onto something more modern, you could have upgraded to the interim releases almost 2 years ago.

---

### Post by wjbmd48 on 2018-08-03
Thanks! Of course, hard to know what you're missing, if anything, with the upgrade. I have several systems, so I can try it with a less critical one I can afford to "lose."

---

### Post by deadflowr on 2018-08-03
Try switching from upgrade to lts to upgrade to any new version in software and updates > updates.
(or change the setting from Prompt=lts to Prompt=normal in /etc/update-manager/release-upgrades, if running non-gui)

My reasoning is there are no supported releases in between the two lts releases, so it might treat the new lts as the next normal release.

---

### Post by wjbmd48 on 2018-08-03
Whoaa, that worked, thanks! I've started with a nonessential, but heavily modified system. We'll see if it crashes it ;-)

Bill

---

### Post by wjbmd48 on 2018-08-03
Well, it did upgrade, but the monitor is a tad fouled up and even libreoffice doesn't open. OK, a cheap lesson with a non-critical system, from now on I'll simply do fresh installs when I need to upgrade.

Thanks all!

Bill

---

### Post by wjbmd48 on 2018-08-03
It worked, but monitor is fouled up and even libreoffice doesn't open. So, cheap lesson with a non-critical system, if I need to upgrade, do a fresh install.

Thanks all!

Bill

---

### Post by Autodave on 2018-08-03
Been using Ubuntu/Xubuntu for over 10 years now.  I used to do all the upgrades even between the LTS ones. Rarely did I have one work with no problems.  I learned about 8 years ago that it is much easier and quicker to just back up everything and do a clean install.

---

### Post by kurt18947 on 2018-08-03
> **wjbmd48 said:**
> It worked, but monitor is fouled up and even libreoffice doesn't open. So, cheap lesson with a non-critical system, if I need to upgrade, do a fresh install.

Thanks all!

Bill

Others more knowledgeable than me will say if this is a bad idea. I think if you have a separate /home partition, you could format and re-install the / partition and tell it where to find the /home partition. This is done in case of a corrupted install, one can re-install the O.S. and apps without losing data & settings. I assume it would work for an upgrade as well but perhaps there'd be issues with package version conflicts, dunno.

---

### Post by Tadaen_Sylvermane on 2018-08-04
I won't consider myself more knowledgeable however I find a dedicated /home dangerous as sometimes you get fouled up conflicts with config files in /home. I've only found this problem when trying to share a /home with multiple DE's however. I personally have a data partition and I just symlink the required folders from there into my /home/"$USER"/. Gives me a clean /home on all installs.

---

### Post by Paddy Landau on 2018-08-07
Does this [question and answer]("https://askubuntu.com/q/1059924/2088") help?

---

### Post by eduardo74 on 2018-08-09
Still happening, should i report as a bug ? More than a week since release of 16.04.5 and 10 days from 18.04.1

I assume that it wont guarantee a perfect upgrade process, but i prefer to upgrade in a tested official way...

Thanks

---

### Post by eduardo74 on 2018-08-09
Well not much i want that do-release-upgrade as official way to upgrade will work as tested as possible. As said in a post perhaps is a bug... Thanks

---

### Post by kansasnoob on 2018-08-09
There actually is a reason:

[https://lists.ubuntu.com/archives/ub...st/004556.html](https://lists.ubuntu.com/archives/ub...st/004556.html)

I hope those choosing to change release notifications to "any new release" remember to change it back to LTS only after the upgrade so they don't end up on 18.10 unintentionally in a couple of months :eek:

---

### Post by ph13rwun on 2018-08-09
That URL was truncated.  Could you please try again?

---

### Post by Bashing-om on 2018-08-09
ph13rwun; Hey -

Though not "official" - here 
[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue539#How_to_upgrade_from_Ubuntu_Linux_16.04_to_18.04](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue539#How_to_upgrade_from_Ubuntu_Linux_16.04_to_18.04)
are the instructions for an alternate means.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by deadflowr on 2018-08-09
[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html]("https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html")
Untruncated link.
Looks like it was copied from [the other thread]("https://ubuntuforums.org/showthread.php?t=2397260&p=13790715#post13790715"), so it cut out the middle (as the forum software does)

---

### Post by Bashing-om on 2018-08-10
Expect the upgrade path to open up next week - sometime:
[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html)

[INDENT][INDENT]patience :)
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2018-08-10
> **deadflowr said:**
> [https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html]("https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html")
Untruncated link.
Looks like it was copied from [the other thread]("https://ubuntuforums.org/showthread.php?t=2397260&p=13790715#post13790715"), so it cut out the middle (as the forum software does)

Oops, thank you.

---

### Post by dfumagalli on 2018-08-14
> **Bashing-om said:**
> Expect the upgrade path to open up next week - sometime:
[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html)
[INDENT][INDENT]patience :)
[/INDENT]
[/INDENT]


As of now, the upgrade path is officially available. No need to add "-d" or other tricks any more.

I am upgrading to 18.04.01 right now.

---

### Post by Bashing-om on 2018-08-14
dfumagalli; Outstanding !

Glad you shared :)

[INDENT][INDENT]together we do
[/INDENT][/INDENT]

---

