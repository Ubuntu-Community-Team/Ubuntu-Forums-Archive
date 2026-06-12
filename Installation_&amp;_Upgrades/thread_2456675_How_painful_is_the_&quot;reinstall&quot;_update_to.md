---
title: "How painful is the &quot;reinstall&quot; update to 20.04"
date: 2021-01-16
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2021-01-16
Hi all,

I'd like to upgrade to lubuntu 20.04 LTS from 18.05 before 18.05 becomes unsupported.

My preliminary question is whether this can be a painless process.

 I've had lububtu from 16.0X on the computer, and in that time it's kinda become the main family PC. Even my wife uses it, and runs a business from there. Thiugh she'll be ok as she just uses vanilla lxde + chrome.

I on the other hand use i3 gaps as my WM, doom emacs, and have (at least) a nextcloud instance i don't want to lose + a bunch of folders synced with resilio and god know what else I've added over the years.

I'm therefore a little terrified I'll have to (remember and) reinstall all my packages, and do the myriad cut-paste terminal fixes for the seemingly gazillion things that didn't "work" as expected first time (bluetooth things, monitors etc).

If it makes any difference the PC itself is a 9-10yr old box with reasonable spec (9-10yr old i7 + 16gb ram, ssd for the OS).

---

### Post by grahammechanical on 2021-01-16
Can you create space and dual boot between 18.04 and 20.04? Then you at least transfer your data over. And you will still have a working OS. Do you have a separate Data partition?

An upgrade to a heavily modified User Interface can bring some pain with it. You should check that your chosen applications are supported in 20.04. Do you have any PPAs? Are there 20.04 versions of them available? Disable the PPAs before upgrading and then re-install the PPAs and upgrade those applications from the 20.04 versions of the PPAs.

Regards

---

### Post by tea for one on 2021-01-16
> Note, due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. Doing so will result in a broken system. If you are on 18.04 or below and would like to upgrade, please do a fresh install.

The comment above is from the official site [https://lubuntu.me/focal-1-released/](https://lubuntu.me/focal-1-released/)

A fresh installation is essential.

---

### Post by GhX6GZMB on 2021-01-16
Been there, done that.
Painful? Not really, but it'll take you half a day (Lubuntu installation itself 45 min.)
First, backup all your personal stuff. This is pretty easy, it's all in /home.

The hassle is reinstalling all your favourite programs, settings, shortcuts etc., but there's no way around it. You'll need to rebuild it.
Take a tour around your existing system and write down everything that's installed or special.

See it as an opportunity, you might get rid of old ballast and discover new programs along the way.

I really like the LXQt GUI, am running 20.04.1 right now.

Good luck :)

---

### Post by guiverc on 2021-01-16
I'll second @grahammechanical's suggestion of dual boot. 

I'll also second @teaforone's note on Lubuntu's change of desktop (your base system will upgrade, but you'll be left with some LXDE things in your menu system that will just be empty menu items, as the LXDE way of doing this will be gone, replaced by LXQt menu items). Some users experience few issues, others experience more significant issues.. but your machine may not be as neat due to the change in the system (thus why re-install is recommended).

I'll suggest re-install using "*Manual Partitioning*", using existing partitions without format, where your additional packages are noted, system directories erased, new system installed, then additional packages noted earlier will be attempted to re-installed (if available on new system), then it'll ask to reboot  (don't format, as format triggers an all new system).  It's not as neat as a clean install, but it'd be what likely do if it was me.

If your machine is lean on resources, I'd consider choosing newer apps for modern Lubuntu (using LXQt) as using GTK libs will waste RAM.  If you've >4GB though this matters less.  This 2009 dell desktop has 8GB and I'm using a number of old GTK programs I started using in GNOME2 days.  On machines with less RAM though, I tend to use different apps.

Are you planning on sticking with Lubuntu (ie. switching from LXDE to LXQt), or moving away from Lubuntu and remaining with LXDE (18.04 was the last release Lubuntu supports LXDE for). It's not clear from your description if you're fully aware of this decision; as it'll dictate the best route (or what I'd choose).

