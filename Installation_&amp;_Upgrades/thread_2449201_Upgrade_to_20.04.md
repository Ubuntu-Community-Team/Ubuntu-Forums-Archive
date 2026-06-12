---
title: "Upgrade to 20.04"
date: 2020-08-22
forum: Installation &amp; Upgrades
---

### Post by Philip_Edwards on 2020-08-22
Hi Group,

I'd like to upgrade my laptop from 18.04 to 20.04

So far, I'm failing.

I tried following the instructions on [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

I've tried this.

sudo do-release-upgrade -d

I got this.


Please install all available updates for your release before upgrading.


So, I do this. Still being told to install updates.

I've tried using the software updater. It tells me that a new version of Ubuntu is available and asks would I like to install. I say yes.
Ythen I get this...
FFailed to download repository information. Check your internet connection.

TThere is nothing wrong with my internet connection.

MMaybe I'm overworrying about this upgrade?

PPhil

---

### Post by TheFu on 2020-08-22
Do these first:
```
sudo apt update
sudo apt full-upgrade
```
Correct any issues.  Do NOT try to move on until all the issues are solved.

---

### Post by mIk3_08 on 2020-08-22
What Ubuntu 18.04 O.S type you have, 32-bit or 64-bit?

---

### Post by Philip_Edwards on 2020-08-23
64 bit

---

### Post by Philip_Edwards on 2020-08-23
Tried the full upgrade.

No issues were found.
I get this now.

sudo do-release-upgrade -d -f DistUpgradeViewGtk3
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

---

### Post by ajgreeny on 2020-08-23
I always clean install and have never upgraded my OS version so I am not the best person to try to help but the command 
***sudo do-release-upgrade -d***
according to ***man do-release-upgrade*** 
> -d, --devel-release
              If using the latest supported release, upgrade to the development release
will take you to the development version from the latest supported version, which 18.04 certainly not; that would be 20.04.

I may have misunderstood the manual so I just add this comment as a "thinking point" in case others know better than I do, but perhaps you need to run the command without any option at all.  
As I say, I've never done this so may be wrong.

---

### Post by TheFu on 2020-08-23
I wouldn't be surprised if the -d command attempted to load Ubuntu 20.10-alpha, but I'm an LTS-only person. I did my volunteer testing in the 1990s when compiling everything from source was the expected solution.

The OP can always download the 20.04.1 ISO and do an upgrade in-place. Just be certain to have excellent backups before doing anything. Stuff like this sometimes fails. When there is any failure at all, it tends to be bad for our data.

I've been upgrading many of my LTS-only systems since 10.04. These aren't desktops, so the non-repo software on them is extremely limited or the primary reason the system exists.  Just checked and my communications server (zimbra) doesn't support 20.04. Perhaps next spring?

On one of my test desktop systems, I migrated from 16.04 --> 20.04. That seemed to go fine, until about a month later when grub was messed up by a patch. After 30 minutes screwing around with grub and not being able to solve it, I wiped the machine, did a fresh install of 20.04 and restored system settings, /usr/local/, my settings, my data, then loaded the list of already installed applications. This took about 45 minutes. When completed, the machine felt exactly like it did before the grub patch mess.  Good backups are always helpful, especially for sleeping at night. No related issues since, just the normal 20.04 problems for me, which we don't need to get into here. For me, 20.04 broke a number of important things. 18.04 broke a number of important things too, which weren't fixed for 2 yrs. We're skipping 18.04 completely here.

New is the enemy of stable. Always remember that.

---

### Post by martago on 2020-08-24
If "sudo do-release-upgrade -d" still fails, probably means the release upgrade is really, realy delayed.  We are in the last week of August, the version to upgrade is 20.04, which means it should have been released in last April, so almost 4 months has passed.  I don't remember with past LT releases this type of delay.  Please do make an effort to catch with present time.  Thank you.

---

### Post by ActionParsnip on 2020-08-24
[https://www.omgubuntu.co.uk/2020/08/ubuntu-20-04-upgrade-notification-delay](https://www.omgubuntu.co.uk/2020/08/ubuntu-20-04-upgrade-notification-delay)

---

### Post by rsteinmetz70112 on 2020-08-24
> **martago said:**
> If "sudo do-release-upgrade -d" still fails, probably means the release upgrade is really, realy delayed.  We are in the last week of August, the version to upgrade is 20.04, which means it should have been released in last April, so almost 4 months has passed.  I don't remember with past LT releases this type of delay.  Please do make an effort to catch with present time.  Thank you.

For LTS releases the availability of do-release-upgrade is delayed until the .1 release to allow time for any initial problems to be worked out. This is typically July but varies. 20.04.1 has been out for a while and last time I checked all blocking issues had fixes released. So I don't know what the hold up is.

---

### Post by Philip_Edwards on 2020-08-25
Thanks everybody..............maybe I shouldn't be in too much of a rush.
I have 20.04 on a USB drive so I could do a fresh install. 
Is that easy to do on a duel boot machine?
Phil

---

### Post by ActionParsnip on 2020-08-25
Is 18.04 giving you issues?

---

### Post by TheFu on 2020-08-25
> **rsteinmetz70112 said:**
> For LTS releases the availability of do-release-upgrade is delayed until the .1 release to allow time for any initial problems to be worked out. This is typically July but varies. 20.04.1 has been out for a while and last time I checked all blocking issues had fixes released. So I don't know what the hold up is.

Perhaps they want to better fix the black screen that a huge number of people are experiencing post-1st boot?  I know they did some work on getting nvidia drivers automatically installed during installation, but perhaps there are more edge cases than we knew which fail?

Or perhaps an nVidia lawyer contacted them with some demands.

---

### Post by CelticWarrior on 2020-08-25
> **TheFu said:**
> Or perhaps an nVidia lawyer contacted them with some demands.

Perhaps.
It used to be that a license agreement must be shown prior to the actual installation of the (freeware) proprietary Nvidia drivers. So, it could be argued that distros providing an automatic installation process (Mint, Manjaro, etc.) where doing so illegally.

Ubuntu as well by not showing the license when installing them but since that was an user action independent from the OS installation the blame could theoretically be shifted to the end-users.

---

