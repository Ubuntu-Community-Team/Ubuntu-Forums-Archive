---
title: "Black GRUB screen after Update Manager Run."
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by vouser on 2010-09-03
I have Ubuntu 10.04 installed on dell inspiron 5150.
Original installation was perfect. Wireless Internet worked right away.
Screen resolution was perfect.
One day, after a month or so, after original installation I got a  notification that new updates are available.
So, I installed all updates. At the end there was a notification: Update is successful, please reboot.
After reboot I got a black screen with the header:

GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like......
.......................
(I hope it's not a ubuntu version of windows blue death screen).
I could install 10.04 from scratch, but I can not do it after every update.
Please, help, if you can.
Regards,
your ubuntu friend.

---

### Post by joromoro on 2010-09-10
hello,

try this, by me work.

1.
type root to see where is your root file system
grub> root
(hd[COLOR="rgb(0, 255, 255)"]0[/COLOR],[COLOR="Red"]7[/COLOR]):Filesystem is reiserfs.

2.
grub> linux /vmlinuz root=/dev/sd[COLOR="Cyan"]a[/COLOR][COLOR="red"]7[/COLOR] ro
grub> initrd /initrd.img
grub> boot

3. now you will have started and worked OS but only to the next restart. You must rty to found from where come the problem. In most case you will just need to update grub (su update-grub).

Good luck.

---

