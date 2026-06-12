---
title: "Upgrading from 11.04 to current."
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by ddevore on 2013-08-02
I guess I put off upgrading my 11.04 server a little too long and now it is out of support. I finally got it to do the apt-get by changing the repository names but I need to know if I can upgrade the release to something more current, I really don't want to reinstall.

---

### Post by Frogs Hair on 2013-08-02
That has worked for some people but there are no guarantees . If you use a CLI sever installation (no desktop environment ) it would make the process less complicated.    [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by sudo san on 2013-08-03
If you want to jump a few releases, then be prepared to take the risk that it may not boot or work properly. If you are using a server, I would suggest upgrading to precise (12.04) but you could upgrade to raring (13.04). Here's how:
```
sudo sed -i 's/natty/raring/g' '/etc/apt/sources.list'
```
You will then need to change the repositories for any ppas by editing any file in the /etc/apt/sources.list directory. Change any instance of natty to raring. Than you can update and then uupgrade. 
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo update-grub
sudo reboot
```

I do not guarantee that this will work but I'd imagine it should. If you do attempt this, I strongly suggest creating something like creating a disk image file of the drive and then you could revert back the upgrade goes wrong. 

Happy upgrading!:P

---

### Post by islandBilly on 2013-08-03
If I may jump in on this, I too have been running 11.04, but on an Acer Aspire One netbook, and had decided not to upgrade until I got a new machine; but what can I say? The phone/convergence thing got me excited and I have been running 13.10 live from a usb stick. It seems to work fine, but does not have more than read permission on my 11.04 home folder. I seem to remember reading about this last year, so I think it's on purpose, even though the live version can write to the Win 7 partition, right? I have a dual-boot system. Sooo, if I try to install 13.10, will it clobber my 11.04 home partition? I would make a backup of it anyway, but what can I expect? Is it really better to go through all the upgrades?

---

### Post by sudo san on 2013-08-04
> **islandBilly said:**
> If I may jump in on this, I too have been running 11.04, but on an Acer Aspire One netbook, and had decided not to upgrade until I got a new machine; but what can I say? The phone/convergence thing got me excited and I have been running 13.10 live from a usb stick. It seems to work fine, but does not have more than read permission on my 11.04 home folder. I seem to remember reading about this last year, so I think it's on purpose, even though the live version can write to the Win 7 partition, right? I have a dual-boot system. Sooo, if I try to install 13.10, will it clobber my 11.04 home partition? I would make a backup of it anyway, but what can I expect? Is it really better to go through all the upgrades?
The convergence thig is just to bring Ubuntu to phones and tablets. I'm not sure why it won't write to your home folder, maybe it is an encrypted partition? My home partition is a separate partition to my root partition, t this is the same case with you, you could wait for 13.10 to come out, install to your root partition and set your home partition to be used as your home partition, but do not format it. But you will need to format the root filesystem. A really easy way would be to use the commands I gave you as an example, change raring to saucy and then upgrade to it. And of course back up before you do this.

Now you have two choices, install to root partition or upgrade. Please let us know how you get on with it.

---

### Post by islandBilly on 2013-08-05
I was thinking over the options, and a little puzzled about the thing you said about "wait for 13.10 to come out", when duh! Dawn breaks on Marble Head (that's an old New England saying). I had installed what pendrivelinux labeled as 13.10 desktop, but we it's only august, so this is an unstable version in the best case. I have now installed 13.04 on my usb stick and am going to spend some time using it. I will be traveling and will not have reliable internet for the next month or so. Then my plan at this point is to go through all the upgrades when 13.10 comes out. I'll let you know some time in October ;)

Thanks. By the way, my home partition is not encrypted, and is separate from the root, so I still do not know why this live version could not write to it. Maybe the 13.04 version will.

---

