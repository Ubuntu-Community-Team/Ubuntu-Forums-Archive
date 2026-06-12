---
title: "Undo jaunty upgrades"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by birdwin on 2009-04-12
Hello all,

I'm running Ubuntu 8.10, i386, 2.6.27-11. In order to save time compiling aMule and deluge, I added the jaunty main and universe repositories to my /etc/apt/sources.list. I apt-got amule and deluge, and they presumably installed the jaunty versions of their dependencies. Not too long after the installations were finished, my keyboard shortcuts stopped working. I rebooted, selected the entry in grub, and now it hangs with a black screen and the circling pointer. I booted into recovery mode, went to a root shell and removed amule and deluge, to no avail. I then ran apt-get autoremove, thinking perhaps that would fix the program. Again, no luck. I booted into recovery mode and tried to use dpkg to fix broken packages; it attempted to download ash, ubuntu-minimal and vim-tiny (I had removed the latter in favor of vim-full), but it couldn't connect to the web. I know that the B43 driver may not have loaded, so I plugged into my router via ethernet and ran ifconfig eth0 up. It still wasn't connecting (even after running ifconfig wlan0 up), so I'm here wondering what I can do. I've removed the jaunty repos from my sources.list, but can't seem to get to a login window. Thanks in advance.

-Matt

---

### Post by Dan_Dranath999 on 2009-04-12
you can download debs for aMule and Deluge from getdeb.net i think.

---

### Post by thunk77 on 2009-04-12
What you did is a great way to mess up a system, although if you are very skilled and experienced with Debian you can actually use mixed repositories. Anyhow, what's done is done and I would suggest upgrading your installation to 9.04. The way to do that would be hitting Alt+F2 and typing "update-manager -d" (without the quotes). I think in your place I would reinstall anyway...

---

### Post by lovinglinux on 2009-04-12
Why did you add the Jaunty repositories in the first place? Amule and Deluge are available through Intrepid's repositories and they both are also available as deb files. There is no need to compile them.

I suggest you read the tutorials below once you fix your system:

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

---

### Post by birdwin on 2009-04-12
@lovinglinux:

The version of aMule in the intrepid repo has a major bug that was fixed in a later version, which is only available in the jaunty repo. The version of deluge in the intrepid repo is way outdated; the most recent version is only available in the jaunty repo. Neither aMule nor Deluge release Linux packages, and I didn't know about getdeb.net (its version of aMule is old anyway). I was under the impression that the only way to get the latest versions (assuming they're not in the repos yet) was to compile, which took over an hour on my box the last time I did it.

@thunk77:

I can't run the update manager because I can't even login, plus network connectivity isn't working in recovery mode.

---

### Post by lovinglinux on 2009-04-12
> **birdwin said:**
> @lovinglinux:

The version of aMule in the intrepid repo has a major bug that was fixed in a later version, which is only available in the jaunty repo. The version of deluge in the intrepid repo is way outdated; the most recent version is only available in the jaunty repo. Neither aMule nor Deluge release Linux packages, and I didn't know about getdeb.net (its version of aMule is old anyway). I was under the impression that the only way to get the latest versions (assuming they're not in the repos yet) was to compile, which took over an hour on my box the last time I did it.

I don't know about aMule, but deluge has all sorts of releases, including deb files and a PPA repository. Look at [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

I hope you fix your system. Good luck.

---

### Post by thunk77 on 2009-04-13
In that case, I would suggest doing a backup of your personal files with a live cd to an external location and reinstalling from scratch.

---

### Post by birdwin on 2009-04-13
I managed to fix everything. I booted into recovery mode, opened a shell and added 'iface eth0 inet dhcp' to /etc/network/interfaces (NetworkManager removes connections it manages from this file, so to get DHCP working during an 'ifup eth0', you need to add this line). I removed the jaunty repositories from my /etc/apt/sources.list file. I then ran 'ifup eth0' to get the ethernet connection working. Then I ran 'apt-get update', then 'apt-get install apt-show-versions'. The latter app will list all of your packages and whether or not they're the newest versions compared to the repos in your sources.list. If they match the version in the repo, they'll say '[package name]/intrepid uptodate [version]' for intrepid. If they're newer (like in my case, where I had packages from the jaunty repos), the line will say that it's newer than the repo version, and most importantly, it won't say 'intrepid' anywhere in the line. So running 'apt-show-versions | grep -v intrepid' showed all of the packages that had upgraded themselves to the jaunty versions when I apt-got amule and deluge earlier. These packages (libc6 and libgtk2, among others) were hanging the system once it got past GRUB. I then booted into my Windows partition and downloaded all of those debs from packages.ubuntu.com/intrepid/i386/[package_name]/download (I couldn't just wget them because the package pages make you pick a mirror, so I needed a GUI). I booted back into the recovery console, mounted the Windows partition and copied the debs to /root. I then ran 'dpkg -i [package_name]' on each, although the order is crucial. One of the packages that was too new was libc6 and friends, so that had to get installed first because dpkg doesn't manage dependencies like apt and friends. Once I got all of the debs installed, I rebooted and everything worked. I had to remove 'iface eth0 inet dhcp' from /etc/network/interfaces so that NetworkManager can manage the connection, however.

Thanks to everyone for their help.

---

### Post by Dan_Dranath999 on 2009-04-14
!! i thought that was beyond repair.

---

### Post by nandemonai on 2009-04-14
Phew, nice save.

---

