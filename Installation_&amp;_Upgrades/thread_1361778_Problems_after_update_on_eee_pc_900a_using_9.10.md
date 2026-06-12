---
title: "Problems after update on eee pc 900a using 9.10"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by phdn on 2009-12-22
Hi,

I've installed Ubuntu 9.10 (desktop - not netbook remix) on my Asus eee pc 900A which is an Intel Atom based netbook.

Up to now I've had few problems and I think that overall 9.10 is the best Linux that I've used to date.

However, a few days ago after installing some updates as recommended by the update manager I have the problem that when I log in to my account which has super user privileges, I no longer have connection to my wireless network (haven't tried ethernet cable yet) and there is no network manager applet.

The strange thing is that other user accounts (non-super user) do have the network manager applet and network connectivity.

Another side effect is that the "click to make changes" button does not work in the Users Settings dialogue box so I can't add another super user account (at least not from the dialogue - command line shouldn't be a problem).

I can however still run sudo so it doesn't appear to be an issue with revoked privileges and since the networking works for other users it does not appear to be a networking issue either.

Has anybody else seen something similar? Does anybody have any suggestions about how to fix this problem?

---

### Post by Sven6210 on 2009-12-23
I do agree, I also think that Karmic Koala is the best Linux I used so far. I have installed the UNR on my Asus EeePC 900a and it works very good. However I di some small changes to make also the microphone and the WiFi to work as it should work.

What I do not understand is hy you even want to log on with an account ith super user rights? I never ever did that and I do not intend to do so. Whenever I need super user rights I obtain it only for the transaction and I hardly recommend you to do so as well.

Details for the to patches I mentioned:

**1. Microphone**

Enter 'sudo gedit /etc/modprobe.d/alsa-base.conf'
Go to the bottom of the text file
Add the following two lines:

===start here===
# eeePC 900a patch
options snd-hda-intel index=0 model=quanta
===end here===

Save the file and close the editor (gedit).

Restart the computer

[B]2. Wireless
[/B]
Enable the reactivation of wireless when switching it on and off with the hot/function key

You have to pass the following parameters to the kernel command line:
pciehp.pciehp_force=1 pciehp.pciehp_poll=1 by doing the following steps:

sudo gedit /etc/default/grub

edit the line with GRUB_CMDLINE_LINUX_DEFAULT:

GRUB_CMDLINE_LINUX_DEFAULT=”pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash”

sudo update-grub2

After you restart your computer you can switsch WiFi on an off without problems.

---

