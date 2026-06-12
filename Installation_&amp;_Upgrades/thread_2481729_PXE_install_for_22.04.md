---
title: "PXE install for 22.04"
date: 2022-12-07
forum: Installation &amp; Upgrades
---

### Post by pashdown on 2022-12-07
Having Ubuntu abandon the Debian style installer that worked great for me on PXE for over a decade has thrown a wrench into managing new installs at my business.  I managed to get the new style of installer with casper and cloud-config working with a VM install, but the bug from [20.04 for RAID install]("https://askubuntu.com/questions/1251655/ubuntu-20-04-server-installer-crashes-when-setting-up-raid-1-drives-for-boot-m") is still present, which severely limits me for installs on bare metal. I've had the new installer crash when simply sitting at a menu choice. It seems very buggy.  The whole decision to abandon Debian installer seems very half-baked. Is any effort underway at Ubuntu to either fix these bugs, or supply a Debian based net-install image?

---

### Post by ian-weisser on 2022-12-07
> **pashdown said:**
> The whole decision to abandon Debian installer seems very half-baked.

We are not the Ubuntu developers. If you are attempting to offer feedback, it is misdirected.

> **pashdown said:**
> Is any effort underway at Ubuntu to either fix these bugs, or supply a Debian based net-install image?

To discover if a bug is being worked, please offer a bug report number or link. AskUbuntu is not the bug tracker, and questions there are questions (not bugs).

Paid Canonical engineers won't be working on a net-install image, as their employer has other work for them to do. The door is wide open for a community-based project to take over and produce a net-install image. Such an effort is possible, and --judging by the number of complainers over the past few years-- might be popular. However, I am not aware of any serious community effort to build a net-install image. Perhaps the movement is still awaiting a leader.

---

### Post by Tadaen_Sylvermane on 2022-12-07
If I may. I just put an LTSP server on lan and pxe boot into debian. I can do a chroot installation of either Debian or Ubuntu at will via debootstrap. Just have to make sure your login user has sudo as needed. I gave up trying to make specific bootable installers awhile back. Fairly certain a chroot install is a plain as it gets.

---

### Post by pashdown on 2022-12-09
Thank you for the suggestion.  As far as I can read on LTSP, it seems like it is just an ISO booter?  Is it possible to do custom templates for install?

---

### Post by Tadaen_Sylvermane on 2022-12-09
No it's an entire linux terminal server. You create a chroot or image and it boots from pxe as long as you have a wired connection. Yuu can use it like a normal computer, a fat client if you will. Works as a regular desktop. And you can do debootstrap and chroot installs same as you would with a standard local hard drive / ssdh installation. Mine currently boots to XFCE on Debian. I have debootstrap and lvm2 in the net booted image so I can get emergency access, do chroot installs... and even add a computer to a room if someone stays for awhile and it's already setup. They just turn it on and it works.

---

