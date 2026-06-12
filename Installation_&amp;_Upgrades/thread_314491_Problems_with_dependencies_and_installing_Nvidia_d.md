---
title: "Problems with dependencies and installing Nvidia driver"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by fakie_flip on 2006-12-07
I tried two methods to install the Nvidia driver. I tried the forum admin's Envy package from here.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

After that, I tried using the Ubuntu package from the repos by following the directions here.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

I am unable to install the nvidia driver from the Envy package. I tried Envy first, and then later another method to install the nvidia driver. Here is what happens. Help please for getting the nvidia driver working. After using envy, X will not start. Neither sudo /etc/init.d/gdm start or xstart will bring the graphics back up. I need helping getting that Nvidia driver to work. The graphics card is this. 

```
brad@Brads-desktop:~$ lspci | grep -i nv
0000:01:00.0 VGA compatible controller: nVidia Corporation NV38 [GeForce FX 5950 Ultra] (rev a1) 
brad@Brads-desktop:~$ sudo dpkg -i envy_0.7.3-0ubuntu2_all.deb
Selecting previously deselected package envy.
(Reading database ... 105873 files and directories currently installed.) 
Unpacking envy (from envy_0.7.3-0ubuntu2_all.deb) ...
Setting up envy (0.7.3-0ubuntu2) ...
brad@Brads-desktop:~$ env
env       envsubst  envy
brad@Brads-desktop:~$ env
env       envsubst  envy
 
brad@Brads-desktop:~$ envy
       +-----------------------------------+
       |       Welcome to Envy 0.7.3         |
       |                                   |
       |    Developed by Alberto Milone    |
       +-----------------------------------+ 

       +-----------------------------------+
       | 1. Install the Nvidia driver      |
       | 2. Uninstall the Nvidia driver    |
       | 3. Exit                           |
       +-----------------------------------+ 

Please select one of the activities displayed above and press ENTER:

1
Your graphic card is supported by the Nvidia Driver
Ubuntu Dapper 32bit
Your graphic card is supported by the Nvidia Driver
 * Stopping GNOME Display Manager...                                     [ ok ] 
sudo: /etc/init.d/kdm: command not found
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-27-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree... Done
xserver-xorg-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree... Done
pkg-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done 
Building dependency tree... Done
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-settings is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
No Nvidia installer detected
Download of the driver in progress, please wait
--15:45:22--  http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run 
           => `NVIDIA-Linux-x86-1.0-9631-pkg1.run'
Resolving us.download.nvidia.com... 66.216.46.11, 66.216.46.17
Connecting to us.download.nvidia.com|66.216.46.11|:80. . . connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,357,240 (13M) [text/plain]

100%[===========================================================================

15:45:44 (584.59 KB/s) - `NVIDIA-Linux-x86-1.0-9631-pkg1.run' saved [13357240/13

md5new: 3676f622897d22f1815365b44139899e
md5sumold: 3676f622897d22f1815365b44139899e
Looking for the existence of an Nvidia folder. Please Wait
Creating directory NVIDIA-Linux-x86-1.0-9631-pkg1
Verifying archive integrity... OK 
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-9631....................................................................................................................................................................... . .
Do you want your xorg.conf to be automatically configured? (y/n) \ "y" is the de
y

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Do you want to Start the Xserver now? (y/n) \ "y" is the default answer
y
 * Stopping GNOME Display Manager...
 * Starting GNOME Display Manager...
sudo: /etc/init.d/kdm: command not found
brad@Brads-desktop:~$ ps -ef | less
``` 

Here is a sample of the output from that:
 
```
root      9073  9041  0 15:46 ?        00:00:00 /bin/sh /etc/gdm/XKeepsCrashing
root      9092  9073  0 15:46 ?        00:00:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /etc/gdm/XKeepsCrashing -noopen 
root      9093  9092  0 15:46 tty7     00:00:00 /bin/sh /etc/gdm/XKeepsCrashing -noopen 
root      9115  9093  0 15:46 tty7     00:00:00 /usr/bin/whiptail --yesno Failed to start the X server (your graphical interf 
ace).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem? 10 
50
```

I got this error trying to follow these directions.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29) 

I have my orginal xorg.conf, and I restored it before doing this and getting the message that my xorg.conf had been altered. It says my xorg.conf has been altered, but I am using the orginal xorg.conf that installed with Ubuntu Dapper Drake on the system. I started apache2 on the computer with the problem, and copied the files over to /var/www/ so you can see them from the web here. 

