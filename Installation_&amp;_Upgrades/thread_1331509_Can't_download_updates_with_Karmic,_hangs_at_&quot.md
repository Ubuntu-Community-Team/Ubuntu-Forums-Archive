---
title: "Can't download updates with Karmic, hangs at &quot;Downloading list of changes&quot;"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by pgacv2 on 2009-11-19
Hey, all.

I recently upgraded from Jaunty to Karmic online with the update manager. Installation went smoothly except that I couldn't browse the web or receive email with Thunderbird. After some hunting, I realized I needed to disable IPv6, so I disabled IPv6 in the about:config of Firefox and Thunderbird and now they work fine. However, now I can't install updates through the update manager. When I open the update manager, it stays a long time just saying "Downloading list of changes," then eventually gives up and says it failed to download the list. When I click to download the updates, it stays a long time without downloading anything and then pops up a window with a lot of lines that say "W: Failed to fetch [http://mirrors.ccs.neu.edu/ubuntu/pool/main/u/udev/libudev0_147~-6.1_amd64.deb](http://mirrors.ccs.neu.edu/ubuntu/pool/main/u/udev/libudev0_147~-6.1_amd64.deb) (or any of the other packages I'm trying to download) Unable to connect to mirrors.ccs.neu.edu http:"

I've tried a number of things: disabling IPv6 by setting /proc/sys/net/ipv6/conf/all/disable_ipv6 to 1 (it gets turned back to 0 on reboot), changing the server in the "Download from:" menu in Software Sources, making sure all of my Jaunty lines in the sources file are removed (not just commented, but really deleted), and adding "net.ipv6.conf.all.disable_ipv6=1" to /etc/sysctl.conf as suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=1163391"). Still nothing.

Any help is appreciated.

EDIT: I forgot to mention that I also can't download any new apps through the Ubuntu Software Center.

---

### Post by pgacv2 on 2009-11-19
Acting on an idea from [http://ubuntuforums.org/showthread.php?t=1329977](http://ubuntuforums.org/showthread.php?t=1329977), I specified a proxy in Synaptic's network settings, and that got it to download and install seven updates. The other 85 still say "Failed." And when I try to install software through the Software Center, it fails and says "Requires installation of untrusted packages."

---

