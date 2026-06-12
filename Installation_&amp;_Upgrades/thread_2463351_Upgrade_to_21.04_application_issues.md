---
title: "Upgrade to 21.04 application issues"
date: 2021-06-09
forum: Installation &amp; Upgrades
---

### Post by drjdmartin on 2021-06-09
Hi,

I've upgraded to 21.04 and I'm just trying to fix a few issues:

1. Boinc didn't work - solution was to add my user back into the Boinc group as per [https://boinc.berkeley.edu/gui_rpc.php](https://boinc.berkeley.edu/gui_rpc.php)

2. The Ubuntu Software icon doesn't work - the icon spins for a while and then nothing happens. Right clicking on it and clicking show details opens up the Gnome software center no problem though. Any ideas how to fix the icon left click? UPDATE - looks like this is a known bug with snap-store [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1931380](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1931380)

3. Barrier doesn't seem to work - it shows as connected to the MacOS client via the logs but the mouse won't move outside the Ubuntu server screen. Any known issues or possible ways to debug? I've increased logging to debug1 and there are no obvious error messages. UPDATE - doing some searching this is to do with Wayland support [https://github.com/debauchee/barrier/issues/109](https://github.com/debauchee/barrier/issues/109). The solution is to switch back to Xorg [https://fostips.com/switch-back-xorg-ubuntu-21-04/](https://fostips.com/switch-back-xorg-ubuntu-21-04/).

Many thanks,

James

---

