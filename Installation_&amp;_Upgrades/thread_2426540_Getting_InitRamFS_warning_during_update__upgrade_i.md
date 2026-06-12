---
title: "Getting InitRamFS warning during update / upgrade in terminal on 18.04"
date: 2019-09-10
forum: Installation &amp; Upgrades
---

### Post by brimcgon on 2019-09-10
Good day, 

I was running my daily update and upgrade in the terminal on Ubuntu Mate 18.04, and got this in the last few lines during the upgrade step. 

```
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/ubuntu--mate--vg-swap_1)
I: Set the RESUME variable to override this.
```

I don't know what to do, but it won't run the upgrade again, and suggests running

sudo apt autoremove

but the list of files it shows to be removed is large (almost a gig), and that strikes me as odd for sure. 

I'm afraid to reboot, as I don't want to not be able to get back in either.  

Any help on what this is and how to best address it is appreciated.

---

### Post by cruzer001 on 2019-09-10
Please run
```
sudo apt -f install
```
and post the results.

---

### Post by Dennis N on 2019-09-10
Nothing is wrong. Its just informing you where it's going to resume from if you suspend. It's your swap partition. 

In Gnome and MATE, the value is also stored in **/etc/initramfs-tools/conf.d/resume** as UUID.

Note: If you ever change the swap location, change the UUID here to the new swap as well as in fstab so initramfs can find it when you boot your OS.

---

### Post by brimcgon on 2019-09-13
Here's the info from "sudo apt install -f"

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer1.0-plugins-base:i386 libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-signals1.65.1 libbsd0:i386 libcairo2:i386 libcap2:i386 libcapi20-3
  libcapi20-3:i386 libcdparanoia0:i386 libcups2:i386 libdbus-1-3:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexif12:i386
  libexpat1:i386 libfdk-aac1 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgd3:i386 libgl1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgmp10:i386 libgnutls30:i386
  libgphoto2-6:i386 libgphoto2-port12:i386 libgsm1:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386
  libicu60:i386 libidn2-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libllvm8:i386 libltdl7:i386
  libluajit-5.1-2 libluajit-5.1-common libmbedcrypto1 libmbedtls10
  libmbedx509-0 libmpg123-0:i386 libnettle6:i386 libodbc1 libodbc1:i386
  libogg0:i386 libopal3.10.10 libopenal1:i386 libopus0:i386 liborc-0.4-0:i386
  libosmesa6 libosmesa6:i386 libp11-kit0:i386 libpcap0.8:i386
  libpciaccess0:i386 libpixman-1-0:i386 libpng16-16:i386 libpt2.10.11
  libpulse0:i386 libroken18-heimdal:i386 libsamplerate0:i386 libsane1:i386
  libsdl2-2.0-0:i386 libsensors4:i386 libsndfile1:i386 libsndio6.1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl1.1:i386 libstdc++6:i386
  libtasn1-6:i386 libtheora0:i386 libtiff5:i386 libunistring2:i386
  libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1:i386 libwebp6:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxkbcommon0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386
  libxxf86vm1:i386 ocl-icd-libopencl1:i386 wine-stable-amd64
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
```

---

### Post by cruzer001 on 2019-09-13
I think wine pulled in all those 32bit (i386) libraries that autoremove now wants to clean up.  You removed wine, right?  And your running a 64bit system?

If so, I see this as safe.  

32bit architecture can be installed on a 64bit system with:
```
sudo dpkg --add-architecture i386
```

---

### Post by brimcgon on 2019-09-13
I did indeed remove wine, so thank you for the clarification and help.  I appreciate it.

---

### Post by cruzer001 on 2019-09-15
Your welcome

I usually use the purge command instead of "remove".  Does a better job of cleaning up.

Please mark your thread as solved (at the top in "thread tools").

---

