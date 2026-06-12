---
title: "Upgrade from 21.04 to 21.10 gives no effect."
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by carlo-sanguineti on 2021-10-19
Hello,
I'm really sorry to bother you since each time I try an upgrade I have some problem.


First I clicked in the usual Upgrade button without any result. The machine does nothing.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289310&stc=1[/IMG]
So, since I had problems before, I tried this sequence on Terminal:

[HTML]sudo apt update && sudo apt upgrade[sudo] password for carlos: Hit:1 http://archive.canonical.com/ubuntu hirsute InReleaseHit:2 http://archive.ubuntu.com/ubuntu hirsute InReleaseHit:3 http://archive.ubuntu.com/ubuntu hirsute-updates InReleaseHit:4 http://archive.ubuntu.com/ubuntu hirsute-backports InReleaseHit:5 http://archive.ubuntu.com/ubuntu hirsute-security InReleaseHit:6 http://archive.ubuntu.com/ubuntu hirsute-proposed InReleaseReading package lists... DoneBuilding dependency tree... DoneReading state information... Done1 package can be upgraded. Run 'apt list --upgradable' to see it.Reading package lists... DoneBuilding dependency tree... DoneReading state information... DoneCalculating upgrade... DoneThe following packages have been kept back:  dh-python0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/HTML]

then

[HTML]update-manager -dChecking for a new Ubuntu releasePlease install all available updates for your release before upgrading.[/HTML]

[HTML]sudo do-release-upgrade -dChecking for a new Ubuntu releasePlease install all available updates for your release before upgrading.[/HTML]

[HTML]sudo do-release-upgradeChecking for a new Ubuntu releasePlease install all available updates for your release before upgrading.[/HTML]

[HTML]sudo apt-get updateHit:1 http://archive.canonical.com/ubuntu hirsute InReleaseHit:2 http://archive.ubuntu.com/ubuntu hirsute InReleaseHit:3 http://archive.ubuntu.com/ubuntu hirsute-updates InReleaseHit:4 http://archive.ubuntu.com/ubuntu hirsute-backports InReleaseHit:5 http://archive.ubuntu.com/ubuntu hirsute-security InReleaseHit:6 http://archive.ubuntu.com/ubuntu hirsute-proposed InReleaseReading package lists... Done[/HTML]

[HTML]sudo apt-get upgradeReading package lists... DoneBuilding dependency tree... DoneReading state information... DoneCalculating upgrade... DoneThe following packages have been kept back:  dh-python0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/HTML]

[HTML]sudo do-release-upgradeChecking for a new Ubuntu releasePlease install all available updates for your release before upgrading.[/HTML]

[HTML]sudo apt full-upgradeReading package lists... DoneBuilding dependency tree... DoneReading state information... DoneCalculating upgrade... DoneThe following packages have been kept back:  dh-python0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/HTML]

[HTML]sudo apt update && sudo apt dist-upgradeHit:1 http://archive.ubuntu.com/ubuntu hirsute InReleaseHit:2 http://archive.canonical.com/ubuntu hirsute InReleaseHit:3 http://archive.ubuntu.com/ubuntu hirsute-updates InReleaseHit:4 http://archive.ubuntu.com/ubuntu hirsute-backports InReleaseHit:5 http://archive.ubuntu.com/ubuntu hirsute-security InReleaseHit:6 http://archive.ubuntu.com/ubuntu hirsute-proposed InReleaseReading package lists... DoneBuilding dependency tree... DoneReading state information... Done1 package can be upgraded. Run 'apt list --upgradable' to see it.Reading package lists... DoneBuilding dependency tree... DoneReading state information... DoneCalculating upgrade... DoneThe following packages have been kept back:  dh-python0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/HTML]

[HTML]update-manager -cChecking for a new Ubuntu releasePlease install all available updates for your release before upgrading.[/HTML]

[HTML]sudo sed -i 's/groovy/hirsute/g' /etc/apt/sources.list[/HTML]

[HTML]sudo apt updateHit:1 http://archive.ubuntu.com/ubuntu hirsute InReleaseHit:2 http://archive.ubuntu.com/ubuntu hirsute-updates InReleaseHit:3 http://archive.ubuntu.com/ubuntu hirsute-backports InReleaseHit:4 http://archive.ubuntu.com/ubuntu hirsute-security InReleaseHit:5 http://archive.canonical.com/ubuntu hirsute InReleaseReading package lists... DoneBuilding dependency tree... DoneReading state information... Done1 package can be upgraded. Run 'apt list --upgradable' to see it.[/HTML]

Finally, I wanted to do a similar command to
[HTML]sudo sed -i 's/groovy/hirsute/g' /etc/apt/sources.list[/HTML]
but for Impish Indri, but I don't know the command line.
I wanted to do this to know what package are still to upgrade.

If someone that had the patience to read until this, I would be glad if he/she could help me.

Thank in advance,

Carlo

---

### Post by Impavidus on 2021-10-20
> **carlo-sanguineti said:**
> 

```
The following packages have been kept back: dh-python
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

You must get that package either upgraded or removed before you can start the release upgrade. If you try to brute force a release upgrade anyway (for example, using your sudo sed -i 's/... command), you'll probably end up with an even more broken system.

What do you get from this:```
sudo apt update
apt-cache policy dh-python
sudo apt upgrade dh-python
```

---

### Post by carlo-sanguineti on 2021-10-20
Your suggestions worked perfectly!

Thank you very much!

Carlo

---

