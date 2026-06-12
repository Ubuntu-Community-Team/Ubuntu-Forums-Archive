---
title: "GRUB Cleaning after Upgrade from 10.04 to 12.1?...."
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by VcDeveloper on 2012-06-19
Hi,

I just upgraded from 10.04 LTS to 12.01 LTS and I had to use Boot Repair from LaunchPad to fix GRUB, but now I have several image listings of 10.04 LTS on the menu.

How and where do I manually clean up the unwanted entries; the cli update grub didn't work.

Thanks!...

---

### Post by drs305 on 2012-06-19
If they are in the same partition as your current OS (in the 10_linux section of /boot/grub/grub.cfg), you can use Ubuntu Tweak's Janitor function to remove older kernels. A link to Ubuntu Tweak is in my signature line. I also wrote a thread about removing older kernels *in the installed system but it could help located them elsewhere as well*
[HOWTO: Remove Older Kernels via GUI]("http://http://ubuntuforums.org/showthread.php?t=1587462")

If the remnants are on another partition and listed in the 30_os-prober section of /boot/grub/grub.cfg you can look for an existing grub.cfg file and remove it if the OS is no longer installed.

---

