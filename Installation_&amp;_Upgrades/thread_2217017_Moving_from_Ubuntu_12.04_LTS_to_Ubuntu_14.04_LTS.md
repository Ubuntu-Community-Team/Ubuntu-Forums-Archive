---
title: "Moving from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by mekon2 on 2014-04-15
I am going to upgrade from 12.04 LTS to Ubuntu 14.04 LTS when it is released on April 26th.

I read that the best way to do this is to wipe everything and do the install from scratch. Is this correct and if so then how can I keep some of the settings I made ? Do I need to backup a folder or folders onto a USB stick.

Thanks

---

### Post by kowloon2 on 2014-04-15
You can upgrade directly from 12.04 to 14.04. Done last week and so far no issue and settings remained the same.

---

### Post by mekon2 on 2014-04-15
> **kowloon2 said:**
> You can upgrade directly from 12.04 to 14.04. Done last week and so far no issue and settings remained the same.

Won't that have to be done by upgrading all the way from 12.04 > 12.10 > 13.04 > 13.10 > 14.04 ?

Will you also upgrade to 14.04 LTS later this month ?

---

### Post by coffeecat on 2014-04-15
> **mekon2 said:**
> Won't that have to be done by upgrading all the way from 12.04 > 12.10 > 13.04 > 13.10 > 14.04 ?

You can go directly from one LTS to another. 12.04 to 14.04 without the intermediate upgrade steps is correct.

---

### Post by buzzingrobot on 2014-04-15
LTS-to-LTS upgrade will be supported in the final release. If you have the updater set to notify you when a new LTS release is available, that should happen sometime after the release.

Backing out PPA's and reverting packages they may have replaced to their default status is usually recommended. (You could use ppa-purge.) I'd certainly make backups of anything I wanted to ensure was not lost. A release upgrade is a big deal in the life of a distribution.

Just in case disaster strikes, burning a 14.04 install image to a USB or DVD before you start the in-place upgrade might be a sensible precaution.

---

### Post by grahammechanical on 2014-04-15
I would add, de-activating any proprietary video driver and use the open source (Nouveau) driver instead. See Additional Drivers. 

If you wish to do a fresh install you do not need to wipe everything. The installation process will take care of that.

A lot depends on your setup. Are you dual booting with some other OS? If you installed Ubuntu using the "Use Entire Disk" option then you can simply do the same but that will remove all your data and settings.

Or you can use the "Something Else" option and direct exactly which partition to install Ubuntu into. You will need to set the file system as Ext4 and the mount point of / but if you do not tick the "format" box your data and settings will not be overwritten.

We can even Upgrade from a DVD with Ubuntu 14.04 on it. Open Ubuntu. Put the Ubuntu 14.04 DVD in the optical drive and Ubuntu will detect the DVD an offer to upgrade 12.04 to 14.04 from the DVD.

Upgrading should preserve our data and settings but it is always wise to have backups of stuff we do not want to lose.

Regards.

---

### Post by pfeiffep on 2014-04-15
> **mekon2 said:**
> I am going to upgrade from 12.04 LTS to Ubuntu 14.04 LTS when it is released on April 26th.

I read that the best way to do this is to wipe everything and do the install from scratch. Is this correct and if so then how can I keep some of the settings I made ? Do I need to backup a folder or folders onto a USB stick.

Thanks

There seems to be conflicting information about Trusty's [release date]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule")

---

### Post by mekon2 on 2014-04-17
> **pfeiffep said:**
> There seems to be conflicting information about Trusty's [release date]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule")

It should be available sometime today. It's not on the download page yet though (09:00 GMT)
Not sure where I heard it was the 26th April though.

