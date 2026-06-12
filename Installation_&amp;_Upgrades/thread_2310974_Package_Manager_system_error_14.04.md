---
title: "Package Manager system error? 14.04"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by Andi_GreyScale on 2016-01-23
So over six months ago I started getting this error. I couldn't figure out to do the get-apt in the terminal because it does not give the full command (and I suck at using the terminal) so I ignored it. But once it showed up, I stopped getting all updates. Eventually I decided to re-install 14.04 yesterday and now it's showing up once again today. Also, whenever I try getting updates it just keeps telling me I can't connect to the net... which is clearly not true.

Can anyone give me a step by step process to help me figure out what I'm supposed to do? I'm an idiot. =P

[IMG]http://i.imgur.com/X3x9v0V.png[/IMG]

---

### Post by grahammechanical on 2016-01-23
The command to fix unmet dependencies is

```
sudo apt-get -f install
```

You will be asked to enter your password which will not be printed on the screen but will be registered. The apt-get commands are usually pre-fixed by "sudo." This is standard procedure in Ubuntu and is why instructions do not always include the word "sudo."

If you also run

```
sudo apt-get update
sudo apt-get upgrade
```

You will do in a terminal what the Update Manager does for us. You may see errors in the screen printout. Those errors could be useful in diagnosing the cause of update/upgrade problems. So, they are useful information to include in a post. Please enclose them in quote or code tags.

Here are some other apt-get commends. If you are interested.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

If we run a command that needs administrator authentication and we do not include sudo as a pre-fix we are told that we need to be root to run the command. We see something like this
> 
graham@sdb7-Dev:~$ apt-get update
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Just re-run the command with sudo as pre-fix.

Regards.

---

### Post by Andi_GreyScale on 2016-01-24
Thank you for the reply [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") !!

I ran sudo apt-get -f install and am now getting the below..

[IMG]http://i.imgur.com/hopkIDv.png[/IMG]

[IMG]http://i.imgur.com/s7ooxKQ.png[/IMG]

I also ran sudo apt-get update as well.

---

### Post by kansasnoob on 2016-01-25
One of those errors is in regard to this PPA:

[https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa)

And there is no Trusty version of that PPA so it needs to be purged using ppa-purge:

```
sudo ppa-purge ppa:openshot.developers/ppa
```

I'm unsure what the other error means specifically so we need to see the full output of the following commands. You'll need to copy-n-paste the full output [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") so we can figure exactly what to do:

```
ls /etc/apt/sources.list.d
```

```
cat /etc/apt/sources.list
```

---

### Post by Andi_GreyScale on 2016-01-27
First one
```

kubuntu-ppa-backports-trusty.list
kubuntu-ppa-backports-trusty.list.save
openshot_developers-ppa-trusty.list
openshot_developers-ppa-trusty.list.save
wine-wine-builds-trusty.list

```

Second one
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main


```

---

### Post by kansasnoob on 2016-01-28
Did you purge that openbox ppa?

If so I suspect you're down to one error instead of two, and we may have to look at the actual lists inside "kubuntu-ppa-backports-trusty.list" and "wine-wine-builds-trusty.list" because I'm not sure where that ppa:launchpad.net error is coming from since your actual sources.list looks OK.

---

### Post by Andi_GreyScale on 2016-02-14
> **kansasnoob said:**
> Did you purge that openbox ppa?

If so I suspect you're down to one error instead of two, and we may have to look at the actual lists inside "kubuntu-ppa-backports-trusty.list" and "wine-wine-builds-trusty.list" because I'm not sure where that ppa:launchpad.net error is coming from since your actual sources.list looks OK.

I believe so. I followed all the steps and commands given to me here. =)

Also, sorry for the late reply.

I'm not getting an error anymore though and I can update with no issues. Everything looks good now. Thanks folks!

---

