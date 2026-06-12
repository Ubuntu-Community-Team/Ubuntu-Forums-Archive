---
title: "Why don't do-release-upgrade / update manager have 14.04 yet?"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by 5-daqid-9 on 2014-04-17
I am on 12.04 LTS and keep trying to check for 14.04, but no joy. Since the thing's been live for over an hour now shouldn't it be up there?

---

### Post by Ismo_Aro on 2014-04-17
I'm hitting my head to the same wall. Two machines another one 12.04 and another 13.10.

---

### Post by buzzingrobot on 2014-04-17
Believe the smallest interval the Update Manager can be set to check for updates is daily. So, for example, if it checked one hour before the release, it may take 23 hours before it knows the upgrade is available. It can also be set to alert users to available updates at different intervals, although I don't know if that affects notificiation of an available release upgrade.

You might try "sudo apt-get update" in a terminal to see if that triggers Update Manager.

---

### Post by 5-daqid-9 on 2014-04-17
You can refresh the apt cache manually on it by clicking "check" but no worky.

---

### Post by josh_g2 on 2014-04-17
Try sudo update-manager -d

---

### Post by 5-daqid-9 on 2014-04-17
> **josh_g2 said:**
> Try sudo update-manager -d

This gives me an upgrade path - but for the development version of 14.04.

---

### Post by deadflowr on 2014-04-17
> **josh_g2 said:**
> Try sudo update-manager -d

Just
```
update-manager -d
```
should suffice.
You'll get authentication like normal, anyway.

To the why it's not up yet, could be because this release, I think, is going to have all the other past releases, pointing(since 12.04) to it, so they might be needing to tweak that. I guess, though.

The reason for that is because 12.10, which normally would upgrade to 13.04, would now be updated to a dead release. So the thinking is to have it(12.10) point directly to 14.04.
Don't know if that make sense, or helps.
Or if it is the actual problem
Speculation at it's best.

Anyway, I would recommend ignoring it today.(And maybe ignore it for the next week or so)
Having experienced release day upgrades, it will be slow, and you might end up with a junked up system.

---

### Post by 5-daqid-9 on 2014-04-17
The major reason for me wanting to install asap is this is a four day weekend so if (when) something goes wrong I have time to sort it before work

Did I mention this is a dual booting laptop with a synaptics touchpad and windows 8.1... :D

---

### Post by Old_Grey_Wolf on 2014-04-17
Edit: see the warning I added to this thread below [http://ubuntuforums.org/showthread.php?t=2217501&p=12992592&viewfull=1#post12992592](http://ubuntuforums.org/showthread.php?t=2217501&p=12992592&viewfull=1#post12992592)

Normally the LTS to LTS upgrade is not offered until the first point release. For 14.04 that is 14.04.01 on 24 July. You can force it with the command ```
do-release-upgrade -d
```

Edit: as my signatures says, do a backup first.

---

### Post by deadflowr on 2014-04-17
Why not grab a fresh copy via torrent, while you're waiting.

[Looky here for torrents and other alternates]("http://www.ubuntu.com/download/alternative-downloads")

Make sure to know which arch you have, 32bit or 64-bit.

Might be helpful if things go really sour.

Hopefully you have backups of what you want.

---

### Post by 5-daqid-9 on 2014-04-17
> **Old_Grey_Wolf said:**
> Normally the LTS to LTS upgrade is not offered until the first point release. For 14.04 that is 14.04.01 on 24 July.

That makes sense, I wasn't aware of that. Maybe this should be mentioned on the upgrade wiki page?

I'm off to upgrade now, if you don't hear back from me, don't cry for me, I'm already dead ;)

---

### Post by Old_Grey_Wolf on 2014-04-17
> **5-daqid-9 said:**
> That makes sense, I wasn't aware of that. Maybe this should be mentioned on the upgrade wiki page?

You may want to post that suggestion in the "Community Wiki Discussions" forum. :)
I am sure an admin will move it if that is not appropriate.

