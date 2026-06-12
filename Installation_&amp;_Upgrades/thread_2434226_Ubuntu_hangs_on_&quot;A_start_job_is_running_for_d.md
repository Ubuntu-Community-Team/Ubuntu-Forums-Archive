---
title: "Ubuntu hangs on &quot;A start job is running for /dev/disk/by-uui/.... until timeout"
date: 2020-01-02
forum: Installation &amp; Upgrades
---

### Post by jacek.gajek on 2020-01-02
Hi,
Ubuntu was booting in about a second. Now I have to wait 1:30m each time.

After pressing F1, I see this:
[IMG]https://ubuntuforums.org/asset.php?fid=278910&uid=2138053&d=1577951411[/IMG]

There are similar posts like these but all seem to relate to slightly different situation.

More info:
- I have a high-end, new laptop dualbooting to Windows 10 and Ubuntu 18.10
- I couldn't find that 1CC38... uuid in the gparted
- I wanted to have my secondary HDD drive mount at startup, so I added a line
UUID=1CC38D34-81A8-42AF-9469-6E3D400C05BD /media/STERTA ntfs-3g defaults,locale=en_US.utf8,windows_names,umask=7000,uid=1000,gid=1000,user  0   0
to fstab, as someone on the Internet suggested, but it doesn't work.
- If go to Nautilus then it can mount that disk, but I'd prefer to have it mounted without having to do this.
- The 2TB secondary disk has uuid "50D4C05FD4C048C4" and label STERTA in gparted

Any support will be appreciated
Thanks,
Jacek

---

### Post by deadflowr on 2020-01-02
Ubuntu 18.10 ended support already, please install a supported release.
(Supported releases are Ubuntu 16.04, Ubuntu 18.04, or Ubuntu 19.10)

That said, you can look at
```
systemd-analyze blame
```
to see what's loading at boot and what's taking up time to load at boot.

Also umask seems wrong.
Should be no spaces.

---

