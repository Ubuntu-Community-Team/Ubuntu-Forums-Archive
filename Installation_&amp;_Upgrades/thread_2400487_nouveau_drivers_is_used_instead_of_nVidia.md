---
title: "nouveau drivers is used instead of nVidia"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by imajor75 on 2018-09-06
I installed Ubuntu 18.04 on my desktop computer with a GeForce GT 730 video card. Then I used the Software & Updates window to install the proprietary driver, which was not reporting any errors, and behaves like I got the right driver:

[https://www.dropbox.com/s/gdyuwg986zc0u21/drivers.png?dl=0](https://www.dropbox.com/s/gdyuwg986zc0u21/drivers.png?dl=0)

But a few games are way slower than I would expect, so I checked the driver from command line:

>glxinfo | grep OpenGL
OpenGL vendor string: nouveau
OpenGL renderer string: NV106
OpenGL core profile version string: 4.3 (Core Profile) Mesa 18.0.5
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 18.0.5
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:


>lspci -k
81:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 730] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GK208B [GeForce GT 730]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

So it seems that it is not using the proprietary driver. I was trying to disable the nouveau driver using instructions from [https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux) but after reboot it is still using the nouveau driver.
Any idea how could I fix this?

Thanks in advance.

---

### Post by Bashing-om on 2018-09-06
imajor75; Hummm .... 

See what we can find out :)

What is the Desktop Environment ?
```

echo $XDG_SESSION_TYPE

```

what parts - if any - of nvidia are installed ?
```

sudo lshw -C display
lsmod | grep nvidia
dpkg -l | grep -i nvidia

```
where we are looking to have the 390 version driver installed:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)
what does the gpu manager think ?
```

cat /var/log/gpu-manager.log

```

Once we are all cleaned up, see what we can do to get that 390 version driver installed.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by imajor75 on 2018-09-07
Thanks a lot for the reply!

Currently the desktop environment is wayland. I switched to wayland after I tried to backlist nouveau, and after that my desktop resolution was set to 640*480, which was unusable. I couldn't find a way to restore back the native resolution of my monitor, and noticed that by switching to wayland I get my original resolution back, so since then I'm using wayland. Without wayland I get this:

```
xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 16384 x 16384
DVI-D-1 connected primary 640x480+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   640x480       59.94* 
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)

```

```
imajor@imajor-ThinkStation-P710:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:81:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:43 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:f000(size=128) memory:fb000000-fb07ffff
imajor@imajor-ThinkStation-P710:~$ lsmod | grep nvidia
imajor@imajor-ThinkStation-P710:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64                   390.48-0ubuntu3                     amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.48-0ubuntu3                     all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.48-0ubuntu3                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.48-0ubuntu3                     i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.48-0ubuntu3                     amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.48-0ubuntu3                     i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.48-0ubuntu3                     amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.48-0ubuntu3                     i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.48-0ubuntu3                     amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.48-0ubuntu3                     i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.48-0ubuntu3                     amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.48-0ubuntu3                     i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.48-0ubuntu3                     amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.48-0ubuntu3                     i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390                   390.48-0ubuntu3                     amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.48-0ubuntu3                     amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.48-0ubuntu3                     amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                   390.48-0ubuntu3                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.48-0ubuntu3                     amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8                               all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            390.42-0ubuntu1                     amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.48-0ubuntu3                     amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390              390.48-0ubuntu3                     amd64        NVIDIA binary Xorg driver

```

```
imajor@imajor-ThinkStation-P710:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-33-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/4.15.0-33-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1287
BusID "PCI:129@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-DVI-D-1
Number of connected outputs for /dev/dri/card0: 1
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do



```

I'm downloading the driver specified the link you sent, and I will try to run it. I will post my result soon.

---

### Post by imajor75 on 2018-09-07
I downloaded the driver and tried to run, but it gave me an error message and asked if I want to continue anyway, or about. I wasn't sure what to do, so I picked abort. If you think I should just continue, let me know. Log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Sep  7 08:44:22 2018
installer version: 390.87

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin

