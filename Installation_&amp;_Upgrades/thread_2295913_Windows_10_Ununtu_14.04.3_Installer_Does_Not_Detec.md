---
title: "Windows 10 Ununtu 14.04.3 Installer Does Not Detect Another OS"
date: 2015-09-22
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-22
Hello,

I have been trying to create a dual boot system with Windows 10 and Ubuntu 14.04.3. The installer failed to detect another OS and this caused a catastrophic failure by erasing my entire Windows 10 build.  When I tried this again I was careful not to hastily press any buttons and therefore avoided a similar outcome. Is there anyone who knows how to do this correctly? Will I have to use the 15.04 installer instead?

[IMG]https://annashope.files.wordpress.com/2011/04/dreamstime_18583772.jpg[/IMG]

Thanks, Hannibal

---

### Post by Bucky Ball on 2015-09-22
Boot to Windows and switch off hibernation. That's why it didn't see the Windows partition. The partition has to be closed. If you have hibernation set, which is by default, it is not.

Doesn't make any difference what release of Ubuntu you use. If hibernation is on you will get exactly the same result.

---

### Post by coljohnhannibalsmith on 2015-09-25
> **Bucky Ball said:**
> Boot to Windows and switch off hibernation. That's why it didn't see the Windows partition. The partition has to be closed. If you have hibernation set, which is by default, it is not.

Doesn't make any difference what release of Ubuntu you use. If hibernation is on you will get exactly the same result.

This worked, thanks.

---

### Post by Bucky Ball on 2015-09-25
Good news. :)

---