[http://darkfusion.bounceme.net/](http://darkfusion.bounceme.net/)
 
```
brad@Brads-desktop:~$ sudo aptitude install nvidia-glx nvidia-kernel-common
Password:
Reading package lists... Done 
Building dependency tree... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gnupg
The following NEW packages will be installed: 
  nvidia-glx
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded. 
Need to get 4063kB of archives. After unpacking 12.5MB will be used.
Writing extended state information... Done
Get:1 http://security.ubuntu.com dapper-security/restricted nvidia-glx 1.0.8776+2.6.15.12-1 [4063kB]
Fetched 4063kB in 8s (483kB/s)
Selecting previously deselected package nvidia-glx.
(Reading database ... 105885 files and directories currently installed.) 
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.15.12-1_i386.deb) ... 
Setting up nvidia-glx (1.0.8776+2.6.15.12-1) ...
brad@Brads-desktop:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum 
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
brad@Brads-desktop:~$ ls -l /etc/X11/xorg.conf 
-rw-r--r-- 1 root root 4442 2006-12-07 15:50 /etc/X11/xorg.conf 
brad@Brads-desktop:~$
```

So I tried to remove the packages I installed.

```
brad@Brads-desktop:~$ sudo aptitude purge nvidia-glx nvidia-kernel-common
Reading package lists... Done 
Building dependency tree... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-2.6.15-23-386 
  linux-restricted-modules-2.6.15-27-386
The following packages have been kept back: 
  gnupg
The following packages will be REMOVED:
  nvidia-glx{p} nvidia-kernel-common{p}
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded. 
Need to get 0B of archives. After unpacking 12.7MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.15-23-386: Depends: nvidia-kernel-common but it i                                             s not installable 
  linux-restricted-modules-2.6.15-27-386 : Depends: nvidia-kernel-common but it i                                             s not installable
Resolving dependencies...
The following actions will resolve these dependencies: 

Keep the following packages at their current version:
nvidia-kernel-common [20051028+1 (dapper, now)]

Score is 1

Accept this solution? [Y/n/q/?]
brad@Brads-desktop:~$
```

Then when I pushed control+C to copy after each time I used aptitude. It also quit aptitude from running. Now I have weird problems with dependencies that I do not know how to correct.

```
brad@Brads-desktop:~$ sudo aptitude install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done 
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  apache2 flashplugin-nonfree
The following packages have been kept back:
  gnupg
The following packages will be REMOVED: 
  apache2-common apache2-mpm-worker apache2-utils gsfonts-x11 libapr0 libdrm-dev
  libxext-dev libxi-dev samba wine x11proto-core-dev x11proto-fonts-dev x11proto
  x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x1 
0 packages upgraded, 0 newly installed, 23 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 63.3MB will be freed.
The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (= 2.0.55-4ubuntu2.1) but it is not insta
                    apache2-mpm-prefork (= 2.0.55-4ubuntu2.1) but it is not inst
                    apache2-mpm-perchild (= 2.0.55-4ubuntu2.1) but it is not ins
  flashplugin-nonfree: Depends: gsfonts-x11 but it is not installable 
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
apache2-common [2.0.55-4ubuntu2.1 (dapper-security, now)]
apache2-mpm-worker [2.0.55-4ubuntu2.1 (dapper-security, now)]
apache2-utils [2.0.55-4ubuntu2.1 (dapper-security, now)] 
gsfonts-x11 [0.17ubuntu4 (dapper, now)]
libapr0 [2.0.55-4ubuntu2.1 (dapper-security, now)]

Score is -195

Accept this solution? [Y/n/q/?]
The following packages have been kept back:
  gnupg
The following packages will be REMOVED:
  libdrm-dev libx11-dev libxau-dev libxdmcp-dev libxext-dev libxi-dev samba wine
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11p
  x11proto-xf86dri-dev xserver-xorg-dev
0 packages upgraded, 0 newly installed, 18 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 59.0MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
brad@Brads-desktop:~$ sudo aptitude keep-all
Reading package lists... Done
Building dependency tree... Done 
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  gnupg
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
brad@Brads-desktop:~$ sudo aptitude purge nvidia-glx nvidia-kernel-common 
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-2.6.15-23-386 linux-restricted-modules-2.6.15-27-386
The following packages have been kept back:
  gnupg
The following packages will be REMOVED:
  nvidia-glx{p} nvidia-kernel-common{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 12.7MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.15-23-386 : Depends: nvidia-kernel-common but it i
  linux-restricted-modules-2.6.15-27-386: Depends: nvidia-kernel-common but it i
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
nvidia-kernel-common [20051028+1 (dapper, now)]

Score is 1

Accept this solution? [Y/n/q/?]
brad@Brads-desktop:~$ sudo aptitude purge linux-restricted-modules-2.6.15-27-386 linux-restricted-modules-2.6.15-23-386
Reading package lists... Done 
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-386 nvidia-glx 
The following packages have been kept back:
  gnupg
The following packages will be REMOVED:
  linux-restricted-modules-2.6.15-23-386{p}
  linux-restricted-modules-2.6.15-27-386{p}
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded. 
Need to get 0B of archives. After unpacking 44.2MB will be freed.
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.8776 which is a virtual package.
  linux-restricted-modules-386: Depends: linux-restricted-modules-2.6.15-27-386 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-restricted-modules-2.6.15-27-386 [2.6.15.12-1 (dapper-security, now)]

Score is 1

Accept this solution? [Y/n/q/?]
brad@Brads-desktop:~$
```

---

