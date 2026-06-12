---
title: "Ubuntu 12.04/Win7 Dual Boot Weird Issue"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by ayrton04 on 2013-11-19
Hello,

I have Windows 7 on an internal hard drive on a Dell 6530. I installed Ubuntu 12.04 LTS via a USB key to a second internal drive that plugs into my optical drive slot. During installation, I could use my mouse, keyboard, and wireless card no sweat. Once Ubuntu installs, however, I have no mouse, no wireless, and no ethernet. My keyboard functions normally. What gives?

Thanks!

---

### Post by electrohandyman501 on 2013-11-19
Are you installing 64bit? 
I've read a couple of other posts today about some m-boards not playing well with 64bit linux without changing a bios option setting. USB, network were not working with 64bit.
They had no troubles with 32bit versions.

---

### Post by ayrton04 on 2013-11-19
It is 64-bit, yes. The only sort-of related posts I've seen were related to UEFI, which I have disabled.

---

### Post by electrohandyman501 on 2013-11-19
Not sure if you motherboar has the option listed in the following post.
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)

With IOMMU DISABLED:    USB and Networking do not work
With IOMMU ENABLED:     USB and Networking work

I've read 3 other threads today about this issue and 64bit os's

---

### Post by electrohandyman501 on 2013-11-19
Can you try/boot with a USB/LiveCD 32bit Version to verify(test).

---

### Post by ayrton04 on 2013-11-19
Perhaps, though it would be ultimately fruitless. I need a 64-bit install.

---

### Post by oldfred on 2013-11-19
You said you disabled UEFI, so it must be a newer computer.

But some older Dells were configured so that removeable drive in DVD caddy was not bootable. Not sure how or why Dell would do that as DVD would be or should be bootable.
Do you know that UEFI/BIOS offers to boot anything from caddy?

---

