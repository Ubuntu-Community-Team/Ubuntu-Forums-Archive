---
title: "Purged package cannot be reinstalled."
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by cov on 2012-12-05
I'm afraid I've been a bit naughty.

I tried to purge the installation of a broken package, which I understood removed the entire package, configuration files, everything.

When I still couldn't install the package again, I looked at the files in /usr/lib/ and notioced that the packages files were still there.

This is where I did something really silly; I manually deleted directories containing the package.

I then downloaded the latest DEB files and tried to install the package from scratch.

This is the error I get:

> sudo dpkg -i Downloads/fpc_2.6.0-120824_amd64.deb 
(Reading database ... 381019 files and directories currently installed.)
Preparing to replace fpc 2.7.1 (using .../fpc_2.6.0-120824_amd64.deb) ...
sed: can't read /usr/lib/fpc/2.7.1/fpc-cross.cfg: No such file or directory
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sed: can't read /usr/lib/fpc/2.6.0/fpc-cross.cfg: No such file or directory
dpkg: error processing Downloads/fpc_2.6.0-120824_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 2
sh: Can't open /usr/lib/fpc/2.7.1/samplecfg
touch: cannot touch `/usr/lib/fpc/2.7.1/fpc-cross.cfg': No such file or directory
sed: can't read /usr/lib/fpc/2.7.1/fpc-cross.cfg: No such file or directory
/var/lib/dpkg/info/fpc.postinst: 8: cannot create /usr/lib/fpc/2.7.1/fpc-cross.cfg: Directory nonexistent
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 Downloads/fpc_2.6.0-120824_amd64.deb


Is there a way of getting apt-get or dpkg to disregard the prior installation? Failing which how easy is it to resurrect deleted files? I used "rm -rf".

The machine has Linux Mint Lisa.

---

### Post by cov on 2012-12-05
Oops. Wrong forum, I think. Sorry.

---

### Post by cov on 2012-12-07
Pity nobody could help me resolve this.

In the event I decided to reinstall, choosing to install Ubuntu 12.10 Desktop as I have found the variants, although lighter and quicker to boot up and power down, inevitably have quirks which throw out various bugs and anomalies.

As it turned out, this was a huge mistake.

The Dowload ISO is slightly too large for a CD and I didn't have a DVD, so I booted up from the ISO using Grub. The problem was the installation program was unable to unmount the partition that the ISO was on, so it trashed the partition table, wiping out months of work. I do have back ups, but unfortunately these were incomplete.

And now it appears that 12.10 is impossibly flawed in any case; my ATI Radeon 5450, purchased a few months ago is apparently not supported, so my two monitor setup is reduced to one monitor only.

Furthermore a number of important software applications including DraftSight no longer work with 12.10 making the machine largely unusable.

---

