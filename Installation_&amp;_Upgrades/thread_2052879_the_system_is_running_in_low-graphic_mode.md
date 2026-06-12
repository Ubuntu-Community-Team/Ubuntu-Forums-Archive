---
title: "the system is running in low-graphic mode"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by xinbye on 2012-09-04
i use gnome ubuntu 12.04
then i switch kde ubuntu
and now my moniter is the system is running in low-graphic mode

i try
     sudo vi /etc/lightdm/light.conf
           it 's blank before i change greeter-session=unity-greeter,
     chown lightdm:lightdm -R /var/lib/lightdm
     chown avahi-autoipd:avahi-autoipd -R /var/lib/avahi-autoipd
     chown colord:colord -R /var/lib/colord

it's fail (error low graphic)

i install nvidia card
     [http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

it't fail (error low graphic)


Could you help me please? 
Thanks

---

### Post by dino99 on 2012-09-04
if you have set an xorg.conf, then remove it :

```
sudo rm /etc/X11/xorg.conf
```

that issue is frequent with nvidia, purge it:

```
sudo apt-get purge nvidia*
```

and reinstall the genuine nvidia-current package (if you have installed/activated some ppa, then deactive them first and reupload again)

```
sudo apt-get install nvidia-current
```

then logout/in to know if that makes a difference.

---

### Post by xinbye on 2012-09-04
> **dino99 said:**
> if you have set an xorg.conf, then remove it :

```
sudo rm /etc/X11/xorg.conf
```that issue is frequent with nvidia, purge it:

```
sudo apt-get purge nvidia*
```and reinstall the genuine nvidia-current package (if you have installed/activated some ppa, then deactive them first and reupload again)

```
sudo apt-get install nvidia-current
```then logout/in to know if that makes a difference.

uhm, i do it but the system is running in low-graphic mode

[IMG]https://bugs.launchpad.net/lightdm/+bug/971891/+attachment/2991904/+files/bad-greeter.png[/IMG]

---

### Post by bogan on 2012-09-06
Hi!, **xinbye,**

After you installed the NVIDIA.com driver you Posted: "it't fail", What does this mean?

The nvidia installer.log shows a successful installation. So what in fact happened.?

If you followed **dino99**'s code you will have installed 295.40 which is bug-ridden.

Have you tried deactivating either the Integrated graphics or the nvidia card from Bios.? If not, please try both and Post the results..

According to Nvidia, your system cannot work unless that facility is available.> 
**[COLOR=Blue]For those with Integrated Graphics[/COLOR]**:    Extract from Nvidia's "Supported Products" notes:".... in particular,    notebook and all-in-one desktop designs with switchable  (hybrid) or    Optimus graphics will not work if means to disable the  integrated    graphics in hardware are not available. ...".If , before you try that, and in both selections, you run nvidia-settings or Nvidia Xserver Settings does it show the nvidia driver in use and can you reset the resolution ?

Please Post the output from: ```
lspci -nnk | grep -iA3 vga
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
/usr/lib/nux/unity_support_test -p
``` Copy/Paste the info to a New Reply edit box, highlight it and press the '#' symbol in the toolbar, to put it in Code boxes for easy reading.

The first command will show what drivers & modules are in use; [ with a lot more detail than your VGA attachement.]
The second will show details of the nvidia-current drivers available and if installed, which.
The third, if you do not have a nvidia.com driver installation will return 'not found' or 'no such'.

Chao!, **bogan**.

---

### Post by xinbye on 2012-09-07
hi, **bogan**
thank you to care about topic

something you need

```
 After you installed the NVIDIA.com driver you Posted: "it't fail", What does this mean?
```uhm, sorry
it's fail (error low graphic)


```
 my vga bios version: nvida N11M-GE1 VER70 .18 .3e .00 .0a
```  the output from: lspci -nnk | grep -iA3 vga

```
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:035b]
    Kernel driver in use: i915
    Kernel modules: i915
--
    Subsystem: Acer Incorporated [ALI] Device [1025:035b]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:035b]
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidia_current, nouveau, nvidiafb
```sudo apt-cache policy nvidia-current

```
nvidia-current:
  Installed: 295.40-0ubuntu1.1
  Candidate: 295.40-0ubuntu1.1
  Version table:
 *** 295.40-0ubuntu1.1 0
        500 http://vn.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://vn.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages

```cat /sys/module/nvidia/version
```
295.40
```i don't understand code
```
/usr/lib/nux/unity_support_test -p
```
i use comand 
```
 nvidia-settings 
```
it not run and request "-- help"
i used any option but it not run and request "-- help"

Chao!, xinbye

---

### Post by bogan on 2012-09-09
Hi!, **xinbye,**

What I meant by:" what does 'it't' mean ?", was: " In what way does what fail?:

The installation? The driver?, The display?, The command or The computer? - and HOW?

In other words: What are the symptoms of the fault you need help with? Is it just that you only get Low-Res screens?

Your Post shows you have both the nvidia.com 295.40 driver installed, and the Ubuntu 295.40 nvidia-current driver, at the same time. This will inevitably cause conflicts.

You should choose one or the other, or a later version instead.

If you copy/paste: " /usr/lib/nux/unity_support_test -p ", into a terminal, and press 'Enter', it will run that script, & it should show which OpenGL, and hence which driver is actually effective, and if unity  3d is fully supported.

I have no idea why you get a request for '-help' with 'nvidia-settings'. Try 'gksu nvidia-settings'. if that does not work run: ```
sudo apt-get update
sudo apt-get install nvidia-settings
```first and re-run nvidia-settings.

Chao!, **bogan.**

---

### Post by xinbye on 2012-09-12
Hi!, **bogan,**

```
What I meant by:" what does 'it't' mean ?", was: " In what way does what fail?:

The installation? The driver?, The display?, The command or The computer? - and HOW?

In other words: What are the symptoms of the fault you need help with? Is it just that you only get Low-Res screens?
```now, my problem is Low-Res screens and i want to use nvidia to resolve the problem

```
Your Post shows you have both the nvidia.com 295.40 driver installed, and the Ubuntu 295.40 nvidia-current driver, at the same time. This will inevitably cause conflicts.

You should choose one or the other, or a later version instead.
```how do i choose ?

====

sudo apt-get update
sudo apt-get install nvidia-settings

```
Reading package lists...
Building dependency tree...
Reading state information...
nvidia-settings is already the newest version.
The following packages were automatically installed and are no longer required:
  freespacenotifier galculator libgmtk0 libjpeg-turbo-progs xscreensaver
  klipper ksysguard kmenuedit kde-window-manager-common libkdecorations4
  libkwinglutils1 giblib1 systemsettings kdm elementary-icon-theme
  python-pysqlite2 kinfocenter libgmtk0-data libksignalplotter4 libqt3-mt
  scrot libjpeg-progs libgmlib0 amarok-help-de xscreensaver-data
  amarok-help-en libkwineffects1abi3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
```i use
     

 ```
     nvidia-settings 
```it not run and request "-- help"
i used any option but it not run and request "-- help"



Chao!, **xinbye.**

---

### Post by bogan on 2012-09-13
Hi!, xinbye,

You Posted: > how do i choose ?You decide which driver you want to use, remove both the existing versions, and either use the default nouveau driver, or install the one you  want to use.

Try both ways and see which is best. I would recommend not using the 295.40 nvidia-current as it is bugged. Rather, if you want to use an nvidia-current driver, use the post -release updates version offered in Additional Drivers, or the x-swat ppa 304.43 version.

I just do not know what causes the " it not run and request "-- help" " message, please post the actual message. 
If you make a typo in entering the code you should get a message saying command not known or not found and suggesting you run --help with the command which will list the options. Is that what you did?

In fact you should run 'nvidia-settings' from root. ie use ```
gksu nvidia-settings
``` but try: 'nvidia-settings --vv' You should get something like: ```
 $ nvidia-settings --vv
nvidia-settings:  version 304.43  (buildd@litembilla)  Tue Aug 28 03:04:38 UTC
2012
  The NVIDIA X Server Settings tool.
This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.
$ 
```Chao!, bogan.

---

### Post by bogan on 2012-09-13
Hi!, **xinbye,**

Reviewing the earlier Posts, I see that trying to install 'nvidia-settings' got a message that it was already the latest version, so perhaps, if it is not running, it is corrupted, & that is one problem's cause.

So run:```
 sudo apt-get install --reinstall nvidia-settings
```When it is properly installed you should also  be able to use it via 'Dash'.

Click on the Ubuntu 'Dash' Icon, and type 'nv', it should display an Icon with the Nvidia logo, entitled " NVIDIA X Server Settings"  clicking on which runs the same program as 'gksu nvidia-settings' does from a terminal.

I also see that the same report notes that there are 72 packages that need updating. You really should update regularly; there is probably a kernal update included in that list.

Chao!, **bogan.**

---

### Post by xinbye on 2012-09-15
Hi!, **bogan,**

my new version nvidia
```
$ 
nvidia-settings --vv

nvidia-settings:  version 304.43  (buildd@litembilla)  Tue Aug 28 03:04:38 UTC
2012
  The NVIDIA X Server Settings tool.
This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.
$
```when i reboot, the screen blank

i configure some command

```
Open and edit xorg.conf like this: sudo nano /etc/X11/xorg.conf. 

Find the line that says: Section "Screen" 

Insert a new line that says Option "UseDisplayDevice" "DFP". 

```and 

```
sudo gedit /etc/modprobe.d/blacklist.conf

[CODE]blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-173 
blacklist nvidia-96
```[/CODE]and

```
RUN+="/sbin/modprobe nvidia"
options nouveau modeset=0
sudo update-initramfs -u
```my problem is the screen blank?
what should i do ?
thank

Chao!, **xinbye.**

---

### Post by bogan on 2012-09-15
Hi!, **xinbye**,

Did you run 'nvidia-settings', without the '--vv'??

At what stage do you get the blank screen ?

Do you get a grub menu? a login screen ? Can you login ?

Can you boot via Recovery if you get the grub menu ?

At the blank screen, [ or at login screen ] do you get a terminal login prompt if you press: 'Crtl+Alt+F1' ?? 

[If you do, to return to the GUI{?} mode, press:  'Crtl+Alt+F7'].

If you can get to a terminal, please re-post:```
lspci -nnk | grep -iA3 vga 
sudo apt-cache policy nvidia-current 
cat /sys/module/nvidia/version 
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan.**

---

### Post by xinbye on 2012-09-16
Hi!, **bogan**,

```
Did you run 'nvidia-settings', without the '--vv'??
```

i run 'nvidia-settings -vv'

```
At what stage do you get the blank screen ?
Do you get a grub menu? a login screen ? Can you login ?
Can you boot via Recovery if you get the grub menu ?
At the blank screen, [ or at login screen ] do you get a terminal login prompt if you press: 'Crtl+Alt+F1' ?? 
[If you do, to return to the GUI{?} mode, press:  'Crtl+Alt+F7'].

```

first system boot grub ( have grub recovery)
then show icon KDE
then blank screen
then i press Crtl+Alt+F1 (F7) , it's not get a terminal login prompt or anything

something you need

lspci -nnk | grep -iA3 vga 

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:035b]
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:035b]
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb
```

sudo apt-cache policy nvidia-current 
```

nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1.1
  Version table:
     295.40-0ubuntu1.1 0
        500 http://vn.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 http://vn.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
```

cat /sys/module/nvidia/version 

```
304.43
```

/usr/lib/nux/unity_support_test -p

```
Error: unable to open display
```

thank for your help.

Chao!, **xinbye.**

---

### Post by bogan on 2012-09-18
Hi!,** xinbye,**

We do not seem to be getting very far, do we?

How are you getting to a Terminal? 

Please run ```
gksu nvidia-settings
``` and Post the results. Do you get a "Error: unable to open display" message? { that is without the '--vv', which only tells what version is installed, and does not run the configuration program}.

Re-reading all the Posts, I do not see anything to say you tried the suggestion in my Post #4:
> Have you tried deactivating either the Integrated graphics or the nvidia  card from Bios.? If not, please try both and Post the results..

According to Nvidia, your system cannot work unless that facility is available.[QUOTE]  **[COLOR=Blue]For those with Integrated Graphics[/COLOR]**:*     Extract from Nvidia's "Supported Products" notes:".... in  particular,    notebook and all-in-one desktop designs with switchable   (hybrid) or    Optimus graphics will not work if means to disable the   integrated    graphics in hardware are not available. ...".     *   [/QUOTE]One thing you could try, with the hybrid Intel graphics working, is to edit the Grub menu Script [ press 'e' with Ubuntu highlighted ] and add to the Linux Boot line: "video=1280x1024-24@60" {without quotes}, & press 'Crt+x' to boot.

It is reported that this can force the recognition of the Intel i915 driver. I know this is not what you want, and I do not know if it will work with a conflict with the nvidia driver, but it might show us something. If necessary, change the figures to those of your Monitor's native resolution.

Chao!, **bogan.**

---

