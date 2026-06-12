---
title: "apt-get problem during Breezy upgrade"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by toastedcheese on 2006-06-25
I've been having problem after problem with my Hoary-to-Breezy upgrade and am trying to sort them out.

I started my update in Synaptic, changed "Hoary" to "Breezy" in the repositories, and reloaded/upgraded from there. Everything was going fine, until Synaptic decided that it was absolutely necessary to upgrade the linux-image package along with the rest. I had been holding off on this upgrade, because my /boot partition is too small and there's not enough room for the upgrade. Until now, using the older package didn't seem to make a difference.

At this point, Firefox was refusing to work, I'm guessing as a result of being in mid-upgrade. I dual-boot Windows, so I decided to reboot and use Windows for a while, intending to finish the upgrade with apt-get once I figured out the best way to deal with my linux-image problem.

However, when I returned to Linux, stuck in the terminal as I expected, there wasn't a whisper of my linux-image problem. Instead, when I ran "apt-get upgrade", it gave me this error message:

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse
Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_
multiverse_binary-1386_Packages) - stat (2 No such file or directory)

W: [...] http://ubuntu-backports.mirrormax.net breezy-extras/main Packages 
(/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) 
[...]

W: [...] http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages 
(/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages)
[...]

W: [...] http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
(/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) 
[...]

W: [...] http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
(/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages)
[...]

W: [...] http://people.ubuntu.com./ Packages
(/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages
[...]

W: You may want to run apt-get update to correct these problems.

E: Unmet dependencies. Try using -f.
```

(The "people.ubuntu.com" line is just a repository for a newer version of OpenOffice than had been released in the Ubuntu repositories.)

I tried using -f, but after a few minutes of removing and installing packages, it gave me the same message, except with the error message

```
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Actually running apt-get update didn't help in the least, since I only got the same error message, with the "index files" error at the end.

So, suggestions on what exactly the problem is? When I googled this error, it seemed to be mainly related to typos in the above, but I don't see any. Thanks in advance!

---

### Post by hippy4life on 2006-06-25
did you manually edit your sources.list?

if so i think that you may have made some errors, either post it here and i'll have a look or use the source-o-matic tool to generate a breezy sources.list

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by aysiu on 2006-06-25
I agree with hippy4life--if your sources.list isn't working for you, get a new one.

I'd recommend [this list](http://www.psychocats.net/ubuntu/breezy.list) (as I've used it before).

Once you update it: ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by toastedcheese on 2006-06-26
Thanks! The Source-o-matic was very useful; I was able to go on with the upgrade process.

However, now I'm (kind of) stuck where I was before. Linux-image-2.6.12-10-386 still needed to be installed, and there wasn't room for it on /boot. I ended up removing an earlier linux-image package, 2.6.10-5-386, in an attempt to fit it in. I've never needed to use this kernel, so I figured this would work.

Whether that was a wise decision or not, I'm still not sure. Now, when I boot up to my usual kernel (2.6.10-6-386), the upgrade is apparently complete, and the only thing that's not working is Nvidia. When I try to run nvidia-glx-config enable, I get this error:

```
Error: Your X configuration has been altered. This script cannot proceed automatically.
If you believe that this not correct, you can update the md5sum entry executing the following
command: md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

Neither suggestion works; my /etc/X11/xorg.conf already says "nvidia." I tried to follow [this guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Breezy") to remedy the situation, but nvidia-glx-config really won't work, and the nvidia installer isn't finding my version of gcc, for some reason.

The reason I'm not using the newest kernel is that it goes into kernel panic when I boot up:

```
RAMDISK: ran out of compressed data.
Invalid compressed format. Kernel panic - not syncing: VFS: Unable to mount root fs on unknown
block (0,0)
```

If I can get the earlier kernel to work, I could care less about this for the time being. But it might well be evidence that I've totally screwed something up with my attempted fix.

---

