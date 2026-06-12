---
title: "Installed 12.04, and all that happens is: Warning: Fake initctl called, doing nothing"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by His Royal Freshness on 2012-05-19
Either "Warning: Fake initctl called, doing nothing." or simply a flashing curser shows up on a black screen when I boot up.  

When I was installing, I believe that it shut down my computer not too long before the installation finished, which I think is the problem.  I've tried running updates in recovery mode, but I can't access updates because I can't connect to the internet.  

This happened before, I think, when I initially installed 11.04 a year ago.  I think it had something to with drivers, maybe.

I did some googling, a few things came up, but all I got for this version was a [bug report from the first alpha release]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/914414"), and it didn't appear resolved.

---

### Post by His Royal Freshness on 2012-05-31
Bump.  I can't seem to find anything for this.

---

### Post by MagicalMonkey on 2012-05-31
I am having the same problem.

---

### Post by Curtis6767 on 2012-05-31
Are you installing over an existing Ubuntu install or are you doing a fresh install?

You could first try running from your LiveCD and see if you can get that working.

Another option would be to try to download and install the alternate image from this list: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

The alternate install is text-based rather than graphics-based so it doesn't have as many chances to conflict with your video drivers.

Hope this helps

---

### Post by jmidgren on 2012-10-01
I had the same problem with a system after some tweaking because of a disk failure and RAID reconstruction. Eventually I found a solution and thought I should share it:

After a lot of Googling I found that it probably had something to do with the package upstart being removed or damaged somehow. In my case it turned out also to be a problem with dpkg, which made package management impossible.

I solved the problems by first repairing dpkg package as described in [this post]("http://ubuntuforums.org/showthread.php?t=1449322"), something you may not need to do if your dpkg is not damaged...

> It is possible that it can be solved in an easier manner by e.g. copying "start-stop-daemon" from a live CD. Remember to use a live CD for the same version of Ubuntu (12.04) and architechture (e.g. i386, x86_64).After that I could again do package management and went ahead re-installing the damaged packages:
```
sudo apt-get --reinstall install dpkg
sudo apt-get --reinstall install upstart
```For various reasons I was not able to use repair mode but had to use a live CD to chroot into my installed system. It is well described [here in ubuntu community wiki]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot") (especially if you are using RAID). The article is about reinstalling grub, so if you don't need to do that, simply skip the last few steps. So in case repair mode does not work: After you have chroot:ed into your system you can run apt-get as described above (omitting "sudo" though)...

---

