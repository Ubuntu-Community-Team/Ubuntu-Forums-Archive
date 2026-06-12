---
title: "sudo apt-get dist-upgrade caused my ubuntu install to think it's linux mint, not work"
date: 2021-07-04
forum: Installation &amp; Upgrades
---

### Post by Ranbunta_Bantubunt on 2021-07-04
Howdy... I have gotten myself into a bit of a pickle. 

Im running ubuntu 20.04, I was using the cinnamon desktop though, and had mintupdate installed associated with that.
Somehow my apt package manager state became invalid, at first it was saying "cannot update cinnamon-desktop-screensaver" because of some dependency (serena?) missing.

I tried to apt update && apt upgrade, but it was unable to update mintupdate because: "trying to overwrite '/usr/share/icons/hicolor/16x16/apps/software-properties.png', which is also in package software-properties-gtk"

I used dpkg --force-overwrite to get that working. Not sure if I would use the word "fix"... @_@ 

There were a few packages which were "held back" at this point, which I unwisely decided to "fix" with sudo apt-get dist-upgrade. It did cause apt to be happy and feel like things were consistent, but on reboot, I couldnt log in to cinnamon.

I got to the login screen, but when I tried to log on, I got the error "Error found when loading /etc/profile: /etc/profile.d/01-locale-fix.sh: line 2: /usr/bin/locale-check: No such file or directory. As a result the session will not be configured correctly.  You should fix the problem as soon as possible." Then, it tried to log in to my desktop but the screen went black, except for the mouse cursor, I couldnt alt-f3 or alt-f5 to get a terminal. Logged in to recovery mode.

In recovery mode, cat /etc/lsb-release showed that the system thought it was linux mint 18.x. I think 18.1 but dont remember for sure.

I tried to do sudo apt reinstall base-files, but it kept re-installing linux mint and thinking the system was linux mint.

I then got a copy of the base files for ubuntu 11ubuntu5 from [http://security.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_11ubuntu5.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_11ubuntu5.3_amd64.deb) and used apt install to install them. 

Now cat /etc/lsb-release showed the system agreed it was ubuntu 20.04. :) 

Then I did sudo apt update && sudo apt upgrade, and it reinstalled the base files for linux mint again  and cat /etc/lsb-release reverted back to linux mint. So there is some flag somewhere indicating that the distro is linux mint.

I re-re-installed the ubuntu base files, and then rebooted, and I was able to log in to the ubuntu default desktop environment. Cinnamon was not available.

However my system seems to be just one sudo apt update && sudo apt upgrade away from breaking again as the software manager is offering me this "update":

```
$ apt list --upgradable
Listing... Done
base-files/serena,serena 18.1.0 amd64 [upgradable from: 11ubuntu5.3]

```

I think I'll stick to the pure ubuntu distro going forward and not use cinnamon as I dont want to run into issues like this again... any advice on how to get my system back to understanding that it is ubuntu 20.04 and not linux mint?

Thanks!!!

Bunts

---

### Post by guiverc on 2021-07-04
If you 

```
sudo apt update
```

on your box, you should see no Linux Mint sources.

My guess is you've added some, leading to your issues.

I cannot see how adding [https://packages.ubuntu.com/focal/cinnamon-desktop-environment](https://packages.ubuntu.com/focal/cinnamon-desktop-environment) would add *Mint* update (there is no Mint packages listed as dependency); my guess is you didn't use the Cinnamon desktop packaged for Ubuntu, but added *Linux Mint* packages which changed your system into a *Linux Mint* system.

*Linux Mint*, like many downstream systems, artificially provide higher package versions in the packaging, so their packages aren't replaced when Ubuntu update packages; this isn't an issue unless you've added those sources to a Ubuntu system, where *Linux Mint* themselves warn you may *break* your system.

If you

```
apt-cache policy cinnamon-desktop-environment
```

plus other packages you have (eg. the "*mintupdate*" package you mentioned), I suspect you'll find they aren't from Ubuntu repositories, ie. your issue was added non-Ubuntu sources and corrupted your Ubuntu system.

If you want to use Cinnamon, I'd suggest using the Ubuntu packaged version.

---

### Post by Ranbunta_Bantubunt on 2021-07-04
Yes I'm sure I did it wrong... this is my first linux laptop and I have been flogging my way through things.

Cinnamon isn't installed any more, but indeed it appears to have been from a linux minut repository:

```
$ sudo apt-cache policy cinnamon-desktop-environment
cinnamon-desktop-environment:
  Installed: (none)
  Candidate: 2018.06.08
  Version table:
     2018.06.08 500
        500 http://packages.linuxmint.com tara/main amd64 Packages
        500 http://packages.linuxmint.com tara/main i386 Packages
     2016.11.28 500
        500 http://packages.linuxmint.com serena/main amd64 Packages
        500 http://packages.linuxmint.com serena/main i386 Packages
     4.5+really4.4.1 500
        500 http://mirror1.totbb.net/ubuntu focal/universe amd64 Packages
        500 http://mirror1.totbb.net/ubuntu focal/universe i386 Packages
```

I've been using this setup though, quite a while now... I migrated to linux maybe 7-8 months ago and installed cinnamon right away, surprising there hasn't been an issue before. 

I can remove the linux mint sources from my apt sources list, and install cinnamon from the link you provided. Do I need to do anything else to undo the mayhem that I caused my system? I am afraid a future apt update && upgrade will again lead to mayhem. :) 

