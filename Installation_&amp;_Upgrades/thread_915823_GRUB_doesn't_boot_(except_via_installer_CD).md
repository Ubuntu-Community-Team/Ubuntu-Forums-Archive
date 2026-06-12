---
title: "GRUB doesn't boot (except via installer CD)"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by all-linux on 2008-09-10
Hi, I installed Intrepid alpha 5 on my laptop (kohjinsha, SC3 / new Menlow platform) successfully, but I can't boot from GRUB. As soon as I select the first boot image, I get a blank screen with the cursor in the upper left corner. The laptop bios is very simple, nothing to modify their.
As soon as I boot from the installer CD and select "Boot from first harddisk" and then select the first boot entry, the system boots just fine. Any idea what's going on here?

---

### Post by Elfy on 2008-09-10
I would try to reinstall grub with the livecd - boot with it and use this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If that doesn't help, then you could check what the menu.lst is trying to boot, ue the livecd again.

Post ```
sudo fdisk -l
```

It could however be a bug - intrepid is still an alpha release.

---

