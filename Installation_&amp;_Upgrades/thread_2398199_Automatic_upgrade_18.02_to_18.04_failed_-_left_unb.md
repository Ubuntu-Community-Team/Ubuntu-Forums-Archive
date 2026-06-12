---
title: "Automatic upgrade 18.02 to 18.04 failed - left unbootable"
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by fwrun2011 on 2018-08-08
Hi;
I was running Ubuntu 18.02 in a 3-boot system (Ubuntu 18.xx, Windows 7, Windows 10) which boots into Grub2 (I think it's Grub2, and not grub legacy).
A week or so ago, I booted into Ubuntu 18.02 for the first time in a while (I was running mostly Windows 7).
It booted fine, but a notice popped up on the desktop informing me that there was an upgrade for my OS.
I chose to do the upgrade directly from the desktop.
There was a download, then the install process began.
Apparently, the install never completed, and either I shut the machine off or it shut off by itself; I don't recall.
The next time I booted the machine, it was into Windows 7.
I found that I had no network connectivity in Windows 7. I didn't think this had anything to do with the failed upgrade in Ubuntu, but now I'm not so sure. Apparently, there was a change to my timezone in Windows 7. That is why the network would not connect. When I reset the timezone to my correct one, I restored network connectivity.

The next time (it might have been a few days) I tried to boot into Ubuntu, there was a black screen with a lot of info on it. I don't recall the exact message that was on the screen, but it had the words "Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0).

I did some Googling (from Windows), and just selected the next oldest Ubuntu on the grub list. It booted fine, and I did the upgrade manually from the terminal. That worked fine and I now have the latest distro installed.

Is this a problem with my install, or is there a bug with the auto-upgrade feature in Ubuntu 18.xx?

Thanks for your help

FW

---

### Post by oldfred on 2018-08-08
There is not a 18.02, were you upgrading from 16.04 or 17.10?
What brand/model system? What video card?

Did you have any proprietary drivers or ppa for non-standard software. Those are usually the issue on upgrading and must be removed before an upgrade.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

