---
title: "Problem installing Nvidia Geforce 6600 GT card"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by nssd2k on 2007-05-25
I am using Ubuntu 7.04 on Intel Mother board D865GSA with integrated Graphics Card Intel Extreme Graphics 2. I also have a Nvidia Geforce 6600 GT PCI card that I would like to use to full capcity. I have tired using all the instructions I could find on the web such as:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

and have also tried using Envy  and Automatix to install drivers. I have tired disabling onboard graphics card (this however does not work as when I reboot without my nvidia card, the system does not start GUI and gives whole host of errors) and nothing works.

Please help. Presently I  have uninstalled drivers and the xorg.conf relevant section is as follows:

Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

No other setting seems to work and gives black screen and I have to go for recovery of the original file.

Thanks.

nssd2k

---

### Post by vikramsharma on 2007-05-25
> **nssd2k said:**
> I am using Ubuntu 7.04 on Intel Mother board D865GSA with integrated Graphics Card Intel Extreme Graphics 2. I also have a Nvidia Geforce 6600 GT PCI card that I would like to use to full capcity. I have tired using all the instructions I could find on the web such as:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

and have also tried using Envy  and Automatix to install drivers. I have tired disabling onboard graphics card (this however does not work as when I reboot without my nvidia card, the system does not start GUI and gives whole host of errors) and nothing works.

Please help. Presently I  have uninstalled drivers and the xorg.conf relevant section is as follows:

Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

No other setting seems to work and gives black screen and I have to go for recovery of the original file.

Thanks.

nssd2k

Check this link out [http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04) .  You would have to boot Ubuntu in in safe mode and then modify is the /etc/apt/sourcse.list file .  The instructions are written/explained in the above mentioned link.  In case of any confusion feel free to ask.

---

### Post by nssd2k on 2007-05-30
> **vikramsharma said:**
> Check this link out [http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04) .  You would have to boot Ubuntu in in safe mode and then modify is the /etc/apt/sourcse.list file .  The instructions are written/explained in the above mentioned link.  In case of any confusion feel free to ask.


Thanks for your help, but nothing seems to work.

---

### Post by nssd2k on 2007-06-01
> **vikramsharma said:**
> Check this link out [http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu_Feisty#how_to_setup_nvidia_drivers_in_7.04) .  You would have to boot Ubuntu in in safe mode and then modify is the /etc/apt/sourcse.list file .  The instructions are written/explained in the above mentioned link.  In case of any confusion feel free to ask.

One correction - I am using an AGP and not PCI card. Still struggling with installation.

---

### Post by remta on 2007-06-02
Hello,

This might sound a little off topic..but i also have a Geforce 6600. And for some reason i can't find the original cd's for it anywhere. Is it possible for you to create an image and then send it to my e-mail address?

P.s. For others, I already went to Lexmark's site and downloaded the drivers for the card. But I wish to have the original software and not the update version from Lexmark.

---

### Post by geoff123 on 2007-06-09
Looks like this part of your xorg.conf file is a little messed up. Try to make it more like this..
Especially note the differences between the "Device" part and the "Screen" part.  Also, note that have the BusId part commented out worked for me - It should not be needed. I hope this helps.  


Section "Device"

   #comment out BusId from PCI:0:2:0
    Identifier     "NVIDIA GeForce 6600"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6600"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"

---

