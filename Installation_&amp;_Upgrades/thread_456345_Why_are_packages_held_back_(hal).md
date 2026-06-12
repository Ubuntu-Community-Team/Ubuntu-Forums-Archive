---
title: "Why are packages held back? (hal)"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2007-05-27
When I try to install libdvdread3, I get the message

```
The following packages have been kept back
```

Tha packages are;
hal hal-device-manager libhal-storage1 libhal1 (from 0.5.8 to 0.5.9)

I can't find a thread newer that 2005 discussing this so I just wanted to make sure it's safe to install it.

Thanks,
Jarlath

---

### Post by Pollywoggy on 2007-05-27
> **jarlath said:**
> When I try to install libdvdread3, I get the message

```
The following packages have been kept back
```

Tha packages are;
hal hal-device-manager libhal-storage1 libhal1 (from 0.5.8 to 0.5.9)

I can't find a thread newer that 2005 discussing this so I just wanted to make sure it's safe to install it.

Thanks,
Jarlath

I have libdvdread3    0.9.7-2ubuntu1 installed on Feisty and it appears to be the latest libdvdread3 package.
'apt-cache showpkg libdvdread3' returns:

Reverse Depends:
  transcode,libdvdread3 0.9.6
  qvamps,libdvdread3 0.9.6
  mplayer-nogui,libdvdread3 0.9.6
  mplayer,libdvdread3 0.9.6
  mencoder,libdvdread3 0.9.6
  lsdvd,libdvdread3 0.9.6
  kmediafactory,libdvdread3 0.9.6
  k9copy,libdvdread3 0.9.6
  cpvts,libdvdread3
  chaplin,libdvdread3 0.9.6
  vobcopy,libdvdread3
  vls,libdvdread3
  vlc-nox,libdvdread3 0.9.6
  vamps,libdvdread3
  thoggen,libdvdread3 0.9.6
  python-mmpython,libdvdread3 0.9.6
  ogmtools,libdvdread3 0.9.6
  ogle-mmx,libdvdread3 0.9.6
  ogle,libdvdread3 0.9.6
  libdvdread-dev,libdvdread3 0.9.7-2ubuntu1
  libdvdplay0,libdvdread3 0.9.6
  gstreamer0.8-dvd,libdvdread3 0.9.6
  gstreamer0.10-plugins-ugly,libdvdread3 0.9.6
  dvdbackup,libdvdread3 0.9.6
  dvdauthor,libdvdread3 0.9.6
  dvd95,libdvdread3 0.9.6
  drip,libdvdread3 0.9.6
Dependencies:
0.9.7-2ubuntu1 - libc6 (2 2.5-0ubuntu1) libdvdcss2 (0 (null)) wget (0 (null)) de
bhelper (0 (null)) fakeroot (0 (null))
Provides:
0.9.7-2ubuntu1 -
Reverse Provides:

I think those other packages you mentioned as being held have nothing to do with the one you want to upgrade.

---

### Post by aysiu on 2007-05-27
It's good those are held back.

Read this thread for more details:
[Recent HAL update caused frequently failure for "suspend when lid closes"](http://ubuntuforums.org/showthread.php?t=443698&highlight=hal+suspend)

---

### Post by QwUo173Hy on 2007-05-27
Thanks guys. They're held back for a reason so. That's good to know. My system is nearly perfect now and I've gotten over quite a few hurdles, including the dreaded 'freeze' so I really don't want to touch that update button for a while!

---

