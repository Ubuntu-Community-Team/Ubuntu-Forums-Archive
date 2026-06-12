---
title: "[SOLVED] update manager"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-10-17
whenever i click the update manager i get the following errors ?
 
 A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages), W:Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

**How to solve this problem ?**

---

### Post by cariboo on 2008-10-17
Post your /etc/apt/soucres.list, it looks like you've got a spelling error. To post your sources.list press Alt-F2 and type the following:

```
gksu gedit /etc/apt/sources.list
```

Copy the text and paste it in your next post. Please use the code tags to make it test easier to read. The code tags are available in the advanced editor just click the # sign.

Jim

---

### Post by Kevbert on 2008-10-17
Please take a look at my post on the [[COLOR="Red"]Ultimate Ubuntu forum.[/COLOR]]("http://forumubuntusoftware.info/viewtopic.php?f=43&t=1872&sid=00a4bd12bfc9900e3573d99a7c99f201")
It seems a lot of people are having this problem...54 replies to the post so far...and at least 4 people have separately posted on this one about this same problem.

---

### Post by sulekha on 2008-10-17
> **cariboo907 said:**
> Post your /etc/apt/soucres.list, it looks like you've got a spelling error. To post your sources.list press Alt-F2 and type the following:

```
gksu gedit /etc/apt/sources.list
```

Copy the text and paste it in your next post. Please use the code tags to make it test easier to read. The code tags are available in the advanced editor just click the # sign.

Jim


[B]I corrected the spelling mistakes and then i removed some repeating entries

and then i tried [/B]

user@ubuntu:~$ sudo apt-get install mplayer
[sudo] password for user:
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_hardy_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


**BTW this is my /etc/apt/sources.list file**

#
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
#ULTAMATIX REPOS END

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

---

### Post by drphat on 2008-10-17
I also am getting the same responses, this seems to be a consistent issue.

---

### Post by cariboo on 2008-10-17
It seems there are problems with the Ultimate edition repositories. Just comment out the entries Between:

```
ULTAMATIX REPOS START
```

and

```
ULTAMATIX REPOS END
```

Then uncomment all the repositories the the script commented out. Then run:

```
sudo apt-get update
```

Jim

---

### Post by drphat on 2008-10-17
Thank you for the gentle response, I did what the linked post stated above and everything worked....sorry for not reading all the posts...thank you again!

---

