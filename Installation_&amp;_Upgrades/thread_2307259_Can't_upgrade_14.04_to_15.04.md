---
title: "Can't upgrade 14.04 to 15.04"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by lordbah2 on 2015-12-23
I can't upgrade 14.04 to 15.04. The error in dist-upgrade/main.log is

2015-12-23 08:26:38,315 ERROR Dist-upgrade failed: 'The package 'ubuntu-release-upgrader-gtk' is marked for removal but it is in the removal blacklist.'

Possibly relevant:

2015-12-23 08:26:38,107 WARNING Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)

However I have no held packages at all (dpkg --get-selections | grep hold) and no broken packages (per synaptic status window not showing a Broken category), so I don't know what it's thinking. No other line in the file mentions hold/held/broken.

No other ERROR or WARNING in main.log. It does know that it's running in 'desktop' mode because of ubuntu-desktop.

I considered removing ubuntu-release-upgrader-gtk in synaptic but it wanted to also remove ubuntu-desktop, which didn't sound like something I wanted to do.

---

### Post by Bucky Ball on 2015-12-23
? 14.04 LTS upgrades to 14.10 which is not out of support so that is a dead end. Not sure how you've attempted the upgrade, but curious to know where you saw that 14.04 LTS upgrades to 15.04?

15.04 is out of support in a month, so wouldn't bother. I would have stuck with 14.04 if everything was fine (if it ain't broke, don't fix it is my principle, though :)). 14.04 is LTS (long-term support) and LTS releases upgrade to the next LTS, in this case, 16.04 sometime after April 2016. If your intention was to get to 15.10 through upgrades, better to clean install.

Can you still boot into 14.04?

---

### Post by lordbah2 on 2015-12-23
I didn't do anything tricky - I ran update-manager and it said "Ubuntu 15.04 is now available (you have 14.04)."  Why would it offer something that isn't going to work?

I did have it set to only notify on LTS upgrades until this morning when I changed that setting. That's why I hadn't been upgraded to 14.10. If I figure out how to get it to offer me an upgrade to 14.10, will the path from 14.10 to 15.04 then work? Or is it impossible to ever change from LTS to non-LTS?

---

### Post by Bucky Ball on 2015-12-23
14.10 is no longer supported so that is a dead end. You would be attempting to upgrade to an EOL release then to one that's supported for a month. You could, with a lot of messing around, time and hunting for a swapping retired repos, maybe get there, but hardly worth the effort, which has a good chance of being unsuccessful anyway. 

No, it's not impossible to change from LTS to interim. Any release will upgrade to the next release (14.04 to 14.10) while the next release is *still supported*.

---

### Post by grahammechanical on 2015-12-23
The command sudo apt-get dist-upgrade does not upgrade one version of Ubuntu to the next version. What it does is upgrade the existing version with packages that are being held back from the normal apt-get upgrade command.

The wiki says this about apt-get upgrade

> This command upgrades all installed packages.  This is the equivalent of "Mark all upgrades" in Synaptic.

and this is what the wiki says about apt-get dist-upgrade

> The same as the above, except add the "smart upgrade" checkbox. It tells  APT to use "smart" conflict resolution system, and it will attempt to  upgrade the most important packages at the expense of less important  ones if necessary.

apt-get dist-upgrade" does not perform distribution upgrade.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

On at least one occasion I have found "smart" conflict resolution to be not so smart as it removed something that should not have been removed. I run the development  version of Ubuntu and I update every day & there are always packages being held back. Sometimes I run apt-get dist-upgrade & I always keep my fingers crossed that nothing breaks. Things do not often break.

If all you have done is run apt-get dist-upgrade, then think yourself lucky. The best advice at this time is to stay with 14.04 and consider upgrading to 16.04 in about 4 months time.

Regards.

EDIT:

> Or is it impossible to ever change from LTS to non-LTS?

No. It is not impossible but we must do it while the next release is still in life support. Or, to put it another way, Within 8 - 9 months of the next release being released. All the versions released in between the 2 yearly release of LTS versions only have 9 months support.

If we are not happy about upgrading every 6 - 9 months then we stick with an LTS.

---

### Post by Bucky Ball on 2015-12-23
> **grahammechanical said:**
> If all you have done is run apt-get dist-upgrade, then think yourself lucky. The best advice at this time is to stay with 14.04 and consider upgrading to 16.04 in about 4 months time.

Regards.

