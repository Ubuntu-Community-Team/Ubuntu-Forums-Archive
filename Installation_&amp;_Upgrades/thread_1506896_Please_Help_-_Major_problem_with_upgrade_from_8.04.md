---
title: "Please Help - Major problem with upgrade from 8.04 LTS to 10.4 LTS"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2010-06-10
It would seem that my upgrade from version 8.04 LTS to version 10.4 LTS has gone wrong. When it rebooted, almost everything was the same as it was before the upgrade. The exception that I can see is that the background has gone from the standard 8.04 background to what appears to be a default which is a mountain with the moon at the top left of the image.
The command that I used to upgrade was directly from the Ubuntu upgrade web page under the heading 'Upgrade from 8.04 LTS to 10.04 LTS – Network Upgrade for Ubuntu Desktops (Recommended) – which is:
Press Alt+F2 and enter update-manager –devel-release
Everything appeared to work OK until the reboot.
To try to get things going again I tried again with the same command. This is what I got
**Not all updates can be installed**

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu

With these buttons

Partial Upgrade      Close

When selecting Partial Upgrade the system appears to go do the job (it shows a dialog with updating and so on) for around 10 seconds then goes quiet. Even a reboot seems to leave things as they were.

I'm no guru so I don't have much of an idea what I can do to fix the problem.

---

### Post by SVEN1 on 2010-06-10
Did you upgrade right to 10.04 from 8.04? If so that is probably your problem.

You have to upgrade thru each new release 8.04-8.10-9.04-9.10-10.04

or do a complete new fresh installation of 10.04

---

### Post by bobmac on 2010-06-11
Sven1,

I don't think that you info is correct. As I mentioned in my initial post I checked with the Ubuntu upgrade page which says:

'Upgrade from 8.04 LTS to 10.04 LTS &#8211; Network Upgrade for Ubuntu Desktops (Recommended)

The command being:

Press Alt+F2 and enter update-manager &#8211;devel-release

---

### Post by oldfred on 2010-06-11
LTS to LTS is the only time you can skip versions on upgrades.

Can you boot and is it booting your 8.04 still or had it updated somethings and booting 10.04?

upgrade can only update existing packages and add new ones 
The command to upgrade to next release version is "sudo do-release-upgrade" (CLI) or "gksudo update-manager -d" (GUI).

If partially updated
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

