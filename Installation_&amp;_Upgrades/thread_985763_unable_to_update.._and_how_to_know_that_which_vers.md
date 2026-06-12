---
title: "unable to update.. and how to know that which version am using"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by chinnusan on 2008-11-17
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu1~hardy1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu1~hardy1_all.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-1_amd64.deb)
  403 Forbidden [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.22-2ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.22-2ubuntu4_amd64.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.22.3-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.22.3-0ubuntu2_all.deb)
  403 Forbidden [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.22.3-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.22.3-0ubuntu2_all.deb)
  403 Forbidden [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.22.3-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.22.3-0ubuntu2_amd64.deb)
  403 Forbidden [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.8.04.1_amd64.deb)
  403 Forbidden [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.7_amd64.deb)
  403 Forbidden [IP: 91.189.88.45 80]

---

### Post by Shwefty on 2008-11-17
Well, to figure out which version you're using, open the command prompt:

```
uname -a
```

That should give you some useful information or somebody useful information if you post it!

---

### Post by Partyboi2 on 2008-11-17
Try going into Software Sources (System>Admin>Software Sources) and changing the download server and see what happens.
You can check what version you are using by
opening a terminal
```
lsb_release -d
```

---

### Post by Shwefty on 2008-11-17
Running my command and then Partyboi2's command should tell everybody which distro version you're on, and which particular .iso (amd64, i686 etc).

---

