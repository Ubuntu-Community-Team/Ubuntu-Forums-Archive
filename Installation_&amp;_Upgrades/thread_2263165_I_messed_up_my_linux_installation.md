---
title: "I messed up my linux installation"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by johnarthurbishop on 2015-01-30
Hello everyone

I've been using Ubuntu for a bit but I have, so far, been able to find a way to fix all of my issues through other user's posts.

I updated a video driver and hard reset my computer during the reboot process which stopped my computer from booting up correctly. I know that this was a really stupid to thing to do after installation, but I tried booting into recovery mode which wasn't able to successfully fsck. It would stop working very early on. Eventually I booted up a previous version on the same page and did sudo apt-get upgrade.

Now my computer boots up fine, although I get a Boot had 0 bytes of space left warning. So I tried using apt-get's autoremove, their update, upgrade. I also tried using dpkg --configure -a beforehand I keep on getting the same errors. I encounter errors while processing linux-image-extra-3.13.0-44-generic, linux-image-generic, linux-generic, and initramfs-tools.

Is there anyone out there that can help me out?

---

### Post by ajgreeny on 2015-01-30
Let's see the output of ```
ls /boot | grep vmlinuz
``` which will show the kernel versions you have installed; it sounds as if you have a separate /boot partition which is full.

Autoremove will sometimes solve that problem, but other times, for no obvious reason, does not.

---

### Post by kc1di on 2015-01-30
I know lots of people do not like ubuntu tweak - but I find it's janitor does a good job of removing old config and kernel files without breaking the system. 
you may want to download and install it and run it's janitor see if it clears the space for you. 
you can find it [here:]("http://ubuntu-tweak.com/")

---

### Post by ajgreeny on 2015-01-30
> **kc1di said:**
> I know lots of people do not like ubuntu tweak - but I find it's janitor does a good job of removing old config and kernel files without breaking the system. 
you may want to download and install it and run it's janitor see if it clears the space for you. 
you can find it [here:]("http://ubuntu-tweak.com/")
Take some care if you do the above and DO NOT simply accept the offer to remove everything it offers as removable or you may find some applications and utilities you use have also gone.

I am one of those people who prefer to keep manual control of my OS rather than use ubuntu-tweak, but I admit that not using Ubuntu (Xubuntu is my preference) I have not actually used it.  I did, however use janitor separately in the past, and thought that it was unnecessary.

---

### Post by johnarthurbishop on 2015-01-30
> **ajgreeny said:**
> Let's see the output of ```
ls /boot | grep vmlinuz
``` which will show the kernel versions you have installed;

my output is 
"vmlinuz-3.12.22-031222-generic
 vmlinuz-3.13.0-37-generic
 vmlinuz-3.13.0-39-generic
 vmlinuz-3.13.0-40-generic
 vmlinuz-3.13.0-43-generic
 vmlinuz-3.13.0-44-generic"

---

### Post by Rex Bouwense on 2015-01-30
I have always used synaptic package manager to remove old kernels.  Open synaptic and search for Linux Image.  Mark those older kernels for complete removal and then apply.  Be sure and save the newest and one other for a back up.  The ones that you want to save are:
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-44-generic

---

### Post by sammiev on 2015-01-30
> **Rex Bouwense said:**
> I have always used synaptic package manager to remove old kernels.  Open synaptic and search for Linux Image.  Mark those older kernels for complete removal and then apply.  Be sure and save the newest and one other for a back up.  The ones that you want to save are:
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-44-generic

+1 I have used synaptic package manager for years now.

---

### Post by johnarthurbishop on 2015-01-30
I remember using Synaptic for things before 10.04 but back then I really had no idea how most all of this worked and I didn't even consider it. 
Thank you, everyone for your help!!!

---

### Post by ajgreeny on 2015-01-31
Another recommendation here for synaptic.  I think software-center is a waste of time and have never used it; it's nearly always synaptic for me for any package management activities, or terminal.

---

