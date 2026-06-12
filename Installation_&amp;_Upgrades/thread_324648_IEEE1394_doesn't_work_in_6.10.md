---
title: "IEEE1394 doesn't work in 6.10"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by TimRead on 2006-12-24
I have an external hard drive which I used to backup my old Ubuntu 6.01 system before formatting my internal drive and installing the new Ubuntu 6.10. Now when I connect the external drive it does not mount and from dmesg I get the following errors:

[17180964.952000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[08004603020396ba]
[17180989.884000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17180991.720000] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[17180992.148000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d0b80e7800f807]
[17180992.148000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17180992.240000] scsi1 : SBP-2 IEEE-1394
[17181023.020000] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[17181023.020000] sbp2: probe of 00d0b80e7800f807-0 failed with error -16

It is not the end of the world for me since I connected the drive using USB and was able to copy my files back without problems, allbeit somewhat slower, but it is a problem for editting video.

Any suggestion?

Thanks,

Tim

---

