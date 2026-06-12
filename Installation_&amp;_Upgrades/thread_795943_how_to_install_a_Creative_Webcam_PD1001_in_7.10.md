---
title: "how to install a Creative Webcam PD1001 in 7.10"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by kami_iwinaru on 2008-05-16
I've looked and looked and looked at a million different things on how to install this webcam. I'm using 7.10, and I have no clue what to do.

If someone could write a step-by-step kinda thing that would be great, because I'm still new to Ubuntu and don't have a clue what compiling and stuff means, let alone how to do it.

---

### Post by MaindotC on 2008-05-16
I can help you with compiling if you can tell me what directions you found.  Can you post the output of the command:
```

shell@rt3: sudo lsusb

```

---

### Post by kami_iwinaru on 2008-05-16
Here are the instructions this guy posted:
> 
   1. Download the source files that are included in epcam-src-ubuntu-0.7.1.tar.gz
   2. Open a terminal
   3. Go the directory where you download epcam-src-ubuntu-0.7.1.tar.gz
   4. Copy-Paste in your terminal each of the following lines exactly as it is :
```

tar xfvz epcam-src-ubuntu-0.7.1.tar.gz
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
sudo make
sudo make install
sudo make clean

```


and here is the output of that command:
```

Bus 001 Device 003: ID 041e:400d Creative Technology, Ltd WebCam PD1001
Bus 001 Device 001: ID 0000:0000

```

---

### Post by kami_iwinaru on 2008-05-16
i dont get how to go to the directory, because it's just on the desktop
and from there i'm basically lost, lol

---

### Post by MaindotC on 2008-05-16
Dude those instructions are perfect!  Ok, the lsusb command shows the webcam as you can see so Ubuntu recognizes it which is good.  The directions you posted seem fine to me - let me explain what they mean.

Start executing those commands - I'm writing up an explanation as we speak.

---

### Post by MaindotC on 2008-05-16
Oh I just saw your post about going to the directory.  Do you have instant message?

---

### Post by kami_iwinaru on 2008-05-16
yea, i have aim that i'm on right now

pwnd j00 nub is my sn
lol

---

### Post by MaindotC on 2008-05-16
Here's an explanation.  First of all, these commands should be run from a command prompt.

```

tar xfvz epcamp-src-ubuntu-0.7.1.tar.gz

```

The file you download is compressed - it's the standard in the open source community.  This command will uncompress it so you can use it.  It's like unzipping files in Windoze.  I recommend you download the file to your desktop.

```

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`

```

He's just making sure you have the latest of stuff.  I can explain it in more detail but I think it'll be a bit over your head.

```

sudo make

```

When you do the tar command, you'll see the uncompressed files will be put in a folder.  Navigate to that folder  in the command prompt.  If you list all the files (use the"ls" command), you'll see a file called "Makefile".  The "make" command is a special command that when you run it, it looks for a file in the current directory called "Makefile".  The makefile has a list of instructions that the command "make" executes.

```

sudo make install

```

The final part - as you can tell, this is the "installation".  It may or may not make a nice little icon on the desktop depending on how the source code is set up.

---

### Post by kami_iwinaru on 2008-05-16
```

   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/booga/Desktop modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/booga/Desktop/drivers/usb/epcam.o
