---
title: "Xubuntu 13.04 64-bit will not install properly"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by Glen_Wilson on 2013-09-02
I have downloaded Xubuntu 13.04 64-bit as an ISO and as a torrent, and both are buggy during installation to a Vell Vostro 230 with Core 2 Quad Q8400 processor. I have run through the inatallation process several times. As far as I can tell, the installation program never offers options for grub installation and never installs grub to the hard disk even though the installation process finishes and declares itself complete. I have been running the 32-bit version with no problems whatsoever on several systems, including this same identical box. Updating grub from another partition on the computer finds the 64-bit installation, but the grub.cfg entries are non-standard and will not boot the system.

I have no idea what the cause of this is, but it's a pretty plain vanilla 2010 computer. I ended up installing the PAE kernel to my existing 32-bit installation to gain access to the ful 4 GB of ram (only 3 GB is available with the generic non-PAE kernel).

If you're having this problem, you are not alone!

**UPDATE:**  Should have checked sooner, but the 64-bit installer installed grub to the first hard drive in my system even though I was installing Xubuntu to the second hard drive in the system and booting from that drive. So, the system boots properly from the other hard drive, but that was NOT my intention. I have never installed a system that did not allow you to specify where grub should be installed and then ask permission to install it. In my case, it is not a problem. In someone elses case, it could be.

---

### Post by rai_shu2 on 2013-09-02
Actually, you can select it, but I've only ever seen it on the "Something Else" screen. See [this for an example]("https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29:").

---

