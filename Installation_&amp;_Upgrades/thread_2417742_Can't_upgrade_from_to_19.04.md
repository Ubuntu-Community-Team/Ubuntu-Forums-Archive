---
title: "Can't upgrade from to 19.04"
date: 2019-04-26
forum: Installation &amp; Upgrades
---

### Post by chendoy on 2019-04-26
Hi,

I have trouble upgrading from 18.10 to 19.04.
Software update does notifies we about the upgrade but when I click "upgrade" nothing happens.

I did try upgrading manually via terminal by following [this]("https://linuxconfig.org/how-to-upgrade-ubuntu-to-19-04-disco-dingo") article with no luck.

It says "Please install all available updates for your release before upgrading."

[ATTACH=CONFIG]283109[/ATTACH]

---

### Post by TheFu on 2019-04-26
```
$ sudo apt update
$ sudo apt dist-upgrade
$ reboot  # if needed
```

**_make a know-you-can-restore backup. This is NOT optional._**

```
$ sudo do-release-upgrade
```

Fix any PPAs that need fixing, but use the newer version in the repos, if possible.
Be happy?

New is the enemy of stable.

---

### Post by chendoy on 2019-04-26
> **TheFu said:**
> ```
$ sudo apt update
$ sudo apt dist-upgrade
$ reboot  # if needed
```

**_make a know-you-can-restore backup. This is NOT optional._**

```
$ sudo do-release-upgrade
```

Fix any PPAs that need fixing, but use the newer version in the repos, if possible.
Be happy?

New is the enemy of stable.

thanks for the reply. I already tried this as I mentioned (the link I provided).
Do you know how to fix the PPA's though?

---

### Post by TheFu on 2019-04-26
Sorry, I didn't look at the link because people seldom actually follow the complete instructions in links.  Also, it was from a website that I don't know to be reputable.  That doesn't mean it isn't reputable, just that I don't know it is.

Did each of the commands actually work without errors?  The error you typed in above doesn't match the window attachment.  Why is that?
Did you reboot?

Each PPA needs different handling post-upgrade.  The do-release-upgrade process disables all PPAs to prevent upgrade failures.  These were a big issue in the early days of Ubuntu.  Post-upgrade, that is a hint for us to install the packages using the repos post-upgrade and only re-enable the PPAs, using the new PPA links for the specific release. Those should be different PPA commands, add-apt-repository.

---

### Post by chendoy on 2019-04-27
The attachment shows what I get when running the update manager GUI and when running the command on terminal I get:

 after [COLOR=#000000][FONT=&amp]sudo apt update[/FONT][/COLOR]:

```

chen@chen-ubuntu:~$ sudo apt updateHit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease
Ign:2 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) cosmic InRelease                                           
Err:3 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) cosmic Release                                           
  404  Not Found [IP: 91.189.92.152 80]
Hit:4 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates InRelease  
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic InRelease                 
Hit:6 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-security InRelease     
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-security InRelease        
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates InRelease
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-proposed InRelease
Hit:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-backports InRelease
Reading package lists... Done 
E: The repository 'http://extras.ubuntu.com/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

and this is after [COLOR=#000000][FONT=&amp]sudo apt dist-upgrade[/FONT][/COLOR][COLOR=#000000]:[/COLOR]

```

chen@chen-ubuntu:~$ sudo apt dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wpasupplicant
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I did reboot even tough I was not needed to.

Still, this is what I get when I run [COLOR=#000000][FONT=&amp]sudo do-release-upgrade[/FONT][/COLOR][COLOR=#000000]:[/COLOR]

```

Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```

I've even tried to reset my repositories using [this]("https://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories") guide. after following this, the software update tool did prompt we of new updates to be installed (around 300mb). I installed them and rebooted but still..no change.

---

