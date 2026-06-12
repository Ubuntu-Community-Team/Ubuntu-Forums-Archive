---
title: "Upgrade 9.10 to 10.4 beta"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by sw40c on 2010-03-19
Upon issuing "update-manager -d" I get the following error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
Trying to install blacklisted version 'openoffice.org-filter-binfilter_1:3.2.0~rc4-1ubuntu1'

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


I updated synaptic, enabled ALL software channels, updated again, installed updates, but no dice.  Is anyone encountering a similar error when attempting to upgrade from 9.10 to 10.4 beta?

My hope is that the dev folks are focusing on the iso rollout and have yet to enable the distribution upgrade.  Then again, I'd really feel like a chump if it's a SNAFU particular to my system and I'd have to resolve it on my own. :-(  The weather is finally good outside and I'm in sloth mode...

---

### Post by chris_andrew on 2010-03-19
Me, too.

I found this:

[https://bugs.launchpad.net/ubuntu/+bug/542011](https://bugs.launchpad.net/ubuntu/+bug/542011)

Cheers,

Chris.

---

### Post by sw40c on 2010-03-19
:P Yippee!!! :P

Thank you for your input Chris!  I looked at [bug #516727]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/516727") and found:

"Removed openoffice.org-filter-binfilter and upgrade succeeded."

How the heck did he do that?  I looked for the very same package with no luck before I posted to this forum this morning.  I applied a search filter for "binfilter" and there is was - weird. :-k

Anyhow, completely removed the package (will just have to reinstall it later) and now I have just an estimated 9 minutes left for the install!

Lets hope this isn't a portent of things to come.  Still, it's great to have the Ubuntu community at your back!

---

### Post by chris_andrew on 2010-03-20
Before you re-install that package, you may want to look at what it does. Basically it enables support for some archaic document types and the package size is huge!

If it's needed as a dependency, it'll get dragged-in. I'd just forget about it.

Hope to do my upgrade today; how's yours looking?

Cheers,

Chris.

---

### Post by skbhat03 on 2010-03-20
Ok... i know it is not directly related to the problem stated here...since the subject line was upgrade.... i want to ask one question on that.
I am a new to upgrade. I have 9.10 on one of my laptops. So now if i upgrade to 10.04, all my data will be wiped out? Do i need to back it up before the upgrade ?
 
Thanks & Best regards,
Subbu.

---

### Post by chris_andrew on 2010-03-20
The official advice is that you should always back-up before an upgrade.

Best practice is to keep all important data on a seperate /home partition.

Just run sudo update-manager -d

Hope this helps.

Chris.

---

### Post by sw40c on 2010-03-20
Hi Chris,

Sorry for the late reply.  I work the midnight shift across the pond.  I had a few hiccups, namely my GNOME panel and network apps weren't installed.  Not a big problem.  Since I hate the CLI (yes, I know some folks would say I'm not a REAL Ubuntu user for that) I created a shortcut on the desktop for xterm and ran synaptic from there to install the necessary, and missing, packages.  I filtered the installed GNOME packages on synaptic and re-installed all.  A few packages were not updated during the upgrade for some reason and I simply did an update and re-installed those as well. Then it ran like a charm although boot time was longer than 9.10.  Still, it's a beta so I'm sure that will be fixed down the line.

KDE on the other hand was a little more trouble.  I logged in and... got a black screen with a mouse cursor on it.  That's it.  So back to GNOME I go to re-install ALL KDA packages before I reboot into KDE.  Then I found the KDE network manager app missing so back into GNOME to install that and now I'm totally good to go.  The new UI will take some getting used to, but I think I'm going to grow to like it.

As for the binfilter, synaptic says it doesn't exist on the new upgrade.  Then again, synaptic seems to still have a large number of karmic packages hanging around so it may be a small bug.  I don't really know.  I haven't had a chance to see if I need any other OO 3.2 packages yet, but a doc and rtf opened fine for me.  I'll cross that bridge when I come to it.


Subbu - I backed up all my data via VPN to my employer's network before the upgrade just in case I lost everything.  To my surprise I didn't lose a thing!  It's not as easy an upgrade as beta versions have been in the past, but considering it is a beta it was not bad at all.

Hope this helps!

---

### Post by lemming465 on 2010-03-20
In general, doing an upgrade-in-place will not lose any data.  However, any time you are fiddling with disk partitions and replacing hundreds of thousands of files things are riskier than normal.  So its definitely a best practice to do backups first.  You want to back up every OS and data file you care about on the connected disks, not just the one you are planning to upgrade.

Also, with the current state of flux in Xwindow video drivers, I really like to boot a live CD and verify that I still have video, audio, and network before I commit to an upgrade in place.  If you have lots of bandwidth and CD-RW media to rewrite this gets a bit easier.

Cautious types will wait about a month past the official release date and then run "sudo update-manager -c".  This allows most of the bugs to shake out before committing to the upgrade.

Bleeding edge pioneers willing to risk data loss and days of downtime will help out with the testing starting with the later alpha's or betas or release candidates.  They are the ones running "sudo update-manager -d".   E.g. last night I upgraded a test system install of 10.04 alpha3 to 10.04 beta1, and the gnome-panels crashed.  I had to wait 24-hours and use a text console to do "aptitude clean; aptitude update; aptitude full-upgrade" to get working GUI back.

If you aren't willing to live with breakage, file bug reports, and recover the hard way or reinstall, don't upgrade anything earlier than release candidates.

Also, keep in mind that upgrades are one-way trips.  You can't easily downgrade; the only real downgrade is to reinstall, and the easiest reinstalls are when you completely reformat partitions, which loses all the data on them.

Not to discourage you, just to make sure that folks know what they are getting into.

Personally, I've been doing upgrade-in-place on my main live home desktops around the release candidate stage, but that's after doing test installs with the alpha's and beta's for a month or two on other spare partitions and 3-4 different computers so that I have some confidence in what I'm going to get.

---

### Post by nutsy.ben on 2010-10-27
One other option: 

Make a fresh burn of the ISO and put your CD in.
It does not calculate anything in this case, it just run the update manager.

At least it worked for me after a week of troubles !!

---

