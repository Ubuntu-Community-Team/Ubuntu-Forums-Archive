---
title: "Problems with AMD Ryzen AMDGPU-PRO with Ubuntu (All versions)"
date: 2018-10-15
forum: Installation &amp; Upgrades
---

### Post by 69saitco on 2018-10-15
Hello,
For over 15 years my pc was running with an Intel CPU Core 2 Duo (very old) and Windows 7, 80Gb & 160GB PATA HDD.
3 years ago I had enough of Windows due to 'to heavy' for cpu and costly in protection, so I changed to Ubuntu.
First trial on small laptop with Intel M cpu and Ubuntu Mate 15. Later with desktop and Ubuntu 16.04 LTS 32bit.
Last week I replaced the whole interior:
Asus A320M-K motherboard, AMD Ryzen 3 2200g CPU with 16GB DDR4 RAM & 2x 1TB SATA HDD.
My dream was to change from Ubuntu 16.04 to Mint 18.
To bad. This option was not possible and this was the beginning of my troubles (now SOLVED). SO BE AWARE!!!
The AMD Ryzen CPU has an internal GPU (Graphical Proc. Unit.) wich needs to be activated by AMDGPU-PRO-INSTALL.
Ubuntu 19.xx = FAILS Live CD does not even boot.
Ubuntu 18.xx = FAILS = Not possible to activate AMDGPU, even after updating and installing every possible tool. VGA in renderring and very slow
Ubuntu 17.xx = FAILS = Idem 18.xx
Several other versions (PClinoxOS, e.o.) of Linux would not even launch on live cd.

PFF!!!!!

After 3 days of stress... , via You Tube I found the only working solution for this type of CPU.
The only working way at this time is to install the Ubuntu 16.04 LTS, AMD-64bit.
To be able to activate the AMDGPU your Kernel needs to be version 4.15.
After the install, Ubuntu does this automatically, so no worry.
After update and reboot, you need to install the driver, provided by AMD VEGA GRAPHICS (Radeon 3xx series).
Search by browser 'Install AMDGPU-PRO for Linux' and you find the link.
Link : [https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)
To install this driver (+/- 300MB) it takes less then 15 minutes for download and install.
Update, reboot and 'Go In Speed' Finally...
Happy to able to stay with Linux, Ubuntu.
I hope other versions will be adapted to activate this AMDGPU...
Good Luck!

---

### Post by him610 on 2018-10-15
69saitco, that's great news.

All of the owners of AMD APU/GPU products should also be advised to read the release notes found here...[https://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx]("https://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx")

If one encounters difficulties, the *how to uninstall* section found here...[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx]("https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx")

---

### Post by QIII on 2018-10-15
AMDGPU is open source, hence Canonical can have it in their repo and it is installed automatically as part of the Ubuntu installation from 16.04 onwards.  AMDGPU installs automatically on kernels prior to 4.15 if such kernels will work with it and the hardware is appropriate.

AMDGPU-PRO is the proprietary overlay to AMDGPU and cannot be installed automatically because Canonical cannot have it in their repo.  This is not going to change.

It is NOT the CPU that is at issue, but the GPU.  If you are running an APU where the CPU ad GPU are on the same die, the physical location of the GPU is simply a matter of how APUs are manufactured.  It is still the GPU that matters.

---

### Post by 69saitco on 2018-10-15
Hello QIII. This is good to know. The only problem now is that Ubuntu offers to perform update to 18.xx. He who does this.... will return in the same problem as I did.
I really tried every thing in the 18.xx. No Way to make this work.
All help is SUPER welcome!!!

---