nvidia-installer command line:
    ./nvidia-installer

Unable to load: nvidia-installer ncurses v6 user interface

Using: nvidia-installer ncurses user interface
-> Detected 48 CPUs online; setting concurrency level to 32.
-> Installing NVIDIA driver version 390.87.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Abort installation)
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.



```

---

### Post by mastablasta on 2018-09-07
are you using xorg now or wayland? do you have any other GPU installed? did you run any benchmarks (e.g. with phoronix)

there used to be a PPA where you could select an older driver. would an older driver version work?

---

### Post by imajor75 on 2018-09-07
At this moment I'm using wayland, but I cannot make it work anywhere. I have only a single GPU. I didn't run any benchmarks yet, I will try that soon.

I don't have older drivers, this Ubuntu install is like a month old?

---

### Post by imajor75 on 2018-09-07
I installed the phoronix test suite, but I realized it has tons of tests and I cannot just run all of them. Do you know which test would be useful for diagnosing my problem?

---

### Post by Bashing-om on 2018-09-07
imajor75; Hey ...

unfortunately, Wayland with nvidia is a work in progress, Best results currently is with the 396 version driver.
Best practice presently for a nvidia driver is under X11.

[INDENT][INDENT]not good
[INDENT][INDENT][INDENT]but all I can say[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by imajor75 on 2018-09-07
I'm using Wayland, but I don't want to use it. The only reason why I'm using it is because if I switch to xorg, my resolution is 640x480, and I can set anything higher. So the ideal for me would be to switch back to xorg, install the proprietary driver correctly, and use the proper resolution (1920x1080). If you could help me with that, I would be super happy.

Thanks in advance

---

### Post by Bashing-om on 2018-09-07
imajor75; K -

It should be as simple as changing the DE to Xorg
run terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo apt purge nvidia*
##verify these files do not exist for nvidia
ls -al /etc/X11/xorg.conf
ls -al /usr/share/X11/xorg.conf.d/*.conf
##install the driver then:
sudo ubuntu-drivers autoinstall

```
where I do expect the system to choose to install the recommended 390 version driver:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

reboot to see the effect.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by imajor75 on 2018-09-07
Thanks a lot! I will try this tomorrow.

---

### Post by imajor75 on 2018-09-08
Here is the full output:


```
$ sudo apt update
Err:1 http://archive.getdeb.net/ubuntu xenial-getdeb InRelease
  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease
Hit:3 http://ppa.launchpad.net/hluk/copyq/ubuntu bionic InRelease
Hit:4 http://hu.archive.ubuntu.com/ubuntu bionic InRelease
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:6 http://hu.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:7 http://hu.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:8 http://packages.microsoft.com/repos/vscode stable InRelease
Hit:9 http://dl.google.com/linux/chrome/deb stable Release
Hit:10 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
W: Some index files failed to download. They have been ignored, or old ones used instead.






$ sudo apt full-upgrade
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages were automatically installed and are no longer required:
  blender-data fonts-dejavu fonts-dejavu-extra gir1.2-ges-1.0 gmic
  gstreamer1.0-gtk3 libavdevice57 libblosc1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libboost-regex1.65.1 libbrotli1
  libclass-data-inheritable-perl libclass-method-modifiers-perl
  libcommon-sense-perl libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl
  libdata-random-perl libebur128-1 libfile-which-perl libgd-perl libges-1.0-0
  libglade2-0 libglew2.0 libgnome-2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-gconf-perl libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgtk2-imageview-perl
  libgtk2-unique-perl libgtkimageview0 libhttp-server-simple-perl libjemalloc1
  libjs-jquery-ui libjson-perl libjson-xs-perl liblog4cplus-1.1-9 libmlt++3
  libmlt-data libmlt6 libmouse-perl libmovit8 libnet-dropbox-api-perl
  libnet-oauth-perl libopencolorio1v5 libopenimageio1.7 libopenshot-audio6
  libopenshot14 libopenvdb5.0 liborbit-2-0 libpath-class-perl
  libproc-processtable-perl libproc-simple-perl libqt5designer5 libqt5help5
  libqt5positioning5 libqt5printsupport5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5webchannel5 libqt5webkit5 librtaudio6
  libsdl2-2.0-0 libsort-naturally-perl libsox-fmt-alsa libsox-fmt-base libsox3
  libspnav0 libtinyxml2.6.2v5 libtypes-serialiser-perl libunique-1.0-0
  libwnck-common libwnck22 libwoff1 libwww-mechanize-perl
  libx11-protocol-other-perl libyaml-cpp0.5v5 python-matplotlib-data
  python-mlt python3-cycler python3-dateutil python3-gst-1.0
  python3-matplotlib python3-numpy python3-openshot python3-pyparsing
  python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-sip
  python3-zmq swh-plugins
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.






$ sudo apt purge nvidia*
Reading package lists...
Building dependency tree...
Reading state information...
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  blender-data dkms fonts-dejavu fonts-dejavu-extra gir1.2-ges-1.0 gmic
  gstreamer1.0-gtk3 libavdevice57 libblosc1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libboost-regex1.65.1 libbrotli1
  libbsd0:i386 libclass-data-inheritable-perl libclass-method-modifiers-perl
  libcommon-sense-perl libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl
  libdata-random-perl libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libebur128-1
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libfile-which-perl
  libgd-perl libges-1.0-0 libgl1:i386 libgl1-mesa-dri:i386 libglade2-0
  libglapi-mesa:i386 libglew2.0 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386
  libgnome-2-0 libgnome2-canvas-perl libgnome2-common libgnome2-gconf-perl
  libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgtk2-imageview-perl
  libgtk2-unique-perl libgtkimageview0 libhttp-server-simple-perl libjemalloc1
  libjs-jquery-ui libjson-perl libjson-xs-perl libllvm6.0:i386
  liblog4cplus-1.1-9 libmlt++3 libmlt-data libmlt6 libmouse-perl libmovit8
  libnet-dropbox-api-perl libnet-oauth-perl libnvidia-cfg1-390
  libnvidia-common-390 libnvidia-compute-390 libnvidia-compute-390:i386
  libnvidia-decode-390 libnvidia-decode-390:i386 libnvidia-encode-390
  libnvidia-encode-390:i386 libnvidia-fbc1-390 libnvidia-fbc1-390:i386
  libnvidia-gl-390 libnvidia-gl-390:i386 libnvidia-ifr1-390
  libnvidia-ifr1-390:i386 libopencolorio1v5 libopenimageio1.7
  libopenshot-audio6 libopenshot14 libopenvdb5.0 liborbit-2-0
  libpath-class-perl libpciaccess0:i386 libproc-processtable-perl
  libproc-simple-perl libqt5designer5 libqt5help5 libqt5positioning5
  libqt5printsupport5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5
  libqt5webchannel5 libqt5webkit5 librtaudio6 libsdl2-2.0-0 libsensors4:i386
  libsort-naturally-perl libsox-fmt-alsa libsox-fmt-base libsox3 libspnav0
  libstdc++6:i386 libtinyxml2.6.2v5 libtypes-serialiser-perl libunique-1.0-0
  libwayland-client0:i386 libwayland-server0:i386 libwnck-common libwnck22
  libwoff1 libwww-mechanize-perl libx11-6:i386 libx11-protocol-other-perl
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxnvctrl0
  libxshmfence1:i386 libxxf86vm1:i386 libyaml-cpp0.5v5 python-matplotlib-data
  python-mlt python3-cycler python3-dateutil python3-gst-1.0
  python3-matplotlib python3-numpy python3-openshot python3-pyparsing
  python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-sip
  python3-zmq screen-resolution-extra swh-plugins
  xserver-xorg-video-nvidia-390
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-compute-utils-390* nvidia-dkms-390* nvidia-driver-390*
  nvidia-kernel-common-390* nvidia-kernel-source-390* nvidia-prime*
  nvidia-settings* nvidia-utils-390*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 31,4 MB disk space will be freed.
Do you want to continue? [Y/n] (Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 266672 files and directories currently installed.)
Removing nvidia-driver-390 (390.48-0ubuntu3) ...
Removing nvidia-compute-utils-390 (390.48-0ubuntu3) ...
Removing nvidia-dkms-390 (390.48-0ubuntu3) ...
Removing all DKMS Modules
Done.
INFO:Disable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
Removing nvidia-kernel-common-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-kernel-source-390 (390.48-0ubuntu3) ...
Removing nvidia-prime (0.8.8) ...
Removing nvidia-settings (390.42-0ubuntu1) ...
Removing nvidia-utils-390 (390.48-0ubuntu3) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 266211 files and directories currently installed.)
Purging configuration files for nvidia-prime (0.8.8) ...
Purging configuration files for nvidia-settings (390.42-0ubuntu1) ...
Purging configuration files for nvidia-dkms-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-kernel-common-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-compute-utils-390 (390.48-0ubuntu3) ...
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic






$ ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1325 szept  6 15:14 /etc/X11/xorg.conf






$ ls -al /usr/share/X11/xorg.conf.d/*.conf
-rw-r--r-- 1 root root   92 márc  20 13:02 /usr/share/X11/xorg.conf.d/10-amdgpu.conf
-rw-r--r-- 1 root root  206 ápr   18 19:01 /usr/share/X11/xorg.conf.d/10-nvidia.conf
-rw-r--r-- 1 root root 1350 ápr   13 17:31 /usr/share/X11/xorg.conf.d/10-quirks.conf
-rw-r--r-- 1 root root   92 márc  20 13:17 /usr/share/X11/xorg.conf.d/10-radeon.conf
-rw-r--r-- 1 root root  945 ápr   11 09:50 /usr/share/X11/xorg.conf.d/40-libinput.conf
-rw-r--r-- 1 root root 3025 ápr    3 09:39 /usr/share/X11/xorg.conf.d/70-wacom.conf








$ sudo ubuntu-drivers autoinstall
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  blender-data fonts-dejavu fonts-dejavu-extra gir1.2-ges-1.0 gmic
  gstreamer1.0-gtk3 libavdevice57 libblosc1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libboost-regex1.65.1 libbrotli1
  libclass-data-inheritable-perl libclass-method-modifiers-perl
  libcommon-sense-perl libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl
  libdata-random-perl libebur128-1 libfile-which-perl libgd-perl libges-1.0-0
  libglade2-0 libglew2.0 libgnome-2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-gconf-perl libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgtk2-imageview-perl
  libgtk2-unique-perl libgtkimageview0 libhttp-server-simple-perl libjemalloc1
  libjs-jquery-ui libjson-perl libjson-xs-perl liblog4cplus-1.1-9 libmlt++3
  libmlt-data libmlt6 libmouse-perl libmovit8 libnet-dropbox-api-perl
  libnet-oauth-perl libopencolorio1v5 libopenimageio1.7 libopenshot-audio6
  libopenshot14 libopenvdb5.0 liborbit-2-0 libpath-class-perl
  libproc-processtable-perl libproc-simple-perl libqt5designer5 libqt5help5
  libqt5positioning5 libqt5printsupport5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5webchannel5 libqt5webkit5 librtaudio6
  libsdl2-2.0-0 libsort-naturally-perl libsox-fmt-alsa libsox-fmt-base libsox3
  libspnav0 libtinyxml2.6.2v5 libtypes-serialiser-perl libunique-1.0-0
  libwnck-common libwnck22 libwoff1 libwww-mechanize-perl
  libx11-protocol-other-perl libyaml-cpp0.5v5 python-matplotlib-data
  python-mlt python3-cycler python3-dateutil python3-gst-1.0
  python3-matplotlib python3-numpy python3-openshot python3-pyparsing
  python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-sip
  python3-zmq swh-plugins
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  nvidia-compute-utils-390 nvidia-dkms-390 nvidia-kernel-common-390
  nvidia-kernel-source-390 nvidia-prime nvidia-settings nvidia-utils-390
The following NEW packages will be installed:
  nvidia-compute-utils-390 nvidia-dkms-390 nvidia-driver-390
  nvidia-kernel-common-390 nvidia-kernel-source-390 nvidia-prime
  nvidia-settings nvidia-utils-390
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/10,2 MB of archives.
After this operation, 31,4 MB of additional disk space will be used.
Selecting previously unselected package nvidia-compute-utils-390.
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 266210 files and directories currently installed.)
Preparing to unpack .../0-nvidia-compute-utils-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-compute-utils-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-kernel-source-390.
Preparing to unpack .../1-nvidia-kernel-source-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-kernel-source-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-kernel-common-390.
Preparing to unpack .../2-nvidia-kernel-common-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-kernel-common-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-dkms-390.
Preparing to unpack .../3-nvidia-dkms-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-dkms-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-utils-390.
Preparing to unpack .../4-nvidia-utils-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-utils-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-driver-390.
Preparing to unpack .../5-nvidia-driver-390_390.48-0ubuntu3_amd64.deb ...
Unpacking nvidia-driver-390 (390.48-0ubuntu3) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../6-nvidia-prime_0.8.8_all.deb ...
Unpacking nvidia-prime (0.8.8) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../7-nvidia-settings_390.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (390.42-0ubuntu1) ...
Setting up nvidia-kernel-source-390 (390.48-0ubuntu3) ...
Setting up nvidia-prime (0.8.8) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Setting up nvidia-settings (390.42-0ubuntu1) ...
Setting up nvidia-utils-390 (390.48-0ubuntu3) ...
Setting up nvidia-kernel-common-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Created symlink /etc/systemd/system/multi-user.target.wants/nvidia-fallback.service &#8594; /lib/systemd/system/nvidia-fallback.service.
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Setting up nvidia-compute-utils-390 (390.48-0ubuntu3) ...
Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory
Adding system user `nvidia-persistenced' (UID 122) ...
Adding new group `nvidia-persistenced' (GID 127) ...
Adding new user `nvidia-persistenced' (UID 122) with group `nvidia-persistenced' ...
Not creating home directory `/nonexistent'.
Setting up nvidia-dkms-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Loading new nvidia-390.48 DKMS files...
Building for 4.15.0-33-generic
Building for architecture x86_64
Building initial module for 4.15.0-33-generic
Done.




nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-33-generic/updates/dkms/




nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-33-generic/updates/dkms/




nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-33-generic/updates/dkms/




nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-33-generic/updates/dkms/




depmod...




DKMS: install completed.
Setting up nvidia-driver-390 (390.48-0ubuntu3) ...
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-33-generic

```