---

### Post by slickymaster on 2014-04-17
> **5-daqid-9 said:**
> I am on 12.04 LTS and keep trying to check for 14.04, but no joy. Since the thing's been live for over an hour now shouldn't it be up there?

Please keep in mind that Ubuntu servers are very loaded right now.
do-release-upgrade will be enabled soon, but Ubuntu is being hammered, so they're trying to not make it worse. They haven't flipped the switch for upgrades yet, everything is really bogged down.

---

### Post by 5-daqid-9 on 2014-04-18
Thanks everything went relatively smoothly, only a few errors (which I won't bore you with).

---

### Post by Old_Grey_Wolf on 2014-04-18
Warning for anyone else that finds this thread about  upgrading from 12.04 to 14.04. After development of 14.10 starts, do no run the command ```
do-release-upgrade -d
```
I only gave it as a suggesting for use by the OP. I haven't seen a schedule for the 14.10 development cycle so I can't give a date for when this command will cause someone a problem.

---

### Post by mekon2 on 2014-04-18
The download page is now offering 14.04
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

So I am hoping my 12.04 LTS will prompt me to upgrade soon.

---

### Post by Old_Grey_Wolf on 2014-04-18
> **mekon2 said:**
> The download page is now offering 14.04
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

So I am hoping my 12.04 LTS will prompt me to upgrade soon.

Normally the LTS to LTS upgrade is not offered until the first point release. For 14.04 that is 14.04.1 on 24 July. 

If you look at the [14.04 release schedule]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule"), you will see 14.04.1 with no explanation as to why it is listed.

---

### Post by w0lrah on 2014-04-18
> **Old_Grey_Wolf said:**
> Edit: see the warning I added to this thread below [http://ubuntuforums.org/showthread.php?t=2217501&p=12992592&viewfull=1#post12992592](http://ubuntuforums.org/showthread.php?t=2217501&p=12992592&viewfull=1#post12992592)

Normally the LTS to LTS upgrade is not offered until the first point release. For 14.04 that is 14.04.01 on 24 July. You can force it with the command ```
do-release-upgrade -d
```

Edit: as my signatures says, do a backup first.


At least for me, this doesn't work.  No matter what I try, any of the upgrade commands keep trying to go to 12.10 instead of 14.04.

Is the old Debian way of changing the release in sources.list, hitting dist-upgrade, and hoping for the best worth trying?

---

### Post by plucky on 2014-04-19
> At least for me, this doesn't work. No matter what I try, any of the upgrade commands keep trying to go to 12.10 instead of 14.04.

It could be that you have "Normal Releases" selected in your **Software Sources** instead of "Long Term Releases" in the Update tab.

Good Luck

p.s. 12.04 won't offer the upgrade until 14.04.1 is released in July.

---

### Post by Mark_in_Hollywood on 2014-04-19
> **deadflowr said:**
> Why not grab a fresh copy via torrent, while you're waiting.

[Looky here for torrents and other alternates]("http://www.ubuntu.com/download/alternative-downloads")

Make sure to know which arch you have, 32bit or 64-bit.

Might be helpful if things go really sour.

Hopefully you have backups of what you want.

Hey! Wouldn't this overwrite the user's files, folders and objects?

---

### Post by deadflowr on 2014-04-19
> **Mark_in_Hollywood said:**
> Hey! Wouldn't this overwrite the user's files, folders and objects?

Don't know if it still works for 14.04, but you could reinstall keeping your settings in place by choosing the "something else" option during install.
Then you select the mount point, but DO NOT select format.
Then, and this is key, you input the exact info you had before.
(ie, user/username/password, etc)

This of course is moot if you set a separate Home Partition.

As well the method reinstalls the base system, thus removing all the programs and packages you have install.
But when you do reinstall all the extra stuff, you'll have the settings for thus already in place.

But that is a sidenote to me, as I think having a fresh copy is good on it's own.
Regardless if you need it or not.

---