/home/booga/Desktop/drivers/usb/epcam.c:33:26: error: linux/config.h: No such file or directory
In file included from /home/booga/Desktop/drivers/usb/epcam.c:47:
/home/booga/Desktop/drivers/usb/epcam.h:162: error: field &#8216;vdev&#8217; has incomplete type
/home/booga/Desktop/drivers/usb/epcam.c:81: error: expected &#8216;)&#8217; before string constant
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_recv_pict&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:257: warning: unused variable &#8216;cp&#8217;
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_start_stream&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:524: warning: assignment from incompatible pointer type
/home/booga/Desktop/drivers/usb/epcam.c:465: warning: unused variable &#8216;endpoint&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:464: warning: unused variable &#8216;interface&#8217;
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_open&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:973: warning: implicit declaration of function &#8216;video_devdata&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:973: warning: initialization makes pointer from integer without a cast
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_close&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:993: warning: initialization makes pointer from integer without a cast
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_ioctl&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:1179: warning: implicit declaration of function &#8216;video_usercopy&#8217;
/home/booga/Desktop/drivers/usb/epcam.c: At top level:
/home/booga/Desktop/drivers/usb/epcam.c:1265: error: variable &#8216;epcam_template&#8217; has initializer but incomplete type
/home/booga/Desktop/drivers/usb/epcam.c:1266: error: unknown field &#8216;owner&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1266: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1266: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1267: error: unknown field &#8216;name&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1267: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1267: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1268: error: unknown field &#8216;type&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1268: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1268: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1269: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1269: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1269: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1270: error: unknown field &#8216;fops&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1270: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1270: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1271: error: unknown field &#8216;release&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1271: error: &#8216;video_device_release&#8217; undeclared here (not in a function)
/home/booga/Desktop/drivers/usb/epcam.c:1271: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1271: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c:1272: error: unknown field &#8216;minor&#8217; specified in initializer
/home/booga/Desktop/drivers/usb/epcam.c:1272: warning: excess elements in struct initializer
/home/booga/Desktop/drivers/usb/epcam.c:1272: warning: (near initialization for &#8216;epcam_template&#8217;)
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_probe&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:1392: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:1392: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:1392: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:1394: warning: implicit declaration of function &#8216;video_register_device&#8217;
/home/booga/Desktop/drivers/usb/epcam.c:1394: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/home/booga/Desktop/drivers/usb/epcam.c:1394: error: (Each undeclared identifier is reported only once
/home/booga/Desktop/drivers/usb/epcam.c:1394: error: for each function it appears in.)
/home/booga/Desktop/drivers/usb/epcam.c: In function &#8216;epcam_disconnect&#8217;:
/home/booga/Desktop/drivers/usb/epcam.c:1413: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
make[2]: *** [/home/booga/Desktop/drivers/usb/epcam.o] Error 1
make[1]: *** [_module_/home/booga/Desktop] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2


```

---

### Post by MaindotC on 2008-05-16
I tried downloading and making the source with the following output:
```

root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2# make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rt3/Desktop/epcam-src-0.8.2 modules
make -C /lib/modules/`uname -r`/build  M=/home/rt3/Desktop/epcam-src-0.8.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rt3/Desktop/epcam-src-0.8.2/drivers/usb/epcam.o
/home/rt3/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function &#8216;epcam_start_stream&#8217;:
/home/rt3/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:885: warning: assignment from incompatible pointer type
/home/rt3/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function &#8216;decode_eplite&#8217;:
/home/rt3/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:1159: warning: unused variable &#8216;i&#8217;
  LD [M]  /home/rt3/Desktop/epcam-src-0.8.2/epcam.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rt3/Desktop/epcam-src-0.8.2/epcam.mod.o
  LD [M]  /home/rt3/Desktop/epcam-src-0.8.2/epcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

I wasn't really satisfied with that so I installed build-essential and here's the output:
```

root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7935kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y

-------edited--------------

Setting up build-essential (11.3ubuntu1) ...
root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2# updatedb
root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2# make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rt3/Desktop/epcam-src-0.8.2 modules
make -C /lib/modules/`uname -r`/build  M=/home/rt3/Desktop/epcam-src-0.8.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2# make install
install -c -m 0644 epcam.ko /lib/modules/`uname -r`/kernel/drivers/media/video
/sbin/depmod -ae
root@rt3-desktop:/home/rt3/Desktop/epcam-src-0.8.2#

```

I don't have a webcam to try this out but it looks like it installed properly - I don't see any errors.  Hope this helps!

---

