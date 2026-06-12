---
title: "Installation type issues"
date: 2017-12-28
forum: Installation &amp; Upgrades
---

### Post by roner2 on 2017-12-28
[COLOR=#000000]I downloaded an Ubuntu 16 iso file and created a bootable image using Rufu on my Windows machine. Now booted from my USB and trying to install on a blank hard drive that's not being recognized for install, though is acknowledged in the BIOS. Got to the "Install (as superuser)" section, but under the Installation type there is nothing listed.[/COLOR]
[COLOR=#000000]When I click the + - or change it just hangs. The drop down only has /dev/sda. [/COLOR] The hard drive has zero time on it but for some reason is never acknowledged during the installation type part of the install.  The BIOS shows that it recognizes the hard drive however and I'm still able to use ubuntu from the USB stick, I'm just unable to install it due to the lack of options at this screen.

---

### Post by roner2 on 2017-12-28
I am doing this as well, still nothing.  I've actually tried it with both of the top two options in Rufus, which are UEFI and the other is UEFI and something else, I would have to look it up.

---

### Post by QIII on 2017-12-28
Hello!

I have moved your post to its own thread from [this thread]("https://ubuntuforums.org/showthread.php?t=2381221").

Please do not hijack the threads of others.  Although your issue may seem to present the same symptoms, the root cause may be completely different.  As attempts are made to diagnose a particular problem, hijacked threads can quickly become confusing for the OP, you, and anyone trying to help.

The OP of that thread deserves personal attention just as you do.

Thanks.

---

### Post by yancek on 2017-12-28
Is this the only hard drive in the machine and are there no other operating systems on it on other drives?

---

### Post by oldfred on 2017-12-28
what brand/model system?
And what hard drive?

If UEFI/BIOS sees it that is good.
But is RAID on in BIOS for drive? should be AHCI.
Was drive every used before as RAID or did you have Windows convert from gpt to MBR (which it does incorrectly)?

---

