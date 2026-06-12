---
title: "do-release-upgrade shows No New Release Found although 14.04.1 is available"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by darthbith on 2014-07-27
Hello,

I am running 12.04.4 LTS server. Running [FONT=Lucida Console]sudo do-release-upgrade[/FONT] shows 

Checking for a new Ubuntu release
No new release found

I know that I have to wait until 14.04.1 is released before upgrading. However [14.04.1 has been released]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes"). Running [FONT=Lucida Console]sudo do-release-upgrade -d[/FONT] begins the update process, but I don't want to switch to the developers channel, or to non-LTS releases. What is the problem here?

---

### Post by Bucky Ball on 2014-07-27
*Thread moved to **Installation & Upgrades**.*

---

### Post by kansasnoob on 2014-07-27
> **darthbith said:**
> Hello,

I am running 12.04.4 LTS server. Running [FONT=Lucida Console]sudo do-release-upgrade[/FONT] shows 

Checking for a new Ubuntu release
No new release found

I know that I have to wait until 14.04.1 is released before upgrading. However [14.04.1 has been released]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes"). Running [FONT=Lucida Console]sudo do-release-upgrade -d[/FONT] begins the update process, but I don't want to switch to the developers channel, or to non-LTS releases. What is the problem here?

I discovered a nasty bug while performing iso/upgrade testing:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

Since I didn't discover and file it until the 23rd Canonical apparently delayed the automated notifications for Precise -> Trusty release upgrades until they get that sorted. But based on my own testing it only effects Precise users who applied the Trusty [HWE upgrade]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") earlier. To see if you're effected run the command:

```
uname -r
```

If that shows you're already running the 3.13 series kernel then the upgrade is known to fail.

If you're not effected maybe you have Software Sources set wrong? Run the command:

```
grep Prompt= /etc/update-manager/release-upgrades
```

That should show *Prompt=lts* if the settings are correct.

I think the safest thing to do is wait for Canonical to sort things out, I know they are working on it :)

---

### Post by darthbith on 2014-07-27
> **kansasnoob said:**
> I discovered a nasty bug while performing iso/upgrade testing:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

Since I didn't discover and file it until the 23rd Canonical apparently delayed the automated notifications for Precise -> Trusty release upgrades until they get that sorted. But based on my own testing it only effects Precise users who applied the Trusty [HWE upgrade]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") earlier. To see if you're effected run the command:

```
uname -r
```

If that shows you're already running the 3.13 series kernel then the upgrade is known to fail.

Thanks for the links. *uname -r* shows *3.2.0-67-generic* so I guess that will not be a problem.

> **kansasnoob said:**
> If you're not effected maybe you have Software Sources set wrong? Run the command:

```
grep Prompt= /etc/update-manager/release-upgrades
```

That should show *Prompt=lts* if the settings are correct.

I think the safest thing to do is wait for Canonical to sort things out, I know they are working on it :)

That did indeed show *Prompt=lts*, so it is correct. Guess I'll just have to wait then. Any idea on an ETA for the update? I'm trying to plan when the server downtime will be :-)

---

### Post by kansasnoob on 2014-07-27
> **darthbith said:**
> Thanks for the links. *uname -r* shows *3.2.0-67-generic* so I guess that will not be a problem.



That did indeed show *Prompt=lts*, so it is correct. Guess I'll just have to wait then. Any idea on an ETA for the update? I'm trying to plan when the server downtime will be :-)

I suspect you may have an additional problem then, or maybe not :redface:

Check to be sure 'update-manager-core' is installed:

```
apt-cache policy update-manager-core
```

If that shows it's installed I see no reason why this shouldn't work:

```
sudo do-release-upgrade
```

