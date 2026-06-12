---
title: "USB Hard Drive Installation"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by DanDennison84 on 2012-02-06
EDIT:  After a bit of research, I found this:  [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/) that seems to be exactly what I want.  Not sure how I missed it the first time around.

Hi everyone,

I have a laptop with Windows XP that I'd like to leave alone.  I have 1 TB USB HD that I'd like to install Ubuntu on.

When I use a LiveCD to install, it asks me where to install grub, on either the laptop HD or the USB HD.  Which one should I choose so I can get an option of either XP or Ubuntu?

Thanks,
Dan

---

### Post by varunendra on 2012-02-07
Hi DanDennison84, Welcome to the forums:)

Nice tutorial there, thanks for the link. Please mark the thread as [Solved] now, as this helps others who have similar questions (follow my signature to see how).

Hope you'll enjoy Ubuntu.
Cheers!:popcorn:

---

### Post by C.S.Cameron on 2012-02-07
I usually make the first partition NTFS or FAT32 so that I can also use the external drive to transfer data to and from Windows computers.

Unless you plan on keeping the external plugged in all of the time it is best to put grub on the external drive.

If you put grub on the internal drive you will not be able to boot without the external plugged in.

---

### Post by C.S.Cameron on 2012-02-07
Oops.

---

