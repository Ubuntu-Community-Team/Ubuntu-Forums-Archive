---
title: "error: can't mount /dev/loop0 during v10.10 install"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2011-04-20
I'm trying to install Maverick onto a Thinkpad T42 with 512MB ram.
During the install for CD, I see the UBUNTU splash and blinking dots
for a while followed by a black screen with error messages.
```

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help for a list of built-in commands.

(initramfx) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //fileysytem.squashfs
udevd[77]: worker [214] unexpectedly returned with status 0x0100

udevd[77]: worker [214] failed while handling '/devices/virutal/block/loop0'

```

At this point the installer appears to stop -- no CD blinking lights,
no disk activity LED, etc.

I fetched a fresh copy of the Maverick ISO in case I had a bad kit.
I burned a fresh CD in case I had a bad burn.

I continue to have this problem.

Stumped,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-04-20
I find this posting is a duplicate of the thread at:
[http://ubuntuforums.org/showpost.php?p=9926705&postcount=1 ](http://ubuntuforums.org/showpost.php?p=9926705&postcount=1 )

I don't know the correct etiquette for handling this. My situation isn't SOLVED. I worry that marking it so would give others the wrong idea about this issue.

~~~ 0;-Dan

---