Of course release upgrades are well known for introducing various degrees of borkage so always be prepared for the worst :(

---

### Post by darthbith on 2014-07-28
> **kansasnoob said:**
> I suspect you may have an additional problem then, or maybe not :redface:

Check to be sure 'update-manager-core' is installed:

```
apt-cache policy update-manager-core
```

If that shows it's installed I see no reason why this shouldn't work:

```
sudo do-release-upgrade
```

Of course release upgrades are well known for introducing various degrees of borkage so always be prepared for the worst :(

update-mananger-core is installed: 

```
~$ apt-cache policy update-manager-core
update-manager-core:
  Installed: 1:0.156.14.15
  Candidate: 1:0.156.14.15
  Version table:
 *** 1:0.156.14.15 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.156.14.5 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     1:0.156.14 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

do-release-upgrade still shows nothing. FWIW, I have upgraded all of the packages on the system as well (i.e. apt-get upgrade shows no upgrades). Is there anything else I can try? How do I check what server do-release-upgrade is checking for upgrades?

Thank you for your help! :-D

---

### Post by darthbith on 2014-07-28
> **darthbith said:**
> How do I check what server do-release-upgrade is checking for upgrades?


By looking at /usr/share/pyshared/DistUpgrade/MetaRelease.py (which do-release-upgrade calls), I found that the URL it looks at to determine if an upgrade is available is [http://changelogs.ubuntu.com/meta-release-lts](http://changelogs.ubuntu.com/meta-release-lts) and there is to Trusty distro on that list. Any idea when it will be added?

---

### Post by ubfan1 on 2014-07-28
Apparently the 14.04.1 release is rolled out in stages to avoid overloading the servers.  You can just wait, or download the iso, and add it to the sources for updates -- then you should be able to upgrade.

---

### Post by kansasnoob on 2014-07-28
> **ubfan1 said:**
> Apparently the 14.04.1 release is rolled out in stages to avoid overloading the servers.  You can just wait, or download the iso, and add it to the sources for updates -- then you should be able to upgrade.

Best to be patient ;)

I discovered two critical bugs during iso/upgrade testing, one in Saucy -> Trusty upgrades:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721)

The other in Precise -> Trusty upgrades:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

And another lesser, but still concerning bug:

[https://bugs.launchpad.net/ubuntu/precise/+source/update-manager/+bug/1348067](https://bugs.launchpad.net/ubuntu/precise/+source/update-manager/+bug/1348067)

The devs are working feverishly at fixing these!

Those who fail to be patient may encounter breakage requiring a full reinstallation which may cause dual-booters to encounter this nasty bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by M._Gruber on 2014-07-29
The two critical bugs [1347721]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721") and [1347964]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964") have been fixed.
When will the LTS upgrade finally be rolled out?

---

### Post by Old_Grey_Wolf on 2014-07-29
When they are ready, and probably on a Thursday or Friday depending on your time zone. It is an LTS to LTS upgrade; therefore, I am not in a hurry. I would much prefer a trouble free upgrade if that is possible. :)

---

### Post by stephenbbb on 2014-07-29
> **kansasnoob said:**
> I discovered a nasty bug while performing iso/upgrade testing:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

Since I didn't discover and file it until the 23rd Canonical apparently delayed the automated notifications for Precise -> Trusty release upgrades until they get that sorted. But based on my own testing it only effects Precise users who applied the Trusty [HWE upgrade]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") earlier. To see if you're effected run the command:

```
uname -r
```

If that shows you're already running the 3.13 series kernel then the upgrade is known to fail.

If you're not effected maybe you have Software Sources set wrong? Run the command:

```
grep Prompt= /etc/update-manager/release-upgrades
```

That should show *Prompt=lts* if the settings are correct.

I think the safest thing to do is wait for Canonical to sort things out, I know they are working on it :)

I have 3.13 on one my Ubuntu machines. Is there a way to downgrade to sth that will upgrade without a fail?

---

### Post by Bucky Ball on 2014-07-30
You could spend the next two days working out how to downgrade just in time for the fixed release on Thurs or Fri which you won't need to downgrade for. You can't wait a couple of days for an LTS upgrade?

On your grub menu at boot don't you have any earlier kernels?

---

### Post by Old_Grey_Wolf on 2014-07-30
> **Bucky Ball said:**
> You could spend the next two days working out how to downgrade just in time for the fixed release on Thurs or Fri which you won't need to downgrade for. You can't wait a couple of days for an LTS upgrade?

On your grub menu at boot don't you have any earlier kernels?

I would expect the upgrade to occur on a Thurs or Fri; however, is it really this week?

---

### Post by stephenbbb on 2014-08-01
> **Old_Grey_Wolf said:**
> I would expect the upgrade to occur on a Thurs or Fri; however, is it really this week?

Apparently not this week and most likely not the next. Ha-ha-ha.

I want to downgrade from the HWE as it messed up the suspend. the only way to wake up after a suspend is to remove the battery and unplug, then plug n start. It was working nicely befpre the HWE and only the devil set me up to upgrade.
also, unlike the now extinct opensolaris, ubuntu does not support BE and once you install sth it messes up everything and choosing one of the previously working versions does absolutely nothing. 
anyway, my goal is not to whine, but to fix it by downgrading.
regards

---

### Post by M._Gruber on 2014-08-02
It's pretty disappointing how the whole LTS upgrade thing is handled.
Initially the 14.04.1 was announced for July 17th, then postponed to July 24th with the release published on July 25th.
At that time the upgrade was said to come in the next hours or days.
Now it's almost 10 days after and there's zero communication about when the upgrade is at least planned to happen.

---

### Post by Yudley on 2014-08-02
> **M._Gruber said:**
> 
It's pretty disappointing how the whole LTS upgrade thing is handled.
Initially the 14.04.1 was announced for July 17th, then postponed to July 24th with the release published on July 25th.
At that time the upgrade was said to come in the next hours or days.
Now it's almost 10 days after and there's zero communication about when the upgrade is at least planned to happen.


I've been watching this thread since July 26th or so, and it's disappointing to me as well.

Don't get me wrong, Ubuntu is a free OS, and I appreciate all the hard work and effort of the developers, maintainers, admins.

However, it seems to be the assumption that LTS-to-LTS folks are in no hurry to upgrade from 12.04 to 14.04. Well 14.04 was released more than 3 months ago and the whole point of waiting until 14.04.1 was to have a more stable platform by July 24th. I waited all this time and now I find people saying LTS people have plenty of time to upgrade, and that the upgrade won't be available even this week, or the next week. Well I think it's safe to say that LTS folks have more important things to do than follow the launchpad bug reports and ubuntuforum threads to find out when the upgrade issue is fixed (even to this day 'sudo apt-get update && sudo do-release-upgrade' shows 'No release found' and I don't even have the HWE thing, just the vanilla 12.04.4 with 3.5.x kernel or something). That was the whole point of making them wait until 14.04.1 AFAIK.

---

### Post by kansasnoob on 2014-08-02
> **Yudley said:**
> I've been watching this thread since July 26th or so, and it's disappointing to me as well.

Don't get me wrong, Ubuntu is a free OS, and I appreciate all the hard work and effort of the developers, maintainers, admins.

However, it seems to be the assumption that LTS-to-LTS folks are in no hurry to upgrade from 12.04 to 14.04. Well 14.04 was released more than 3 months ago and the whole point of waiting until 14.04.1 was to have a more stable platform by July 24th. I waited all this time and now I find people saying 'LTS people have plenty of time to upgrade'. Well I have more important things to do than follow the launchpad bug reports and ubuntuforum threads to find out when the upgrade issue is fixed (even to this day 'sudo apt-get update && sudo do-release-upgrade' shows 'No release found' and I don't even have the HWE thing, just the vanilla 12.04.4 with 3.5.x kernel or something). That was the whole point of making LTS folks wait until 14.04.1 AFAIK.

Would you have preferred they allow the upgrades knowing the process was broken? I did not discover and file [the bug that stalled this]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964") until the 23rd.

I'm following up on some other lesser release upgrade bugs now ([example]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1351414")) and once I have enough info I'm going to file a bug report against [the release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes") themselves because they still show 13.10 release upgrade notes (even though [they're borked]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721")) and outdated upgrade bug info :(

Nothing gets fixed by accident and the lion's share of testing is performed by volunteers like me that don't get paid a dime ;)

---

### Post by uRock on 2014-08-02
> **kansasnoob said:**
> Would you have preferred they allow the upgrades knowing the process was broken? I did not discover and file [the bug that stalled this]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964") until the 23rd.

I'm following up on some other lesser release upgrade bugs now ([example]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1351414")) and once I have enough info I'm going to file a bug report against [the release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes") themselves because they still show 13.10 release upgrade notes (even though [they're borked]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721")) and outdated upgrade bug info :(

Nothing gets fixed by accident and the lion's share of testing is performed by volunteers like me that don't get paid a dime ;)

If the upgrade is buggy, then I am glad they are holding a back a little longer.

You may not get paid, but you do get a thank you from time to time. Thank you for everything you do for the greater good of Ubuntu! :p

---

### Post by M._Gruber on 2014-08-04
@kansasnoob: I'm following your efforts and **really** appreciate them, however there's seems to be a total lack of interest from Canonical's (paid) developers to get things going, as it can be seen in your latest [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826").

It's also completely intransparent to me, who is actually responsible to add the Trusty LTS section to [http://changelogs.ubuntu.com/meta-release-lts](http://changelogs.ubuntu.com/meta-release-lts) in order to offer the upgrade.

In one bug report you mention Michael Vogt, who seems to be involved in this process.
Well, I've emailed him 4 days ago about the upgrade issue without any response at all...

---

### Post by kansasnoob on 2014-08-04
> **M._Gruber said:**
> @kansasnoob: I'm following your efforts and **really** appreciate them, however there's seems to be a total lack of interest from Canonical's (paid) developers to get things going, as it can be seen in your latest [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826").

It's also completely intransparent to me, who is actually responsible to add the Trusty LTS section to [http://changelogs.ubuntu.com/meta-release-lts](http://changelogs.ubuntu.com/meta-release-lts) in order to offer the upgrade.

In one bug report you mention Michael Vogt, who seems to be involved in this process.
Well, I've emailed him 4 days ago about the upgrade issue without any response at all...

I share some of those feelings, my most recent rant is here:

[http://ubuntuforums.org/showthread.php?t=2237479](http://ubuntuforums.org/showthread.php?t=2237479)

The installer bug I mention there is possibly the worst I've seen in recent history. But we need to keep our rants and opinions over there at chat instead of here in the support section ;)

---

### Post by philhughes on 2014-08-05
Support for 12.04.4 ends in two days (2014-08-07). So at that time it seems we have two options:

1. Wait for the release to become available and run the risk of having no security updates for the kernel and graphics stack.
2. Install the 12.04.5 HWE stack, which will then mean an upgrade from 12.04.5 to 14.04.1, with the possibililty of further undiscovered upgrade bugs.

Is this correct?

That there are bugs is understandable, and  I'm sure the developers are working hard to fix them, but the lack of communication is disappointing.

---

### Post by mörgæs on 2014-08-05
No, not correct. Support for 12.04 runs through 2017 for Ubuntu and 2015 for Xubuntu. 

The third number (as in 12.04.4) does not matter with regards to support.

---

### Post by philhughes on 2014-08-05
Sorry, I should have said 12.04 with the 12.04.2, 12.04.3 or 12.04.4 HWE stacks, support for which does end in 2 days:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Of course the third option is to reinstall, but I really don't want to do that:)

---

### Post by M._Gruber on 2014-08-07
This is like a time loop - 14 days and not even a sign that the folks at Canonical are at least aware of the problem.
2 days ago I emailed Adam Conrad ([who published the release notes]("https://lists.ubuntu.com/archives/ubuntu-announce/2014-July/000188.html") 2 weeks ago) to point him towards the bug report -> no response.
1 day ago the [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826") was escalated to the QA tracker -> no one cares.

---

### Post by kansasnoob on 2014-08-07
> **M._Gruber said:**
> This is like a time loop - 14 days and not even a sign that the folks at Canonical are at least aware of the problem.
2 days ago I emailed Adam Conrad ([who published the release notes]("https://lists.ubuntu.com/archives/ubuntu-announce/2014-July/000188.html") 2 weeks ago) to point him towards the bug report -> no response.
1 day ago the [bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826") was escalated to the QA tracker -> no one cares.

I'm the one that added it to the QA Tracker during 12.04.5 iso testing with the reasoning that based on the original 14.04 release announcement all 12.04 users should now be getting the prompt to upgrade.

---

### Post by grahammechanical on 2014-08-07
Regarding the length of support to the kernel in 12.04, which was raised earlier in this thread, this wiki page has some charts at the bottom of the page that indicate that there is kernel support up to April 2017 for Ubuntu 12.04.0 and 12.04.1 and also 12.4.5 but not for 12.04.2; 12.04.3 and 12.04.4.

Regards.

---

### Post by dstein on 2014-08-07
/etc/motd on my Ubuntu 12.04 machine contains the following:

[INDENT]Your current Hardware Enablement Stack (HWE) is going out of support
on 2014-08-07.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)

To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade

OR

* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty

and reboot your system.[/INDENT]

However, even though it suggests to do do-release-upgrade, running do-release-upgrade reports "Checking for a new Ubuntu release\n No new release found", as mentioned in this thread.

---

### Post by stephenbbb on 2014-08-10
has anyone received communication that Canonical is working on making the upgrade possible??

if they perceive that it's just about 20 folks who need this and everybody else is on 14.04 they may simply ignore us. maybe it is time to consider switching to the original Debian?

---

### Post by kansasnoob on 2014-08-10
> **stephenbbb said:**
> has anyone received communication that Canonical is working on making the upgrade possible??

if they perceive that it's just about 20 folks who need this and everybody else is on 14.04 they may simply ignore us. maybe it is time to consider switching to the original Debian?

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762/comments/7](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762/comments/7)

> The meta-release file will be updated on Monday, August 11th.

I'd guess someone just had a brain fart :oops:

---

### Post by kansasnoob on 2014-08-10
> **mörgæs said:**
> No, not correct. Support for 12.04 runs through 2017 for Ubuntu and 2015 for Xubuntu. 

The third number (as in 12.04.4) does not matter with regards to support.

But kernel version does:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

Xubuntu opted out of the HWE thing, but Ubuntu and Edubuntu users that installed using the 12.04.2, 12.04.3, or 12.04.4 images have to upgrade to the Trusty HWE (or upgrade to Trusty altogether).

---

### Post by dstein on 2014-08-11
do-release-upgrade now detects an available upgrade.

---

