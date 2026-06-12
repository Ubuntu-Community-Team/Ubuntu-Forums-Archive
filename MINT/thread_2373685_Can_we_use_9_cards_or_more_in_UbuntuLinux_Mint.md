---
title: "Can we use 9 cards or more in Ubuntu/Linux Mint?"
date: 2017-10-08
forum: MINT
---

### Post by CameronJohnson on 2017-10-08
I asked this on the linux mint forums originally but got sent to this one. Original thread:
[https://forums.linuxmint.com/viewtopic.php?f=59&t=255132&p=1374799#p1374799](https://forums.linuxmint.com/viewtopic.php?f=59&t=255132&p=1374799#p1374799)

I have a TB250-BTC Pro that I'm trying to set up with 9 or more nvidia 1060 3gbs. I can boot into Mint no problem with 8 cards, but with 9 or more it hangs at a blank screen forever after grub loads the system. I've played around with a bunch of BIOS settings and am pretty confident my hardware is fine, is this a software issue in Mint? I see the CONFIG_VGA_ARB_MAX_GPUS kernel parameter is set to 16, thought that could be the issue at first.

Managed to take a look at the failing boot logs, and it loops on something like this:
```

/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
Error: can't open /lib/modules/4.8.0-53-generic/updates/dkms
Error: can't open /lib/modules/4.8.0-53-generic/updates/dkms
update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf

```

---

### Post by Autodave on 2017-10-09
[https://devtalk.nvidia.com/default/topic/406065/max-number-of-gpus-/](https://devtalk.nvidia.com/default/topic/406065/max-number-of-gpus-/)

According to Nvidia's site, 8 is the max number.

---

### Post by CameronJohnson on 2017-10-09
That's old information and don't think it's accurate anymore, here's a link of somebody building an 18 card rig with nvidia cards in linux. I just wonder if Mint has a built in limit somewhere.

[https://devtalk.nvidia.com/default/topic/649542/cuda-setup-and-installation/18-gpus-in-a-single-rig-and-it-works/](https://devtalk.nvidia.com/default/topic/649542/cuda-setup-and-installation/18-gpus-in-a-single-rig-and-it-works/)

---