Press release: [http://insights.ubuntu.com/news/ubuntu-14-04-lts-the-cloud-platform-of-choice/](http://insights.ubuntu.com/news/ubuntu-14-04-lts-the-cloud-platform-of-choice/)

---

### Post by mastablasta on 2014-04-17
> **grahammechanical said:**
> I would add, de-activating any proprietary video driver and use the open source (Nouveau) driver instead. See Additional Drivers. 


13.04 to 13.10 deactivated them automaticly. and reactivated them back when 13.10 was installed (or rather notified me again that proprietary drivers exist) I wonder if 12.04 will deactivate them on upgrade to 14.04?

---

### Post by mekon2 on 2014-04-21
12.04 LTS won't show a prompt to upgrade till July 24th
Shame this wasn't detailed on the main Ubuntu download page and I had to search around to find it. Another Linux frustration :icon_frown:.

[http://fridge.ubuntu.com/2014/04/17/ubuntu-14-04-trusty-tahr-released/](http://fridge.ubuntu.com/2014/04/17/ubuntu-14-04-trusty-tahr-released/)
> [COLOR=#333333][FONT=Lucida Grande]Users of Ubuntu 12.10 and 13.10 will be offered an automatic upgrade to 14.04 LTS via Update Manager shortly. Users of 12.04 LTS will be offered the automatic upgrade when 14.04.1 LTS is released, which is scheduled for July 24th. [/FONT][/COLOR]

---

### Post by Mark Phelps on 2014-04-21
Might want to take this into account:

According to Ubuntu Engineering Foundations team manager Steve Langasek:

Upgrades between LTS releases are not enabled by default until the first point release, 12.04.1/14.04.1, scheduled for July/August. It is recommended that most LTS users wait until then before upgrading to 12.04/14.04.

---

### Post by djchandler on 2014-05-01
> **mekon2 said:**
> 12.04 LTS won't show a prompt to upgrade till July 24th
Shame this wasn't detailed on the main Ubuntu download page and I had to search around to find it. Another Linux frustration :icon_frown:.

[http://fridge.ubuntu.com/2014/04/17/ubuntu-14-04-trusty-tahr-released/](http://fridge.ubuntu.com/2014/04/17/ubuntu-14-04-trusty-tahr-released/)

Thanks for this. I was wondering why I wasn't getting a notice of the 14.04 upgrade on my old laptop with 12.04.

As for frustrating, it's always been that way unless you're willing to pay someone else to do stuff for you. Otherwise, roll up your sleeves and figure it out.

Thanks again.

---

### Post by mekon2 on 2014-05-02
> **djchandler said:**
> Thanks for this. I was wondering why I wasn't getting a notice of the 14.04 upgrade on my old laptop with 12.04.

As for frustrating, it's always been that way unless you're willing to pay someone else to do stuff for you. Otherwise, roll up your sleeves and figure it out.

Thanks again.

I think I was more frustrated at the Ubuntu website and the lack of information about automatic LTS to LTS upgrades than Linux in general.

You also need to know where to look for answers and when you do find them quite a lot of them are different or conflicting.

---

### Post by hockeybum27 on 2014-08-15
buzzingrobot,

I am following your recommendation on the ISO USB.  And from what I've gathered, backing up my Home directory will preserve pretty much everything of import.
Can you please explain what ppa-purge does?
If I've added some PPAs (e.g., virtualbox, LibreOffice, probably some others) - would they be removed, and just the 'default' (for lack of a better term) PPAs be there?
Lastly - what becomes of all the programs installed in /usr/bin/ and such?  Are they removed as part of the upgrade?  For example, I have Virtualbox 4.3 and Libreoffice 4.2, will they be removed (in the case of VB) and/or updated (in the case of LO, which comes with the distro)?

If there is an online resource I should be looking at for these answers, instead of taking up space here in the forum, please let me know; and thanks in advance for any guidance.

---

### Post by buzzingrobot on 2014-08-15
When you add a PPA, the repository that hosts the software is added to the list of servers your system checks for updates. That means when packages at that PPA are updated, the package you installed will be updated during normal system updates. 

PPA-Purge removes the PPA's entry in the list of repositories used by your system *and* it attempts to remove any packages installed from that system and, in effect, roll things back to the moment before the PPA was installed. 

Configuration edits, personalizations, etc., are written to files in a user's home directory.  So, yes, backing up all of your home directory will backup all those files, along with, of course, the other files you've stored there. 

If you're doing a full upgrade, everything on your system for which a new version is available gets upgraded.

---

### Post by hockeybum27 on 2014-08-15
br,

Thanks for the quick reply!  So if I installed software through a PPAthat I added, then ppa-purge would remove the PPA and delete the application?  Is that correct?  If so, I guess I should get a list of PPAs I added (so I can add them back in) - is there a way to do that?

Thanks again so much for your direction on this!

---

### Post by buzzingrobot on 2014-08-15
> **hockeybum27 said:**
> br,

Thanks for the quick reply!  So if I installed software through a PPAthat I added, then ppa-purge would remove the PPA and delete the application?  Is that correct?  

Yes. Note, too, that it *attempts* to remove packages.  If the system has changed enough, or if packages from the PPA are needed as dependencies by other packages, then it may not be able to.  Nothing magic is happening here.  It just queries your system to see what packages are installed from a PPA and tries to remove them.

> If so, I guess I should get a list of PPAs I added (so I can add them back in) - is there a way to do that?

The files that contain the entries are in /etc/apt/sources.list.d. Their names reflect the PPA. (ppa-purge seems strict about getting the PPA's name right.  Worse comes to worse, you can always Google a PPA's page and see the exact name used when you installed it.)

You can also get a list in one of the GUI apps that can list your software sources: Software Center, the updater, etc.

There is a GUI app -- Y PPA Manager -- that I haven't used but it says it does all this more conveniently. A quick Google ought to turn something up.

---

### Post by mushistereck on 2014-08-15
I have both Win 7 64 bit and cannot get 14.04 LTS 64 bit to install with Win 7.

---

### Post by mushistereck on 2014-08-15
Can I do the upgrade from 12.04 LTS 32 bit to 14.04 LTS 64 bit??

---

