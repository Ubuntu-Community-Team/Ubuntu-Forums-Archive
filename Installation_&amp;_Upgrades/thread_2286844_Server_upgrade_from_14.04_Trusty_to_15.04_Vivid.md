---
title: "Server upgrade from 14.04 Trusty to 15.04 Vivid?"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by gurabli on 2015-07-15
Hi,

I'm running a small home server with Ubuntu Server 14.04 (Kernel updated to Linux 3.19.0-22-generic). Actually it is working fine, but I would prefer to upgrade to Vivid, for one reason because the systemd, and to get a little more familiar with the new version as I'm considering to use it on my new htpc too running Kodi with new Intel Braswell SoC.

AFAIK, the upgrade is not complicated, I should do the following:

```
sudo apt-get install update-manager-core

sudo nano /etc/update-manager/release-upgrades
```

Change:

 Prompt=LTS to Prompt=normal

```
sudo do-release-upgrade -d
```

It will first upgrade me to 14.10 Utopic, If I'm not mistaken, then to 15.04 as I can' jump versions. 

Questions:

1) I have compiled VDR Server with plugins, openVPN client, and some other stuff on Trusty. Will these work on Vivid or I will most likely need to recompile everything after upgrade?

2) I have configured upstart scripts for each, tried to replace upstart.d in every case I managed (VDR, Deluge, Crashplan, openVPN, PlexMedia Server, Sonarr, Flexget, CouchPotato, etc) and everything is working fine. What will happen with these upstart scripts once the system is upgraded to Vivid? 
-> converted to systemd during upgrade?
-> remain functional as upstart scripts and only newly installed stuff will use systemd?
-> they will not start, I will need to create systemd for each (in this case it would be better to create them before upgrade process)?
-> I can install upstart-sysv package and revert back to upstart scripts (by this loosing systemd)?

I believe most of you will recommend to stick with the 14.04 LTS and you are probably correct. After all, this is a server and it's doing its job perfectly, why touch something that is working fine? However, I'm tempted to try Vivid. Maybe I should make a backup and do the upgrade on the backup? Anyway, I will really like to know the answers to these questions.

Thank you for your support!

---

### Post by Bucky Ball on 2015-07-15
I can see where you're coming from, but LTS is recommended for servers. Once you go down the interim path, you are stuck there until 16.04 LTS. 15.04 dies in January 2016 at which time you'll need to install 15.10 which will die nine months later. Then you'll be ready for 16.04 LTS which will be supported for five years, until 2021.

I suggest that if you just want to tweak about with systemd, install 15.04 on another partition or as a virtual machine and do it there. Very few server folk would want the uncertainty of installing new interim releases every six months, or even upgrading their servers every six months. Pretty rare.

PS: Kodi works just fine in 14.04 LTS. I have it running faultlessly on an Odroid as we type (in case you are under the impression you need 15.04 or systemd for a smooth ride with it). Good luck. :)

---

### Post by gurabli on 2015-07-15
Many thanks for pointing me to the correct direction. I was hesitating to upgrade, but though it would not harm as it is after all a home small server and not the main centre of a huge company. But anyway, you are correct, if everything works fine (and it does) why should I bother. 

I will do some testing on another partition or VM and see the systemd part. 

Just curious: if I had decided to upgrade, the compiled on Trusty programs would work on Vivid?

EDIT: I have already upgraded to Kernel 3.19.0-22-generic which is great since it support my DVB-S2 card and I don't need to compile the dvb drivers each time after a kernel update.

---

### Post by Bucky Ball on 2015-07-15
> **gurabli said:**
> 
Just curious: if I had decided to upgrade, the compiled on Trusty programs would work on Vivid?

Good question. Possibly not if they were compiled specifically for Trusty and that kernel. If they are working in the Vivid kernel already, though, possibly. One I can't answer.

---

### Post by SeijiSensei on 2015-07-16
If you want to get experience with systemd, install VirtualBox, then install CentOS 7 in a virtual machine.  It uses systemd pretty much everywhere.

---