I did all of this at runlevel 3. Then if I switch to runlevel 5 with xorg, my desktop resolution is only 640x480, and I cannot increase it. And I think it is still using nouveau.


```

$ xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 16384 x 16384
DVI-D-1 connected primary 640x480+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   640x480       59.94* 
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)


$ sudo lshw -C display
[sudo] password for imajor: 
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:81:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:43 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:f000(size=128) memory:fb000000-fb07ffff

```

---

### Post by imajor75 on 2018-09-10
Could anyone please help me here? I'm still stuck with nouveau and I need the proprietary driver.

Thanks in advance!

---

### Post by Bashing-om on 2018-09-10
imajor75; Yukkie - on me and on you too.

> 
Err:1 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb InRelease
Hit:8 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease
Hit:10 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease


I do not even know where to start now to find a solution:
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)

Maybe purge these strange sources .. and see what then results ?

[INDENT]linuxstiens - hard to handle
[/INDENT]

---

### Post by imajor75 on 2018-09-11
Sorry, I'm not sure what are you suggesting. Are you saying I should make a clean reinstall of Ubuntu? I'm willing to do that if there is no other solution. I really need the proprietary driver to work.

---

### Post by mastablasta on 2018-09-11
> **imajor75 said:**
> Sorry, I'm not sure what are you suggesting. Are you saying I should make a clean reinstall of Ubuntu? I'm willing to do that if there is no other solution. I really need the proprietary driver to work.

