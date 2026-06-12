---
title: "Driver Problem &amp; several questions to get started w Ubuntu"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by ScientificProp on 2012-02-01
First, I'm new to this Forum and in trying to get Ubuntu working. Before installing to a hard drive I'm trying to configure on a USB boot using the latest version 11.10 (64-bit) on my AMD64 HP machine. The main problem is the graphics card driver, I have a Zotac Nvidia 520 card. Seems like a default driver (VESA) installed (I can't switch to higher resolution, it's at 800x600). I have a 22" LG Flatron Wide monitor. The Additional Drivers window does not show any other driver options, but I know others are available, either from NVidia or from PPA. I started trying to complete the system upgrades, but there are 524 to do. When I tried to do all of them at once (and walked away), it failed.

Do I need to install upgrades or can I download a newer ISO that has them incorporated?

Why isn't the Additional Drivers finding any drivers?

I think there are other issues also, so I'm wondering if I should switch to the LTS version 10.04? But, I thought it'd be better to get used to the programs being introduced in 11.10...

Thanks.

---

### Post by bogan on 2012-02-01
Hi!, **Scientificpro**p.

I am running an nvidia GT520 card and was advised that only the latest NVIDIA driver v.290.10 would handle it properly.

Nvidia Download Drivers website will confirm that and give you lots of info. 

Do not use the nvidia-current driver which Additional Drivers or Synaptic might offer you.


I believe that the Iso files do not get revised between major issues.

All the best, **bogan**.

---

### Post by ScientificProp on 2012-02-01
bogan,
Thanks for the information. That helps clarify my next strategy. I already downloaded a .run file from Nvidia and I also have a .deb file from a PPA archive (?). Both are described as 290.10 driver.
So now I need to decide which to go with and how to install either a .run or a .deb file.
Earlier, I tried to dbl-click on the .deb file and was asked if I wanted to run in the Archive Manager - which I did. In the archive manager the only thing I could do was to Extract the files. It's not clear what I need to do next to install (load) the driver?
Does anyone have any insight?

---

### Post by bogan on 2012-02-02
Hi!, ScientificProp,

I am a little confused that you said>  " before I install to a hard disk". As far as I know you cant update things until you have done so, and  any changes will be lost when rebooting, including the new driver installation, and I do not believe a LiveUSB can be updated either.

I will not go into the .deb file installation, you will find that elsewhere.

To Install the nvidia driver all that is necessary is to CD to the folder where you have downloaded the .run file, make it executable and run it.
First, you should add some Blacklists to the /etc/modprobe.d folder, and then, as the nvidia driver must only be installed when the GUI xorg server and screen is inactive, reboot to a Text Terminal, or shut down the Xsession from a GUI screen, 

To do this check the /etc/modprobe.d folder for a file named blacklist.conf,
If it does not exist you will need to create one.

In the terminal enter:```
 gksu gedit /etc/modprobe.d/blacklist.conf 
```then add:```
 # Added for nvidia driver.
blacklist vga16fb
blacklist rivafb
blacklist rivatv
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidiafb
blacklist nvidia-173
blacklist nvidia-96
``` And Save As:  /etc/modprobe.d/blacklist.conf.

Reboot, preferable to Restart, and either:
From a GUI screen Terminal:```
 sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10
```OR:
From the Grub Menu, put cursor on the Ubuntu entry you intend as your primary usage and press 'e' to edit,
Go to the Linux boot line where it should have ' ro quiet splash' and add ' text'.
press Ctrl+x to boot.
At the prompt log in and enter password.
CD to where the nvidia file is and enter: dir
This will check you are in the right place and enable you to copy the exact name of the file.
```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto
```Follow screen instructions.
 You may get a warning that nouveau is running and must be purged first, but carry on, that's what the blacklists are for.
When complete reboot.
nvidia-installer, nvidia-settings and nvidia-XServer-config will be installed and you can adjust things to suit your hardware and wishes.

Good luck.
Chao!, bogan.

---

