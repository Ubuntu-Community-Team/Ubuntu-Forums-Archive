---
title: "Installing 8.04 on Dell XPS 720 w/ RAID 1, getting &quot;Missing Operating System&quot;"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by JMann on 2008-04-02
I'm trying to install 8.04 on a new Dell XPS 720 machine with a RAID 1.

I manually partitioned both hard drive for RAID 1 configuration, and the rest of the installation seemed to go fine, but on restarting the computer I got a message saying "Missing Operating System."

Has anyone else had this problem that can give some advice?

Thanks.

---

### Post by mrsteveman1 on 2008-04-02
I believe that message is part of the boot code that Windows installs by default, either in the MBR or the VBR.

Have you tried manually reinstalling grub to each drive again?

Since this is a mirror config it would be a good idea to ensure grub is installed to the actual partition on each drive, and that there is generic boot sector code in the MBR of each disk.

---

### Post by jeffhollon on 2008-04-02
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

give this link a look, helped me out a ton

jeff

---

### Post by JMann on 2008-04-02
> **mrsteveman1 said:**
> I believe that message is part of the boot code that Windows installs by default, either in the MBR or the VBR.

Have you tried manually reinstalling grub to each drive again?

Since this is a mirror config it would be a good idea to ensure grub is installed to the actual partition on each drive, and that there is generic boot sector code in the MBR of each disk.

Thanks Steve, this solved the issue.

I booted off the super grub cd and selected "Grub MBR & Linux Autotmatic" and it's working fine now!

---

