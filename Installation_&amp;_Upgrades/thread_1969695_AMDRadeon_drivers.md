---
title: "AMD/Radeon drivers ?"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by DeKosta85 on 2012-04-30
Hello
I am having big problems with getting my Ubuntu 12.04 to work correctly with my AMD Radeon graphic card.

I have both tried manually installing the new drivers from amd.com, with "sudo apt-get fglrx" and proprietary drivers from additional drivers.

The first two either gives me a blank screen typing something is wrong with xorg.conf cant find files OR just giving me graphical errors but still with a slow system.

The latter options enables me to boot into Ubuntu but then i have the following drivers installed = "VESA: _113-BA4302-106" and the OS i sloow..

I have a Intel i5, 8gb RAM and a radeon HD4770 so I think I am able to run Gnome or Ubuntu with the nice effects.

Anyone who could give me some input,
would be much appreciated!

---

### Post by TBABill on 2012-04-30
First, uninstall the drivers you tried to add from the repos. They've been hosed for a while. This link should help you get the file and install of the driver you are looking for.
 
[http://www.upubuntu.com/2012/03/how-to-install-amd-ati-catalyst-123.html](http://www.upubuntu.com/2012/03/how-to-install-amd-ati-catalyst-123.html)
 
That's catalyst 12.3. Hopefully still the latest.

---

### Post by QIII on 2012-04-30
If the driver in the Precise Repo (12.4) has been hosed for a while, it hasn't affected me on several installs.  No need to go anywhere but the repo, so no need to do a manual installation.

Purge all of your attempts.

Do

```
sudo apt-get install fglrx fglrx-amdccle
```

(I've had some success with fglrx-updates, but not enough to recommend it yet)

Then, BEFORE you restart

```
sudo aticonfig --initial
```

to generate an xorg.conf and avoid the black screen.

Gnome does not work well with the ATI driver.  Notice the order I typed that in.  It is a known issue the Gnome devs are working on.

---

### Post by TBABill on 2012-04-30
I had only experienced issues through Beta, then got the driver via AMD to work fine. Hadn't tried it recently because of the issues so if that works, I stand corrected.

---

### Post by DeKosta85 on 2012-04-30
> **QIII said:**
> If the driver in the Precise Repo (12.4) has been hosed for a while, it hasn't affected me on several installs.  No need to go anywhere but the repo, so no need to do a manual installation.

Purge all of your attempts.

Do

```
sudo apt-get install fglrx fglrx-amdccle
```

(I've had some success with fglrx-updates, but not enough to recommend it yet)

Then, BEFORE you restart

```
sudo aticonfig --initial
```

to generate an xorg.conf and avoid the black screen.

Gnome does not work well with the ATI driver.  Notice the order I typed that in.  It is a known issue the Gnome devs are working on.

I began by trying your way it looks very simpel, anyway I went into system settings / additional drivers and then took "remove" on the AMD propreatery FGLRX driver that i had activated before.

And typed the commands above(**sudo apt-get install fglrx fglrx-amdccle** & **sudo aticonfig --initial[**)  into terminal and it boots fine but I still have "VESA: _113-BA4302-106" if I go into system info.

On a sidenote - how do I find out if I have 3D/2D acceleration from my graphicscard enabled ?

Thanks

---

### Post by QIII on 2012-04-30
There was (and still may be) a bug indicating that this is a reporting issue.

Still Gnome DEs may not work well.

For hardware acceleration, you will have to add a few packages.  Unlike NVIDIA, which has its proprietary VDPAU acceleration out of the box, ATI uses the open standard VAAPI with the XvBA back end.

```
sudo apt-get install vainfo xvba-va-driver libva-egl1 libva-glx1
```Then, run

```
vainfo
```You should get something that looks like this:

```
vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```If you get some lines looking something like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1

```a symlink is out of place.

I can help you solve that.

Try adding the acceleration and let me know what happens.

---

### Post by QIII on 2012-04-30
> **TBABill said:**
> I had only experienced issues through Beta, then got the driver via AMD to work fine. Hadn't tried it recently because of the issues so if that works, I stand corrected.

Sorry.  Not trying to be nasty.  24 years of being in the Army makes for a rather direct manner.  I should be more civilized.

---

### Post by DeKosta85 on 2012-04-30
xxx

---

### Post by livewire94 on 2012-04-30
I installed the proprietary drivers from the Additional Drivers.  I only installed the second one, not the first one which is post release update. 

The second one installs just fine. The first one will give you a failed error and partially install which requires you to remove it before installing the second one.

My pc locks up sometimes on shutdown, not sure if its related to proprietary driver or not.  This is using Ubuntu 12.04 64bit with Radeon HD 4670

---

### Post by ratcheer on 2012-04-30
@QIII, that is pretty cool. I've been using my HD6770 for almost a year and I did not know that. It worked for me, except I get "vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8". I just now installed it, so why do I have an older version?

Tim

---

### Post by QIII on 2012-04-30
> **ratcheer said:**
> ...so why do I have an older version?

Hmmmm....  Well.... ah....

Actually, you got me there.  I'll have to do some research.  That's a bit odd.


Edit: Doh!  0.8.0 comes directly from Splitted Desktop.  I deleted the package, got rid of the ppa and reinstalled and now I'm getting 0.7.8, as you are.  Still works fine.

---

### Post by QIII on 2012-04-30
@DeKosta85

You probably have a broken symlink, which sometimes seems to happen.  Computer gremlins.

Would you check to see if you have one of the two following files:

/usr/lib/dri/fglrx_drv_video.so
 /usr/lib/va/drivers/fglrx_drv_video.so

We'll have to sort out a symbolic link pointed to one of them.

---

### Post by DeKosta85 on 2012-05-01
> **QIII said:**
> 
```
sudo apt-get install vainfo xvba-va-driver libva-egl1 libva-glx1
```Then, run

```
vainfo
```You should get something that looks like this:

```
vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```If you get some lines looking something like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1

```a symlink is out of place.

I can help you solve that.

Try adding the acceleration and let me know what happens.

This is what I get after installing and running "vainfo":
```
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

---

### Post by DeKosta85 on 2012-05-01
> **QIII said:**
> @DeKosta85

You probably have a broken symlink, which sometimes seems to happen.  Computer gremlins.

Would you check to see if you have one of the two following files:

/usr/lib/dri/fglrx_drv_video.so
 /usr/lib/va/drivers/fglrx_drv_video.so

We'll have to sort out a symbolic link pointed to one of them.

Check my new quote to your earlier message, I totally forgot to run all the commands.

And to your new message, I got:

/usr/lib/dri/fglrx_dri.so
But no /usr/lib/va directory..

Only got 1 "fglrx_drv_video.so" file and it is in the folder "/usr/lib/x86_64-linux-gnu/dri"

**EDIT**
I did a reinstall, typed in all the commands given and when I run vainfo this time:
```
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```

Though I still have "VESA: _113-BA4302-106" in system settings.

---

### Post by QIII on 2012-05-01
OK.  Good on VAAPI.

As for the VESA message, I'll look around launchpad.  I know there was a reporting error at some point.  The gist was that fglrx is running, but not reported.

---

### Post by DeKosta85 on 2012-05-01
> **QIII said:**
> OK.  Good on VAAPI.

As for the VESA message, I'll look around launchpad.  I know there was a reporting error at some point.  The gist was that fglrx is running, but not reported.

Thank you, appreciated!

Am I running with hardware acceleration now?
And am I running with VESA drivers still?

---

