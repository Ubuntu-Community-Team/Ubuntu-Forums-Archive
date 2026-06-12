---
title: "Fresh 8.04 install hanging on bootup"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by sysyphus on 2008-04-27
Hi I've done a clean install on a compaq nx9010 using an Ubuntu 8.04 alternate disk.

It seems to have installed cleanly but when I go to boot up it hangs, when I try to boot up in recovery mode the hang occurs when trying to sort out the wireless lan. I get this line:

[  29.918670] b43legacy-phy0: Broadcom 4301 WLAN found

I have previously had 6.06 running on this system fine, I can do without the wireless lan working so an interim could be to turn this off but this did work under 6.06 so I am interested why it's now causing issues

So any pointers on either switching off the wireless lan or getting it working properly

Thanks in advance.

---

### Post by sysyphus on 2008-04-27
I've been doing some research and it seems I'm not the only person with this issue. I'm assuming my issues correspond to the following bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720)

With one possible solution here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720/comments/21)

I'm not going to look into this fix until later tonight but thought I'd post this here for others having the same issue. hope it helps

---

### Post by solitaire on 2008-04-28
I'm having the same issue

I've also got a Broadcom 4301 WLAN (I have to disable it in BIOS to get laptop to boot)

I also got another error sometimes before it freeze  "b44 ssb0:1: Problems fetching inversion of chip; Aborting" (or something like it, I can't seem to find it in the logs).

---

