---
title: "I broke nvidia which broke compiz how to get compiz back?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-10-03
I tried to upgrade nvidia driver to latest one from their site.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
 But it was disaster. No x starting up and console flashing, could do nothing. So I went to recovery and removed nvidia* packages. removed xorg.conf. 
Then I reboot into x and am running the free nv driver.
but system cant find any drivers for nvidia, so i reinstalled from /var cache.

As you can see I am running the nvidia driver, but system does not know this. And desktop effects cannot be enabled.

So what do i need to do?

I might have fixed it, I find kernal mode aliases 173 and installed thru synaptic, reboot and now ubuntu says activate hardware video driver, so I am trying that.

---

### Post by sdowney717 on 2009-10-03
no good, still wont enable desktop effects
> scott@scott-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
> scott@scott-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2624x1200) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I may have fixed this. I selected more of the 173 version files and it removed some 185 version files and it is working.

Is the 185 a later version of the driver? and Can I select this thru synaptic?

yes, i upgraded to 185 version thru synaptic. Got rid of 173.
have to do a complete reboot then it is running fine.

---

### Post by cariboo on 2009-10-03
The 185 driver is in the repositories.

---

### Post by sdowney717 on 2009-10-03
thanks,
the reason i wanted 185 is this for applications to enable VDPAU
support.

> This library provides NVIDIA's implementation of the Video Decode
and presentation API.  It provides acceleration for NVIDIA 7 and later
series cards for h264 video.

---

