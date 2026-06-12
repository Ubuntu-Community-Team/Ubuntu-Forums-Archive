---
title: "libOSMesa.so.4"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by barna on 2006-06-21
Hi
I managed to install LabVIEW (via rpm) to my notebook. When trying to launch the program, it tells 

labview: error while loading shared libraries: libOSMesa.so.4: cannot open shared object file: No such file or directory

I made a search at packages.ubuntu.com, and found libOSMesa.so (libOSMesa.so.6) in the packages     libdevel/libgl1-mesa-swrast-dev,devel/libgl1-mesa-glide3-dev 
Hoping that version 6 would be usable also, I tried to install these packages, but then the package management wanted to remove other packages (like kubuntu-desktop, x-window-system-core, etc), which I do not want. Do these packages really conflict? Why? Can I have somehow libOSMesa.so on my machine without removing kubuntu-desktop?

Thanks
Daniel

---

### Post by glotz on 2006-06-21
Do you have any version of libOSMesa on installed? You could try just brutally copying it to ibOSMesa.so.4... Worked for me on one occasion. (different library file though though)

disclaimer: glotz is a clueless linux newbie

---

### Post by 89c51 on 2006-09-07
Labview 8 must be one of the crapiest pieces of software EVER -on linux-

your problem can be solved by 

sudo ln -s /usr/lib/libOSMesa16.so.6.4.1 /usr/X11R6/lib/libOSMesa.so.4

this will start labview OK but after it crashes X very often :evil: :evil:

---

### Post by dmontalvao on 2007-10-31
I managed the situation like this:

Installing Labview 8.0 on Gusty Gibbon (Ubuntu 7.10):

1) On terminal window, install libdb1-compat:
sudo apt-get install libdb1-compat

2) Install Labview 8.0 from its install directory with default installation directories:
./INSTALL

Now the following may contain redundant steps, but worked fine for me:

3) cd /usr/local/natinst/LabVIEW-8.0/linux

(instead of step 4a u can try step 4b)

4a) cp libLVMesaGL.so.3 libOSMesa.so.4
4b) ln -s libLVMesaGL.so.3 libOSMesa.so.4

5) mkdir -p /usr/local/lib/linux/

6) cd /usr/local/lib/linux

7) ln -s /usr/local/natinst/LabVIEW-8.0/linux/libLVMesaGL.so.3
8) ln -s /usr/local/natinst/LabVIEW-8.0/linux/libOSMesa.so.4

I suppose step 7 is redundant and that step 4a can be replaced by 4b, but this is how I orginally made it and it worked out for me.

Hope this helps!

Cheers!

(Didn't crash yet for me. CROSS FINGERS!!! Anyway, I still need Dual Boot and WinXP to use MAX and a DAQCard :()

---

