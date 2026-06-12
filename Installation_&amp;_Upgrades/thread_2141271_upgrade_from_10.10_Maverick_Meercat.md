---
title: "upgrade from 10.10 Maverick Meercat"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by pjclinch on 2013-05-02
A colleague has asked about upgrading a workstation which has been complaining it's out of date.  I think it should be done but my Linux experience is mainly in SuSE so I'd like a more ubuntu-centric opinion than I can provide myself on the best way to go about it.  Having a gander it is running 10.10 Maverick Meerkat and suggesting it wants to be 11.04 Natty Narwhal, but some further investigation suggests that's not exactly cutting edge either and is about to go out of support itself.

Experience with other Linux distributions (Fedora and SuSE) suggests that the more jumps one makes in an upgrade the more it's likely to go Horribly Wrong, so I'm asking for advice from those more familiar with Ubuntu about the best way to proceed.

Obviously I will start with a comprehensive backup...

Does The Panel Think That?

 - trying to upgrade is doomed to fail, do a fresh install and save time attempting salvage
 - just use do-release-upgrade, it'll go like clockwork
 - do-release-upgrade -p, see how it goes, there shouldn't be too much fallout
 - several incremental installs through different versions
 - some other option

The machine dual boots with Windows, with Win on a separate 500 Gb partition, and there are 2 separate 1 Tb drives with ntfs file systems accessed for data from either OS.  The Linux install is on another 500 Gb partition that looks like it's all in a single blob (e.g., no separate /home etc.).  The Linux partition reports 227 Gb free.  It's used as a compute engine from the console by a single user at a time and doesn't interface with other machines beyond basic network access (usually just for internet).  

Comments welcome!

Thanks, Pete.

---

### Post by TheFu on 2013-05-02
Which OS do you plan to run?  I'd strongly suggest running 12.04, an LTS release.  It seems this user prefers long support cycles and 12.04 will be supported/patched until Apr 2017.  All the other releases will have 9-14 month support cycles.  I would NOT recommend any of the newer releases for 95% of end-users.  12.10 and 13.04 are NOT LTS releases, so only people that have specific feature needs from those releases should consider them. **Newer** is not always **better**, after all.

So, first, I'd run the LiveCD of the target release to ensure it "likes" his hardware. Don't install it until the major items like networking, GPU, monitor, audio are all proven to work.

To upgrade or do a fresh install?  That is a tough question.  With Ubuntu, non-LTS releases only update to the next release, so you'd need to do 2 updates from 11.04 to 11.10 to 12.04 at a minimum.  With 12.04, the way that networking is configured changed.  /etc/resolv.conf isn't used directly anymore. I think your preferred distros did that change too.

If there isn't much customization, I'd recommend a fresh install.  If there is lots of local changes, I suppose that I'd risk the release-upgrade churn.  Only you can answer that.  If you do the release-upgrade process, be 100% patched before you try to do it. Run
```
* sudo apt-get update
* sudo apt-get dist-upgrade

```a few times to be certain you are on the latest libraries and kernel for each major release.  Yes - "**dist-upgrade**" is the correct command. It will update within the same major release ... 11.10.1 to 11.10.2 .... you get the idea.  It does NOT do the 11.10 to 12.04 updates.

The more I think about this, the more I'd try the do-release-upgrade processes and if anything fails, I'd fall back to the wipe and fresh install method.

Good luck!

---

### Post by grahammechanical on 2013-05-02
If you are going to upgrade from one Ubuntu version to the next I would use the Update Manager (or whatever it is called in Ubuntu 10.10) it is already giving you an invitation to upgrade to 11.04. Just accept the invitation and the next time it is run (perhaps after a reboot) it will invite you to upgrade again to 11.10. After that upgrade you will be invited to upgrade to 12.04.

Reduce the desktop to a default desktop as much as you can. Non standard themes and wallpapers can cause problems. If enhanced effects are in place (Appearance utility, I think, in those days) put it back to standard. And yes, the more jumps the greater the risk. Remember, the upgrade process is designed to upgrade from one default install to another. The developers cannot take into account every modification that a user does to the system and Linux lets us modify everything.

I would not use dist-upgrade. According to this documentation it does not upgrade one distribution release to the next. It is another form of apt-get upgrade. It will upgrade packages on that distribution and it may remove existing packages and so break the system. It was the intention from the beginning that Ubuntu be for ordinary people. I am one of those. I find it simpler to use the utilities provided by Ubuntu. 

[COLOR=#333333][FONT=Ubuntu][https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)[/FONT][/COLOR]

This page has official advice on upgrading. Especially from End Of Life version of Ubuntu.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

> [COLOR=#333333][FONT=Ubuntu]"apt-get dist-upgrade" does not perform distribution upgrade[/FONT][/COLOR]

By the way, what does do-release -p do? Are you confusing p with d? Do not run do-release -d. We use that when we want to convert the latest Ubuntu to the development version of the next release of Ubuntu. What does the -p switch do?

> [COLOR=#333333][FONT=Ubuntu]It is also possible to use [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*do-release-upgrade*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] to upgrade to a development version of Ubuntu. To accomplish this use the [/FONT][/COLOR][COLOR=#333333][FONT=inherit]*-d*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] switch:[/FONT][/COLOR]

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html#do-release-upgrade](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html#do-release-upgrade)

Regards.

---

### Post by pjclinch on 2013-05-02
Thanks for the input folks.


 **-p**, **--proposed**               Try upgrading to the latest  release  using  the  upgrader  from               Ubuntu-proposed


sounded like it might be the right thing.  Maybe not!

I'll get back to the owner and chew over strategies, though I think from what's been said we'll probably be aiming at 12.04.  Shame /home isn't on its own somewhere, that would make a decision to start from scratch a bit easier... ho hum.

Any further comment welcome, and much appreciated.

Ta, Pete.

---

### Post by TheFu on 2013-05-02
>  I would not use dist-upgrade. According to this documentation it does not upgrade one distribution release to the next. It is another form of apt-get upgrade. 

**dist-upgrade** will upgrade kernel versions within the same release. This is often important.  Plain "upgrade" will only patch the same kernel for security reasons.  I've never had a package removed by dist-upgrade for being out-of-date.  That definitely does happen with updates between different major ubuntu releases.  I have been burned by that, but it cannot be helped.

To update (I have a hard time calling new Ubuntu releases an "upgrade") from major release to major release, definitely use do-release-upgrade, but we really need to be certain that the current system is fully patched first. If not, unknown and strange things can happen.

---

### Post by TheFu on 2013-05-02
oops. double post for some reason.

---

### Post by TheFu on 2013-05-02
> **pjclinch said:**
> Shame /home isn't on its own somewhere, that would make a decision to start from scratch a bit easier... ho hum.

Have you considered moving /home to a separate partition first? Pure Linux commands, so that would be easy for you.

---

### Post by gordintoronto on 2013-05-02
DO NOT UPGRADE! Backup /home to an external drive. Back it up to the other internal drive. Back it up to Dropbox or some other service. Back it up to a flash drive. Make sure there are at least two full backups.

Then install Ubuntu 12.04, Xubuntu 12.04 or Linux Mint 13. As previously suggested, try them from a LiveCD or LiveUSB first. Make separate root and home partitions during the install. Restore home. Install other packages. 

10.10 expired more than a year ago.

---

