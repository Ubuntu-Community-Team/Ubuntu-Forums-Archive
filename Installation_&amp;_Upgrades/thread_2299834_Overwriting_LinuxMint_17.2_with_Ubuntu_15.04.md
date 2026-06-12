---
title: "Overwriting LinuxMint 17.2 with Ubuntu 15.04"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by greigpj2 on 2015-10-21
I have a dual boot. Windows 10 and 17.2 Linuxmint. I like Linuxmint but I want to take part in the convergence of the phone/tablet/PC and so far it's limited to Ubuntu from what I can see.

Grub controls the boot menu with Mint at the top (good cause I use it most of the time).
Windows 10 I use the down arrow to access.
Everything runs smoothly.

I just want to overwrite Mint with Ubuntu and the swap partition for Mint should become the swap partition for Ubuntu 15.04.
Is this doable?
Will Ubuntu replace Mint in the Grub Menu?
I still want to be able to access Windows 10 through Grub as I can now.

Another question. If I use Ubuntu 15.04 are upgrades done in place? (I have a penchant for staying with the latest).
This is a non Uefi system. Built it myself and it still runs like a charm.

Thanks for any assistance.

---

### Post by james_moore2 on 2015-10-21
1. It should be doable, when installing just install over the Linuxmint partition.
2. It should stay, I think Linux is always first with the boot loader.
3. Define upgrades done in place please.

---

### Post by greigpj2 on 2015-10-21
I just mean that when the software bumps up from say 15.04 to 15.10 or to say 16 that I can do that without reinstalling from scratch. LinuxMint will say that an upgrade is available from 17.1 to 17.2 and if you select to do that it goes ahead and does. No re-installation necessary.

---

### Post by james_moore2 on 2015-10-21
The way I understand it is that, you can always upgrade Ubuntu without reinstalling but you have to reinstall to downgrade.

---

### Post by ajgreeny on 2015-10-21
To move from Linux Mint to Ubuntu you will have to use the "Something Else" option at partitioning stage of the installation and then overwrite the Mint partrition(s) with Ubuntu.

You can then upgrade from 15.04 to 15.10 (why not wait a few days and just install 15.10?) and then from 15.10 to 16.04.  16.04 will be the next LTS version and it will be possible two years on from that to upgrade in one step to 18.04, also an LTS version.

I have to admit that I have never upgraded from version to version and have always clean installed; I have a separate /home partition which makes clean installs much easier, but many other users do upgrade with the upgrade-manager successfully.

---

### Post by grahammechanical on 2015-10-21
The installer will detect an existing Linux swap partition and use it. You will not have 2 swap partitions of the hard drive unless you create another one and specifically tell the Ubuntu installer to use it.

I do not want you to be misinformed. Ubuntu 16.04 will not be a "converged" version of Ubuntu. It will be a traditional Ubuntu that runs on the Xserver and the Compiz compositor and use Unity 7 as the user interface. In this sense it will be like Ubuntu 14.04 and 15.04 and 15.10. All the packages will be deb packages and will be updated as packages using apt-get.

At the moment the main development effort for convergence is aimed producing a Ubuntu phone that can become a Ubuntu desktop when it is connected to keyboard, mouse and monitor. Back in May of this year Mark Shuttleworth announced that this year there will be a Ubuntu mobile device that will be "a desktop in your pocket" and it will be a Ubuntu Phone. There are 11 weeks left to this year.

Regards.

---

