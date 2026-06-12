---
title: "Trouble getting 14.04 64 bit to re-install"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-08-19
I had Ubuntu 14.04 64 bit up/running/ and quite nicely tuned.  Then ... potential virus + my-cat-rebooted-my-system (*seriously) - and now when I am attempting to re-install a big series of headaches.

MB:  Gigabyte 970A-UD3P
Bios:  American Megatrends F1  8/6/13
Processor:  AMD FX 8320 64 bit

When I insert my Ubuntu 14.04 disk  (I believe I am on attempt # 34..) it no longer even attempts to begin set-up.   Instead the system goes directly to 12.04 ubuntu.

How do I get my bios to boot the disk?
It seem strange that the bios would stop letting me try versions of Ubutu/Mint.

Thoughts?

---

### Post by xigen on 2014-08-19
I re-set the bios to its original config.  Then I went in and changed the boot sequence to:
-- DVD Rom
-- SSD
-- ubuntu

The install seems to have worked.   However, when I try to boot I get a blank screen.

I changed the boot sequence to:
-- ubuntu 
-- SSD
-- DVD  
.......and ... I still get a blank screen

-- SSD
-- ubuntu
-- Disabled(DVD) 
.... and I get a blank screen.

Thoughts?

---

### Post by xigen on 2014-08-19
Ubuntu 14.04 is now installed.    Networking is not working - however, that is the subject of a different post.

-- ubuntu
-- SSD (Disabled)
-- DVD (Disabled)
... is the config which lets me boot to 14.04.

Cheers.

---

