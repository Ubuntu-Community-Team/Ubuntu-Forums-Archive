---
title: "Hardy 8.04 Upgrade on D620 Kills Video Resolution"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by paulnema on 2008-05-18
--------------------------------------------------------------------------------

Took the plunge and upgrade to hardy 8.04 from my previous version of 7.10 (which was running GREAT). Now my hardy version will not give me a resolution greater than 800X600 with a fixed refresh rate of 61 Hz. 

After enabling the restricted NVIDIA driver and rebooting I get an error msg stating "Ubuntu is running in low-graphics mode". I go through the configure screens but cannot find the current driver. So, something is not healthily.

With 7.10 I was running a restricted driver from NVIDIA.

Some details:
Chip Set: 256MB NVIDIA Quadro NVS 110M TurboCache, Latitude D620
Dell: Latitude D620

Any help would greatly be appreciated.

Thanks

---

### Post by iaculallad on 2008-05-18
To fix your limited resolution problem do this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf

Locate the section named "Screen" then copy and paste (merge) the lines which does not contain any asterisk and restart your gdm.

*Section "Screen"
	*Identifier	"Default Screen"
	*Device		"Intel Corporation 82865G Integrated Graphics Controller"
	*Monitor		"771S"
        *DefaultDepth 24
        SubSection "Display"
        Depth 24
        Modes "1280x1024"
        EndSubSection
*EndSection

---

### Post by paulnema on 2008-05-18
Thanks
After restarting the gdm, resoultion is now 1280x1024.  
Decided to enable my NVIDIA driver and rebooted.  Resolution is now back to 640x480.  Any other ideas for a clean fix?

---

### Post by iaculallad on 2008-05-18
Check if you enabled your main,universe,restricted,multiverse
System->Administration->Software Sources

then from your terminal:

sudo apt-get update && sudo apt-get upgrade

and try enabling your restricted nvidia driver.

Could you post the output of this: lspci | grep VGA

---

### Post by paulnema on 2008-05-18
main,universe,restricted,multiverse all enabled

ran the apt-get (update && upgrade)
NVIDIA was enabled

root@LX-D620:~# lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

Thoughts?

---

### Post by paulnema on 2008-05-18
Follow Up on dmesg data:

root@LX-D620:~# dmesg | grep -i nvr
[   18.408000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   33.200000] NVRM: API mismatch: the client has the version 169.12, but
[   33.200000] NVRM: this kernel module has the version 100.14.19.  Please
[   33.200000] NVRM: make sure that this kernel module and all NVIDIA driver
[   33.200000] NVRM: components have the same version.
[   38.276000] NVRM: API mismatch: the client has the version 169.12, but
[   38.276000] NVRM: this kernel module has the version 100.14.19.  Please
[   38.276000] NVRM: make sure that this kernel module and all NVIDIA driver
[   38.276000] NVRM: components have the same version.
[   43.352000] NVRM: API mismatch: the client has the version 169.12, but
[   43.352000] NVRM: this kernel module has the version 100.14.19.  Please
[   43.352000] NVRM: make sure that this kernel module and all NVIDIA driver
[   43.352000] NVRM: components have the same version.

Something is not right with the current modules.  Anyone have better knowledge what these messages mean?

---

### Post by iaculallad on 2008-05-18
Try this one: Reboot your PC then hit ESC when you reach GRUB, select your recovery option and you will arrive at the root terminal:
sudo apt-get update && sudo apt-get upgrade
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common

sudo apt-get install build-essential xserver-xorg-dev
shutdown -r

Or if this still fails, try installing Envy and use this to install your NVIDIA driver.

sudo wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu4_all.deb)
sudo dpkg -i envy_0.9.4-0ubuntu4_all.deb
sudo apt-get install -f

---

### Post by paulnema on 2008-05-22
Closing this issue out
Seems this is a reoccurring issue...
My solution, back everything, fresh install of 8.04
All is well

---

### Post by iaculallad on 2008-05-22
> **paulnema said:**
> Closing this issue out
Seems this is a reoccurring issue...
My solution, back everything, fresh install of 8.04
All is well

Sure hit :guitar:

---

