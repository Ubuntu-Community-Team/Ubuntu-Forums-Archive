---
title: "Installing packages offline without gdebi?"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by krlrvr on 2012-09-29
Hello everyone.

I'm attempting to install ubuntu-12.10-beta2-desktop-amd64 on a desktop without Ethernet. It does have a Netgear WNDA3100 dongle. So of course I need to install bcmn43xx64.inf with Windows Wireless Drivers-NDISwrapper. Oh, it's not in there? Okay, that's easy enough. I'll place ndisgtk_0.8.5-1_amd64.deb, ndiswrapper-common_1.57-1ubuntu1_all.deb and ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb on an external drive and install with gdebi package installer. Okay, stop laughing. It's been awhile. So, how can I install gdebi_0.8.5ubuntu1_all.deb and gdebi-core_0.8.5ubuntu1_all.deb without screwing the pooch somehow? Can this be done without gdebi? I'm at a loss. Any help would be vastly appreciated.

---

### Post by zvacet on 2012-09-30
Every deb file can be installed in old fashion way 

```
sudo dpkg -i package_name
```

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box). You may need to install the x64 version.[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

### Post by Mark Phelps on 2012-10-24
While you certainly CAN install deb packages offline, one at a time, unfortunately, Ubuntu is really not designed to do this easily.

If that package is a meta-package, it's likely there will be a LOT of dependencies with other packages.  Installing each one offline could yield additional "dependecies not met" error messages, forcing you to hunt down more and more packages -- until ALL the dependencies are met.

Not saying it can't be done; just saying it can translate into a LOT of work hunting down lots of individual packages.

---

