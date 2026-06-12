---
title: "Intel DQ965GF mobo won't recognize CD-ROM drive for install"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by Directrix1 on 2006-12-11
This seems to be a linux wide issue.  The Intel DQ965GF motherboard for some reason or another does not detect my standard CD-ROM drive so I can't install.  Anybody have any ideas at all here?  BTW, I have set the drives to AHCI already.  This applies to both the X86 and AMD64 6.06 LTS versions.

---

### Post by Spidernet on 2007-01-02
Hi, I had the same problem. After 2 days. It runs on Mandriva 2007 and Fedora Core 6, all You need to do is add the parameter to kernel while installing
all-generic-ide

Have fun.

---

### Post by Directrix1 on 2007-01-02
For anyone having this same problem who would like to still use Ubuntu.  You can do what I did.  Install Edgy or higher netboot installer onto a USB stick and boot and install off that.  The CD-ROM drive still doesn't work though.  But thats not really needed in my case.

---

