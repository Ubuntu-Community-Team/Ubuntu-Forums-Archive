---
title: "RPM Pkg. Mngr or Debian (DPKG)"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2005-11-19
Trying to install modem driver, I need to select a "method" from the options shown below, Do I use A or B?


"If your Linux distribution supports the RPM Package Manager, it is easiest to install the binary RPM package with METHOD A. If your system is based on Debian (DPKG), METHOD B is for you. METHOD C is for distributions without RPM or DPKG support, or those who prefer not to use packages."

---

### Post by btdown on 2005-11-19
You Want the DPKG method...

if you download a .deb file, you would install it (as root) with dpkg -i <filename>

---

### Post by amwil1024 on 2005-11-19
Thanks to all so far,

I have downloaded linux modem driver for my conexant hcf modem from Linuxant. 

I have it unzipped and on a floppy disk,

I'm pretty sure the ?command/?root to install will be,

dpkg -i hcfpcimodem_1.08full_k2.6.12_386_ubuntu_i386.deb

Where do I enter the above comand?, 

Do I simply insert the floppy in the drive and it will be found and installed?

Can I do this running livecd?

All I'm doing is trying to prove it will work on my pc before buying the full version of linux driver. I'm not ready to go dual os yet, not until I can get onthe Internet and after format of HD after virus checks then reoad of Win98SE with minimal software.

---

