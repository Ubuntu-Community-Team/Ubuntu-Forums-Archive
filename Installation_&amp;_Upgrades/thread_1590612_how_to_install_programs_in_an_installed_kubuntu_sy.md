---
title: "how to install programs in an installed kubuntu system through kubuntu live usb/cd ?"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by radiobert on 2010-10-08
I am in a big trouble...
Accidentally I 'apt-get remove' a lot of essential packages needed by the KDE, as a result,  window-related problems appear...I can't make the windows to be focused, so I can't even type a character into the konsole to reinstall the packages back.

The idea to mount the filesystem and then install the packages using apt-get through Livecd /liveUSB come to my mind, but the question is, can this method work? If this is a feasible method, how can I do it?

For those who like to know what I have removed, see the list below:
bison ccache cvs flex fontforge gcc git-core libasound2-dev libaudio-dev libc6-dev \
libcapi20-3 libcapi20-dev libdbus-1-dev libesd0-dev libexif-dev \
libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev \
libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev \
libgphoto2-2-dev libgsm1-dev libhal-dev libice-dev libieee1284-3-dev libjpeg62-dev liblcms1-dev \
libldap2-dev libmad0 libmad0-dev libmng-dev libmpg123-dev libncurses5-dev libodbcinstq1c2 \
libogg-dev  libopenal-dev libopenal1 libpng12-dev libpopt-dev libqt3-headers libqt3-mt libqt3-mt-dev libsane-dev \
libsm-dev libssl-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 libusb-dev libvorbis-dev \
libvorbisfile3 libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdmcp-dev \
libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev \
libxmu-headers libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev \
libxxf86vm-dev linux-libc-dev m4 make mesa-common-dev odbcinst1debian1 qt3-dev-tools \
unixodbc unixodbc-dev x11proto-composite-dev x11proto-core-dev x11proto-fixes-dev  \
x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86vidmode-dev x11proto-xinerama-dev x-dev xtrans-dev zlib1g-dev \
libelfg0 libfreebob0 libgif-dev libhal-storage-dev libjack-dev

---

### Post by mörgæs on 2010-10-08
It might work, but in that case you are installing old packages (from the CD) into an updated system. You could end with a lot of trouble with dependencies. 

Maybe it is best to reinstall. It takes one hour and is guaranteed to work on your hardware.

---

### Post by sikander3786 on 2010-10-08
Hi and welcome to the forums :popcorn:

Morgaes suggested a reinstall. Still you can try to boot into recovery mode. You can do this by holding down Shift as soon as the computer gets past the bios screen. Try

```
sudo apt-get update
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by radiobert on 2010-10-08
Finally I found myself a solution to the problem ---use chroot...
What a nice day I have had....

---

