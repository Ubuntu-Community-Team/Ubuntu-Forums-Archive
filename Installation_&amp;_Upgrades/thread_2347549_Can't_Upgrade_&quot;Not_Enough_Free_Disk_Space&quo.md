---
title: "Can't Upgrade: &quot;Not Enough Free Disk Space&quot;"
date: 2016-12-26
forum: Installation &amp; Upgrades
---

### Post by BlacklightHalo on 2016-12-26
Hello all,

I'm trying to upgrade to Kubuntu 16.04. My current distro (14.04) is apparently broken, and to make things worse, the drives have somehow had their priority changed so that the disk drive is not #1, and therefore the LiveCD approach (which I usually prefer) doesn't work.

I looked for a terminal command to make this happen for me, and found

```
sudo kubuntu-devel-release-upgrade
```

I used this. First, I got "Error: '/var/tmp/kdecache-myname' is owned by uid 1000 instead of uid 0." I don't know what that means, but the process seemed to continue anyway. After some waiting, my terminal said "Checking for a new Ubuntu release," and then began connecting to the Ubuntu servers. Then the GUI I was expecting appeared. I got as far as "Setting new software channels" before I got an error, "Not enough free disk space. The upgrade has aborted. The upgrade needs a total of 93.7 M free space on disk '/boot'. Please free at least 6.965 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I followed the last two steps, but what I'm writing this to ask is, how do I free-up the necessary space in '/boot'? I found [this page]("http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot") which says I can use

```
sudo apt-get purge-linux-image
```

to do this. However, I assume I can't execute this command without typing the names of the previous kernels I'm trying to purge, and I don't know how to figure-out which ones are there/need purging.

---

### Post by Impavidus on 2016-12-26
Use```
uname -r
``` to see which kernel you currently run and use```
dpkg -l | grep linux-image
``` to get a list of your installed kernel packages. You can uninstall the old ones. Those labelled ii are installed. rc means config files remain, you can ignore those or purge them, doesn't really matter except for the clutter. Any capital letters means problems.

Upgrading won't fix a broken system, but in your case the problem may be simple enough to fix before upgrading. But don't spend too much time fixing it, or a fresh install may be faster.

---

