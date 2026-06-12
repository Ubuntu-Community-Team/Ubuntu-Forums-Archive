---
title: "What the heck should I do with this if anything?"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Tominator on 2006-09-08
I have been trying to update from version 5.10 to 6.06. Last night I was advised to go study some articles which I have done. I am cautiously trying different things. The following is my latest result, do you think I should go for it? Does uncomment mean removing all those pound signs and then hitting the enter key? Considering changing my screen name to clueless, lol. I shoot a real mean game of pool though, lol. Back to business, am trying to upgrade using update manager. Here is the error message I started with............Failed to Fetch [http://security.ubuntu,com/ubuntu/di...curity/Release](http://security.ubuntu,com/ubuntu/di...curity/Release) Unable to find expected entry deb/binary-i386/packages in Meta-Index file (malformed Release file?) Please excuse any typos in that.
So, here is the subject of my inquiry......## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
..........Thanks in advance, Tom

---

### Post by qamelian on 2006-09-08
Follow the instructions at the wiki page linked below. 
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
I've found this to be the easiest and safest way to go.

---

### Post by Emerzen on 2006-09-08
Go to [this page]("http://www.ubuntulinux.nl/source-o-matic") and create a new sources.list for breezy.  Then, save your current sources.list -> rename /etc/apt/sources.list to something else.  Save the file from the above website as sources.list and copy it to the above directory.  Then do the sudo apt-get update -> sudo apt-get dist-upgrade.

For most, this way of updating works well.  I typically do a clean install as my system is tweaked and breakage happens.  I have a separate partition (not a home partition) where I save stuff I don't want to lose, everything else is expendable.

---

### Post by confused57 on 2006-09-08
I used this method to upgrade from breezy to dapper:
[http://psychocats.net/ubuntu/dapper](http://psychocats.net/ubuntu/dapper)

Just remove the # sign in front of anything that looks like a url, which are your repositories.  Place a # in front the CD-rom at the top of the sources.list.

I was definitely quite apprehensive about doing the dist-upgrade, but the above method worked quite well for me.  Read over the above guide and see what you think, and I'll try to answer any questions and give you more details of my experience with the upgrade.

Edit:  As Emerzen suggested, a new sources.list would probably be a good idea.

---

### Post by zxee on 2006-09-08
You do not need to remove the "#" symbols from the comments. It looks like your sources list has the "extra" repos enabled, but if you want to upgrade to dapper you need dapper repos. I've attached a copy of a dapper sources.list.
Refer to your guide for doing the upgrade to 6.06.
Usually in apt it's > sudo apt-get update> sudo apt-get dist-upgrade

Added: My method will work-I believe but the link provided by the previous poster is a good guide.

---

