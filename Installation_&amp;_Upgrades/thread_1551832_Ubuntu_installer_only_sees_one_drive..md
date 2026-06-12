---
title: "Ubuntu installer only sees one drive."
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by cn23 on 2010-08-12
Hey all,  I went to install Ubuntu 10.04 64bit tonight on my new system, with the intention of running it alongside Windows XP when the installer gave me a scare.

First, applicable parts of my setup.

2 Hard Drives
300GB IDE Drive - Currently has Win XP (Don't Intend on Moving It)
1.5 TB SATA Drive - A few pieces of data

When I ran the installer, it only found the 1.5TB drive which concerned me.  I was afraid that since the XP drive wasn't seen, GRUB wouldn't see XP as an option to boot from and I'd be locked out of my XP install.  Now, I do intend on installing Ubuntu on the 1.5TB drive, it just seemed strange that the other one wasn't there.  I assume there's something wrong here, but as long as GRUB sees the XP install, I'm not too worried, just hoping someone can confirm that everything will work out right when I go ahead and install or give me steps to fix it.  I realize I'm terrible at explaining, so let me know if you need me to clarify anything.

Also, not sure if it matters but, I'm installing from a flash drive.

Thanks in advance for any help!

---

### Post by ubunterooster on 2010-08-12
And if it does not see the XP drive, you can change the boot order via the motherboard and dualboot that way. I do not see this as a problem that is dangerous.

---

### Post by MAFoElffen on 2010-08-12
> **ubunterooster said:**
> And if it does not see the XP drive, you can change the boot order via the motherboard and dualboot that way. I do not see this as a problem that is dangerous.
True... I have ASUS A8N32-SLI Deluxe with multiple IDE's and SATA's and have BIOS popup for boot... But Ubuntu's "install" didn't see the IDE's until I went to manual mode for the partitioning.  My installs went okay from there, including everything in the GRUB2 menu items (look at sig) except the Solaris OS's which I had to add manually and chainload.

Question to "cn23"- If you run the LiveCD do you see the other drive?

---