Good punt and recommended, but user states:

> I didn't do anything tricky - I ran update-manager and it said "Ubuntu 15.04 is now available (you have 14.04)." 

:)

---

### Post by ian-weisser on 2015-12-23
Update-manager offering unsupported or inappropriate upgrade choices is part of [LP #1252843]("https://bugs.launchpad.net/bugs/1252843"). 
If you think this bug has indeed bitten you, please click on the 'Does this bug affect you?' link at the top of the bug report.

---

### Post by lordbah2 on 2015-12-23
Actually, update-manager is all I did to get offered 15.04. Once that didn't work, some of my later attempts were "sudo do-release-upgrade". It never offered me any choices. Did this run "apt-get dist-upgrade" under the hood?

---

### Post by kansasnoob on 2015-12-23
> **Bucky Ball said:**
> 14.10 is no longer supported so that is a dead end. You would be attempting to upgrade to an EOL release then to one that's supported for a month. You could, with a lot of messing around, time and hunting for a swapping retired repos, maybe get there, but hardly worth the effort, which has a good chance of being unsuccessful anyway. 

No, it's not impossible to change from LTS to interim. Any release will upgrade to the next release (14.04 to 14.10) while the next release is *still supported*.

Actually back in September Canonical changed that, so if 14.04 is set to upgrade to interim releases it would offer 14.04 -> 15.04:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

Of course it would be stupid to do so because in one month you'd need to upgrade from 15.04 to 15.10, and I've found the process to be broken anyway:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688)

The best bet is to change the settings back to offering only LTS to LTS and wait for 16.04 which is only 4 months from now.

---

### Post by lordbah2 on 2015-12-23
> [COLOR=#000000]Actually back in September Canonical changed that, so if 14.04 is set to upgrade to interim releases it would offer 14.04 -> 15.04:

Which is what I tried to do, which failed. Any feedback on the ERROR and WARNING from main.log?[/COLOR]

---

### Post by kansasnoob on 2015-12-23
> **lordbah2 said:**
> I can't upgrade 14.04 to 15.04. The error in dist-upgrade/main.log is

2015-12-23 08:26:38,315 ERROR Dist-upgrade failed: 'The package 'ubuntu-release-upgrader-gtk' is marked for removal but it is in the removal blacklist.'

Possibly relevant:

2015-12-23 08:26:38,107 WARNING Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)

However I have no held packages at all (dpkg --get-selections | grep hold) and no broken packages (per synaptic status window not showing a Broken category), so I don't know what it's thinking. No other line in the file mentions hold/held/broken.

No other ERROR or WARNING in main.log. It does know that it's running in 'desktop' mode because of ubuntu-desktop.

I considered removing ubuntu-release-upgrader-gtk in synaptic but it wanted to also remove ubuntu-desktop, which didn't sound like something I wanted to do.

I would change that back to offering upgrades to LTS versions only for the reasons I stated in my last post.

Then concentrate on fixing the "held broken packages" error, so after changing that back to offering only LTS release upgrades close the software updater, open the terminal and run:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

Then post the full output of the latter of those two so we can try to get a handle on what's borked in package management.

---

### Post by lordbah2 on 2015-12-23
man page: "install is followed by one or more packages" -- what does it do with zero package names?

---

### Post by kansasnoob on 2015-12-23
> **lordbah2 said:**
> > [COLOR=#000000]Actually back in September Canonical changed that, so if 14.04 is set to upgrade to interim releases it would offer 14.04 -> 15.04:

Which is what I tried to do, which failed. Any feedback on the ERROR and WARNING from main.log?[/COLOR]

In addition to what I already suggested I think we should have a look at your software sources so post the full output of these two commands:

```
cat /etc/apt/sources.list
```

```
ls /etc/apt/sources.list.d
```

---

### Post by kansasnoob on 2015-12-23
> **lordbah2 said:**
> man page: "install is followed by one or more packages" -- what does it do with zero package names?

Just provides info, eg;

```
lance@lance-desktop:~$ sudo apt-get -f install
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-generic linux-image-3.13.0-65-generic
  linux-image-extra-3.13.0-65-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

In your case it will probably provide info on held broken packages.

---

### Post by lordbah2 on 2015-12-23
It didn't list any broken packages, or really anything.
bar.txt is the apt-get -f install output, foo.txt is the sources. main.log.txt is the output from the upgrade which I thought I had attached to the original post.

---

