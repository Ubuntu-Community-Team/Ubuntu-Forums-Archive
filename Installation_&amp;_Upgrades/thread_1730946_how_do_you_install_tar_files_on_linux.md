---
title: "how do you install tar files on linux"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by masterrob213 on 2011-04-16
ive been useing linux for awhile but i don't know how to install a tar file i know its like a zip file but the contents like install.sh i click on it and it asks if i want to run run in terminal or display but none works what do i do?

---

### Post by cjhabs on 2011-04-16
You can extract the files from the command line using:
tar xvf filename.tar

I usually first do:
tar tvf filename.tar
This will just list the files.
Also, I do this into a clean folder.

---

### Post by steveneddy on 2011-04-16
What exactly are you trying to install - if you don't mind me asking....?

---

### Post by masterrob213 on 2011-04-16
tar tvf mupen64plus-bundle-bin-32-1.99.1.tar.gz
tar: mupen64plus-bundle-bin-32-1.99.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
thats what happend when i tried the  tar tvf  and im trying to run mupen64plus

---

### Post by scott-ian on 2011-04-16
It sounds to me like your talking about installing from source.  There probably is a file called "Install" in the folder that explains the process.  It is often a somewhat difficult process for those with little Linux experience.

---

### Post by masterrob213 on 2011-04-16
there is nothing in the folder telling me what to do at all all thats in there is /home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/font.ttf
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/install.sh
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/libmupen64plus.so.2
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/libmupen64plus.so.2.0.0
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus.6.gz
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus.cht
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus.ini
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus-input-sdl.so
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus-rsp-hle.so
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus-video-rice.so
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/RiceVideoLinux.ini /home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/m64p_test_rom.v64
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/mupen64plus-audio-sdl.so
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/uninstall.sh
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/font-license
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/gpl-license
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/lgpl-license
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-audio-sdl
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-core
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-input-sdl
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-rsp-hle
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-ui-console
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/LICENSES-mupen64plus-video-rice
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/README-mupen64plus-core
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/README-mupen64plus-input-sdl
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/README-mupen64plus-ui-console
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/README-mupen64plus-video-rice
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-audio-sdl
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-core
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-input-sdl
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-rsp-hle
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-ui-console
/home/masterrob213/Desktop/mupen64plus-bundle-bin-32-1.99.1/doc/RELEASE-mupen64plus-video-rice
all that is whats in the fodler

---

