---
title: "amd iso ?"
date: 2014-12-03
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2014-12-03
I downloaded the file "ubuntu-12.04.5-desktop-amd64.iso.part" to attempt to install the 64 bit version of 12.04 lts on my system.   Is this download for the AMD processor, as it has the letters amd64 in the file name?  I have an Intel Core 2 Duo.

---

### Post by deadflowr on 2014-12-03
Meaningless.
It'll install on [s]any[/s]most 64-bit system.(It'll install on yours for sure)
It's a name convention, that is all.

Just like i386 is for [s]any[/s]most 32-bit system.(there are probably exception, though I don't know...)
From what I remember, the kernel can no longer even install on a i386 processor...

---

### Post by michael-piziak on 2014-12-03
Thanks

From this version, if I decide to in the future, I can upgrade to 14.04 lts in the software center and have 14.04 lts 64 bit version, right ?
Also, Is this download the same as the "[Ubuntu 12.04.5 alternate (64-bit)]("http://releases.ubuntu.com/12.04/ubuntu-12.04.5-alternate-amd64.iso.torrent")"  just above it at alternative downloads for desktop.  See attached image that I was choosing from.

---

### Post by oldfred on 2014-12-03
The 12.04 was the last to have the alternative desktop installer. It is not gui based, although it is very similar looking.
The alternative installer was for those with desktops more like servers with RAID or LVM which the gui installer did not support. You could use it for a standard desktop installer. Sometimes also needed if major video issues.

With 12.10 they dropped the alternative installer and said to use either 12.04 & upgrade or use server installer if you have RAID or LVM. And they said later they would add LVM & RAID to desktop gui installer.
I now see they do have LVM in current version as an advanced full drive install option. It also is used with full drive encryption. But it still looks like gui Desktop installer only has partial support for RAID so far. 

All Ubuntu installs now install the same underlying Linux system, but each has different GUI and desktop or all the default included applications. But using the repository can install all the gui or applications from any supported Ubuntu version. Usually best if wanting to experiment to have one base working install and then install in another 20 or 25GB / (root) partition another version so you can experiment without creating issues with main working install. But backups are still important.

---

### Post by michael-piziak on 2014-12-03
> **oldfred said:**
> The 12.04 was the last to have the alternative desktop installer. It is not gui based, although it is very similar looking.
The alternative installer was for those with desktops more like servers with RAID or LVM which the gui installer did not support. You could use it for a standard desktop installer. Sometimes also needed if major video issues.

With 12.10 they dropped the alternative installer and said to use either 12.04 & upgrade or use server installer if you have RAID or LVM. And they said later they would add LVM & RAID to desktop gui installer.
I now see they do have LVM in curent version as an advanced full drive install option. It also is used with full drive encryption. But it still looks like gui Desktop installer only has partial support for RAID so far. 

All Ubuntu installs now install the same underlying Linux system, but each has different GUI and desktop or all the default included applications. But using the repository can install all the gui or applications from any supported Ubuntu version. Usually best if wanting to experiment to have one base working install and then install in another 20 or 25GB / (root) partition another version so you can experiment without creating issues with main working install. But backups are still important.

When you say the last to have the alternative desktop installer, is this alternative installer you speak of simply the choice between 32 bit install and 64 bit install when making your Ubuntu OS installation ?

p.s. I'm waiting on someone to bring me a usb thumb drive, so I have some time to ask these questions and make sure I get the install right.

---

### Post by Elfy on 2014-12-03
I assume that the iso is still not called ubuntu-12.04.5-desktop-amd64.iso.part but rather ubuntu-12.04.5-desktop-amd64.iso

If it's still got .part then it'll not work - it's not finished downloading.

---

### Post by deadflowr on 2014-12-03
the alternate installer allows you to tweak the installation a little bit more than the normal installer.
But the 32-bit will only install a 32-bit installation, as does the 64-bit.
From here
[http://releases.ubuntu.com/12.04.5/](http://releases.ubuntu.com/12.04.5/)

> [h=3]Alternate install CD[/h][COLOR=#000000][FONT=Ubuntu]The alternate install cd allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:[/FONT][/COLOR]

[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installs on systems with less than about 384MiB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]
[COLOR=#000000][FONT=Ubuntu]In the event that you encounter a bug using the alternate installer, please file a bug on the [debian-installer]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+filebug") package.[/FONT][/COLOR]




---

### Post by michael-piziak on 2014-12-03
> **Elfy said:**
> I assume that the iso is still not called ubuntu-12.04.5-desktop-amd64.iso.part but rather ubuntu-12.04.5-desktop-amd64.iso

If it's still got .part then it'll not work - it's not finished downloading.

The file name in my download folder is now "ubuntu-12.04.5-desktop-amd64.iso"    file size is 794.8MB 
So I think I'm good to go.

Thanks !

---

### Post by grahammechanical on 2014-12-03
There are minimum system requirements for the installation of Ubuntu. A machine might have enough system memory (RAM) to run Ubuntu but not enough RAM to install Ubuntu because the installer makes use of RAM. In this case we use the Alternative installer CD. But Ubuntu does not provide an alternative installer CD for versions of Ubuntu that were released after Ubuntu 12.04 or to put it another way, that were released after April 2012.

> [COLOR=#333333][FONT=Ubuntu]You may not wish to always use the standard LiveCD, because[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]it may so happen occasionally that _your computer is not able to run the standard Desktop installation CD because it does not meet the hardware requirements_, or the required drivers are missing from the standard LiveCD. The LiveCD is designed to keep most basic hardware in mind, but there are a few that are bound to be absent from it.[FONT=inherit][/FONT]
[*=left][FONT=inherit][FONT=inherit]**Or**[/FONT], you may simply prefer to [FONT=inherit]**install a more customized version of Ubuntu**[/FONT] different from the standard install depending on your taste.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]Ubuntu has you covered in this regard, and towards this end you can use an **Alternate Installation CD** instead - refer to [Getting Ubuntu]("https://help.ubuntu.com/community/GettingUbuntu") page for download locations. The Alternate CD allows more advanced installation options which are not available with the Standard LiveCD.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]




[https://help.ubuntu.com/community/Installation#Minimal%20installations](https://help.ubuntu.com/community/Installation#Minimal%20installations)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

If the system memory (RAM) is so small as to make it difficult to install Ubuntu then running Ubuntu would not provide such a good user experience. It maybe better to install a flavour of Ubuntu such as Lubuntu or Xubuntu which have lower system requirements.

Regards.

---

### Post by ajgreeny on 2014-12-03
> **michael-piziak said:**
> The file name in my download folder is now "ubuntu-12.04.5-desktop-amd64.iso"    file size is 794.8MB 
So I think I'm good to go.

Thanks !It is still worth checking the md5sum of your iso file against the listed values at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

