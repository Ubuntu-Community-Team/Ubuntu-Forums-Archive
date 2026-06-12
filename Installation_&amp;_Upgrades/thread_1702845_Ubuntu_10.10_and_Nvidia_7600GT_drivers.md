---
title: "Ubuntu 10.10 and Nvidia 7600GT drivers"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by nikosdi on 2011-03-08
Hello,
I installed ubuntu 10.10 on my pc.I didnt have 3d acceleration on my computer so i tried to install nvidia-current drivers and glx-185.When my computer restarted i didnt have desktop only terminal.Is 7600GT compatible with ubuntu 10.10 ?My computer was running very good with ubuntu 7.10.Which driver i must install to have 3d acceleration?:o:o:o
thank you!

---

### Post by runeh76 on 2011-03-08
Hi check this out:


[http://www.ubuntuupdates.org/ppas/27]("http://www.ubuntuupdates.org/ppas/27")

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Hi check this out:


[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Is there an list of supported cards ? Because if the driver is not supported i must reinstall ubuntu (i installed ubuntu 7 times in one day)

---

### Post by runeh76 on 2011-03-08
Install it and go to Additional Drivers and there should be recommended driver marked as green.

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Install it and go to Additional Drivers and there should be recommended driver marked as green.

which package do you recommend to install at step 3 ?[FONT=monospace]
[/FONT]sudo apt-get install <package name> 

Could you please write the full command :D

---

### Post by runeh76 on 2011-03-08
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

I did it Checked additional drivers and recomended driver is activated but when i restarted my pc monitor is unable to display.
Now how can i change the resolution to a supported?
When ubuntu loads monitor says Video mode not supported but i can access the command line with ctr alt f2.Is there a way i can change res to a supported one ?

---

### Post by runeh76 on 2011-03-08
There should now be control-panel under **System / Administration**

---

### Post by nikosdi on 2011-03-08
I dont have display at all.The monitor can not display because of unsupported resolution or refresh rate!I can only use terminal now with ctr alt f2.

---

### Post by realzippy on 2011-03-08
1. Does your 7.10 version still exist?
   If so,we could use that xorg.conf..

2.If not,boot in recovery mode,there is an option "failsafe X" or
  something,which lets you boot in low resolution,then post the content  
  of the file: /etc/X11/xorg.conf



BTW,
doubt that it makes sense to run the xswat driver (which is currently 270.29).since you have an old card which used to work.
Want to say that the problem might not be the driver version...



EDIT:

**Is it an AGP or PCIe card?**(Both exists I think..)

---

### Post by runeh76 on 2011-03-08
Look this: [http://www.linuxquestions.org/questions/linux-newbie-8/using-a-terminal-to-change-resolution-672211/]("http://www.linuxquestions.org/questions/linux-newbie-8/using-a-terminal-to-change-resolution-672211/")

---

### Post by nikosdi on 2011-03-08
> **realzippy said:**
> 1. Does your 7.10 version still exist?
   If so,we could use that xorg.conf..

2.If not,boot in recovery mode,there is an option "failsafe X" or
  something,which lets you boot in low resolution,then post the content  
  of the file: /etc/X11/xorg.conf

1)It doesnt exist .... :(
2)There is no such a file in X11 directory:o(I didnt boot in failsafe X or recovery mode i dont know how to enter those modes because in ubuntu 10.10 there is no grub menu in my installation.I just used ctr alt f2 to access command line)

---

### Post by runeh76 on 2011-03-08
Post output: ```
cat /etc/X11/xorg.conf

```

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Post output: ```
cat /etc/X11/xorg.conf

```

no such file or directory.
//I used sudo X -configure to generate a new xorg.conf file
I cant post the output to the forum because i am using a different pc to read the forum.My ubuntu machine has only command line so i can only write by hand the output.

---

### Post by runeh76 on 2011-03-08
exactly from the terminal u type that command..

---

### Post by runeh76 on 2011-03-08
Check that earlier link, and make changes with:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by realzippy on 2011-03-08
sudo X -configure
 cannot create a xorg.conf for the nvidia-driver,this command would be
```
sudo nvidia-xconfig
```

You could try this,but it will claim *no nvidia-driver* or something..

Press "shift" during boot until menu opens...recovery mode.
Then you could at least uninstall the driver..
Back in 2 hours,good luck..

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Check that earlier link, and make changes with:

```
gksudo gedit /etc/X11/xorg.conf
```

That file doesnt exist.I used another monitor and i was able to have display.I created an xorg.conf file with sudo nvidia-xconfig.When i restarted the pc the x server failed to start and comand line appeared.I removed xorg.conf restarted the pc and x server started.But i cant change resolution via system preferences and Nvidia x server settings is not working
(You do not appear to use NVIDIA X driver error appears when i start System/Administration NVIDIA X Server properties.

---

### Post by realzippy on 2011-03-08
@runeh76

I may be wrong,but I think due to a failed nvidia-driver installation attempt there is no xorg.conf to open or edit.If *nvidia-xconfig* does not run,this is the case,

---

### Post by realzippy on 2011-03-08
> **nikosdi said:**
> That file doesent exist.I used onother monitor and i was able to have display.I created an xorg.conf file with sudo nvidia-xconfig.When i restarted the pc the x server failed to start and comand line appeared.I removed xorg.conf restarted the pc and x server started.But i cant change resolution via system preferences and Nvidia x server settings is not working
(You do not appear to use NVIDIA X driver error appears when i start System/Administration NVIDIA X Server properties.

So the driver is installed ...but not in use.
If so,do that again and post the xorg.conf so we can modify it.

---

### Post by nikosdi on 2011-03-08
> **realzippy said:**
> So the driver is installed ...but not in use.
If so,do that again and post the xorg.conf so we can modify it.

After creating the xorg.conf via nvidia-xconfig the x server fails to start.I created a backup file of the created xorg.conf and i ll post it now.I now have desktop enviroment because i deleted the xorg.conf file.If i create it again i wont have desktop enviroment.

---

### Post by nikosdi on 2011-03-08
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.29  (buildmeister@swio-display-x86-rhel47-02.nvidia.com)  Wed Feb 23 16:38:34 PST 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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

---

### Post by runeh76 on 2011-03-08
Yeah driver in use. Edit Section "Screen"


Option         "metamodes" "1024x768_60 +0+0"

---

### Post by realzippy on 2011-03-08
Which monitor (brand aso) do you want to run ?

---

### Post by nikosdi on 2011-03-08
> **realzippy said:**
> Which monitor (brand aso) do you want to run ?

I cant understand the question .....:P
I am a bit noob:P

//Edit I will install the driver again using the nvidia driver from nvidia.com if it fails again i will disable the driver

---

### Post by runeh76 on 2011-03-08
Yeah try that, and now u at least have xorg.conf. Remember that command to put resolution to xorg.conf if it do same thing.
There should read like this: (u can change what res/refresh rate u want



Edit Section "Screen"


Option "metamodes" "1024x768_60 +0+0"

---

### Post by nikosdi on 2011-03-08
I found the answer!I havent attached the power cable to the graphics card so the driver couldnt started!
Thanks for all your help!:D:D:D:D:D

---

### Post by realzippy on 2011-03-08
..fine!

---

### Post by runeh76 on 2011-03-08
Power cable...?

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Power cable...?

Yes ..... triple FAIL......
Sorry for the wasted time.......:(
and thank you again!!!:D

---

### Post by runeh76 on 2011-03-08
Where is Nvidia-card power-cable?

np u didnt waste my time.  :)

---

### Post by nikosdi on 2011-03-08
> **runeh76 said:**
> Where is Nvidia-card power-cable?

np u didnt waste my time.  :)

My nvidia card needs external power to operate.
The card was working fine without the power cable but without 3d acceleration.
Now the nvidia driv is working fine!

---

### Post by runeh76 on 2011-03-09
Okey, cool!  :)

---

