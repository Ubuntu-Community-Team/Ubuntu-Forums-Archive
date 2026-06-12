---
title: "Unable to install V14.04.1, Radeon 3000"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2015-02-03
Folks,

I have been using 12.04 since it was released and have installed every update I'm aware that 12.04 LTS is good until 2017 but if possible would like to update to 14.04.1. My Update Manager is set for New Versions to 'For Long Term Support, and sure enough when Update Manager is opened it shows the message ' New Ubuntu release '14.04.1 LTS' is available.

When I select the Upgrade button, the new installation appears to start. However, after a few seconds the message:
Your graphics hardware may not be fully supported in Ubuntu 14.04.

'Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?'

I've read the stuff at the wiki.ubuntu.com/X/Bugs./UpdateManagerWarningForUnity3D but don't really understand what it means.

Does it mean, for exanple, that I need to get a different graphics card? And if so any suggestions as to what to get will be gratefully received.

My motherboard is:GA-78LMT-USB3, If that's any help.

I'm not a guru so I will be grateful if someone could let me know what I need to do to be able to update to V 14.04.1

Regards,

Bob

---

### Post by QIII on 2015-02-03
Would you share with us the OEM and model of your graphics adapter?

Edit:  In case I'm not around when you get back, please run the following in the terminal:

```
sudo lshw -C video | grep product
```

If that doesn't show anything interesting, do 

```
sudo lshw -C video
```

Copy the results back here between code tags. 

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by bobmac on 2015-02-04
Blöder Esel,

It seems that the graphics is part of the motherboard. The motherboard Users Manual gives the following:
North BRIDGE
1 X d-SUB PORT, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
1 X dvi-d PORT, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
The DVI-D port does not support D-Sub connecion by adapter
1 x HDMI port, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
Simultaneous output for DVI-D and HDMI is not supported
Support for S/PDIF Out

Bob

---

### Post by deadflowr on 2015-02-04
> **bobmac said:**
> Blöder Esel,

It seems that the graphics is part of the motherboard. The motherboard Users Manual gives the following:
North BRIDGE
1 X d-SUB PORT, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
1 X dvi-d PORT, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
The DVI-D port does not support D-Sub connecion by adapter
1 x HDMI port, SUPPORTING A MAX RESOLUTION OF 1920 X 1200
Simultaneous output for DVI-D and HDMI is not supported
Support for S/PDIF Out

Bob

None of this though is helpful in telling us what the actual card is.
Post the info that the two commands in post #2 show.

Edit: Looking over what the motherboard specs are it would seem it's an ati(amd)radeon 3000.
On 12.04 did you installed the additional drivers, by chance.

(I think 12.04 and 12.04.1 still used the supported X stack for that card, but succeeding versions do/did not.)
Double edit: Sorry my wording is bad, I mean amd dropped support for that card so no new (fglrx)drivers are being written for it against the latest X stacks, so the X stack on original 12.04 would be the last for it, if that makes sense. The open source driver is, though, still being supported for that card.

Of course the commands would have easily told us that...

---

### Post by bobmac on 2015-02-04
Using 'udo lshw -C video | grep product' the result is:

```
product: RS780L [Radeon 3000]
```

Bob

---

### Post by bobmac on 2015-02-04
When using 'sudo lshw -C video', the result is

 ```
*-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:ee00(size=256) memory:fdee0000-fdeeffff memory:fdd00000-fddfffff
```

Bob

---

### Post by grahammechanical on 2015-02-04
We can see for sure if the graphic adapter can support Unity 3D by running this

```
/usr/lib/nux/unity_support_test -p
```

This is what I see when I run that test

> OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.113


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes




That tells us that I have an Nvidia GT220 and it is running on the Nvidia proprietary video driver. If I was using the open source video driver it would say "Nouveau." What is really useful is the knowledge that this video adapter can run Ubuntu 3D.

What does that test show for you? When you installed Ubuntu 12.04 if the graphic adapter could not run Unity 3D then the installer would have installed Ubuntu 2D automatically. You may be running Unity 2D. But versions of Ubuntu after 12.04 do not come with Unity 2D.

