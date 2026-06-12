---
title: "Network Manager issue on Unattended Install 12.04"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by dougbrown on 2013-02-19
First of all, let me say that I have read post after post trying to find an answer to this problem. Been trying to do an unattended preseed install. Originally wanted to do an unattended OEM install using the Alternate CD. I have found available documentation on this subject to be rather confusing at times. I have pretty much given up trying to do an OEM setup and am now working on setting up with one preconfigured admin account.

 My Issue at this time is the fact that the Wired Network will come up as un-managed after the setup completes.
The Network functions properly during the setup, several packages are downloaded and installed with no problem.
I can go and edit the NetworkManager.conf file afterward, changing managed=false to managed=true, and the network comes right up. 
If I perform a hands on installation on the same machine I do not have this problem. 
I have thought it might be a hardware issue on the particular test machine I am using, so I tried a different machine and the issue repeats on the other machine as well.
I am really left with the feeling that there is something in my preseed file, or missing from it that is causing this to occur. 
Would any one be able to offer a suggestion as to why this is happening?

---

### Post by OpenThinking on 2013-02-20
Hi!

Are the Alternate CD available after Ubuntu 12.04? Because if it's not, this route for unattended installation will be a dead end... I've heard Canoical are going to drop the Alternate CD, but I'm not sure.

---

### Post by dougbrown on 2013-02-20
I used this image..
[http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-alternate-i386.iso](http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-alternate-i386.iso)
old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-alternate-i386.iso

---

### Post by dougbrown on 2013-02-21
BUMP

It can't be this hard to install and expect to find a working network afterward. 
I know the network works, I can fix the issue easily.
What is happening during the unattended install that is different from the hands on install?
I have attached a copy of my preseed file.

---

### Post by steeldriver on 2013-02-21
I'm confused about what the problem is exactly? the 

```

[ifupdown]
managed=false

```entry should have no effect on whether the network comes up or not - only on whether the network-manager service can 'see' connections that are instantiated via the older networking service (/etc/network/interfaces)

AFAIK this is the default config for the current Desktop versions (where network-manager is the default and /etc/network/interfaces only defines the loopback)

---

### Post by grahammechanical on 2013-02-21
I will need some convincing that it is possible to do an unattended installation by means of the alternate installer.

The Network Unmanaged message comes up when Network Manager is not being used to manage the networks.

As has been previously pointed out Network Manager does not use the /network/interfaces file. If the interfaces file has anything other than this

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

then there will be a conflict with Network Manager that will prevent Network Manager from managing the network adapter. Deleting any extra information in the interfaces file will let Network Manager take over the managing of the Network adapter be it ethernet or wireless.

Some people use something like wcid as the network manager

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

That uses the interfaces file and so conflicts with Network Manager. Have you scripted the putting of information into the interfaces file? If you have, then try leaving it out and letting Network Manager do its stuff.

Regards.

---

### Post by dougbrown on 2013-02-21
I'm sorry if I have not been clear about the issue I'm experiencing.
Please allow me to clarify...
!. If I do a manual install I have no problems at all.
2. If I do a preseed install the process goes perfectly up to restarting the system. Network connectivity is fine during the install. 
3. after rebooting following the preseeded install the status of the wired network in Network Manager is unmanaged.and I have no connectivity.
4. if I edit the NetworkManager.conf file as described and restart the service the network everything is ok.

I simply want it such that I do not have to edit the conf file by hand after the installation completes. Well that and that I have a functional network connection of course. :)

---

