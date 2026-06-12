---
title: "Howto: Upgrade Feisty to latest 2.6.20-15.25 kernel without panic freeze!"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by muncrief on 2007-04-13
OK, as most people know something was broken in the kernel yesterday and many of us can no longer boot into our systems without using an earlier kernel.

Well, it appears that the problem has been fixed and there is a kernel that works, but Aptitude is not working correctly so you can't load the new kernel without removing all hard drives except for the root drive.

However, using the following apt-get command sequence you can upgrade all the way from the Feisty 7.04 install CD to the correct kernel, 2.6.20-15.25-generic without suffering catastrophic system failure. It should also work for any currently installed Feisty system, but I've only tested it from a fresh install.

First, you can optionally add medibuntu to your repository list if you want mulimedia:

Get the key:
**wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -**

Edit your sources:
**sudo gedit /etc/apt/sources.list**

Add these two lines anywhere in the file:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Save and close the file.

Now, to upgrade your system execute the following command EXACTLY as typed. Cut and paste it if you can:

**sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoclean**

apt-get will first present a bunch of packages that are being held back (and unlike aptitude they are the correct ones) and a bunch to be installed and updated. Just hit "y" and wait for awhile .

After it's done updating apt-get will present a screen of packages to be upgraded, and once again these are the correct ones, so once again press "y" and wait for awhile.

When it's done apt-get will clean up some errant and unused packages and all you need to do is reboot.

Presto! You are hopefully finally up and running the latest Feisty!.

Whew, it's been a scary day or so. I hope this doesn't happen again.

---

### Post by Slim Odds on 2007-04-13
And why exactly would I trust these repositories?

---

### Post by muncrief on 2007-04-13
The medibuntu repositories are one of Ubuntu's standard multimedia repositories. They even have w64codecs now which allow mplayer64 to play wmv!.

In any case, adding the extra repositories is not necessary. I just threw it in because a lot of newbies want to install multimedia stuff right after the OS, and in Feisty it's missing in the default sources.list.

You can just execute the apt-get command sequence to upgrade it you want. You don't need medibuntu.

---

### Post by deevus on 2007-04-14
This solution did not work for me, still froze @ bootscreen.

---

### Post by nbound on 2007-04-14
Same here, different error this time though :'(

---

### Post by muncrief on 2007-04-14
I'm sorry it's not working for everyone. I used the procedure from a clean 7.04 CD install, with a complete reformat of the root partition, so if it's still not working it must be hardware dependent.

However, you can also try installing with only one hard drive, and then when the upgrade is complete putting the second drive back in. It seems that for most people the kernel panic occurs when the second physical drive is accessed with the errrant kernels.

I know this is a hassle, but when I tried it this afternoon it worked even without the apt-get sequence above. I only needed to use apt-get with more than one hard drive installed.

This is really a horrible bug so soon before release. I hope the developers fix it soon. I'm sorry I couldn't be of more help but I only have one machine to test things on.

---

### Post by nbound on 2007-04-14
Heh, i only have one hard drive to begin with :P

---

### Post by TheForkOfJustice on 2007-04-14
It must be hardware dependent.

My 2.6.20-15.25 kernel works but is slower than 15.24

I tried upgrading but I get this error in synaptic

```
E: /var/cache/apt/archives/linux-image-2.6.20-15-386_2.6.20-15.25_i386.deb: failed in buffer_write(fd) (9, ret=-1)
```

it also said that /usr/bin/dpkg returned an error(1) or something like that.

Good thing I didn't remove 15.24

---

### Post by jonom on 2007-04-14
Worked a charm for me! Thanks muncrief!

Oh and it worked on my non-clean install of feisty.

---

### Post by oliver123 on 2007-04-14
Is there a launchpad bug with technical details about this combined kernel and aptitude bug?

Thanks,
Oliver

---

### Post by nirv117 on 2007-04-14
Thank You!  I go the new kernel and can boot now.

my system wasn't a fresh install I had been using it for a bit.

I had to rebuild a few things to work with the new kernel - such as vmware and Nvidia drivers, but no big deal - that process is all but automated...

Thanks again.

---

