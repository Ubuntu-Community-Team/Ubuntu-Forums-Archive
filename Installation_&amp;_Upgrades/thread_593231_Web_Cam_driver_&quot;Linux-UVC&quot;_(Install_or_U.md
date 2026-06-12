---
title: "Web Cam driver &quot;Linux-UVC&quot; (Install or Upgrade)"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by linux23dragon on 2007-10-27
_**[SIZE="4"]Summery [/SIZE]**_

If you have a webcam that does not appear to work with Ekiga or any other web cam applications. Then this 
thread maybe the solution for you.  I've written some steps that will help you determine if the Linux-UVC driver
will (or should) work for you or not.  This thread supports Hardy (Ubuntu-8.04), Gutsy (Ubuntu-7.10) and Ubuntu-7.04
  


**_Check to see if your webcam is supported with the Linux-UVC driver_**.

I'll first point you to the [**_[COLOR="Blue"]Supported Device[/COLOR]_**]("http://linux-uvc.berlios.de/#devices") Section of the official Linux-UVC home page ([http://linux-uvc.berlios.de](http://linux-uvc.berlios.de)).
That should give you a list of supported Webcam models with the Linux-UVC driver itself. 

You can find that out if the Webcam is working (or is detected by the UVC driver) by reading the Kernel System
log, using a program called System Log  Viewer.  You will find this program in the System menu on your task bar:-
*System->Administration->System Log*

Select the "kernel.log" and carefully read (line by line) until you see something like the following:-

[i]```
Oct 27 10:19:07 core2-desktop kernel: [   32.416587] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
Oct 27 10:19:07 core2-desktop kernel: [   32.430238] usbcore: registered new interface driver uvcvideo
Oct 27 10:19:07 core2-desktop kernel: [   32.430242] USB Video Class driver (v0.1.0)
```[/i]


If you find the "uvcvideo" lines in the kernel.log, then its safe to say that your webcam is detected and uses the
Linux-UVC drivers.  

If you don't see any line that states "uvcvideo", then its safe to say that you don't have a UVC Webcam. And so
the webcam will not work with the Linux-UVC driver.  There is lots of other [*_[COLOR="Blue"]**Linux webcam drivers**[/COLOR]_*]("http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html") that may
support your webcam.  And here is more information about [*_[COLOR="Blue"]**webcam drivers and applications**[/COLOR]_*]("http://www.exploits.org/v4l/"). 

**UPDATE:-** more web cam driver support info can be found from [[COLOR="Blue"]**tuxmobil.org**[/COLOR]]("http://tuxmobil.org/laptop_webcams_linux.html")


**_Installing or upgrading the Linux-UVC driver_**

Ubuntu-7.04 and 7.10 already has the Linux-UVC Driver installed in the kernel.  However, this does not mean that
it will just work out of the box for everybody.  The Linux driver is new (just around 2 years) and is improving with
more supported web cam models added every month or so.   

Copy and past the following code into a terminal, to upgrade the Linux-UVC driver:-

**For Hardy (Ubuntu-8.04) and Gutsy (Ubuntu-7.10)**
[i]```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo cp -av /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae $(uname -r) 
```[/i]
Reboot

[COLOR="gray"]Note: You have a backup of the original driver located at "/lib/modules/***uvcvideo.ko***", in case the upgrade turned out
for the worst.  You only need to copy it back to ***/lib/modules/$(uname -r)/ubuntu/media/usbvideo/*** 
to restore the original driver.  You can try to upgrade again at later date after the developers release some updates.[/COLOR]


**For Ubuntu-7.04**
[i]```

sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo cp -av /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae
```[/i]
Reboot

[COLOR="gray"]Note: You have a backup of the original driver located at "/lib/modules/***uvcvideo.ko***", in case the upgrade turned out
for the worst.  You only need to copy it back to ***/lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/***
to restore the original driver.  You can try to upgrade again at later date after the developers release some updates.[/COLOR]
 

The Linux-UVC driver only supports V4L2 (Video 4 Linux 2) applications.  You should be able to use Ekiga by using
the V4L2 plug in found in  Ekiga preferences (Edit->preferences:- Video device section).

There is a unofficial [**_[COLOR="Blue"]WiKi[/COLOR]_**]("http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC") page that details the applications that work (or not) with your supported webcam. Have
a look at the "*[COLOR="DarkOrange"]Known Problems[/COLOR]*" section for workarounds and patches, that  you might need.  The Wiki
also details on how to use an official test program called [**_[COLOR="Blue"]luvcview[/COLOR]_**]("http://mxhaard.free.fr/spca50x/Investigation/uvc/").  It is recommended to use luvcview, to see if
your Webcam is working correctly with the Linux-UVC driver.

---

### Post by tyboon on 2008-01-14
man.........you rock ......
It did work .... thanks a lot...):P):P\\:D/

---

### Post by magicrobotmonkey on 2008-02-09
yea, this helped me with getting skype to work right, thanks a lot!

---

### Post by maconlysource on 2008-02-29
Cannot get my compaq c756ca webcam to work in Ubuntu 7.1.

If I install Hardy, it works fine. It does use uvcvideo in Hardy.

Any ideas how I can get it to work  in 7.1?

If I start xawtv  in 7.1 I get a black screen and the webcam blue light blinks. Cheese freezes, and camoram cannot find dev/video0.

Thanks in advance.

---

### Post by tribunal on 2008-03-01
yes, it works :)
But no so good as I want it to :(
I have some bugs with my Logitech Ultra-Vision
After some time SOMETHING happens and my cam stops working :confused:
It works ok only after restarting PC, or shutting down the cam, and rmmod/modprobe drivers
What should I do?
There are something about patches in 
[here]("http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC"), but I'm not a system developer to use them :(

---

### Post by ericstoesser on 2008-03-09
will this work with stickam

---

### Post by Mustard on 2008-03-09
> **ericstoesser said:**
> will this work with stickam

I dont think it will help with stickam, as the problem with stickam is that it is using Adobe Flash, and Adobe Flash doesnt support V4L2.  The UVC drivers only work with V4L2.  So basically if your camera relies on UVC drivers, it wont work with anything that uses V4L1.

---

### Post by Koen460 on 2008-03-24
thnx for your reply. I m new user and have to get used to this environment. So sorry if I don't reply correctly at this very moment. :)

---

### Post by cirpo on 2008-03-29
hi,
can't get it working... :(


modprobe uvcvideo
```


FATAL: Error inserting uvcvideo (/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

dmesg output:

> 

[  312.503261] uvcvideo: disagrees about version of symbol video_devdata
[  312.503266] uvcvideo: Unknown symbol video_devdata
[  312.503469] uvcvideo: disagrees about version of symbol video_unregister_device
[  312.503472] uvcvideo: Unknown symbol video_unregister_device
[  312.503536] uvcvideo: disagrees about version of symbol video_device_alloc
[  312.503538] uvcvideo: Unknown symbol video_device_alloc
[  312.503588] uvcvideo: disagrees about version of symbol video_register_device
[  312.503590] uvcvideo: Unknown symbol video_register_device
[  312.503749] uvcvideo: disagrees about version of symbol video_device_release
[  312.503751] uvcvideo: Unknown symbol video_device_release



:( help...


thanks 

cirpo

---

### Post by carlos_listas on 2008-03-29
Hi all, until today morning my web can was working very well, but I installed a cx18 driver to try do work a hp tv tuner ([http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)) and after this my webcan didn't work more.

hp pavilion dv9640us
/var/log/messagesNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu hardy (development branch)
Release:	8.04
Codename:	hardy



before cx18 module

Mar 28 21:02:02 tocals-linux kernel: [   46.453205] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b023)
Mar 28 21:02:02 tocals-linux kernel: [   46.455223] usbcore: registered new interface driver uvcvideo
Mar 29 14:41:01 tocals-linux kernel: [   47.412424] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b023)
Mar 29 14:41:01 tocals-linux kernel: [   47.414471] usbcore: registered new interface driver uvcvideo

after cx18 module

:# modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-12-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Mar 29 16:12:22 tocals-linux kernel: [   55.180567] uvcvideo: disagrees about version of symbol video_devdata
Mar 29 16:12:22 tocals-linux kernel: [   55.180571] uvcvideo: Unknown symbol video_devdata
Mar 29 16:12:22 tocals-linux kernel: [   55.180988] uvcvideo: disagrees about version of symbol video_unregister_device
Mar 29 16:12:22 tocals-linux kernel: [   55.180990] uvcvideo: Unknown symbol video_unregister_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181122] uvcvideo: disagrees about version of symbol video_device_alloc
Mar 29 16:12:22 tocals-linux kernel: [   55.181124] uvcvideo: Unknown symbol video_device_alloc
Mar 29 16:12:22 tocals-linux kernel: [   55.181211] uvcvideo: disagrees about version of symbol video_register_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181214] uvcvideo: Unknown symbol video_register_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181473] uvcvideo: disagrees about version of symbol video_device_release
Mar 29 16:12:22 tocals-linux kernel: [   55.181475] uvcvideo: Unknown symbol video_device_release

---

### Post by 300890 on 2008-04-01
Works perfectly on my ASUS U3S laptop! 

Thank you.

---

### Post by linux23dragon on 2008-04-05
> **carlos_listas said:**
> Hi all, until today morning my web can was working very well, but I installed a cx18 driver to try do work a hp tv tuner ([http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)) and after this my webcan didn't work more.

hp pavilion dv9640us
/var/log/messagesNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu hardy (development branch)
Release:	8.04
Codename:	hardy



before cx18 module

Mar 28 21:02:02 tocals-linux kernel: [   46.453205] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b023)
Mar 28 21:02:02 tocals-linux kernel: [   46.455223] usbcore: registered new interface driver uvcvideo
Mar 29 14:41:01 tocals-linux kernel: [   47.412424] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b023)
Mar 29 14:41:01 tocals-linux kernel: [   47.414471] usbcore: registered new interface driver uvcvideo

after cx18 module

:# modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-12-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Mar 29 16:12:22 tocals-linux kernel: [   55.180567] uvcvideo: disagrees about version of symbol video_devdata
Mar 29 16:12:22 tocals-linux kernel: [   55.180571] uvcvideo: Unknown symbol video_devdata
Mar 29 16:12:22 tocals-linux kernel: [   55.180988] uvcvideo: disagrees about version of symbol video_unregister_device
Mar 29 16:12:22 tocals-linux kernel: [   55.180990] uvcvideo: Unknown symbol video_unregister_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181122] uvcvideo: disagrees about version of symbol video_device_alloc
Mar 29 16:12:22 tocals-linux kernel: [   55.181124] uvcvideo: Unknown symbol video_device_alloc
Mar 29 16:12:22 tocals-linux kernel: [   55.181211] uvcvideo: disagrees about version of symbol video_register_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181214] uvcvideo: Unknown symbol video_register_device
Mar 29 16:12:22 tocals-linux kernel: [   55.181473] uvcvideo: disagrees about version of symbol video_device_release
Mar 29 16:12:22 tocals-linux kernel: [   55.181475] uvcvideo: Unknown symbol video_device_release

Your using Ubuntu-8.04 Beta :-)

I'll be writing  up for support Hardy after the stable version  has been released.  Or perhaps I could add support now?

Just a question.  Is the kernel tree [COLOR="DarkOrange"]/lib/modules/$(uname -r) [/COLOR] the same as the Gutsy kernel tree (apart from the kernel version)?

Is the uvcvideo.ko driver in the same location we are installing too? 

I have not yet installed the beta version of Hardy yet, but I could get a head start from your feed back.

Thanks for the report.

---

### Post by linux23dragon on 2008-04-05
> **cirpo said:**
> hi,
can't get it working... :(


modprobe uvcvideo
```


FATAL: Error inserting uvcvideo (/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

dmesg output:



:( help...


thanks 

cirpo

Thanks for the report.

I've updated the modprobe commands to make sure that we are updating the correct kernel modules that is being used. 

Also, Its possible to load the kernel module (without installing the driver) using the  insmod command.

[I]Note that you may need to move the backup driver[COLOR="DarkOrange"] /lib/modules/uvcvideo.ko [COLOR="Black"]and/or[/COLOR] /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko [/COLOR] to another location.  Then use the updated modprobe commands:-
```
modprobe -ae $(uname -r)
```
Then reboot,  to help make sure this following instruction is to work correctly. [/I]



You don't need to install the kernel driver (after compilation) if you want to  test the driver first.  You only need to be in the same [COLOR="YellowGreen"]trunk[/COLOR] directory (where the new uvcvideo.ko is) to use this following command:-   
```
sudo insmod uvcvideo.ko
```

That should load the driver, and run the camera.  Please check your kernel logs (System -> Administration -> System log) to see what is happening once you try to load the kernel driver.

---

### Post by oodledoodle on 2008-04-05
hey, thanks alot buddy, i managed to use your guide to get the creative live optia af webcam working on amsn. 

cheers.

---

### Post by bogoliubov on 2008-04-10
Hello. I checked out the driver from the subversion repo, but doesn anyone know how to install it in Hardy?

---

### Post by bogoliubov on 2008-04-10
Perhaps I should also mention that I compiled it, changed the makefile to what seemed to be correct: 

Is this OK?

Then I did "sudo make install" and rebooted.

When adding the driver with modprobe, I get this in kern.log:
kernel: [  266.326392] Linux video capture interface: v2.00
kernel: [  266.332451] usbcore: registered new interface driver uvcvideo
kernel: [  266.332459] USB Video Class driver (SVN r200)

But I don't get any /dev/video0 device! 
What have I done wrong?

---

### Post by linux23dragon on 2008-04-11
> **bogoliubov said:**
> Perhaps I should also mention that I compiled it, changed the makefile to what seemed to be correct: 

Is this OK?

Well yes :)

> **bogoliubov said:**
> 
Then I did "sudo make install" and rebooted.

When adding the driver with modprobe, I get this in kern.log:
kernel: [  266.326392] Linux video capture interface: v2.00
kernel: [  266.332451] usbcore: registered new interface driver uvcvideo
kernel: [  266.332459] USB Video Class driver (SVN r200)

But I don't get any /dev/video0 device! 
What have I done wrong?

That seemed to work ok.  Is your web cam connected via USB?  If so,  make sure that the web cam is directly connected into the PC, not to a external USB hub.

The kernel should auto load the driver once the web cam is plugged into the PC (or detected by the kernel on boot up).  Are you sure that your web cam is compatible with the UVC driver? 

Otherwise, you may need to see if an SVN update might fix the issues your currently having.

---

### Post by bogoliubov on 2008-04-11
> **linux23dragon said:**
> Well yes :)



That seemed to work ok.  Is your web cam connected via USB?  If so,  make sure that the web cam is directly connected into the PC, not to a external USB hub.

The kernel should auto load the driver once the web cam is plugged into the PC (or detected by the kernel on boot up).  Are you sure that your web cam is compatible with the UVC driver? 

Otherwise, you may need to see if an SVN update might fix the issues your currently having.

The camera is built in the laptop.

I'm not 100% sure it's supported, but in one of the driver source files, it says something about a Clevo M540SR, and I thought it would be the same camera as in my laptop (Clevo M540N).

So, if my camera was supported by the driver, there would be some more info in kern.log or what? Or dmesg? 
If I turn off the camera (short-cut using function keys) and then turn it on again, dmesg shows this:
[   46.571491] usb 5-7: USB disconnect, address 3
[   47.820370] usb 5-7: new high speed USB device using ehci_hcd and address 8
[   47.960230] usb 5-7: configuration #1 chosen from 1 choice

---

### Post by bogoliubov on 2008-04-11
Hmm, it seems that I have the Ali M5602 cam, and the UVC driver supports the ALi M5606 cam. Still, I hoped it would have been so similiar that it worked. 
I'll just wait around til someone writes a driver for the 5602...

Well, sorry to have taken your time, and thanks for the help

---

### Post by linux23dragon on 2008-04-11
> **bogoliubov said:**
> Hmm, it seems that I have the Ali M5602 cam, and the UVC driver supports the ALi M5606 cam. Still, I hoped it would have been so similiar that it worked. 
I'll just wait around til someone writes a driver for the 5602...

Well, sorry to have taken your time, and thanks for the help

I'll look into that.  

I'm not sure, but I suspect that it uses the same chip as the ALi M5606.  However the kernel driver was not auto loaded when you re-enabled the web cam.  So It is possible that is not supported.  But I'll check it out to see if that is the case.


**UPDATE:**

I have found a driver project on sourceforge that supports your web cam.  

[[COLOR="Blue"]Ali M560x Linux Driver[/COLOR]]("http://sourceforge.net/projects/m560x-driver/")

It looks new but they do have code in SVN:

```
svn co https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver m560x-driver
```

Hope that helps.

---

### Post by bogoliubov on 2008-04-12
Yeah, I found this project yesterday as well! I did check out the "branches/m5602-ov9650"  version, but I can't "insmod" it for some reason (I get a segfault).

---

### Post by bogoliubov on 2008-04-12
Actually, I get a segfault, but still the driver loads. But I can't see anything with xawtv, so I still need to wait for a better version of the driver...

---

### Post by ExBuM on 2008-04-14
Is it just me me or does ```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
``` not work? :/ I get a timed out error.

---

### Post by linux23dragon on 2008-05-16
I was able to install the latest Linux-UVC driver using Hardy.

Here is my kernel log.  I'm using QC-Fusion webcam with the Hardy 64bit OS. 

```

usb 1-10: new high speed USB device using ehci_hcd and address 4
usb 1-10: configuration #1 chosen from 1 choice
Linux video capture interface: v2.00
ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usbaudio.c:1289: 4:3:3: cannot set freq 16000 to ep 0x86
uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
input: UVC Camera (046d:08c1) as /devices/pci0000:00/0000:00:0b.1/usb1/1-10/1-10:1.0/input/input7
usbcore: registered new interface driver snd-usb-audio
usbcore: registered new interface driver uvcvideo
USB Video Class driver (SVN r209)

```

Tested with skype.

---

### Post by athianos on 2008-07-15
This worked perfectly for me to install a Bison webcam on a Packard Bell Easynote SJ 51-B-008 running Ubuntu Hardy Heron 8.04 64-bit.

THANKS!:KS

---

