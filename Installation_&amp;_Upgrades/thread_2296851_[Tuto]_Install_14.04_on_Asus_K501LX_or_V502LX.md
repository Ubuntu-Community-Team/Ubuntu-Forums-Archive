---
title: "[Tuto] Install 14.04 on Asus K501LX or V502LX"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by thatoo2 on 2015-09-29
Before going further, my computer is the persian version of K501LX, it's a V502LX. Differences are minimal such as the keyboard (mine has a persian keyboard which doesn't have backlit, I hope the backlit works for lucky owner of V501LX).

 I installed Ubuntu 14.04 because I trust more the LTS.

 To install the last version of the nvidia driver, I add the repository ppa:graphics-drivers/ppa
```
*sudo add-apt-repository -y ppa:xorg-edgers/ppa*
```
```
*sudo apt-get update*
```
 
 Then
 I assure that  bumblebee is not install, I checked in synaptec and I entered that command anyway
```
*sudo apt-get purge bumblebee* primus libvdpau-va-gl1*
```
 
 Then I installed Prime
```
*sudo apt-get install nvidia-prime mesa-utils vdpau-va-driver*
```
 
 Then
 I installed the addon drivers nvidia-355, if it's not offered through the settings (software and update), you can enter the command  
```
*sudo apt-get install nvidia-355*
```
 and then you enter
```
*sudo apt-get install nvidia-settings*
```
```
*sudo reboot*
```
 
 It works, your two graphic card are good to go. You can change it from the Nvidia setting and then reboot. You can also install prime-indicator
```
*sudo add-apt-repository ppa:kranich/cubuntu*
```
```
*sudo apt-get update*
```
```
*sudo apt-get install prime-indicator*
```
 but I don't recommend it because it only logout/login and that work only from Nvidia to Intel, to change from Intel to Nvidia, you need to restart or you'll face an error.
 
 If you can't control the brightness, just follow that,
 (source : [http://ubuntuforums.org/showthread.php?t=2028269](http://ubuntuforums.org/showthread.php?t=2028269) and [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/))
 
 In /etc/X11/xorg.conf
 add
 
[PHP]      Option "RegistryDwords" "EnableBrightnessControl=1"[/PHP]
 
 below

 [PHP]Section "Device" 
     Identifier "nvidia"  
     Driver "nvidia" 
     BusID "PCI:4@0:0:0"[/PHP]
 
 and, in /usr/share/X11/xorg.conf.d/20-intel.conf
```
*sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf*
```

 add
 
 [PHP]Section "Device" 
     Identifier "intel"  
     Driver "intel" 
     BusID "PCI:0@0:2:0"  
     Option "AccelMethod" "SNA"  
     Option "Backlight" "intel_backlight"  
 EndSection
[/PHP]

For me, the brightness works now in the settings in both nvidia and intel, but the hotkey (fn f5/f6) are not yet working.
You can add a shorcut linked to the following command in order to decrease brightness
```
xbacklight -dec 10
```
and an other one to the following comand to increase brightness
```
xbacklight -inc 10
```

If you don&#8217;t want the brightness to start at maximum, open the &#8220;Startup Applications&#8221; and add a new startup item with the command:
```
xbacklight -set 40
```
(40 is for 40 % but you can set the one you want)

 For the wifi/airplane hotkey, the only one which is not working with the brightness, follow that (source : [http://forum.ubuntu-fr.org/viewtopic.php?id=1770081](http://forum.ubuntu-fr.org/viewtopic.php?id=1770081))
```
*sudo gedit /etc/default/grub*
```

 Replace in the file, the line

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/PHP]
 by  
[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="[/PHP]
 Save it and then you add this command in your terminal
```
*sudo update-grub*
```
 Restart the computer and the hotkey should work. For me, all work except the brightness.
 

 To make the touchpad working properly,
You could either
install the driver
```
sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms
```
Then reboot, or do this to get things working instantly, as documented in README:
Code:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

or update the kernel
I followed this threat, [https://forum.ubuntu-fr.org/viewtopic.php?id=1891911](https://forum.ubuntu-fr.org/viewtopic.php?id=1891911)
Install Kernel and [http://www.yourownlinux.com/2015/08/how-to-install-linux-kernel-4-1-6-in-linux.html](http://www.yourownlinux.com/2015/08/how-to-install-linux-kernel-4-1-6-in-linux.html)
It Works! You've got a small error when the computer start, &#8220;Error parsing PCC subspaces from PCCT&#8221; because of a conflict between the new kernel and the nvidia driver but nothing to worry about. It just slow down a little bit the boot time.
Don't expect pinch to zoom or rotation with two fingers&#8230;

Only one problem so far, the touchpad is not working after you suspend your computer.
 If you suspend the activity of your computer, you&#8217;ll need to restart.
 However, if it gives a clue, before suspending ( it doesn&#8217;t work after I suspend the computer) I can deactivate and activate again the touchpad with the hotkey of my keyboard.

 I found that but it doesn't help too much so far,, [http://ubuntuforums.org/showthread.php?t=2182922&page=2](http://ubuntuforums.org/showthread.php?t=2182922&page=2)
 It gave a solution to a similar problem :  
 create a file here /etc/pm/sleep.d/0000trackpad  
```
*sudo gedit /etc/pm/sleep.d/0000trackpad*
```
 and add
 
 [PHP]#!/bin/sh  
 case "$1" in  
     suspend|hibernate)  
         modprobe -r psmouse;  
     resume|thaw)  
         modprobe psmouse;  
 esac  [/PHP]
 
 Save it.
 Now, the computer will refuse to suspend so no risk to loose your keyboard. However, you can't suspend your computer... tricky choice.
 Some people have the same problem with Elantech keyboard on other computer, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130) .
 My keyboard is a Focaltech.
 I file a bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445) and I ask a question on this forum here, [URL="http://ubuntuforums.org/showthread.php?t=2296850&p=13364663#post13364663"]http://ubuntuforums.org/showthread.php?t=2296850&p=13364663#post13364663

[/URL]I wish I could add the tag asus k501lx and asus v502lx to help others...

---

