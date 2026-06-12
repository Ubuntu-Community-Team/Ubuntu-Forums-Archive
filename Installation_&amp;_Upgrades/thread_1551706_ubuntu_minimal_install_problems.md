---
title: "ubuntu minimal install problems"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by Joe Awsome on 2010-08-12
I have just installed a fresh server install on my old HP Pavilion N3390 (P3 @ 600Mhz, 128Mb ram, 10gig hdd) trying to do a custom install on it. It seemed simple enough until I hit trying to install LXDE on it. The reason for this is that there was some bug on the lubuntu live cd where it wouldn't get past a certain process and came up with a stupid general warning. I've tried to apt-get everything but it always comes up with
```
joe@CrapTop:~$ sudo apt-get install lxde
[sudo] password for joe:
Reading Package Lists... Done
Biulding dependency tree
Reading state information... Done
E: Couldn't find package lxde
joe@CrapTop:~$
```
I think that the problem here is network settings, I don't think I have a DHCP server because it won't auto detect my home network, thus no package install.

---

### Post by zvacet on 2010-08-13
Under system>admin>software sources check all under Ubuntu software and first two under updates tab.Reload.If you can browse net then everthing is fine with your connection.If you still have problems,just let us know.

---

### Post by Joe Awsome on 2010-08-13
sorry for not explaining my problem better, all i have is CLI (command line interface) like in a terminal on a regular ubuntu install. I need to be able to set up my network only using the command-line/terminal. I did a bare-bones server install on my old hp CrapTop so i could do a simple/minimal install, the only problem is that i can't install a GUI (graphical user interface) because i don't know how to set it up on a wired home network. Once i get lxde installed i can install ndiswrapper for my wireless usb dongle. i just need to know how to get my network setup using the command-line. any and all help is greatly appreciated, and sorry i didn't explain it better the first time zvacet, but thanks anyways.

---

### Post by davidmohammed on 2010-08-13
I've not used the minimal install myself, but it looks like from the error message that the respository information needs to be updated - have a look [here]("https://help.ubuntu.com/community/Repositories/CommandLine") for the explanation.

---

### Post by snowpine on 2010-08-13
You need more RAM (512mb is my recommendation for anything in the 'buntu family) or a lighter distro such as Puppy or the 'loram' flavor of SliTaz.

With that being said, the typical way to connect to wired ethernet from the command line would be:

```
sudo dhclient
```

Followed by:

```
sudo apt-get update
sudo apt-get install lxde
```

This is assuming you can get more RAM, of course. :)

---

### Post by Joe Awsome on 2010-08-15
I'm getting nowhere with any of those commands. when i try to setup the network it keeps telling me there is no dhcp found, and bash says that i don't even have an /ect folder on my HDD. I think I will try the other OS you suggested.

---

### Post by phillw on 2010-08-16
Hi,

if you're on a low RAM machine, I'd really suggest that you go via the [Minimal Installation](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall) method. Also, there is a known bug on the self test of the lubuntu CD, there is a work around for [Check 10.04](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/CheckCD) and [Check 10.10](https://wiki.ubuntu.com/Lubuntu/Developers#Check downloaded image file and CD) The minimal iso install should automatically find your ethernet connection, although you will need to follow the work-around to have it managed (this does not stop it working).

Regards,

Phill.

---

### Post by Joe Awsome on 2010-08-17
my downloaded iso seems to be fine right now, not sure about the cd because that code doesn't work on my machine. looks like it loads the disk in /media/disk_ folder instead. my machine is just wierd, it's not ur fault. thanks for the links anyways, but i don't think i have dhcp setup on my home network. I'll have to look into that (would i configure that through my wireless router?).

---

