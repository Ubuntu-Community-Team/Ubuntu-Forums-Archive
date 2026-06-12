---
title: "gspca driver will not compile in intrepid"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ElTimo on 2008-10-19
I have a logitech quickcam e2500 webcam, and I cannot get the necessary driver (gspca) to compile. I have all of the necessary packages, and I was able to get the driver to compile under hardy. Any help at all would be greatly appreciated, as this problem is driving me NUTS!

---

### Post by yostral on 2008-10-19
Why do you want to compile it ? Gspca driver is now in the kernel. Even in v4l2 version.

---

### Post by ElTimo on 2008-10-19
I want to compile it because the default driver apparently doesn't support my webcam. If it actually does, how can i get it to work?

---

### Post by ElTimo on 2008-10-19
Bump. Any ideas? Anyone?

---

### Post by avb on 2008-10-19
there is latest gspca driver bundled in intrepid. If your camera is not detected, that mean it just not supported. 

Please, plug in your camera and run 'dmesg' in terminal. Output of dmesg attach to this thread. Lets see, is it v4l2 issue or your camera just not supported.

---

### Post by ElTimo on 2008-10-19
well, that's the thing. My webcam wasn't supported by the normal gspca driver before. I had to apply a patch to it before it would work. that's why I want to compile it from source if possible, or at least find out if there's a patched version I can use.

---

### Post by ronacc on 2008-10-19
at what stage is it failing to compile and what are the error messages ? the build chain is pretty good about telling you why something dosent work.

---

### Post by ElTimo on 2008-10-20
Usually it fails when looking for the header file asm/semaphore.h, but I removed the line that said #include<asm/semaphore.h> without trouble. After that, it fails on some functions:```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/tim/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/tim/gspcav1-20071224/gspca_core.o
/home/tim/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/tim/gspcav1-20071224/gspca_core.c:2465: error: implicit declaration of function ‘video_usercopy’
/home/tim/gspcav1-20071224/gspca_core.c: At top level:
/home/tim/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘owner’ specified in initializer
/home/tim/gspcav1-20071224/gspca_core.c:2611: warning: initialization from incompatible pointer type
/home/tim/gspcav1-20071224/gspca_core.c:2613: error: unknown field ‘type’ specified in initializer
/home/tim/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/tim/gspcav1-20071224/gspca_core.c:2771: error: implicit declaration of function ‘video_device_create_file’
/home/tim/gspcav1-20071224/gspca_core.c:2782: error: implicit declaration of function ‘video_device_remove_file’
/home/tim/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/tim/gspcav1-20071224/gspca_core.c:4313: error: incompatible types in assignment
make[2]: *** [/home/tim/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/tim/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

```
Sorry for not including that earlier.
Has something in the framework of the kernel changed drastically since 2.6.24? Or am I just missing something completely.

---

### Post by ronacc on 2008-10-20
thats what it looks like , are you using the same source that you used for .24 ? also it might be the version of gcc , have a look at the config script and see what version its looking for .

---

### Post by ElTimo on 2008-10-20
Yes, I'm using exactly the same source I used with .24
The dumb thing is that there isn't a config file per se, but there is a file called "gspca_build" that does essentially the same thing, but I can't find anything particularly helpful in there.

---

### Post by ronacc on 2008-10-20
is it the same source that is in synaptic for that driver ? if not take a look at the one in synaptic and mabye ou can see what they did to get it to compile , I'm suspicious about those "implicit" declarations  mabye they need to be "explicate" .

---

### Post by ElTimo on 2008-10-20
I tried the one in Synaptic and that one didn't compile either. I think they're the same version. Is there a source package I could patch?

---

### Post by ronacc on 2008-10-20
hmm if the one in synaptic won't compile file a bug on it .I'll see if I can get it to compile here .

---

### Post by ElTimo on 2008-10-20
Awesome, thanks. If you do manage to get it to compile, let me know what changes you had to make (if any) to the source code to get it to work. Oh, and by the way, you wouldn't happen to know what it means by "implicit function declaration" would you?

---

### Post by ronacc on 2008-10-20
don't take what I say as gospel . a function or variable can be declared explicitly which tells the program what that function means or implicitly by just calling that function , I don't know if GCC allows inplicit functions . If theres a programer reading this please correct this if I'm wrong .

---

### Post by ronacc on 2008-10-21
I'm getting the same errors trying to compile the driver . Checking launchpad I found this bug .[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/273727](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/273727)  . It never explains the compile error but does say the builtin driver is now working with the latest kernel so give that a try again .also add your comments to the bug .

---

### Post by ElTimo on 2008-10-21
Did it say which kernel version was being used? And did it specify what type of webcam was working? Because I'm fairly sure the normal gspca driver works fine, but my webcam needs a patched version, like I said. Until I can fix it though, I have a separate install of Hardy for when I need to use my webcam.

---

### Post by ronacc on 2008-10-21
take a look at the bug and add your comments . If you don't report bugs they don't get fixed . I added a comment to the bug saying that  the builtin driver working did not address the bug because that was about gspca-source not compiling and it still doesn't . add your comments the more reporters the more likely it will get worked on .

---

### Post by avb on 2008-10-21
i propose to fill a bug against gspca or linux package on launchpad saying that your webcam XXX is not working with stock gspca driver and before u was patching it with non upstream patch. Attach a patch and probably guys will take care of it. 
An issue why its not compiling now, is that there is a lot of work was done in v4l sybsystem so its api was broken again.

---

### Post by ronacc on 2008-10-21
thanks for the info about v4l . ElTimo was trying with the patched driver source I was trying with the driver source from synsptic with no patch , either way it dont compile , there are already several bugs on launchpad about don't work with xyzwebcam mabye a list somewhere about which ones work and which don't would be better than a whole mess of individual bugs ?

---

### Post by linux6994 on 2008-10-24
Same trouble here. Logitech works with vlc method, cature device /dev/video0
entries but kopete and camorama still unable to open device.

[ 7143.004067] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 7143.128087] usb 4-1: device descriptor read/64, error -71
[ 7143.455142] usb 4-1: configuration #1 chosen from 1 choice
[ 7143.458219] gspca: probing 046d:08d7
[ 7145.103959] zc3xx: probe 2wr ov vga 0x0000
[ 7145.151950] zc3xx: probe sensor -> 11
[ 7145.151963] zc3xx: Find Sensor HV7131R(c)
[ 7145.162678] gspca: probe ok
[ 7145.164446] gspca: probing 046d:08d7

---

### Post by inportb on 2008-10-24
Yeah, implicit declaration means calling a function before it has been declared, which is illegal in all cases of C that I have seen.

You removed the include directive to semaphore.h, which presumably contains the necessary declarations. If you don't have that file, then something else's up.

---

### Post by Permafrost91 on 2008-10-26
same problem here ... Ubuntu Intrepid 32bit with latest updates/kernel and Logitech QuickCam. Has anyone gotten this to work yet?

---

