---
title: "Updating to a later version of specific software"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by Michael_Mather on 2013-10-11
I am running 12.04 (LTS), which has version 1.3.8-10 of the package rkhunter. The rkhunter web site flashes at you the message:
[I]Rootkit Hunter release 1.4.0 obsoletes all previous releases. Please upgrade real soon now.
[/I]
The problem of what to do is more general than just rkhunter, but it makes a good example of a general problem.

Q1: Should I do this by using a package from a later version of Ubuntu? (Eg, 13-04 has version 1.4.0-2 of rkhunter.) How is that done, and what are the risks?

Q2. Or should I download rkhunter-1.4.0.tar.gz from sourceforge, unzip it, and try to work out which files go where. Are there risks with that?

Q3. And how do you recommend that I try to avoid overwriting changes I have made to config files, cron jobs etc.

Q4: Anyway, you would think this is a security update. So why is it not included in 12.04?

Thanks

---

### Post by varunendra on 2013-10-13
Welcome to the forums Michael !

I'd try to answer the questions to the best of my ability, however, be informed (or rather 'warned') that 'my' ability itself is not the best around here :P
So do some research and backup your system before trying any of the suggestions, and ofcourse keep the fire-extinguisher ready.
> **Michael_Mather said:**
> Q1: Should I do this by using a package from a later version of Ubuntu? (Eg, 13-04 has version 1.4.0-2 of rkhunter.) How is that done, and what are the risks?
In my opinion, this would be the best and safest way to upgrade. But if it doesn't show up by itself after doing an "apt-get update", you may be out of luck with this option. In that case, you may try manually downloading it from [here]("http://archive.ubuntu.com/ubuntu/pool/universe/r/rkhunter/") then install with a double-click, but that may lead to dependency issues and is not recommended.

If this goes smooth there is no risk. But if not and you 'force' install it (manually downloading the package and dependencies etc.) then broken libraries and unmet dependencies are the worst that can happen. These can be fixed, if required, but may cause some headache. There are a couple other options too, but practically it would be safer and easier to just upgrade to 13.04 (clone/backup your system first, updates tend to fail often).

> Q2. Or should I download rkhunter-1.4.0.tar.gz from sourceforge, unzip it, and try to work out which files go where. Are there risks with that?
tar.gz packages usually come with their own compiler (if required) and installer scripts. If the usual update doesn't offer you the desired version, this is the next safest option. Either it will build/install or it won't. There is no risk involved unless you had to manually 'Replace' some files. But then again, this is just what is 'usual', and there is no guarantee that 'unusual' can't happen. Since you would be installing with 'sudo', it may replace some libraries that may cause troubles with some other applications later.

I'm not familiar with rkhunter package and so the above is just a 'general' idea. If it is a self contained package, then it is perfectly safe to install and use.

> Q3. And how do you recommend that I try to avoid overwriting changes I have made to config files, cron jobs etc.
Backup-backup and backup. There is no alternative to backups.

> Q4: Anyway, you would think this is a security update. So why is it not included in 12.04?
No it is not a security update. It is an optional package, a 'Security Tool', that comes from 'universe' repository.

Hope someone else with a first hand experience with it may offer a better answer. :)

---

### Post by oldos2er on 2013-10-14
The README file has installation instructions: [http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README) specifically 
```
To perform a default installation of RKH simply unpack the tarball and,
as root, run the installation script:

    tar zxf rkhunter-<version>.tar.gz
    cd rkhunter-<version>
    ./installer.sh --install
```

---

### Post by Michael_Mather on 2013-10-17
Thanks for the help. Here is the advice I am giving myself.

RKHunter is special because it changes too rapidly for Ubuntu to keep up.

So I am going to remove it as an Ubuntu package, and reinstall it from the tarball.
(If the package is not removed, then running "apt-get upgrade" could cause a mess.)

When it needs updating, that will be done from a tarball as well.

Note that there is more to installing RKHunter than just a simple install, but that is not the subject of this thread.

Note also that, even if this is not a "security update", keeping RKHunter up-to-date may help security.

---

### Post by Psil0cybin on 2014-04-08
Any update with this? I have Ubuntu 12.04, I noticed that rkhunter is outdated, and cannot update. I am also considering updating it manually via the tarball, instead of upgrading my system completely..
any recommendations?

---

