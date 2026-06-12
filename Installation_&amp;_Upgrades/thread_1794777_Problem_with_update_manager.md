---
title: "Problem with update manager"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-07-01
You may remember how a while back I had this notice pop up saying, "Requires installation of untrusted packages" every time I tried to install something in the USC. I still have this problem, but I got around it by using terminal commands to install things. Well, now I've got the same problem with the update manager. Is there a terminal command to install updates? Just "update", or something a little longer?

---

### Post by mörgæs on 2011-07-01
Yes:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

There is more on apt in the manual in my signature.

---

### Post by Rubi1200 on 2011-07-01
Yes, there is:

```
sudo apt-get update && sudo apt-get upgrade
```The first part of the command updates the packages in the repositories you have enabled in your sources.list, the second carries out any upgrades of packages. The && means carry out the second command if the first one completes successfully. 

See here for more:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by TimmyK. on 2011-07-02
Doesn't seem to be working. When I go the update manager, it still says that all these files have no been downloaded.

---

### Post by mörgæs on 2011-07-02
Please post the exact error message.

---

### Post by TimmyK. on 2011-07-02
There is no error message. I just enter these commands in the terminal, and when I open the update manager it still says I have all these uninstalled updates.

---

### Post by mörgæs on 2011-07-03
Have you tried to change mirror?

---

### Post by TimmyK. on 2011-07-07
No. How would one go about doing that?

---

### Post by Rubi1200 on 2011-07-08
The screenshot here shows for 10.04 but the idea is the same:

**Ubuntu Software Tab**

 
[LIST]
[*][IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]
[/LIST]
Change whatever you have set under Download from to the Main Server and then try things again.

Let us know what happens.

If this still doesn't work, then open a terminal and post the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by imradzi on 2011-07-27
Hi,
I am having the same problem. Using the apt-get clean and update. Got this error message:

Fetched 869 B in 13s (65 B/s)
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release: Unknown error executing gpgv
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release: Unknown error executing gpgv

how to fix this?

thanks.

---

### Post by imradzi on 2011-07-27
This is the content of my sources.list:


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

