---
title: "From ATI video card to Nvidia Steps?"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by onlybui on 2007-01-23
Hi Was wondering what would be the best way to install the nvidia drivers so I can boot up using the nvidia drivers. Should I take out the nvidia card and then boot into Ubuntu 6.10 using onboard ATI card and then follow these instructions [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) and then restart and put in new nvidia card? cause it wont boot using mesa....

and how do I back up the ati drivers so I can reinstall them when I take out the Nvidia card...

---

### Post by sterilegenie on 2007-01-23
I would think you could edit your xorg.conf file and change the driver to "nv", shut your computer down, install your new nvidia card and restart the computer. This should work. :biggrin:

P.S 
You dont need to backup your ati drivers, they will remain on your system until you remove them.

---