or comment out the strange sources. you are using some debian stuff it seems. debian and ubuntu usually do not mix.

btw i had same issue on one machine with same GPU chip. i could not resolve it on 14.04 and in the end returned the card. On the other PC it does give the same low resolution, but i can later change it. i tried in install on a USB stick (16.04). i use VGA port for monitor, but the DVI points to the TV. the annoying part is that the card by default (windows or linux) always boots to TV (or empty). ridiculous!!!

the resolution can be changed. however the priority i believe should be to load the proprietary driver. if you decide on reinstall make sure to boot (sign in) to x11 first.

---

### Post by imajor75 on 2018-09-11
Thanks. I'm supper beginner with Linux, could you please elaborate what "[COLOR=#000000]boot (sign in) to x11 first" means?[/COLOR]

---

### Post by Bashing-om on 2018-09-12
imajor75; hey ,
> 
"boot (sign in) to x11 first" means


in 18,04 we have a serious shift in the desktop(s) environment.
Now as defaults for the DE are Xorg (X11) running under GDM3, and the new one Wayland running under Mir.
One can select which they want. At the password entry screen in the lower right is a gear icon. Select thls and a drop down pops up to select the booting  environment.

I personally in my small use case find that Wayland does in fact perform the better than X11 ( though my preference remains as xfce ).

