---
title: "Removable Drives Not Mounting"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deanjm1963 on 2009-04-20
Both removable hard drives and USB sticks won't auto-mount after a reboot.

I have no problems with both Hardy and Intrepid.

I thought the last kernel updates might have fixed the problem, but appears not to.

Any ideas?

TIA

---

### Post by bennachie on 2009-04-20
I've had no similar problems (I have been running Jaunty on three different machines - netbook, laptop and desktop - since the beta was released, and the system has turned out to be almost completely trouble-free in each case). 

Could you tell us a bit more about your physical system, and about the actual symptoms? For example, does Jaunty recognise the drives in question once they have been removed and reinserted (some BIOS setups may block immediate recognition of non-bootable USB drives).

---

### Post by deanjm1963 on 2009-04-20
It's a desktop system, AMD 6000+ 4gb ram, sata dvd/rw, ide hd, nvidia 9600 1gb 26" viewsonic lcd, nothing out of the ordinary. Both Hardy and Intrepid run very well on it.

I am using 32bit Jaunty.

Drives are recognizable after unpluging and pluging back in.

But I'm still getting a kernel error on boot.

modprobe: FATAL: Could not load /lib/modules/2.6.28-generic/modules.dep No such file or directory

Could that be the problem?

I installed with the alternate CD, checked the md5sums of both the iso and the cd and they were both good. It's an RC install with all the current updates.

Has me puzzled...

---

### Post by fballem on 2009-04-20
> **deanjm1963 said:**
> It's a desktop system, AMD 6000+ 4gb ram, sata dvd/rw, ide hd, nvidia 9600 1gb 26" viewsonic lcd, nothing out of the ordinary. Both Hardy and Intrepid run very well on it.

I am using 32bit Jaunty.

Drives are recognizable after unpluging and pluging back in.

But I'm still getting a kernel error on boot.

modprobe: FATAL: Could not load /lib/modules/2.6.28-generic/modules.dep No such file or directory

Could that be the problem?

I installed with the alternate CD, checked the md5sums of both the iso and the cd and they were both good. It's an RC install with all the current updates.

Has me puzzled...

There is a bug report in Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034)

If this matches the symptoms that you describe, then please feel free to subscribe.

---

### Post by deanjm1963 on 2009-04-20
> **fballem said:**
> There is a bug report in Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034)

If this matches the symptoms that you describe, then please feel free to subscribe.

Thanks for that!

---

