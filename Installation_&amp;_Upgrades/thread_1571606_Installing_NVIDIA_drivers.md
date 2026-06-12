---
title: "Installing NVIDIA drivers"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by deamon_knight on 2010-09-09
I'm installing 10.4 fresh but I can't get the Nvidia drivers installed. I'm using a 9400 GT. Ubuntu installs normally but when I try to enable to the proprietary driver, I get an error on reboot "Failed to initialize NVIDIA graphics device" and have to restart X. Any suggestions on how to get this working?

---

### Post by tommcd on 2010-09-09
Did you try to install the nvidia driver from nvidia.com? Or just the nvidia driver in the Ubuntu repos?

Anyway, first uninstall any nvidia driver(s) you may have installed.
Then boot up Ubuntu and hit ctrl + alt + F2. This will take you to a virtual terminal. Login and run:
```

sudo service gdm stop

```
This will stop the X server (just a precaution). Then to install and enable the nvidia driver:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
If you get errors, post them back here.
This is the most fail safe method to install the nvidia driver from the Ubuntu repos. The newest driver in the Ubuntu repos is the 195 driver; but that should work for your card:
[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

---

### Post by deamon_knight on 2010-09-09
Thanks Tommcd, I have only tried installing the nvidia driver from SYSTEM>ADMINISTRATION>HARDWARE DRIVERS. I've done a fresh install and tried activating the driver after all available updates had completed.

 I followed your instructions but only got as far as : "sudo apt-get install nvidia-current nvidia-settings" . "sudo nvidia-xconfig" reports command not found. When I rebooted, I got to the desktop, but now hardware drivers says "another version of this driver is in use"

Trying to run "sudo nvidia-settings" now launches the Nvidia X server settinsg application, but it reports "You do not appear to be using the nvidia X driver."

Any suggestions?

---

### Post by tommcd on 2010-09-09
Did you remove the nvidia driver from the:system > administration > hardware drivers before following my instructions?

Can you post the contents of your: *etc/X11/xorg.conf* file?

Also post the output of:
```
aptitude search nvidia
```

---

### Post by deamon_knight on 2010-09-10
I did remove the nvidia driver from hardware drivers before following you instructions. I had tried some suggestions from the Internet before posting, so I erased and reinstalled, and tried your instructions again and had the same result. I've reinstalled a third time and applied all the updates and added lucid proposed updates, as I had not done that last time. I haven't made any changes beyond that since this last reinstall, so lets consider this a fresh install.

Right now, there is no xorg.conf. in /etc/X11

Here is the output of ```
aptitude search nvidia
```

```
p   nvidia-173                                                       - NVIDIA binary Xorg driver, kernel module and VDPAU library                 
p   nvidia-173-dev                                                   - NVIDIA binary Xorg driver development files                                
p   nvidia-173-kernel-source                                         - Transitional package for nvidia-glx-173-kernel-source                      
i   nvidia-173-modaliases                                            - Modaliases for the NVIDIA binary X.Org driver                              
p   nvidia-180-kernel-source                                         - Transitional package for nvidia-glx-185-kernel-source                      
p   nvidia-180-libvdpau                                              - Transitional package for nvidia-185-libvdpau                               
p   nvidia-180-libvdpau-dev                                          - Transitional package for nvidia-185-libvdpau-dev                           
p   nvidia-180-modaliases                                            - Transitional package for nvidia-185-modaliases                             
p   nvidia-185-kernel-source                                         - Transitional package for nvidia-glx-185-kernel-source                      
p   nvidia-185-libvdpau                                              - Transitional package for nvidia-185-libvdpau                               
p   nvidia-185-libvdpau-dev                                          - Transitional package for nvidia-185-libvdpau-dev                           
p   nvidia-185-modaliases                                            - Transitional package for nvidia-185-modaliases                             
p   nvidia-96                                                        - NVIDIA binary Xorg driver, kernel module and VDPAU library                 
p   nvidia-96-dev                                                    - NVIDIA binary Xorg driver development files                                
p   nvidia-96-kernel-source                                          - Transitional package for nvidia-glx-96-kernel-source                       
i   nvidia-96-modaliases                                             - Modaliases for the NVIDIA binary X.Org driver                              
p   nvidia-cg-toolkit                                                - NVIDIA Cg Toolkit Installer                                                
i   nvidia-common                                                    - Find obsolete NVIDIA drivers                                               
p   nvidia-current                                                   - NVIDIA binary Xorg driver, kernel module and VDPAU library                 
p   nvidia-current-dev                                               - NVIDIA binary Xorg driver development files                                
i   nvidia-current-modaliases                                        - Modaliases for the NVIDIA binary X.Org driver                              
p   nvidia-glx-173                                                   - Transitional package for nvidia-glx-173                                    
p   nvidia-glx-173-dev                                               - Transitional package for nvidia-glx-173-dev                                
p   nvidia-glx-180                                                   - Transitional package for nvidia-glx-185                                    
p   nvidia-glx-180-dev                                               - Transitional package for nvidia-glx-185-dev                                
p   nvidia-glx-185                                                   - Transitional package for nvidia-glx-185                                    
p   nvidia-glx-185-dev                                               - Transitional package for nvidia-glx-185-dev                                
p   nvidia-glx-96                                                    - Transitional package for nvidia-glx-96                                     
p   nvidia-glx-96-dev                                                - Transitional package for nvidia-glx-96-dev                                 
p   nvidia-kernel-common                                             - NVIDIA binary kernel module common files                                   
p   nvidia-settings                                                  - Tool of configuring the NVIDIA graphics driver 

```

thanks again

---

### Post by deamon_knight on 2010-09-10
So I tried simply activating the Nvidia driver from hardware drivers after installing the Lucid Proposed updates, but I had the same result; Failed to Initialize NVIDIA device and start ubuntu in low graphics mode.

This also created an xorg.config file, here it is:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by tommcd on 2010-09-10
> **deamon_knight said:**
> ... so I erased and reinstalled, and tried your instructions again and had the same result. ...
Here is the output of ```
aptitude search nvidia

```        
p   nvidia-current                                                   - NVIDIA binary Xorg driver, kernel module and VDPAU library                 
p   nvidia-current-dev                                               - NVIDIA binary Xorg driver development files                                
i   nvidia-current-modaliases                                        - Modaliases for the NVIDIA binary X.Org driver    
                         
 
You must have done something wrong when following my instructions because your output from: "*aptitude search nvidia*" indicates that *nvidia-current* is not installed. (An "i" before a package means it is installed. A "p" before a package means it is not installed.

---

### Post by tommcd on 2010-09-10
> **deamon_knight said:**
> So I tried simply activating the Nvidia driver from hardware drivers ... but I had the same result; Failed to Initialize NVIDIA device and start ubuntu in low graphics mode.

This also created an xorg.config file, here it is:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

```
In your xorg.conf file, try changing the **Driver  "nv"** line to **Driver  "nvidia"** and then reboot and see if the nvidia driver is activated.

---

### Post by deamon_knight on 2010-09-11
Unfortunately that did not work. So I retried your steps from the beginning. I'm still stuck. Here is the output from xorg.conf


```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

```

and the output from "aptitude search nvidia"
```
p   nvidia-173                               - NVIDIA binary Xorg driver, kernel module and VDPAU
p   nvidia-173-dev                           - NVIDIA binary Xorg driver development files       
p   nvidia-173-kernel-source                 - Transitional package for nvidia-glx-173-kernel-sou
i   nvidia-173-modaliases                    - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-180-kernel-source                 - Transitional package for nvidia-glx-185-kernel-sou
p   nvidia-180-libvdpau                      - Transitional package for nvidia-185-libvdpau      
p   nvidia-180-libvdpau-dev                  - Transitional package for nvidia-185-libvdpau-dev  
p   nvidia-180-modaliases                    - Transitional package for nvidia-185-modaliases    
p   nvidia-185-kernel-source                 - Transitional package for nvidia-glx-185-kernel-sou
p   nvidia-185-libvdpau                      - Transitional package for nvidia-185-libvdpau      
p   nvidia-185-libvdpau-dev                  - Transitional package for nvidia-185-libvdpau-dev  
p   nvidia-185-modaliases                    - Transitional package for nvidia-185-modaliases    
p   nvidia-96                                - NVIDIA binary Xorg driver, kernel module and VDPAU
p   nvidia-96-dev                            - NVIDIA binary Xorg driver development files       
p   nvidia-96-kernel-source                  - Transitional package for nvidia-glx-96-kernel-sour
i   nvidia-96-modaliases                     - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-cg-toolkit                        - NVIDIA Cg Toolkit Installer                       
i   nvidia-common                            - Find obsolete NVIDIA drivers                      
i   nvidia-current                           - NVIDIA binary Xorg driver, kernel module and VDPAU
p   nvidia-current-dev                       - NVIDIA binary Xorg driver development files       
i   nvidia-current-modaliases                - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-glx-173                           - Transitional package for nvidia-glx-173           
p   nvidia-glx-173-dev                       - Transitional package for nvidia-glx-173-dev       
p   nvidia-glx-180                           - Transitional package for nvidia-glx-185           
p   nvidia-glx-180-dev                       - Transitional package for nvidia-glx-185-dev       
p   nvidia-glx-185                           - Transitional package for nvidia-glx-185           
p   nvidia-glx-185-dev                       - Transitional package for nvidia-glx-185-dev       
p   nvidia-glx-96                            - Transitional package for nvidia-glx-96            
p   nvidia-glx-96-dev                        - Transitional package for nvidia-glx-96-dev        
p   nvidia-kernel-common                     - NVIDIA binary kernel module common files          
i A nvidia-settings                          - Tool of configuring the NVIDIA graphics driver 
```

I discovered that I can't get to a virtual console with the "nv" nuveau? driver enabled. I get a screen full of "V"s on a pink background. I had to run in low graphics mode before I could get to a virtual console.

Thanks again TommCd

---

### Post by deamon_knight on 2010-09-11
I suppose I should have listed the error I got. It was "Failed to load module: NVIDIA . Module does not exist.

---

### Post by tommcd on 2010-09-11
Were you able to run: "*sudo nvidia-xconfig*" after installing the *nvidia-current* driver? 
You could try replacing your xorg.conf with mine and see if it makes a difference. First backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then relace the contents of your xorg.conf with this:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Fri Mar 12 01:42:27 PST 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
As you can see in the comments at the top, my xorg.conf was generated by running *nvidia-xconfig*.
You can replace the numbers for HorizSync and VertRefresh in the Monitor section with the correct values for your monitor if you want.
Also, make sure nouveau is blacklisted. Add this to the end of the 
*/etc/modprobe.d/blacklist.conf* file:
```
blacklist nouveau
```
Then reboot and see if it makes a difference.

---

### Post by deamon_knight on 2010-09-11
Ok. I have never been able to run nvidia-xconfig. I keep getting Command not found.

I Blacklisted the nooveau driver and replaced my xorg.conf with yours but still no luck, it gives an error and I have to restart x, then I can get to a low graphics mode.

The Error is "Failed to Load module 'NVIDIA' module does not exist."
"No drivers available."

---

### Post by tommcd on 2010-09-12
> **deamon_knight said:**
> Ok. I have never been able to run nvidia-xconfig. I keep getting Command not found.
I don't know why some people get this error about nvidia-xconfig being not found. It seems to follow a botched attempt at installing the nvidia driver, and then trying to install the nvidia driver properly from what I have seen.
 I have never had this problem in 5+ years of using Ubuntu with nvidia graphics cards. And I have never relied on the: system > administration > hardware drivers manager to install the driver. I always install the nvidia driver as per the instructions I gave in my first post in this thread.
> **deamon_knight said:**
> 
I Blacklisted the nooveau driver ... 
The driver to blacklist is **nouveau** and not **nooveau**. Please be sure you have the correct spelling of the driver blacklisted in */etc/modprobe.d/blacklist.conf* file.

---

### Post by deamon_knight on 2010-09-12
Thanks Tommcd, I mistyped in my post but I did blacklist the nouveau driver. I'll try a clean reinstall, enable the "proposed" updates, then blacklist nouveau, then stop gdm and install apt-get nvidia-current and nvidia-settings as you recommend.

I use Hardware Drivers (Is this Jockey BTW?, I'm not sure) because its there and I presumed it was the right way to do things. I've been using Ubuntu since Hardy and though I'm no expert it has worked for me this far. I was also confused as to weather other ways of install the nvidia drivers would break with kernel updates.

Also, on a personal note, if you don't mind me asking; If your location really is Philly it looks like you are in the same time zone as me (Columbus, Ohio). Do you really spend your nights helping random linux users with problems?

Thanks again, and I'll report back after that reinstall.

---

### Post by deamon_knight on 2010-09-12
No luck after a reinstall. I installed all updates then blacklisted the nouveau driver. From there I used :

```

sudo service gdm stop

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot
```

So nvidia-xconfig worked! Progress!

However, it still fails to load the desktop. I get "Failed to initialize NVIDIA graphics device. Check the syslog, Check Chapter 8 for common problems. Screens found but has useable configuration."

I then get the prompt to run Ubuntu in low graphics mode. If I load in low graphics mode I can get to the desktop, but the same thing happens when I reboot. Hardware Drivers report that the correct drivers are active and in use, Progress! However, nvidia-settings says the drivers aren't installed.

Here is my xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Any ideas on what to do next?

---

### Post by tommcd on 2010-09-13
> **deamon_knight said:**
> I did blacklist the nouveau driver. I'll try a clean reinstall, enable the "proposed" updates, then blacklist nouveau, then stop gdm and install apt-get nvidia-current and nvidia-settings as you recommend.
This is fine.
In my experience, I did noteven have to blacklist nouveau, nor did I stop X to install the nvidia driver from the Ubuntu repos.  I simply did this, as per my first post in this thread:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
When you install the nvidia driver from the Ubuntu repos as per my instructions it should create a file in *etc/modprobe.d* that blacklists nouveau. It did for me. Stopping X is just a precaution. It is mandatory to stop X when installing the driver from nvidia.com. I usually don't even bother with stopping X when I install the nvidia driver from the Ubuntu repos.
> **deamon_knight said:**
> 
I use Hardware Drivers (Is this Jockey BTW?, I'm not sure) because its there and I presumed it was the right way to do things. I've been using Ubuntu since Hardy and though I'm no expert it has worked for me this far. I was also confused as to weather other ways of install the nvidia drivers would break with kernel updates.
If you are installing the nvidia driver from the Ubuntu repos, the driver will be automatically reinstalled when ever there is a kernel update for Ubuntu. If you install the driver from nvidia.com, you will likely have to reinstall that driver when ever there is a kernel update for Ubuntu.
> **deamon_knight said:**
> 
Also, on a personal note, if you don't mind me asking; If your location really is Philly it looks like you are in the same time zone as me (Columbus, Ohio). Do you really spend your nights helping random linux users with problems?

Yes, I really am in Philadelphia. I am in Northeast Philly to be exact. And yes, I do spend my nights 
(and many days as well ...) hanging out in linux forums. 
I hang out here (and on the LQ forums and many other linux sites) for 2 reasons:
1. To increase my knowledge level and skill when using linux.
2. To try to help others when I can and pass the knowledge on.
I almost always accomplish goal #1 when hanging out here.
Sometimes I manage to accomplish goal #2 as well.

---

### Post by tommcd on 2010-09-13
Well, I just booted into Ubuntu to check on a few things ...

When I installed the nvidia driver from the Ubuntu repos as per my instructions in my first post in this thread, it created a *nvidia-graphics-drivers.conf* file in the */etc/modprobe.d* directory. The file is symlinked to: 
*/etc/alternatives/nvidia_modconf*.
 The contents of that file are:
```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```
If you do not have a *nvidia-graphics-drivers.conf* file in the */etc/modprobe.d* directory, then just create one and add the contents of that file that I posted here to it and then reboot and see if the nvidia driver works.

Also, here is the output of my: "*aptitude search nvidia*". The only nvidia stuff I have installed are the *nvidia-current* package and *nvidia-settings*:
```

tom@ubuntu:~$ aptitude search nvidia
p   nvidia-173                      - NVIDIA binary Xorg driver, kernel module a
p   nvidia-173-dev                  - NVIDIA binary Xorg driver development file
p   nvidia-173-kernel-source        - Transitional package for nvidia-glx-173-ke
i   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-180-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-180-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-180-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-185-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-185-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-185-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-185-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-96                       - NVIDIA binary Xorg driver, kernel module a
p   nvidia-96-dev                   - NVIDIA binary Xorg driver development file
p   nvidia-96-kernel-source         - Transitional package for nvidia-glx-96-ker
i   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit Installer               
i   nvidia-common                   - Find obsolete NVIDIA drivers              
i   nvidia-current                  - NVIDIA binary Xorg driver, kernel module a
p   nvidia-current-dev              - NVIDIA binary Xorg driver development file
i   nvidia-current-modaliases       - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-glx-173                  - Transitional package for nvidia-glx-173   
p   nvidia-glx-173-dev              - Transitional package for nvidia-glx-173-de
p   nvidia-glx-180                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-180-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-185                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-185-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-96                   - Transitional package for nvidia-glx-96    
p   nvidia-glx-96-dev               - Transitional package for nvidia-glx-96-dev
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
i A nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
tom@ubuntu:~$ 


```

---

### Post by tommcd on 2010-09-15
Please see this for a possible solution for your nvidia driver problem:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04)
I really hope this helps. Please update me with your progress (or lack thereof ...).

---

### Post by deamon_knight on 2010-09-16
Well, I'm still stuck. My *sudo aptitude search nvidia* looks like yours, and the */etc/modprobe.d/graphics-drivers.conf* also looks like yours. I followed the instructions on the page you linked and I'm still unable to start the NVIDIA device.

I do have a question, in the Binary Driver Howto, the second step is

```
sudo update-alternatives --config gl_conf
```

and offers 3 choices, 

```
  Selection    Path                                Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
  1            /usr/lib/mesa/ld.so.conf             500       manual mode
  2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

```

the default in my system is */usr/lib/nvidia-current/ld.so.con*, and that is the default for the nvidia-current driver I'm trying to install. 

Should I select one of these manual alternatives, choice 2?

Thanks again for all the help.

---

### Post by tommcd on 2010-09-16
> **deamon_knight said:**
> Well, I'm still stuck. ... I followed the instructions on the page you linked and I'm still unable to start the NVIDIA device.
Crap! I really thought that would fix it for you. I'm running out of ideas here.
> **deamon_knight said:**
> 
I do have a question, in the Binary Driver Howto, the second step is
```
sudo update-alternatives --config gl_conf
```
and offers 3 choices ...
the default in my system is */usr/lib/nvidia-current/ld.so.con*, and that is the default for the nvidia-current driver I'm trying to install. 
Should I select one of these manual alternatives, choice 2?

Well, if you followed the steps at: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04) And you also ran "*sudo ldconfig*" and "* sudo nvidia-xconfig*" as it says there, and the driver still is not enabled after a reboot, then I suppose it would not hurt to try selecting:
```
2   /usr/lib/nvidia-current/ld.so.conf   9700      manual mode
```
Try that and see if it makes a difference.

---

### Post by deamon_knight on 2010-09-18
Still no luck, I've got some odd behavior here.
Running:
```
sudo update-alternatives --config gl_conf
```
gives three choices, 0, the default, didn't work, although it did let me complete the following two steps,
```
sudo ldconfig
```
and
```
sudo nvidia-xconfig
```

choosing option 3 gives the same results.

Choosing option two fails when trying to run,
```
sudo nvidia-xconfig
```
it reports command not found.

?

I don't know where to go from here.

---

### Post by tejota on 2010-09-18
deamon_knight: I have the exact same problem as you. Tried reinstalling in several different ways with no luck.

I dont have a nvidia-xconfig either, says command not found.

Got a Vostro 3300 with Geforce 310M and Ubuntu Studio 10.04 with kernel 2.6.32-24 generic.

Just bought the computer and it is on hold until I fix that, really turning me down on ubuntu. Using nouveau as a temporary substitute gives a few weird glitches at boot/shutdown...

I subscribed to the topic and will check it again, can you please let me know if you solve the problem? I'll do the same.

---

### Post by tejota on 2010-09-18
**Wow I think I finally solved it somehow!**

I tried reinstalling it again with the driver from nvidia.com (search for your video card)

this time I had nouveau installed and activated, uninstalled all nvidia packaged using

"sudo apt-get --purge remove nvidia-*"

then rebooted and started in recovery mode, in root terminal.

executed the driver installation file with "sudo sh ..."

and ignored the message saying that it should be run with run-level 3, because whenever I did that, it was re-enabling X server and preventing me to continue the installation.

the nvidia installation software took care of the rest, blocked nouveau and etc, and when I rebooted there it was the NVIDIA logo and nvidia-settings working fine

:)

can you try this and let me know? I`m not sure of the steps I took prior to this method, from the several tutorials I went through..

---

### Post by deamon_knight on 2010-09-19
Tejota, I haven't tried the method you suggest because I think it will work. I know that sounds nuts, but here is the catch; as Tommcd noted earlier, installing the nvidia binary driver as you have done will require you to reinstall the driver whenever there is a kernel update. I've done it the way you describe in previous versions, but I'm trying to avoid that hassle. Reinstalling isn't really a disaster but it is a pain in the neck, and something I'd like to avoid.

The problem you are describing where *nvidia-xconfig* was not installed, was solved for me by taking tommcds advice and installing the nvidia-current driver on the the command line. However, the ultimate problem of the video driver not working remained.

I'm not sure how to proceed. I'm glad installing the nvidia binary straight from nvidia worked for you but I'm still not sold on that solution.

---

### Post by davidvandoren on 2010-09-19
Open your package manager and see if you have the 

linux-headers-generic-pae or no pae matching your kernel your are trying to boot.

---

### Post by tommcd on 2010-09-19
> **deamon_knight said:**
> Still no luck, I've got some odd behavior here.
Running:
```
sudo update-alternatives --config gl_conf
```
gives three choices, 0, the default, didn't work, although it did let me complete the following two steps, ...
What exactly happens when you choose option 0, the default?
I am not sure what else you can do at this point to get the nvidia driver from the Ubuntu repos working.
Can you post the contents of the */var/log/nvidia-installer.log* file? Perhaps this will give us a clue as to what the problem is.

If you can't get the driver from the Ubuntu repos working. perhaps you could try the driver from nvidia.com. I don't know what else you could try. I can not explain why the nvidia driver from the Ubuntu repos refuses to work for you. 
If you do try the driver from nvidia.com, you first have to remove all nvidia nvidia packages you have installed from the Ubuntu repos. You then have to install the build-essential package, and the linux headers for the kernel you are running. See this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
Also, you will need to make sure nouveau is blacklisted in */etc/modprobe.d/blacklist.conf*.
Reinstalling the nvidia driver from nvidia.com after a kernel update is not difficult. You just have to stop X and reinstall the driver. Then you restart X and the driver should be working.

---

### Post by deamon_knight on 2010-10-01
I haven't given up, RL just got in the way. I'll look into your suggestion and post when I know more.

---

### Post by deamon_knight on 2010-10-07
So, ```
uname -r
``` gives me ```
2.6.32-25-generic
```. Synaptic says "linux-headers-2.6.32-25-generic" are installed, but not "linux-headers-2.6.32-25-pae". I don't see an entry for "linux-headers-2.6.32-25-no-pae", but there is a long list of headers not installed, and I'll admit the long list of linux headers is one of those aspects of linux/ubuntu I do not understand.

if I run

```
sudo update-alternatives --config gl_conf
```

I get 

```
There are 2 choices for the alternative gl_conf (providing /etc/ld.so.conf.d/GL.conf).

  Selection    Path                                Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
* 1            /usr/lib/mesa/ld.so.conf             500       manual mode
  2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

Press enter to keep the current choice[*], or type selection number: 0

```

I had option 1 selected, if I change to option 0 I get this result:

```
Press enter to keep the current choice[*], or type selection number: 0
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.

```

I'm not sure that happened last time when i tried all 3 options, but they did not work in any case.

I'm just tinkering now, this isn't my main system, however, I'd like to get it working so its one less thing I have to remember to support.

---

### Post by dabl on 2010-10-07
@daemon-knight, I was just reviewing this thread and saw you are a fellow Buckeye*, so I've just gotta help you.  :)

First check this and see if you can follow it:  [http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

Then PM me if you need more.


* I'm in Dayton, went to OSU long ago.

---

### Post by deamon_knight on 2010-10-10
Thanks for the link dabl, but I'm still trying to avoid using the binary driver because this isn't my main system and I just don't want to spend that much more time making sure it works after updates. I know its not a huge problem but it is an inconvenience I'd like to avoid. I also inherit a number of abandoned system that I recycle to family members. If I can get them out of windows and into Linux its a plus (really love the LTS for this), but it can't break with a kernel update in those cases, so I'm really trying to educate myself on how to make the ubuntu package work. I may move to 10.10 in this case, but keep 10.4 for others. I wish there was an easy way to get the ubuntu package to work!

---

### Post by deamon_knight on 2010-10-11
Well, I tried Ubuntu 10.10, and the situation is similar. I can get it installed but when try to activate the drivers from "additional drivers" I have problems after the reboot. In this case, don't even get a display error, I just end up at a virtual terminal TTY1.

---

### Post by dabl on 2010-10-13
Unfortunately, the jockey thing has always been somewhat iffy for me, and that's with 3 different Nvidia cards over the past 4 years.

If you're even slightly interested in a KDE desktop for your friends and family, and the hardware has an Nvidia GPU in it, then I can testify that the nouveau driver looks great.  No 3D or fancy effects, mind you, but a very functional display on Nvidia hardware.  That would eliminate the issue with new kernels.  Some folks migrating from Windows find KDE a little more intuitive than Gnome.

---

### Post by wojox on 2010-10-13
You could try [manually installing]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx").

---

### Post by tommcd on 2010-10-14
For what it's worth, I just did a clean install of Lubuntu 10.10. I installed nvidia-current using apt-get. Then I ran the nvidia-xconfig and got the "command not found" error. I simply ran the command again and it worked.

---

### Post by dabl on 2010-10-14
The only pointer I can give, regarding the jockey-gtk or jockey-kde "Hardware Drivers" method, is to note that the driver has to be downloaded (in the background) after you click the "Apply" or "OK" or whatever.  So, the speed at which you get a result is dependent on the quality of your Internet connection, and the server at the other end.  I think sometimes people don't realize what's going on behind the curtain, and give it the normal time that you would allow for some "setting" to take effect, and then conclude that it's not working.  It takes some time to download the proprietary drivers.

---

### Post by deamon_knight on 2010-10-15
So , I'm dumb. I admit it. I already knew why this doesn't work. I have an Hauppauge PVR-1600 and I was exploring setting up a Mythbunutu (still am) and discovered this:

[http://ubuntuforums.org/showthread.php?p=6315676#post6315676](http://ubuntuforums.org/showthread.php?p=6315676#post6315676)

of course I had forgotten about it until yesterday. After removing the Hauppauge card the system boots to 10.10, with binary drivers enabled. Success! The same thing will likely be true of 10.04.

This leaves some questions for how I should proceed. Should I stick with 10.04 for any reason? I'm trying a few things with this box. I'd like to explore Virtual machines and running Windows & other OSes as guests. I'm also experimenting with Mythbuntu and the Hauppauge cards so I do want to get that to work. I'm also interested on running some games in WINE, I have Civ4 running nicely on my 9.10 system. I'm less familiar with the new GRUB2, I don't know how to add

```
vmalloc=256M
```

as a boot option. I guess that is the next step.

---

### Post by tommcd on 2010-10-16
> **deamon_knight said:**
>  I already knew why this doesn't work. ... After removing the Hauppauge card the system boots to 10.10, with binary drivers enabled. 
Glad you finally got this working! Perhaps if we had known about the conflicting TV card we could have solved this earlier.  
> **deamon_knight said:**
> 
Should I stick with 10.04 for any reason? I'm trying a few things with this box. ... I'm also experimenting with Mythbuntu and the Hauppauge cards ... I'm also interested on running some games in WINE ...
I would stick with Ubuntu 10.10. It has newer drivers and newer apps, including a newer version of Wine, which may be of benefit if you want to run Windows games in Wine. 
Perhaps you could install Ubuntu 10.10 and Mythbuntu 10.10 to separate partitions. This way you could experiment with Mythbuntu, while still having a reliable Ubuntu to boot in case you get into trouble with Mythbuntu.
> **deamon_knight said:**
> 
 I'm less familiar with the new GRUB2, I don't know how to add vmalloc=256 as a boot option.
Both 10.04 and 10.10 use grub2, so you will have to learn to work with grub2 in either case.
Here are 2 great tutorials for grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
To add extra boot options to the kernel when grub2 boots, add them between the quotes to the *GRUB_CMDLINE_LINUX_DEFAULT=* line in */etc/default/grub*, with a space between each option. For example, the default on Ubuntu is:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
So if you wanted to add *vmalloc=256M*, you would add it like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"

```
This appends vmalloc=256M to the kernel line of the normal boot option only. If you want to add vmalloc=256M to both the normal mode and recovery mode, then add it between the quotes to the *GRUB_CMDLINE_LINUX=""* line in */etc/default/grub*. See this section of the first tutorial:
[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)
Then don't forget to run:
```

sudo update-grub

```
This will write the changes to your */boot/grub/grub.cfg* file. You must run *sudo update-grub* after making any changes to grub2.

---

### Post by deamon_knight on 2010-10-19
Thanks Everyone, this has me up and running! Now its a few days of software installations ahead of me.

---

