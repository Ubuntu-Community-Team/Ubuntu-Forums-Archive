---
title: "[SOLVED] Navidia needs X window system off"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Limvot on 2008-02-14
Plese help. I am runnning ubuntu on an old laptop and it has an old navidia geforce4 420 go grafics card, which i am trying to get up and running. (works fine in xp) The desktop works fine, but stuff that requires opengl aceralation does not. (can i use my xp driver in ubuntu?) I may have found the driver on the navidia website, but i can't find out how to install. It seems to need x window system off, but ctrl alt backspace just restarts it. Also going into recovery mode, the installer tells me to shift into a greater mode. If i do the commad it sugjests i get the x window system again! Plese help.

---

### Post by MultipleSargasms on 2008-02-14
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html ]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html")

Your card appeared on the list, so there are drivers available, I think.  And, I believe you can't use XP drivers in Linux

---

### Post by Limvot on 2008-02-14
i know i can, i have the driver, but i can't install.

---

### Post by Limvot on 2008-02-14
ok, the driver is wrong. looking for new one.

---

### Post by mrsteveman1 on 2008-02-14
Are you sure that the ubuntu restricted drivers installer can't install the driver for your card?

To stop the Xserver you want to open a virtual terminal (not a terminal window):


```
ctrl-alt-f1
```

then type 

```
init 3
```

From there you should be able to run the binary installer from nvidia.


Note that you will need to have the kernel headers for your system installed, if you don't have them run:
```

sudo apt-get install kernel-headers
```

the package name might be linux-headers or linux-kernel-headers, i cant remember

---

### Post by Pumalite on 2008-02-14
sudo apt-get install linux-headers-`uname -r`
Better run:
sudo aptitude install build-essential
For the driver:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxxx.run
Accept License
Let driver compile the module into the kernel
Let the driver reconfigure your xorg.conf file
Then: startx
Or:
sudo /etc/init.d/gdm start

---

### Post by Limvot on 2008-02-15
> **Pumalite said:**
> sudo apt-get install linux-headers-`uname -r`
Better run:
sudo aptitude install build-essential
For the driver:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxxx.run
Accept License
Let driver compile the module into the kernel
Let the driver reconfigure your xorg.conf file
Then: startx
Or:
sudo /etc/init.d/gdm start
It dosent work...
It says it cant find the sources. (i did what you said)

---

### Post by Pumalite on 2008-02-15
What command are you referring to? Post the exact error message and at what stage of the process.

---

### Post by Limvot on 2008-02-15
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Feb 15 10:06:28 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> There appears to already be a driver installed on your system (version: 1.0-
   9643).  As part of installing this driver (version: 1.0-8762), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC test with CC="cc".
ERROR: Unable to determine the version of the kernel sources located in
       '/lib/modules/2.6.22-14-generic/build'.  Please make sure you have
       installed the kernel source files for your kernel and that they are
       properly configured; on Red Hat Linux systems, for example, be sure you
       have the 'kernel-source' RPM installed.  If you know the correct kernel
       source files are installed, you may specify the kernel source path with
       the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Limvot on 2008-02-15
I installed some packages in Sanaptic manager, like some kernal sources package and a some sort of viritual hedder. (looked like what the error was, so i tried it)

---

### Post by Limvot on 2008-02-15
I could try reinstalling than trying again. As you can see from the log, i already installed a driver like i am trying to do with this one.

---

### Post by Limvot on 2008-02-15
( i have only been using this install for 2 days)

---

### Post by Pumalite on 2008-02-15
Before you try to install, make sure you install build-essential:
sudo aptitude install build-essential

---

### Post by Limvot on 2008-02-15
Ok, it said something like this. (did over in terminal window because coudn't copy/paste in the virtual terminal.

nathan@nathan-laptop:~$ sudo aptitude install build-essential
[sudo] password for nathan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
nathan@nathan-laptop:~$ 

Thanks for your time.

EDIT: By the way... When i did that command the first time it uninstalled two unnessary packages (so it said.)
2'd edit: would this help? My card is so outdated ubuntu can not find a driver for it, but i may have. i could try someting like this.
[http://ubuntuforums.org/showthread.php?p=4262751](http://ubuntuforums.org/showthread.php?p=4262751)

---

### Post by Pumalite on 2008-02-15
Give me a detail of your card and tell me what driver are you trying to install.

---

### Post by Limvot on 2008-02-15
NVidia geforce4 420 go
I just used Envy to manualy install the 71.86.01 driver just now.
It worked, but now i only have 800x600 resulation. Should i try to install the driver one up, or is there a way to force higher resulation. (i know i can, been using it all this time and on windows. Or is there a way to normaly use the open source dirver than swich when i need openGL acceleration?

---

### Post by Pumalite on 2008-02-15
I know very little about installing with Envy.

---

### Post by Limvot on 2008-02-15
Thanks for your time. I think i will take a break, maby see what i can do later.
Maby i can just swich to the nvidia driver when i need it. I'll make a script to do that.

---

### Post by Limvot on 2008-02-15
Ok, i installed the driver, but 3d accel is not working. How ever i am salving this thred and opeing a new one under a different section becuase it would not be approit here.

---