*FYI:  I did try and keep LXDE & LXQt running on this box awhile, but decided it wasn't worth the effort; I like @ml9104 prefer LXQt*

---

### Post by steve234 on 2021-01-17
@grahammechanical Yep, have a separate 1tb spinner in fact for data. I think I have used near infinite ppas over the years

---

### Post by steve234 on 2021-01-17
Thanks, @ml9104 hopefully it'll be a little easier than I'd worried.

Thst said, I have a new baby, so half a day is a lifetime. I'm always treading a fine line with my family's acceptance of the "linuxy-ness" - like "dad why doesn't X work" followed by an afternoon here and on stackexchange cutting and pasting terminal commands.

I've done so much of the above, hopefully a lot of old ballast will be shed.

I imagine the list of installed / special things may be quite long!

---

### Post by guiverc on 2021-01-17
> **steve234 said:**
> Thanks, @ml9104 hopefully it'll be a little easier than I'd worried.

That said, I have a new baby, so half a day is a lifetime. ...

The suggestion I made with

> I'll suggest re-install using "*Manual Partitioning*", using  existing partitions without format, where ....

is by far the fastest.  Depending on your hardware (which varies a lot), a fresh *hirsute* install on one box takes ~60 seconds (*not including boot & me selecting the options* in the installer) time.   The *upgrade via reinstall* (manual, no format) I was talking about takes only a few minutes longer (it's near the same install, but it has to additionally download the packages you had installed & then install them as well; time varies on how much you had installed).

I've had *release-upgrades* take hours+ (up to 18 hours!), which varies on hardware as well as your bandwidth (download) speed (and for me, when it's run). Re-installs are FAST, and by far the fastest option in my experience.

In case you're interested, the box used for my mentioned timing is
- dell [optiplex] 990 (i7-2600, 16gb, nvidia geforce gt 6600 gt)
it also uses SSD and not *spinning-rust (hard disk)*.

(I do QA-test installs on various boxes; so I'm doing hundred+ installs a year; other boxes aren't quite as fast, but even if a pick an older/slower (2006, c2d-e6320) hp that uses *spinning-rust/*HDD, the install still takes considerably less than 15 minutes, and not the many hours a *release-upgrade* takes me.

---

### Post by TheFu on 2021-01-17
> **steve234 said:**
>  
I imagine the list of installed / special things may be quite long!

No need to write down a list of installed programs.  APT has that. Why not use it?
```
apt-mark showmanual > ~/manually-installed
```
will save the list.  Backup your HOME and do a fresh install. Put your HOME back, then feed that list into apt to install those programs.  Some won't exist anymore.

All this should take 30-45 minutes.
[LIST=1]
[*]15min fresh install
[*]15min restore HOME
[*]15min reinstall old packages
[/LIST]
I assume you do backups nightly, so just add the **apt-mark** command to that effort/script before you backup your HOME.

BTW, I'm just now moving from 16.04 to 18.04 on my servers. 20.04 needs a little more simmer time to me.  Did a release upgrade twice in the last few days. Both had some pain. Both refused to boot when completed and needed some kernel help. I have until April to get them all migrated. Some parts went smoother than expected.  Like a mixed box of chocolates. We never know what we will get.

---

### Post by steve234 on 2021-01-17
Thanks, this is useful

---

### Post by TheFu on 2021-01-17
> **steve234 said:**
> Thanks, this is useful

[LIST]
[*][https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.
[*][https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[/LIST]
Backup
Restore

Another way to get a longer list: sudo apt list --installed

---

### Post by steve234 on 2021-06-27
All done, I'm now the proud owner of a 20.04 lts setup. Just need to work through the various (and myriad) i3-gaps things which have fallen over (my fault for "customising" my OS one weekend years ago and promptly forgetting how everything worked)

I'll mark this as solved.

Thanks again everyone

---

### Post by monkeybrain20122 on 2021-06-27
Well you don't need to dualboot or mess with your existing system in anyway if you have a large enough external hard drive, install 20.04 on it, boot off it and do as much tweaking and testing as you like. When you are happy with everything just delete 18.04 from the internal hard drive and clone the one in the external driver over. Have been doing that for many distro updates.

---

