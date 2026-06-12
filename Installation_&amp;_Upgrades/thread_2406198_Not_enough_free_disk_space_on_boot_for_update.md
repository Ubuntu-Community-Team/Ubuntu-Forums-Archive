---
title: "Not enough free disk space on boot for update"
date: 2018-11-17
forum: Installation &amp; Upgrades
---

### Post by sashko.taylor on 2018-11-17
Hi,

I've been ignoring the software updates for a while, and now the Software Updater is giving me the following message:
> 
The upgrade needs a total of 94.4 M free space on disk '/boot'. Please free at least an additional 51.8 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove', and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs.

Before I simply hit 'sudo apt autoremove' I thought I'd rather ask, cause I smell some risk here.

Please advise.

---

### Post by Impavidus on 2018-11-17
You probably have a somewhat small /boot partition and accumulated too many old kernels. You only need a /boot partition if you use LVM or full disk encryption. Try```
sudo apt autoremove --purge
```and see if that helps. It's the suggested command, with the purge option to clean it a bit more thoroughly. If not, run```
dpkg --list 'linux-*'
```and show us the output. First make your terminal window large, so we can read long lines of output. That tells us which kernel-related packages are installed. Also run ```
uname -r
df -h
```to show us the currently running kernel and available space on your file systems.

---

### Post by dino99 on 2018-11-17
Only hold the last 2 kernels version and purge the others. This is usually made by autoscript nowadays. So my question: which flavour is it ?
Synaptic is an easy tool for such maintenance.

---

### Post by ajgreeny on 2018-11-17
Those commands shown by Impavidus are the ones we need to see output of so please let's see that and we can then move forward.

I suspect the **autoremove** command will do nothing as apt needs more headroom than you will have available and we are probably going to need to begin with a dpkg remove command, however we need to know exactly what to remove which the **dpkg --list linux-*** command will tell us.

---

### Post by sashko.taylor on 2018-11-19
Thank you for the replies.
It's ubuntu 16.04 I'm running

sudo apt autoremove --purge seems to have fixed the issue for me.

---

### Post by ajgreeny on 2018-11-20
Great news! 

I am a bit surprised that it worked for you as there is generally insufficient headroom for autoremove to be successful if you have seen that error, but please now mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

