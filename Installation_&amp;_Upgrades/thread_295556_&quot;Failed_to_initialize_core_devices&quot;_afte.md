---
title: "&quot;Failed to initialize core devices&quot; after upgrade"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by elpresidente on 2006-11-08
I ran through the upgrade manager yesterday (from Dapper to Edgy). I actually ended in an error (something regarding an X11 package - unfortunately, I did not write it down in my haste). Now GDM/X will not start. I had tried reconfiguring xserver-xorg numerous times. I changed the driver to vesa to rule ATI driver issues out. The error message I am now receiving is "Failed to initialize core devices". I'm at a loss. Any help would be appreciated.

---

### Post by elpresidente on 2006-11-08
Ok. I just tried running apt-get -f install and there were packages to be installed. It error again saying that a package was trying to  change /usr/X11R6/bin to a symlink but could not delete it because it was probably not empty. So after it dropped back to the command line I deleted it. Probably shouldn't have, I know. So now when I run apt-get -f install I get:

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcairo2 libcairo2-dev libpango1.0-0 libpango1.0-common libpango1.0-dev libxft-dev libxft2 x11-common
Suggested packages:
  libcairo2-doc ttf-thryomanes libpango1.0-doc
The following NEW packages will be installed:
  libxft-dev
The following packages will be upgraded:
  libcairo2 libcairo2-dev libpango1.0-0 libpango1.0-common libpango1.0-dev libxft2 x11-common
7 upgraded, 1 newly installed, 0 to remove and 1229 not upgraded.
5 not fully installed or removed.
Need to get 0B/1880kB of archives.
After unpacking 1102kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 230273 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xgl
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm in some dependency hell, I know. What do I need to do?

---

### Post by elpresidente on 2006-11-08
Sorry multiple post this but I saw the same problem in several threads while searching.

[http://ubuntuforums.org/showthread.php?t=286351&highlight=x11-common\](http://ubuntuforums.org/showthread.php?t=286351&highlight=x11-common\)

For me -
sudo dpkg --purge xgl
got things moving.

---

### Post by elpresidente on 2006-11-08
Now it's borked. The above got it working and into X. I then was trying to install Automatix2 and it complained that I was using Dapper and not Edgy so I:

apt-get dist-upgrade
and it errored so I
apt-get -f install
and it rolls along and completes but
apt-get dist-upgrade
still has a bunch of packages to upgrade and I alternated between the two commands a few times and then I rebooted. Now I get

Uncompressing Linux... Ok, booting the kernel.
0

Uh-oh. I'm in trouble now. What do I do?

---

### Post by elpresidente on 2006-11-08
Every entry in Grub "hangs" after:
Begin: Running /scripts/init-bottom ...
Done.

Sigh. elpresidente is not happy.

---