In the situation where a graphic adapter cannot do the hardware accelerated rendering that is needed for Unity 3D the 14.04 installer will load an open source video driver called llvmpipe. This will give an approximation of Unity 3D on graphic adapters that cannot run Unity 3D. It is also used for Recovery mode Resume. It works. It does what it is supposed to do but I would not call the opening and closing of application windows "snappy." Even on hardware can run Unity 3D.

My advice would be before you upgrade to de-activate any proprietary video driver that may be in use and revert to using the open source video driver, which is called "Radeon" for ATI/AMD graphic adapters. I advise this because the upgrade to 14.04 will bring in the latest stable proprietary video driver which may no longer support your graphic adapter. Support for older cards is sometimes dropped from later proprietary video drivers. So, I think that it is always best to start an upgrade with an open source video driver.

The important point to take away from this is that upgrading will still give you a working OS, even if it is by using llvmpipe. If the user experience is close to being unusable than in 14.04 we can install Gnome Session Flashback (search the software centre for Gnome Flashback). That will give us 2 extra login screen options neither of which use Unity. But you have a working computer operating system.

Regards.

---

### Post by mörgæs on 2015-02-04
> **grahammechanical said:**
> 
My advice would be before you upgrade to de-activate any proprietary video driver that may be in use and revert to using the open source video driver, which is called "Radeon" for ATI/AMD graphic adapters. I advise this because the upgrade to 14.04 will bring in the latest stable proprietary video driver which may no longer support your graphic adapter. Support for older cards is sometimes dropped from later proprietary video drivers. So, I think that it is always best to start an upgrade with an open source video driver.



There are no closed source / proprietary drivers in use in the present system and there are none available for this GPU in 14.04.

---

### Post by bobmac on 2015-02-04
Graham Mechanical,

This is the result of running the command you suggested.

/usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

Bob

---

### Post by bobmac on 2015-02-04
Morgaes,

I'm not sure what you and GrahamMechanical mean when you talk about these graphic drivers and so on. I'm afraid that I'm no guru when it comes to the techo stuff in ubuntu.

Is it possible to simply buy a graphics card that would do the job and let me install the new LTS version?

Regards,

Bob

---

### Post by mörgæs on 2015-02-04
I meant that you should forget everything that people have written about closed source drivers in the thread. Irrelevant since you are not using them and you are not going to. This is no problem as the open source drivers are getting good, especially in 14.10.

No need for buying new hardware. Have you considered a clean install of X/Lubuntu?

---

### Post by Mark Phelps on 2015-02-04
> Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. 

In your case, this means that you will be doing Software Rendering and that will seriously load the CPU for graphics operations, as the fglrx driver is not available for your AMD card and any Ubuntu release newer than 12.04.1.

It will still work, but it will be slow and tax your processor.

---

### Post by bobmac on 2015-02-04
mörgæs,

Seems to me that perhaps the real answer to my problem is to get a new motherboard. If this is so, perhaps you could advise me as to which one I should get.

Bob

---

### Post by mörgæs on 2015-02-05
No, I would advise you to do what I posted in #11.

---

### Post by bobmac on 2015-02-05
mörgæs,

I thank you for your information and in particular your patience. Can I ask if X/Lubuntu versions come with LTS? which I like as then I don't have to upgrade every 6 months or so.

Bob

---

### Post by deadflowr on 2015-02-05
Indeed, discussions on the fglrx drivers were merely speculatory, since the driver was unknown at the time.

My advice is try one of the less hungry flavors, as suggested.
And if you wanted to spend money, I suggest buying an external usb (or even a second internal)  hard drive for quick/easy backups, over buying a new motherboard or gpu.

--as for how long Lubuntu and Xubuntu run LTS's, I think Xubuntu's is 3 years. But I can't remember Lubuntu's. Though I think it is 2 years.

---

### Post by bobmac on 2015-02-05
Folks,

Many thanks for your patience and information. It is much appreciated especially from a group of volunteers.

I will now close this thread.

Again, many thanks,

Bob

---

