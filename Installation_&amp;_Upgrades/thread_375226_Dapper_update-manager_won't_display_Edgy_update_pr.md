---
title: "Dapper update-manager won't display Edgy update prompt"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by tathamg on 2007-03-03
I'm trying to update from Dapper (6.06 LTS) to Edgy (6.10) using the "official method":
[INDENT][COLOR="Navy"]gksudo "update-manager -c"[/COLOR][/INDENT]

When I do this, I receive no option to upgrade the distribution (I get "Your system is up to date" only).  That is, there's no indication that it's found Edgy, and no button/link/message for me to click to perform an update to Edgy.

I've tried many variants on my sources.list file, including emptying it out just down to the main/restricted settings.  My current sources.list is as follows:

[INDENT][COLOR="Navy"]
# UBUNTU ITSELF
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

# MAJOR BUG FIXES
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

# BACKPORTS
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse

# CANONICAL COMMERCIAL
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# PLF REPOSITORY
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## Skype
# - Fails
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
# XGL
# - Fails
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
# deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# Easy Ubuntu
# deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

[/COLOR][/INDENT]

I'm sure there's some simple setting somewhere that I'm missing . . . but Googling, and reading through this forum, the FAQs, etc., I don't seem to be able to find it.  Nor are there any obvious messages in my log files.  Given the dire warnings against upgrading in any way other than through update-manager, I'm loathe to try other avenues.

Any hints appreciated!

---

### Post by zvacet on 2007-03-03
```
gksu "update-manager -c" 
```

---

### Post by tathamg on 2007-03-03
. . . unfortunately, same thing.  Update-manager works fine (has successfully updated system over time, including successfully just earlier today) . . . just won't display the Edgy prompt!

---

### Post by blknit on 2007-03-03
same problem here

---

### Post by jocko on 2007-03-03
I think you need to add the edgy repos to your sources.list.
Just change every "dapper" to "edgy" and try the update manager again.

---

### Post by tathamg on 2007-03-03
Thanks!  Tried that just now.  What happened is that update-manager came up with a long list of packages that wouldn't be removed (I guess what are now old versions?) and suggested that I use "sudo apt-get dist-upgrade" . . . which, as I understand it, is not what I want to do.  Still didn't prompt to update from Dapper to Edgy, though.

---

### Post by jocko on 2007-03-04
A dist-upgrade is exactly what you want to do.
I think (but I'm not sure) you can do it by ```
sudo update-manager -d
``` otherwise ```
sudo aptitude update && sudo aptitude dist-upgrade
``` will do it.

---

### Post by Kateikyoushi on 2007-03-04
> upgrade
          Upgrades installed packages to their most recent version. Installed
          packages will not be removed unless they are unused (see the section
          &#8220;Managing Automatically Installed Packages&#8221; in the aptitude
          reference manual); packages which are not currently installed will
          not be installed.

          If a package cannot be upgraded without violating these constraints,
          it will be kept at its current version. Use the dist-upgrade command
          to upgrade these packages as well.

       dist-upgrade
          Upgrades installed packages to their most recent version, removing
          or installing packages as necessary. This command is less
          conservative than upgrade and thus more likely to perform unwanted
          actions. Users are advised to either use upgrade instead or to
          carefully inspect the list of packages to be installed and removed.


So dist-upgrade won't upgrade you to a newer release, you have to change the sources-list and then dist-upgrade.
Read more here. [LINK]("https://help.ubuntu.com/community/UpgradeNotes")

---

### Post by xyz on 2007-03-04
For what it's worth, this worked for me:
```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```
finds and replaces dapper with edgy.
```
sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade 
```

---

### Post by tathamg on 2007-03-04
Thanks for the suggestions.  I'd already tried "update-manager -d" (actually with -c, as well), but that didn't help.

I wanted to avoid the aptitude/apt-get route, as the [community upgrade instructions]("https://help.ubuntu.com/community/EdgyUpgrades") (as well as various other mutterings around the 'Net) say:
> Upgrading using apt-get -- NOT RECOMMENDED

Please note - this method is much less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectantly, etc. Using Update Manager (see above) is likely to be much less problematic. 

What I wound up doing, which appeared to resolve my issue (still part-way through the install) is to:
1.  Download the ISO
2.  Burn it to a CD
3.  gksu sh /cdrom/cdromupgrade

This prompted me to upgrade as I would have expected.

---

### Post by steveyos666 on 2007-03-04
I don't think it's working for anyone. I guess they messed something up or a server went down or something like that. It's XP time until they fix it :D

---

### Post by pgn674 on 2007-03-04
Another similar thead is happening [here]("http://ubuntuforums.org/showthread.php?t=376158"). Guess it's a server thing.

---

