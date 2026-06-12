---
title: "Upgrade 14.04LTS Blank Screen Nvidia Graphics Card"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by Jerry_Price on 2015-07-06
I know this is and old problem with many existing threads and the sticky ongoing thread but I'm going berserk. I'm pretty new at this.
Hardware: Toshiba Tecra M5 with a Nividia Quadro NVS 110m  graphics card and it's 9 years old.

I have been using Ubuntu for a year now and it's worked just fine. When I installed it I used "nomodeset" in the grub menu to get unity to load and then the Synaptic Package Manager to install an Nvidia driver 304.117 and it's worked through all the updates and upgrades until a week ago.

I had been away for 2 months, got home turned on the computer and Ubuntu loaded OK, I updated and the reboot installed a unity screen that was unreadable and unworkable.
I have since then tried all the suggestions that I have obtained from this forum and google to try to get the Unity screen up and running at a reasonable speed - and failed.

I have reinstalled ubuntu with kernel 3.13.0-30. It boots to the Password entry screen, enter password and it freezes. I then use the "nomodest" in the grub menu and it will get to the unity screen using the nouveau driver. This appears to be in a low graphic mode and works very slowly. I loaded Synaptic Package Manager and looked for Nvidea drivers and 304.117 (the one that did work) is no longer there. I tried 304.125 and that loads but gives me the unreadable, unworkable screen. The other one that.s in the package will no load.

I then reboot to the password screen do a control alt F1 and follow the instruction in the "sticky" at "Notes about Nvidia cards and SLI
sudo apt-get update 
sudo nvidia-installer --uninstall  # this may return not found, but do it just in case it is there. 
sudo apt-get remove nvidia-* 
sudo apt-get install linux-headers-('uname -r') 
sudo apt-get install nvidia-current 
sudo nvidia-xconfig 
sudo apt-get update
I then reboot and get the same unworkable unity screen. No extra Nvidia drivers appear to have been loaded.

I then tried the instructions in the "Table of Contents" at the end of the sticky, Installing Nvidia Binary drivers, I am doing this from the command line obtained from Ctrl Alt F1 at the password screen. I get to the line :
sudo apt-get install build-essential gcc -4.5....etc and it doesn't find the packages or the linux-headers etc.
I tried to load the Nvidia proprietory driver number 319.76 listed on the Nvidia site as the driver for the NVS110m but that failed and the 304.117 driver downloaded from the Nvidia site also failed.
I haven't tried Solution Step 11 yet as it's getting complicated and I wanted to find out if the computer or graphics cards are just too old(is that why 304.117 is not included in the Synaptics Packages... or am i doing something or not doing something basic 
A live CD will not load.
I have reinstalled unbuntu again to get a fresh start
I would love some guidance on where to go from here. 
Thanks
Jerry

---

### Post by ubfan1 on 2015-07-06
You might try a lower system requirements release like Lubuntu.  unity just proved too much for my old (9 yr HP with Nvidia 304.125 driver).  I went through a similar problem -- thought my motherboard was dying when using the 304.117.  Looked at it months later, and 304.125 was the current, which was now the same as the xorg-edgers version.  Turn off that ppa if you have it, it's not needed.  I did notice that there was an unnoticed problem building the nvidia-304.ko module from the software updates/additional drivers selection of nvidia-current.  Check in /lib/modules/... for the nvidia-304.ko driver -- if not present in your running kernel directory, rebuild it from the command line:
sudo apt-get --reinstall install nvidia-current
and watch for any errors.  Once the nvidia module was present, it should show up after a reboot in the lsmod output (not the nouveau or vga).  When you get the nvidia module in use, getting rid of unity may solve your other problems (install another desktop like xfce4 or just use Lubuntu).

---

### Post by Jerry_Price on 2015-07-07
Thanks ubfan1
I took your advice and installed XFCE and was give the option of using Xubuntu. That seems to be working OK. pretty fast and stable and using the 304.125 driver.
Although I'm up and running I'm still a little confused as to why ubuntu worked just fine for a year and then crashed with an upgrade. Do they right upgrades to suit the newer computers knowing that older computers will just not handle to new software ??? and if that is the case how come xubuntu handles the same driver just fine.
Cheers anyway

---

