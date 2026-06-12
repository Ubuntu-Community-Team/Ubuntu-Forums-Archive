---
title: "Upgrade to 22.04 failed"
date: 2022-12-08
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2022-12-08
Hello,

Upgrade to 22.04 failed and resulted in the following error message:
[IMG]https://i.postimg.cc/7hwk0NYb/Screenshot-from-2022-12-08-20-39-28.png[/IMG]
I examined main.log and noticed following message:
2022-10-23 14:33:54,353 ERROR Dist-upgrade failed: 'Broken packages after upgrade: gnome-control-center, gnome-shell, libgirepository-1.0-1, ubuntu-desktop'
Does it mean that I should remove gnome-control-center, gnome-shell, libgirepository-1.0-1, ubuntu-desktop' ?
Thanks.

---

### Post by ubfan1 on 2022-12-08
No, look at your /etc/apt/sources.list and sources.d  for PPAs you have added, do the suggested purge on them and remove the ppa, then apt update and upgade, then try the release upgrade

---

### Post by py-ohayo on 2022-12-08
Thanks.
There is no **sources.d** in [B]/etc/apt/.

[/B]In sources.list the most of lines are commented. I couldn't recognize I added.
Here it is ...

```
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic universe
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable # disabled on upgrade to focal

```

Should I check other files ?
Sincerely.

---

### Post by ubfan1 on 2022-12-08
Are you trying to upgrade an 18.04 system to 22.04?  I think you need to go to 20.04 first in that case.  Reinstall might be easier in that case.

---

### Post by TheFu on 2022-12-08
> **ubfan1 said:**
> Are you trying to upgrade an 18.04 system to 22.04?  I think you need to go to 20.04 first in that case.  Reinstall might be easier in that case.

+1.

Lots of internal things change with each LTS.  1 upgrade and the remaining cruft isn't too bad.  But with 2 upgrades, there will be 2 or more subsystems that have been completely replaced ... unless the old release kept them.  Now you have 3 versions of stuff trying to manage 1 thing.  Which is actually doing that management?  Who knows.  

Best to avoid all of that, backup your data, a list of manually installed packages, and custom settings, then do a fresh install.  Restore the data, selectively restore the custom settings, then feed a list of the manually installed packages to be reinstalled into APT.  This is actually how I create my daily backups, so I've practiced restoring from this information a few times every year (when bad things happen, or when I'm an idiot).

---

### Post by py-ohayo on 2022-12-08
> **ubfan1 said:**
> Are you trying to upgrade an 18.04 system to 22.04?  I think you need to go to 20.04 first in that case.  Reinstall might be easier in that case.

No, I'm trying to upgrade from 20.04:

xxx@yyy:/etc/apt$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.5 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.5 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

---

### Post by py-ohayo on 2022-12-08
> **TheFu said:**
> +1.
Best to avoid all of that, backup your data, a list of manually installed packages, and custom settings, then do a fresh install.  Restore the data, selectively restore the custom settings, then feed a list of the manually installed packages to be reinstalled into APT.  This is actually how I create my daily backups, so I've practiced restoring from this information a few times every year (when bad things happen, or when I'm an idiot).

You mean install 22.04 from scratch ?

---

### Post by TheFu on 2022-12-08
> **py-ohayo said:**
> You mean install 22.04 from scratch ?

Yep. Seems you've already done 1 upgrade from 18.04 at some point. We see that in the sources.list. You have some cruft already.

---

### Post by Bashing-om on 2022-12-08
py-ohayo; Hey

My 2 cents:
> 
Broken packages after upgrade:


It will also be most informative to see the results:
```

sudo apt update
sudo apt upgrade

```

so we see the errors in context.

[INDENT]just what I think
[/INDENT]

---

### Post by mIk3_08 on 2022-12-09
> **ubfan1 said:**
> Are you trying to upgrade an 18.04 system to 22.04?  I think you need to go to 20.04 first in that case.  Reinstall might be easier in that case. I agree... This is a long jump. :P I experienced this long jump in a kernel, though it was amazingly successful but I don't share this since it is not advisable. But if you are eager to do it, then do it at your own risk. Doing step by step is better. I prefer to do a fresh install of 22.04 LTS for less headaches for you py-ohayo. Regards and cheers.

---

### Post by py-ohayo on 2022-12-09
> **Bashing-om said:**
> py-ohayo; Hey
It will also be most informative to see the results:
```

sudo apt update
sudo apt upgrade

```
so we see the errors in context.
[INDENT]just what I think
[/INDENT]

Done.
There were no errors.

---

### Post by py-ohayo on 2022-12-09
> **TheFu said:**
> Yep. Seems you've already done 1 upgrade from 18.04 at some point. We see that in the sources.list. You have some cruft already.
Yes, I upgraded to 20.04.

---

### Post by TheFu on 2022-12-09
> **mIk3_08 said:**
> I agree... This is a long jump. :P I experienced this long jump in a kernel, though it was amazingly successful but I don't share this since it is not advisable. But if you are eager to do it, then do it at your own risk. Doing step by step is better. I prefer to do a fresh install of 22.04 LTS for less headaches for you py-ohayo. Regards and cheers.

