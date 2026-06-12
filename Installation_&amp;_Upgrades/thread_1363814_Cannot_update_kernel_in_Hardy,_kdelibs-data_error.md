---
title: "Cannot update kernel in Hardy, kdelibs-data error"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by talatnat on 2009-12-24
In trying to update the kernel from Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic to Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic, all goes well until this error:

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10-0ubuntu1~hardy1.5_all.deb: unable to make backup link of `./usr/share/icons/crystalsvg/22x22/actions/stop.png' before installing new version

1. The kdelibs-data update is aborted and Synaptic shows that it still has to be updated.
2. Uninstalling re-installing 26-generic kernel and kdelibs-data does not help. (Same error.)
3. The system is completely Updated except for kdelibs-data.
4. sudo update-grub shows 26-generic kernel, says it is upgrading /boot/grub/menu.lst, but this still remains at 25-generic.
5. Manually updating /boot/grub/menu.lst to include 26-generic shows an empty desktop (no folders, etc.) after reboot using 26-generic.
6. I cannot figure out how to install/update kdelibs-data...

I am not too bright on Ubuntu/Linux, so some newbie instructions/help would be vastly appreciated.

---

