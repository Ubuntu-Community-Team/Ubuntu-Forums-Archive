---
title: "Upgrade and clean installtion problems"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Kobi Haron on 2007-10-29
I have (actually had...) Ubuntu 7.04 which worked very well. The 6.10 original installation and the upgrade to 7.04 were uneventful. My 7.10 was on drive D and I also have W2000 on C, dual boot. Before I attempted to upgrade I backed up my data from D to C.

1. Upgrade

I used the upgrade entry in the administration menu. At the installation phase I got messages about dependency problems with some important packages such as login, passwd, dbus and many more. Eventually the installation aborted and a recovery process started, warning me that the resulting system may not be usable. This recovery also aborted.

2. Clean install

As I had all my data backed up I figured I should do a clean install. I booted my W2000 which I hardly use these days, downloaded the ISO, burned it using Nero and started installing. I told the partition software to get rid of the existing installation - possibly a mistake. The installation aborted because of bad files.

3. A mess

I tried to reboot and I got GRUB error 15. I guess it was looking for Ubuntu and it wasn't there because of whatever happened to it. **Attention GRUB developers - if GRUB can find something to boot from it shouldn't abort**.

I had no computer. I inserted my old 6.10 alternate disk and installed it, hoping that the installation will fix the GRUB. For some reason this installation also failed but I could complete the GRUB phase and now I can boot my W2000. No data is lost.

Checking the 7.10 disk I found that it had 2 bad files.

Now I have reburned the 7.10 ISO at the slowest speed possible and I take a break to write this message.

I have some technical background otherwise I would be lost. My aunt couldn't do that.

Stay tuned.

---