We already determined that the OP did a 18.04 --> 20.04 upgrade previously.  Something failed in the 20.04 --> 22.04 move.
At least two people already suggested that he backup and precious and do a fresh install.  Reads like that is your recommendation as well.

The other option is to restore from a pre-attempt backup, then ensure all the patches are installed, with no warnings or errors, clean all the excess stuff - I'd use 'apt autoclean' and 'apt clean', purge any unwanted kernels (headers, modules too), especially if there are multiple lines installed - say 4.15.x and 5.4.x and remove any unwanted snaps ... which could be all of them.   Having a very clean, functioning system BEFORE attempting an OS upgrade is smart.  But it won't prevent subsystem cruft from being pulled forward (resolvconf, ifupdown, and a bunch of less-great systemd stuff).  Starting with a clean, freshly rebooted, system that doesn't have any issues at all, makes for an upgrade that is more likely to succeed. 

Once, I had an upgrade fail because I'd forgotten to change my development perl (the default) back to the operating system perl version.  Everything seemed fine. The upgrade took nearly 3 hrs and when it was all done, there were lots and lots of issues.   I use a virtual environment manager to make switching between different versions of perl and perl modules really easy.  I used to write professional perl servers.  Anyway, all the OS stuff expects a specific version of perl, not the newer version(s) that I use for clients.  In the end, I did a fresh install of the new OS and used backups from the night before to restore my settings, system settings, my data, system data and the list of installed packages.  The new OS was up and working feeling like "my" computer in about 45 minutes, though fixing some of the file permissions from the TB and TB of data on that box did take a bit to figure out because I was a little dense and forgot that uids and gids would change between installs.  Nearly all the data needed to be owned by Jellyfin, so it wasn't THAT hard to figure out ... just wasn't a priority after the new install.

OMHO, changing kernels doesn't really matter that much, unless you are using proprietary, binary, drivers, like nvidia.  Then sticking with the installed or HWE kernels really is the best answer.  But it isn't hard to put a 6.x kernel onto an 18.04 system if new AMD drivers are needed.  I've done that myself.  5.4.x wasn't new enough to support the AMD GPU drivers.  That's what the 'mainline' tool is about, 
```
$ mainline
mainline 1.0.18
Distribution: Ubuntu 20.04.5 LTS
Architecture: amd64
Running kernel: 5.15.0-56-generic

mainline 1.0.18 - Ubuntu Mainline Kernel Installer

Syntax: mainline <command> [options]

```
None of those kernels are considered QC'd and may not be as stable as the fully tested, Canonical approved, kernels for any OS release.  But I haven't had too many issues picking a specific kernel for a specific purpose.

But I'm getting off topic.

---

### Post by py-ohayo on 2022-12-09
> **TheFu said:**
> We already determined that the OP did a 18.04 --> 20.04 upgrade previously.  Something failed in the 20.04 --> 22.04 move.
At least two people already suggested that he backup and precious and do a fresh install.  Reads like that is your recommendation as well.


Ok, thanks. Can fresh install be made from command line, or should I create "install flash" and launch installation from flash ?

---

### Post by TheFu on 2022-12-09
> **py-ohayo said:**
> Ok, thanks. Can fresh install be made from command line, or should I create "install flash" and launch installation from flash ?

I don't know how to magically do a fresh install without all the existing storage being un-mounted.  Do you?  That would be a need trick.  None of my systems are setup for dual boot ... at least I don't think they are.  Last time I dual booted was perhaps 2012.

I would use the "Try Ubuntu" ISO on a flash drive. Honestly, I don't install desktops very often, perhaps 2 times every 2 yrs and that is seldom the GnomeDE version (if ever).  I often install Ubuntu Server for desktops and servers, then specifically install the window manager I want, fvwm.  I'm happy not to have all the desktop integrations and bloat.  Anything to stop network-manager, avahi, and desktop applications that I'll never use, from being automatically installed is high on my "desired features list."  Even the "minimal" install options for all the DEs are still way, way, way, too bloated.  Ubuntu Server is pretty bloated already too, with lots of things that aid Canonical, but not me.  I've spent far too much time disabling and removing their cruft.  Sigh.

Of course, we are all different, with different desires and goals.

---

### Post by mIk3_08 on 2022-12-09
> **TheFu said:**
> not to have all the desktop integrations and bloat.  Anything to stop network-manager, avahi, and desktop applications that I'll never use, from being automatically installed is high on my "desired features list."  Even the "minimal" install options for all the DEs are still way, way, way, too bloated.  Ubuntu Server is pretty bloated already too, with lots of things that aid Canonical, but not me.  I've spent far too much time disabling and removing their cruft.  Sigh.
Of course, we are all different, with different desires and goals. This is the thing why I always do with the fresh installs than doing the disk upgrade. Its a bunch of non-sense stock in your storage. I already had a poor system hardware with a small capacity storage drive and bunch of non-sense system files. Though, disk upgrade is convenient but theirs a lot of make up to do with your system. The crawling system is not good to use. Fresh install is like you when you are freshly just got from a shower.

---

