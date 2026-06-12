---
title: "KDE 4 upgrade problem"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by brett611 on 2008-04-04
Had Kubuntu 7.10, 32 bit.  worked awesome.  I got 'greedy' and decided to try to upgrade to KDE 4.  Everything looked fine until I rebooted.  Now I'm fubar'd.  I get the black screen of death with the following message:

[31.147012] Kernal Panic - not syncing:VFS: unable to mount root fs on unknown-block(0,0)

I've tried loading in various recovery modes to no avail.  Haven't tried with the kubuntu cd yet.

Any help is appreciated.

---

### Post by PmDematagoda on 2008-04-04
The problem cannot be directly related to KDE4 since it is something with the kernel, which means that you may have messed around with some kernel settings or packages related to the kernel.

In your case, you would have to use the Kubuntu Live CD, and after booting to the Live CD can you post the output of:-
```
cat /*kubuntu-root*/boot/grub/menu.lst
```
kubuntu-root is replaced by the mount point of your Kubuntu installation's root folder.

---

### Post by brett611 on 2008-04-05
Thanks.  I reinstalled from scratch in a fit of rage at my stupidity.  I tried loading the live cd but wasn't able to do much.  For what its worth, here are the verbatim instructions that I followed:

[http://news.softpedia.com/news/KDE-4-0-3-and-Kubuntu-Packages-Are-Now-Available-82366.shtml](http://news.softpedia.com/news/KDE-4-0-3-and-Kubuntu-Packages-Are-Now-Available-82366.shtml)

specifically:
How to install or upgrade?

• If you have a computer powered by Kubuntu 7.10, then follow the instruction below to upgrade to KDE 4.0.3:

- Open the Software Sources application, go to the "Third-Party Software" tab, click the 'Add' button and paste the following line:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

- Click OK and close the Software Sources window. Reload the information about new software.

- Open a terminal and type:

sudo apt-get update
sudo apt-get upgrade

- When the upgrade is over, reboot your computer and you'll have KDE 4.0.3!

---

