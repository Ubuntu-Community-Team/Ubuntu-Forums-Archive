---
title: "problem with downloading repository information"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by smilescraz on 2011-12-16
I'm having a problem updating my system. Every time I try it comes out with: 
"Failed to download repository information. Check your Internet connection."
I am connected to the internet I can browse the web perfectly fine.

The description in the error message is thus:
W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

im at a loss what to do any help would be appreciated. XD

---

### Post by 2F4U on 2011-12-16
It complains about a cdrom. Is that cdrom in the machine? If not I would disable that repository.

---

### Post by Old_Grey_Wolf on 2011-12-16
Goto the Update Manager then Ubuntu Software tab then remove the check next to the Cdrom.

---

### Post by smilescraz on 2011-12-17
> **2F4U said:**
> It complains about a cdrom. Is that cdrom in the machine? If not I would disable that repository.

so how would I do that? Iv gone into system settings > software sources  and I don't see any tab or check box or anything to do with cdrom

oh and there is no cd in the drive and I have never used a cd to update other than when I installed my os

---

### Post by bashishtha on 2011-12-17
Somewhat similar problem to this, when i press check button on update manager,  "Failed to download repository information. Check your Internet connection."
I am connected to the internet I can browse the web perfectly fine.

And I get following message.

W:Failed to fetch 
[http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

-----------

Please help to restore update manager to normal.

---

### Post by Old_Grey_Wolf on 2011-12-17
> **bashishtha said:**
> 

W:Failed to fetch 
[http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Ubuntu 11.10 does not have a PPA for webcontentcontrol at launchpad. Remove the PPA from the sources list.

---

### Post by smilescraz on 2011-12-21
:confused: i still am having this problem with updating. my system still updates and collects updates but i get this stupid error message every time i update... dos anyone know how to get rid of it? :confused:
error message:
Failed to download repository information

Check your Internet connection.

details:
W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Old_Grey_Wolf on 2011-12-21
> **smilescraz said:**
> :confused: 

Goto the Update Manager then Ubuntu Software tab then remove the check next to the Cdrom. See attachment.

---

### Post by smilescraz on 2011-12-22
that field has no check-boxes

it says "please insert medium into drive"

I would post a screen shot but I haven't figured that out yet

---

### Post by spcwingo on 2011-12-23
Could you please post the output of this command ran from a terminal:

```
cat /etc/apt/sources.list
```

---

### Post by smilescraz on 2011-12-23
> **spcwingo said:**
> Could you please post the output of this command ran from a terminal:

```
cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security multiverse

# Remastersys
# deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
# deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
# deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
# deb [https://jeff-maddriver:8M9T8nXFzT3m5M3BJN0J@private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu](https://jeff-maddriver:8M9T8nXFzT3m5M3BJN0J@private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu) oneiric main
# deb-src [https://jeff-maddriver:8M9T8nXFzT3m5M3BJN0J@private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu](https://jeff-maddriver:8M9T8nXFzT3m5M3BJN0J@private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu) oneiric main



I think I figured it out you gave me an idea and I checked my other software tab and removed everything I didn't know what it was for and the problem is now fixed thx everyone for your patience.

---

