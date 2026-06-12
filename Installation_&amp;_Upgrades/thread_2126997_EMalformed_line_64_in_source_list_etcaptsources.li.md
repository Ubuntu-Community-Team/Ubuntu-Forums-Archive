---
title: "E:Malformed line 64 in source list /etc/apt/sources.list (dist parse)"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by poignantprick on 2013-03-18
Hi there!

Just came back to Linux (long story why I left) and I am running into some issues. I don't have much of a grasp on the terminal, or much of anything with what seems to be advanced computing, but I can follow specific directions fairly well. :grin:

Using Gnome 3 desktop on Ubuntu 12.04

Not sure exactly when my issue came about, but I think it may have been when I was trying to install Adobe Acrobat (for school stuff related to the long story as to why I was relegated to Win 7). I know for sure that I didn't get it installed and that I now cannot update or open Software center. I, of course, searched out information and saw that other users had the same issue with different lines in their source lists. But I couldn't get a handle on how to identify, fix, or remove the problem. I'm not a dolt, but I really do need simple directions with these things. Thank you in advance for any assistance.

Here is the source list:

```

# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
```

---

### Post by ibjsb4 on 2013-03-18
edit

---

### Post by schragge on 2013-03-18
> **ibjsb4 said:**
> The last two lines
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner 
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Should read
```
deb http://archive.canonical.com/ precise partner 
deb-src http://archive.canonical.com/ precise partner

``` Note the space between the URL and *precise*.

---

### Post by poignantprick on 2013-03-18
Perfect. You have magical powers. Now I will figure out how to make this read as "solved" #-o which I am sure is easy to do.

Thank you for your help. It is very much appreciated.

---

### Post by varunendra on 2013-03-18
Thread marked as [Solved] on OP's request.

@ poignantprick,
The regular 'Mark thread Solved' function is broken since forum upgrade. We hope to bring it back as soon as possible.
Meanwhile, there is a workaround to do the same. Please follow the '[COLOR="#000080"]see how[/COLOR]' link in my signature to see that.

Thanks for your interest in marking threads Solved.
:)

---

### Post by ibjsb4 on 2013-03-19
Now I see the confusion, lol

[http://ubuntuforums.org/showthread.php?t=2127036&p=12564119#post12564119http://ubuntuforums.org/showthread.php?t=2127036&p=12564119#post12564119](http://ubuntuforums.org/showthread.php?t=2127036&p=12564119#post12564119http://ubuntuforums.org/showthread.php?t=2127036&p=12564119#post12564119)

---

### Post by poignantprick on 2013-03-19
Yeah, made it through this problem to find another one lying in wait. Is there anything I can learn from those issues? Known causes? As I said, I was copy & pasting commands from a third party site trying to get Adobe Acrobat Reader for Firefox, that didn't work, then i went into trying to get themes. I hit a wall somewhere between not getting Adobe, screwing with themes, and posting this.

---

### Post by ibjsb4 on 2013-03-19
What caused it...Unk, a glitch in the system.

Could it happen again...yes, but unlikely. 

Third party sites can cause you grief.  Check to be sure what your downloading is up to date.  When offered, go for .deb packages just cause that a ubuntu (debian) package.  If you can, see what others have to say about the package.

A good way to search the forums for info:

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by varunendra on 2013-03-19
> **poignantprick said:**
> Is there anything I can learn from those issues? Known causes?
Study the /etc/apt/sources.list file and files in /etc/sources.list.d/ directory. Note their format and syntax.

Initially, that is all there is to learn.

Known causes are almost always either a dead ppa, dead (too old) official repository, error in syntax/spelling while manually adding a ppa, or a temporary server issue.

Before and while studying them, read and use as reference these guides :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

Except in rare cases when an installation/upgrade is interrupted midway, the issues are minor and troubleshooting is very easy if you are familiar with the basic concept of repositories.

Hope that helps, and glad to see you are interested in learning. :)

---

