---
title: "URGENT. Can't get my (nVidia Geforece Go 7950 GTX)  Driver to work...!!!"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by seijiroikeda on 2008-04-18
Upfront, I would like to thanks in advance for any help.!

**This is what I have:**

Alienware Area-51 m9750 Laptop.
Video card: nVidia Geforce Go 7950 GTX.

**Here it's my problem:**

I tried almost everything to get my nVidia Driver to work. 

**First**, I tried the "Restrictive Driver Manager" and it says "You hardware does not need any restricted drivers". 

**Second**, I tried the "Add/Remove Application", searched for nVidia. I activated the NVidia binary X.org driver ('new' and 'legacy' drivers, and they just simple don't do anything.

**Third**, I went to nVidia's website, download the right Driver for my video card (Geforce Go 7950 GTX), place the file on my Desktop, then ran it from the Terminal using SUDO, and still doesn't work. I get:

- You don't appear to have NVIDIA GPU supported by the 169.12 NVIDIA Linux graphic driver installed in this system. For further details, please see appendix SUPPORTED NVIDIA GRAPHICS CHIP in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

- You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

- Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

**Fourth**, I went to Alberto's Milone website, downloaded his Script program, and it installed perfectly, but when I click on "Install the NVIDIA driver" and I get:

- There was an error in the installation process. You can see the log file /var/log/envy-installer.log

After all this, I've been searching for other methods, codes or any other way to make my video card's driver to work and enable the 3D effects.

Any repository sites where the may have the right driver for my video card (nVidia Gefore Go 7950 GTX "Not SLI Enable")?. Or maybe, to get the ENVY to work properly? Or any other idea other than what I've tried already?

Again, thanks in advance for any help here, its really appreciate it.

---

### Post by dstew on 2008-04-18
Post the output of ```
lspci
cat /var/log/envy-installer.log
```

---

### Post by seijiroikeda on 2008-04-20
> **dstew said:**
> Post the output of ```
lspci
cat /var/log/envy-installer.log
```

This is what i get:


chino@chino-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
chino@chino-laptop:~$ cat /var/log/envy-installer.log
python pulse.py nvidia 
root@chino-laptop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
ENVY ERROR: Nvidia card not found

---

