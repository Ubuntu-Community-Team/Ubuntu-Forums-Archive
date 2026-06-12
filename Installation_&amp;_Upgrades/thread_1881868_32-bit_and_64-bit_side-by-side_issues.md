---
title: "32-bit and 64-bit side-by-side issues?"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by TZed on 2011-11-16
Hi all,

I'm very new to Ubuntu. I installed 10.04 for a project I'm working on here, but, unbeknownst to me, I needed 32-bit, and installed 64-bit instead. Since I had some extra space, I decided to install 32-bit on a new partition, alongside the 64-bit version, as a safeguard against losing data. I followed the instructions  at [http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

I realize now that was probably a bad idea, as the installation sometimes looks for the 64-bit stuff, it seems, Specifically, when I run sudo apt-get update, I get the error message:
W: Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/restricted/binary-i386/Packages.gz

Considering it says "Release AMD64" and "binary-i386", I think I probably screwed something up. Any ways to fix it?

Thanks in advance!

---

### Post by tartalo on 2011-11-16
> **TZed said:**
> W: Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/restricted/binary-i386/Packages.gz

What happens if you comment the CD as a source in /etc/apt/sources.list ?

---

### Post by TZed on 2011-11-16
Thanks, I don't get the error message anymore. But isn't that line important for updates or something? Can I change the "amd64" part to "i386"?

---

### Post by oldos2er on 2011-11-16
Assuming you have a working internet connection, you can do without the CD line in sources.list.

---

### Post by TZed on 2011-11-16
Excellent! Thanks all!

---