[INDENT][INDENT]see what works best
[/INDENT][/INDENT]

---

### Post by imajor75 on 2018-09-13
Thanks. I will do that.

---

### Post by imajor75 on 2018-09-13
Update: I reinstalled Ubuntu 18.04 into a new clean partition. After the installation on the next reboot I encountered some weird messages about secure boot, and somehow managed to disable it (wasn't easy). After that Ubuntu was correctly using the proprietary driver. After that I rebooted into my previous Ubuntu install, and the proprietary driver is used correctly in that one too. So my guess is that the reason why it wasn't working is that secure boot wasn't properly disabled? I was assuming it will be disabled automatically, and I only need to provide the password, but maybe I should have done something during the boot, not sure. Anyway, it is working now correctly, thanks again! For those having a similar problem: check secure boot.

Update2: I was trying to collect some more information about this secure boot, because I had no idea what it is. It seems this is something related to Windows? So maybe all of this was happening because the main operation system on this computer is windows, and I only installed Linux later?

---

### Post by mastablasta on 2018-09-14
> **imajor75 said:**
> 
Update2: I was trying to collect some more information about this secure boot, because I had no idea what it is. It seems this is something related to Windows? So maybe all of this was happening because the main operation system on this computer is windows, and I only installed Linux later?

it is connected with windows (it protects it from rootkits that load themselves in boot sectors), however Ubuntu should work well with secure boot enabled providing it was properly implemented (UEFI standards) by the motherboard manufacturer.

---

### Post by imajor75 on 2018-09-14
I hope it is implemented properly. This computer is a Lenovo Thinkstation P710, I'm not sure about the exact motherboard. The interesing thing is that it wasn't asking for the password, it was asking for some random individual letters from the password. For example it was asking for the 3rd letter in the password, then the 8th... Is this usual? I've never seen anything like this before.

---

### Post by mastablasta on 2018-09-18
> **imajor75 said:**
> I hope it is implemented properly. This computer is a Lenovo Thinkstation P710, I'm not sure about the exact motherboard. The interesing thing is that it wasn't asking for the password, it was asking for some random individual letters from the password. For example it was asking for the 3rd letter in the password, then the 8th... Is this usual? I've never seen anything like this before.

could be. this would then try to prevent brute force attack of sorts. In any case i don't think secure boot was the very necessary thing to do. they hsould be more focused on capturing the malware at entrance point not when it already passes the OS and tries to add itself to UEFI.

---