Thanks again for the insight and help.

---

### Post by Ranbunta_Bantubunt on 2021-07-04
OK I got rid of the two repositories which were in /etc/apt/sources.list/d that referred to linux mint... the "official-package-repository" or something like that, was sneaky and stealth but I managed to find it, and made sure there was nothing else in there by cat /etc/apt/sources.list.d | grep mint, nothing else there.

Now when I ask the software manager to check for updates, it reports that the software is up to date, rather than offering the linux mint "update" to my ubuntu distro.

Also Cinnamon is back and working properly. I think all is well.

Do I still need to take further steps such as reinstalling the distro entirely, purging caches, etc? I think it's solved now... 

Thanks again!! Really helpful.

---

### Post by grahammechanical on 2021-07-05
For the benefit of those who do not know.

The command apt-get dist-upgrade will "fix" package conflicts by removing packages it decides are least important in order to install packages it considers most important. The man page for apt-get says

> dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

It can an does break the OS. Do not use this command thinking it will upgrade one version of Ubuntu to the next version. It does not do that.

Regards

---

### Post by guiverc on 2021-07-05
I would check for what other *Linux Mint* packages you have.

They may not cause problems until *release-upgrade* time comes, then you risk having problems, but they may also prevent security fixes from Ubuntu from reaching your system (due to the artificially higher package versions used by *Linux Mint*)

You could try using

```
ubuntu-security-status --thirdparty
```

to find those packages  (*note: I believe it's `ubuntu-security-status`; I forget which release switched from `ubuntu-support-status` to `ubuntu-security-status` so apologies if it's the wrong command*.* I don't have a focal (20.04) system handy to test*).

Personally I'd try and remove all *Linux Mint* packages, as they can cause security fixes for Ubuntu *not being installed*; meaning you're more at risk. *Linux Mint* has a different security model than Ubuntu, and being *reliant* on *runtime adjustments* has meant they have to accept some things which won't impact a Ubuntu system. 

Sure if the only packages found are wallpapers (*Linux Mint* have had some wonderful! wallpapers over the years), I'd not worry about them, it's the packages that contain code that I'd worry about, esp. if it replaces packages from the ['main' Ubuntu repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") (ie. highest level of security for Ubuntu; *Mint* packages cannot match that those for security review).

---

### Post by Ranbunta_Bantubunt on 2021-07-05
Yup ubuntu-security-status --thirdparty worked...

I looked through the list of installed packages, they are all stuff I recognize and nothing from Linux mint.

I think I've fixed my issues. Thanks for the advice. My mistakes were adding linux mint repositories in the first place, then using the apt-get dist-upgrade command after that.

Bunts

---

### Post by sudodus on 2021-07-05
Thanks to everybody who posted in this thread,

I think you have added valuable knowledge to many of us :KS

---

### Post by CatKiller on 2021-07-05
> **Ranbunta_Bantubunt said:**
> I think I've fixed my issues. Thanks for the advice. My mistakes were adding linux mint repositories in the first place, then using the apt-get dist-upgrade command after that.
Also adding a repository directly rather than using a PPA. With a PPA you can use the **ppa-purge** command to automatically downgrade all relevant packages to the standard repository versions rather than the PPA versions from the PPA you're removing.

---

