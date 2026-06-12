---
title: "Custom kernel can't resolve UUID"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by porterde on 2007-05-15
Hi,

I have recently upgraded my system from dapper to edgy and things work fine as long as I use an ubuntu kernel package.

If I try to compile a stock kernel (which I have done successfully since breezy), it won't boot.  In particular, it panics at the VFS mount line, claiming that it can't find my root disk "UUID-hex-string...".  If I change the grub option to use /dev/hda1, it boots.

Am I missing a kernel option here?  Or perhaps there is some other problem?  

Obviously, not using UUIDs in boot is a workaround, but I'd like to understand why this isn't working in my kernel and does in the Ubuntu kernel.  

I use my system for kernel hacking, so I need to be able to build custom kernels.

Thanks in advance for the help!

---

