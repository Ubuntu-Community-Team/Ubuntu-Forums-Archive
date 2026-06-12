---
title: "Installing ubuntu 9.10 server on Dell Studio XPS 9000"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by dant262 on 2009-12-27
I'm trying to installing ubuntu 9.10 server on some new Dell Studio XPS 9000 boxes, and am not sure whether I should be using the i386 or the x86_64 version.  It appears that I should use x86_64, but it fails during the base install saying "base-installer: error: exiting on error base-installer/kernel/failed-install"

I had installed the i386 version, but was having some trouble getting VMware server 2.0.2 to install correctly on it, so thought maybe I needed to be using the x86_64 version instead, but got the above error when trying that.

Any advice will be appreciated.

Thanks,
dant262

---

### Post by taurus on 2009-12-27
Maybe there is something wrong with the media!  Did you run the checksum to check the integrity of the ISO image before you burnt it?  Did you run the check cd for defects option at the first screen?

---

### Post by dant262 on 2009-12-27
So, there was an error on the DVD.  I've fixed that and the amd64 install seemed to complete successfully.

The question still remains, however: which version should I be installing on the Dell Studio XPS 9000?  It's an Intel Core i7-920 processor.

---

### Post by taurus on 2009-12-27
Why not go for the x86_64 (AMD64)!

---

