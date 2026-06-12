---
title: "script doesn't work on 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by noworldorder on 2011-04-29
Hey,

I just installed 11.04

I have the following script that is not working:

#!/bin/sh
mount -t smbfs //192.168.1.106/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.106/Backup /mnt/Backup

If  I enter this in terminal:

sudo mount -t smbfs //192.168.1.106/MediaShare /mnt/MediaShare

it doesn't work either - cannot mount this device anymore sinse upgrade.

Any ideas.

Thanks,
Chris

---

