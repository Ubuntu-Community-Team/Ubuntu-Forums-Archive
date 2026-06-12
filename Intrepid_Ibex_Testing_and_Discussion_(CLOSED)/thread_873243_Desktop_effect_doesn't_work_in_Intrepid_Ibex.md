---
title: "Desktop effect doesn't work in Intrepid Ibex"
date: 2008-07-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ajeetraj on 2008-07-28
I just updated from Hardy to Ibex and everything seems to work fine apart from the visual effects. I am using Dell Latitude D630. When I try to use the visual effects (normal or extra) my whole screen just scrambles and freezes. I then have to click (guess the place) the no effect and then I am back to metacity (without compiz theme). 

I had compiz working before I upgraded to Ibex. Any ideas?

So far, I like the theme (even though its dark) :)

---

### Post by overdrank on 2008-07-28
moved to Intrepid Ibex Testing and Discussion :)

---

### Post by olskar on 2008-07-28
What is the output of > compiz --replace in a terminal?

---

### Post by ajeetraj on 2008-07-28
My terminal output. It still gets scrambled and I can't see any windows (the screen is mostly black with few colors at the borders of the windows). I press Ctrl+C and then get back my metacity.

> deepu@raj:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered



Thanks for your help

---

### Post by olskar on 2008-07-29
Hm, according to that compiz is running at least.. You should check if anyone knows in the compiz irc-channel; #compiz at ircfreenode.net :)

---

### Post by ronacc on 2008-07-29
what is the video on your dell ? right now the are problems with some drivers .

---

### Post by jfernyhough on 2008-07-29
Try disabling Blur in CompizConfig before enabling Compiz. That plugin has been a pain for a while on Intel graphics, something to do with a lack of shaders (whether drivers or hardware, I'm not sure). At least, on GMA950 or before (not sure if it's still the same with X3100).

---

### Post by F-3582 on 2008-08-02
Hi. I just did a fresh install of Intrepid Alpha3 (and 200 updates), but Compiz fails to load. It keeps outputting

```
$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity
```

I'm using an ATI mobilityRadeo 9700 and glxinfo tells me that direct rendering is indeed enabled. What's up with Compiz?

Okay, found the reason. Compiz working fine, by the way. It crashed X only once ;)

---

### Post by mullenrbock on 2008-09-17
Has anyone had any success? I'm having somewhat of the same problem. When I run "compiz --replace", it says that Xgl is not present. Shouldn't that be taken care of when the compiz package is installed? My video card is a Radeon 3100, but I think the drivers are already out for it. I have both fglrx and radeonhd installed, because I'm not sure which one is more suited to the task, and I don't know which one is currently being used as the driver.

---

### Post by inportb on 2008-09-17
No, Xgl is not required and not recommended for running Compiz.

I don't think fglrx works just yet, so you'd be better off using radeon (read: not radeonhd). Radeon's what you'd get if you use a fresh xorg.conf, though you could specify explicitly.

---

### Post by mullenrbock on 2008-09-17
I forget where to add the drivers in xorg.conf or if there's a way to automatically update it to use radeon. Is there a quick way to do it?

---

### Post by kimda on 2008-09-23
I had the same problem. Glxinfo would crash and couldn't get compiz to work till I checked the Xorg.0.log for errors. I found out that the symbolic link to libglx.so was wrong! It pointed to an old driver which was probably the Hardy package. I removed the symlink and made a new symlink to libglx.so.177.76. After this compiz worked again. Maybe the package could check remove the old symlink and make a new symlink. The location of this symlink is at /usr/lib/xorg/modules. Hope this helps since I tried a lot of stuff like reinstalling drivers and nothing worked.

---

### Post by mullenrbock on 2008-09-24
kimda, where did you find libglx.so.177.76?

---

### Post by kimda on 2008-10-10
Today it broke again. If you are experiencing the same problems (no Compiz) issue the following command: 

1. remove old symlink 
sudo rm /usr/lib/xorg/modules/libglx.so

2. create new symlink
sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.177.80 /usr/lib/xorg/modules/libglx.so

Restart X server (log out/in). 

mullenrbock:
I have nvidia-glx-177 installed which installs the libglx.so.177.80 file. 

I have installed these packages:
nvidia-177-kernel-source
nvidia-177-modaliases
nvidia-glx-177
nvidia-kernel-common
nvidia-settings

I filed a new bug report here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/281259](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/281259)

---

### Post by gaixixon on 2008-10-15
me too, I can not start Desktop visual effect and here is the error I got:
"Desktop effects could not be enabled".
when I try compiz --replace it says:
> teppy@BP:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

any hints?

---

### Post by d34dh0r53 on 2008-10-15
Try removing the package xserver-xgl

You also may need to remove the file /etc/X11/Xsession.d/98xserver-xgl_start-server

HTH

---

### Post by jadedoto on 2008-10-22
And it's still broken. But this fixed it.

---

### Post by ngine13 on 2008-10-22
If you upgraded the system from 8.04 and installed the nvidia 177.80 drivers from nvidia site like i did.. you can check the following that solved my problem (i hope your too!) :

sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.177.80 /usr/lib/xorg/modules/libglx.so

Now everything is working fine and gpu temp dropped 10 degrees!

Don't forget to restart the xserver!

P.S. : Thanks kimda!!! :)

---

### Post by caryb on 2008-10-22
> sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.177.80 /usr/lib/xorg/modules/libglx.so



I can confirm this fixes the problem in Kubuntu as well:)


Cary

---

### Post by ronocdh on 2008-10-29
> **d34dh0r53 said:**
> Try removing the package xserver-xgl

You also may need to remove the file /etc/X11/Xsession.d/98xserver-xgl_start-server
This was awesome, thank you! It really was as simple as removing xserver-xgl. I was never able to get Compiz running under Hardy without XGL, but in Intrepid it's evidently possible!

I'm running the Intrepid beta with a fully working autoconfigured fglrx, for those interested.

---

