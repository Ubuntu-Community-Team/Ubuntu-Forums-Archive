---
title: "installing 14.04 over 14.10"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by jgw on 2015-07-24
I was having a different problem and one of the responses, from Bucky Ball (moderator) was:
"        The update would have been unsuccessful as 14.10 reached end-of-life yesterday and the repositories possibly no longer exist. That's why your updater is doing nothing. All over for 14.10, move on, nothing to see here. There will be no further updates or upgrades.

        I suggest you boot from Live media, backup valuable data and install a supported release, 14.04 LTS supported until 2019 or 15.04, supported until January 2016. You can also upgrade via the net but if you have a broken system, not a good idea. If you do go that way switch off all manually installed PPAs prior to the release upgrade. "

I have tried 15.04 and had problems so I thought I would wait that one out.  So, one of the suggestions above was to install 14.04 over my 14.10 via live media (dvd).  If I remember correctly I can, in theory, just install it over the top whilst leaving my data.  Backing up is always good but, I wonder, would one just backup the home directory, or other stuff?  In other words, I would appreciate thoughts on what I should be backing up.  My concern is that I might backup something that, when restored, would screwup the newly installed 14.04

I also have problems on this system.  One is that its currently trying to open a drive that no longer exists when it boots up.  I have tried to get rid of all instances that refer to that drive but seem to have failed.  My thought is that if I reinstall that should take care of that problem.  

I should also, I guess, mention that when I updated, from 14.04 to 14.10 that I thought that was simply an update to v14 and was not aware that each iteration is to itself and was an actual upgrade rather than an update.  This has me a bit confused.  It seems that an earlier version is supported long time and a later update is not.  Just mentioning a confusion that may be of some interest.  

I have another machine that I did put 15.04 on.  Then I thought I would upgrade another to 15.04 and that was a mistake.  I had an nvidia display on the second one and that did not dance well with 15.04

Thank you...........

---

### Post by grahammechanical on 2015-07-24
Just to clear up on small point.

At present we get a new release of Ubuntu every six months. They come out towards the end of April and the End of October. Every two years the April release is termed LTS (Long Term Support) and is supported for 5 years. The interim releases are only supported for 9 months.

We have two LTS releases that are still being supported - 12.04 and 14.04. The next LTS will be Ubuntu 16.04. Of the interim releases it is only 15.04 that is presently supported (January 2016) as 14.10 reached end of life this week and any release earlier than that which is not LTS has also reached end of life.

When a release reaches end of life its software repositories are closed and archived. There will be no more updates to it and it will be difficult to install software and to upgrade to the next release in line.

So, unless we are prepared to upgrade to each release within a couple of months of its release it is recommended that we install the newest LTS release.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Regards

---

### Post by TheFu on 2015-07-24
What should you back up?  That depends.  If you only used the system as an end-user would, then just the data from your HOME.  Be careful backing up the settings - those are usually not "forward compatible" - take you risks if you do.

OTOH, if you've placed any data outside the HOME, perhaps you ran a web server or a DB or a TV tuner, then you'd want to backup that data as well.  See - it just depends.

Disks are usually mounted through the /etc/fstab. If there is a reference to a drive that is not available inside the fstab, that would cause an error - there are options to make it ignore missing disks. Just review the manpage for that information.

If you do go back to 14.04, know that you'll have to wait for 16.04 to upgrade ... or you'll have to install 14.10, 15.04, 15.10 and 16.04 to get there.  I only load LTS releases.

If you do go backwards, you need to format the main OS partition.  An overlay would be a really bad idea.

---

### Post by jgw on 2015-07-24
Thank you for the replies!

grahammechanical: Thanks for the explanation.  I should have know that!

TheFu:  
The machine in question is the one I have hooked up to my tv and contains downloads, etc.  I use KODI for this stuff and was a bit concerned that I might lose that program.  I also use sickbeard and couchpotato which are a bit more difficult to reinstall (lotsa settings) but I think all the stuff for those two are in the home directory.    KODI is an easy one to reinstall so not too concerned about it.  Yep, I think everything is in my home folder - hopefully.

Thanks again - I will attack it tomorrow.

---

### Post by jgw on 2015-07-30
I have decided to setup a new drive, install a new 14.04 and all the rest and then replace my existing.  As far as I can tell there is little difference between doing a complete replace and reinstalling on an existing.  I suspect nobody really thought somebody would do what I did and, now, I get to pay.

Thanks again for all the help - I will mark this done.

---

