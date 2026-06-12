---
title: "Audio does not work anymore after upgrade"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by guandalino on 2011-03-13
Hi, hopefully it's the right place for some answer to this question... Today after a software update on my Ubuntu 8.0.4 I noticed that audio didn't work anymore. I mean this:

```

$ sudo aplay -l
aplay: device_list:205: no soundcards found

$ find /lib/modules/`uname -r` | grep snd
$
```And that's weird, because my sound card was being recognized before the upgrade and after as well:
```

$ lspci -v | less
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 4314
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at f9fd8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```This is the log of packages updated or installed.

Updates:
```
avahi-daemon (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
firefox (3.6.13+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-3.0 (3.6.13+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.6.13+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-branding (3.6.13+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
firefox-gnome-support (3.6.13+build3+nobinonly-0ubuntu0.8.04.1) to 3.6.15+build1+nobinonly-0ubuntu0.8.04.1
fuse-utils (2.7.2-1ubuntu2.2) to 2.7.2-1ubuntu2.3
libavahi-client3 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-common-data (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-common3 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-compat-libdnssd1 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-core5 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-glib1 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libavahi-ui0 (0.6.22-2ubuntu4.2) to 0.6.22-2ubuntu4.3
libfuse2 (2.7.2-1ubuntu2.2) to 2.7.2-1ubuntu2.3
libpango1.0-0 (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libpango1.0-common (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libpango1.0-dev (1.20.5-0ubuntu1.1) to 1.20.5-0ubuntu1.2
libsmbclient (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
libtiff4 (3.8.2-7ubuntu3.6) to 3.8.2-7ubuntu3.7
linux-headers-generic (2.6.24.28.30) to 2.6.24.29.31
linux-libc-dev (2.6.24-28.86) to 2.6.24-29.87
mplayer (2:1.0~rc2-0ubuntu13.1+medibuntu1) to 2:1.0~rc2-0ubuntu13.2
openssh-client (1:4.7p1-8ubuntu2) to 1:4.7p1-8ubuntu3
openssh-server (1:4.7p1-8ubuntu2) to 1:4.7p1-8ubuntu3
samba-common (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
smbclient (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
ssh (1:4.7p1-8ubuntu2) to 1:4.7p1-8ubuntu3
ssh-askpass-gnome (1:4.7p1-8ubuntu2) to 1:4.7p1-8ubuntu3
sun-java6-bin (6.22-0ubuntu1~8.04.1) to 6.24-1build0.8.04.1
sun-java6-jdk (6.22-0ubuntu1~8.04.1) to 6.24-1build0.8.04.1
sun-java6-jre (6.22-0ubuntu1~8.04.1) to 6.24-1build0.8.04.1
sun-java6-plugin (6.22-0ubuntu1~8.04.1) to 6.24-1build0.8.04.1
tzdata (2011b~repack-0ubuntu0.8.04) to 2011c~repack-0ubuntu0.8.04
winbind (3.0.28a-1ubuntu4.13) to 3.0.28a-1ubuntu4.14
```New install:
```
linux-headers-2.6.24-29 (2.6.24-29.87)
linux-headers-2.6.24-29-generic (2.6.24-29.87)
linux-image-2.6.24-29-generic (2.6.24-29.87)
```Please help, what should I do to recover my audio?

---

