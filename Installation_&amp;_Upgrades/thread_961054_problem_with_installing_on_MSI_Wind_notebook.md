---
title: "problem with installing on MSI Wind notebook"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Okliw on 2008-10-27
presently Windows XP is installed on this machine and i am trying to intall Ubuntu 8.04 LTS Desktop Edition as an alternative Operating System. so i would like to be able to use them both and eventually one day decide to get rid of Windows...


MSI Wind Notebook has no CD drive, so i prepared an USB Stick as booting device to install from: I made an ISO image from the installation disk and used the UNetbootin program to be able to install Ubuntu from the USB stick after booting from it.

so far so good. Installation starts with stating:

[B]Loading casper/vmlinuz................
Loading /casper/initrd.gz..............................[/B] 

next the ubuntu loading screen appears, but then i get the following system message on the screen:

**udevd-event [1495]: run program: '/sbin/modprobe' abnormal exit**

in the various times i tried to install Ubuntu i got to different results after this. One of the two was the following:

[B]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for build in commands.

(initramfs)[/B]

And then nothing further happened....
in the other case the intallation program starts detecting and  checking the different hardware components. The screen fills with messages of successful detection and configuartion results, but then with 

**Starting Common Unix Printing System: cupsd**

the computer gets stuck. once i have waited close to an hour at this stage without that anything further happened. Though if i press CTR+ALT+DEL the process is interrupted and the intallation routine continues and even gets as far as to return onto the ubuntu loading screen and tell me to reeboot the system for completing the installation.
But when rebooting the systems just starts loading windows XP again, or goes back into the boot menue of the USB stick if i don't pull it out....


As i am a absolute beginner to Linux and also have stopped to try to follow what is going on inside my computer since the times of DOS and WIN 3.11 are over i am right now completely helpless on this problem and already consider just downloading a version of SUSE instead...

if anyone out there has solved this problem before or can help me, i would very happy to hear of it.
Otherwise i will just give up on Ubuntu and give SUSE a shot.

thank you for taking the time to read this post :)

---

### Post by mecannotread on 2008-11-01
Hai,

Instead install 8.04 you should install 8.04.1. But I suggest install 8.10(ibex).

---

