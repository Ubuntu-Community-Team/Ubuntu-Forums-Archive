---
title: "hardy-lucid upgrade hosed, report where?"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by gerryg001 on 2010-05-17
On this laptop I upgraded karmic to lucid. All went well, so I then tried my desktop with Hardy 8.04LTS to Lucid. After several hours, the upgrade aborted leaving the system hosed. Message to report this bug against the upgrade-manager with certain logs, which I snapped.

However, I can't use the new reporting method ubuntu-bug from that system as it's hosed. Been awhile since I reported a bug, so went to launchpad and searched for upgrade-manager. Nothing found. Does this go in upgrade-system?

> please report this bug against the 'upgrade-manager' package and include the files in /var/log/dist-upgrade/ in the bug report. E:Sub-process /usr/bin/dpkg returned an error code (1). E:Sub-process /usr/bin/dpkg returned an error code (1).

So, where does this get reported, and what do I do now? I can boot the desktop off a flash drive for access and probably mount the drives, but what then?

---

### Post by kansasnoob on 2010-05-17
This is the only thing I can think of:

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20when%20off-line](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20when%20off-line)

> Filing bugs when off-line

In the event that you have a bug with your internet connection or want to file a bug for another system you can still do this using apport. Using the command apport-cli -f -p <package name> on the target system will collect information and provide you with an option to "K: Keep report file for sending later or copying to somewhere else". The report is then saved on the target system, in your /tmp directory which is cleared out on reboot, with a .apport extension. After copying it to a different system you can file that report using ubuntu-bug  <location of apport file>. 

Or possibly:

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

> Filing bugs at Launchpad.net

If for some reason you cannot file a bug through the Apport tool you can file one via Launchpad. When doing so please ensure that you have determined which package it should be filed against. Read 'finding the right package' for guidance or use Launchpad's package search feature. To file a bug against a specific package use a url similar to the following, **[http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect)**, where PACKAGENAME is the name of the source package about which you want to file the bug. In the event that you want to request a piece of software be packaged for Ubuntu please follow the instructions in the wiki. To report a bug when you don't know the package name [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

Kudos for taking the time to file a bug and try to make Ubuntu better :)

---

### Post by gerryg001 on 2010-05-17
> [https://bugs.launchpad.net/ubuntu/+source/upgrade-manager/+filebug?no-redirect](https://bugs.launchpad.net/ubuntu/+source/upgrade-manager/+filebug?no-redirect)

Seems to be what they're saying to use, but no such page. I already read the stuff you mentioned and more. Guess I'll report this as generic and let somebody move it elsewhere.

But I'm also looking for some info on what to do with a completely hosed upgrade. Haven't seen anything.

Just tried a generic launchpad submission.
(Error ID: OOPS-1598C2111)Launchpad  
and that failed with a timeout.

---

### Post by kansasnoob on 2010-05-17
I tried also and get the same thing :(

Anyway look here:

[http://ubuntuforums.org/showthread.php?t=1471183](http://ubuntuforums.org/showthread.php?t=1471183)

I know that's horribly long but if you can boot into recovery mode you might try:

```
sudo dpkg --configure -a
```

or:

```
sudo apt-get -f install
```

And see if that gives any clues.

Sometimes you can rescue a borked upgrade in a chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Potentially helpful commands include the two above and:

apt-get update
apt-get dist-upgrade
apt-get clean
apt-get autoclean
apt-get autoremove

The very first issue below has been a killer with Hardy to Lucid upgrades:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

> Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")

For those not wanting to read the bug report in detail, the fix is :

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```



---

### Post by gerryg001 on 2010-05-17
Still found no clue on troubleshooting this. This was a 64-bit system with a lot of development stuff on it That upgrade was big and complex and a quick scan of the logs doesn't show more than dpkg errors. I can mount the drives from a USB boot. Now torrent downloading a 64-bit desktop iso. Unless somebody has a better suggestion, it sounds like I should just make a bootable flash with lucid and try to install it, ripping apart any of the old stuff that's in the way. That'll lose so much it'll probably take weeks to get that system back to where it was.

Have used ubuntu for years with many installs and upgrades. I'm disappointed with both the launchpad issues and the lack of any guidance (that I've been able to find) on how to approach this. Looks like a lot of dependency problems from dpkg, especially with python. I have no idea how to try fixing that on a system that can only be booted from a flash drive.

---

### Post by kansasnoob on 2010-05-17
I wish I had a better answer for you :(

I've had about a 90% success rate fixing borked upgrades thru a chroot if I have the computer right in front of me. There is no single "best place to start" it doesn't seem like.

I always just start with the simplest commands as stated above. Quite often I have to check software sources. Sometimes purge and then reinstall packages, etc.

I know how bad it can suck so you truly have my empathy.

---

### Post by gerryg001 on 2010-05-17
kansasnoob, thank you for the sympathy. I've fixed a few, but this is too messy. Fortunately, I have enough disk space with /home and other data on separate partitions. Just installed fresh from a Lucid flash and all seems good. Except, of course, for a few hundred missing applications:)

Oh well, along the long path from BSD2.3 to Ubuntu Lucid, I can hardly say this is the first such rebuild...and far from the worst.

---

