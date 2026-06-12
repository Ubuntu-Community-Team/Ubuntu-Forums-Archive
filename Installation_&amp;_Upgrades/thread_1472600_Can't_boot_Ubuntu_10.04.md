---
title: "Can't boot Ubuntu 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by aydee on 2010-05-04
When I boot ubuntu it just sits at the ubuntu boot screen. I had some issues with the upgrade from 9.10 to 10.04 but I don't remember what the error message said. Thank you for your help!!!!

---

### Post by oldfred on 2010-05-04
Error messages are important, it would help a lot.

Is this before the grub menu or after?

---

### Post by tgalati4 on 2010-05-04
Try turning off kernel-mode-setting, KMS.  You will have to boot into the rescue shell (root console) and edit a grub entry to turn off KMS.

---

### Post by aydee on 2010-05-05
After Grub and the message was in 9.10 i thought the upgrade failed so I turned off my computer and went home (I do my web stuff at school as I have dial-up at home!) then when I went to do my homework, It just sat at the ubuntu 10.04 start up screen. If I hit any butten, it shows a bunch of stuff that I just found out about will tell you what it is after I try the KMS stuff

---

### Post by aydee on 2010-05-06
The Error I got was quote:
"fsck from util-linux-ng 2.17.2
Ubuntu was not cleanly mounted, check forced"

---

### Post by oldfred on 2010-05-06
Filechecks have to run to completion, sometimes they can take 5 minutes or more. It is one of the advantages of ext4 that file checks run much quicker.

Run this on all ext partitions
sudo fdisk -l

Where X drive & Y partition are from above command for all linux partitions:
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdXY
if errors:
sudo e2fsck -f -y -v /dev/sdX?Y

---

### Post by aydee on 2010-05-11
I some how destroyed the partition ubuntu is on so I remade the partition and installed ubuntu on my compuiter thanks anyway

---

