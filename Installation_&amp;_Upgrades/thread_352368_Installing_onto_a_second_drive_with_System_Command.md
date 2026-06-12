---
title: "Installing onto a second drive with System Commander"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by pauldb126 on 2007-02-03
Hi,
I'm trying to install onto my second hard drive. I want Grub to remain on that drive and not in the MBR. This is because I use System Commander.

On the last screen of the installer, it even asks where you want Grub to be installed. I have tried two ways: putting it into the root partition and putting it into a separate boot partition, both on the second hard drive.

Both times, the installer stops because it's attempting to do something on the first drive in a fat16 partition and it doesn't like it. This is where System Commander will be. I think Ubuntu is trying to modify what it thinks is the MBR there.

BUT it should not be going near my first drive. I am specifically asking to install Grub to the second drive.

Anyway, it gives me the option of continuing but I always cancel the installation at that point because I do not want it to corrupt my System Commander files.

Any idea how to get around this?
Many thanks,
-Paul

---

### Post by pauldb126 on 2007-02-03
Sorry, I should have added that both drives are SATA. I notice that someone else has a similar problem where the 6.10 installer tries to install on hda and not sda or sdb. 

They didn't get the problem with 6.06 should I try that and later upgrade to 6.10?

Thanks,
-Paul

---

