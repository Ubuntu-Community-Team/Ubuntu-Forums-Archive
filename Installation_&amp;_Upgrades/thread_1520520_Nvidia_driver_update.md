---
title: "Nvidia driver update"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Zirts on 2010-06-29
Hi,

I'm planning to update my Nvidia video driver.

Now in the Terminal, it sayd that my driver is something like this:

nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)

So, I googles nvidia drivers and got to the nvidia homapage and inserted all the info there and got to this page:

[http://www.nvidia.com/object/linux_nforce_1.25.html](http://www.nvidia.com/object/linux_nforce_1.25.html)



Now, my questions are:

Is this the right one for my driver?
When I download it, I get a .zip file and I'm not yet familiar with installing with thoes, so how can I do it.

---

### Post by Zirts on 2010-06-29
Hate to do it, but bump. 

The thread was allready on the second page...

---

### Post by davidmohammed on 2010-06-29
why do you need to install from the nvidia website?  What version are you using from the "hardware drivers" screen?

My view - you don't really need to download the nvidia website version unless you've got a very new graphics card that the stock ubuntu version doesnt cope with.

---

### Post by RJARRRPCGP on 2010-06-29
That's not the right drivers, because that's not for graphics.

---

### Post by Zirts on 2010-06-30
Well the problem is that  the "hardware drivers" screen is showing absolutly nothing, it says that my comptuer does not have any drivers lol.

---

### Post by okplayer02 on 2010-06-30
run the following command to list all the pci devices in your machine including the video card. we have to determine which one you have. 


```
lspci
```

---

### Post by dino99 on 2010-06-30
into a console, run:

sudo rm -f /etc/X11/xorg.conf

goto synaptic and check that: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings are installed

then reboot and check again that nvidia-current is activated (system admin hardware driver)

---

### Post by Zirts on 2010-06-30
Well i got the lspci list now:

```

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```

But the command dino99 suggested did not do anything at all in Terminal.

Edit: nvidia-cuurent OK, nvidia-current-modaliases OK, nvidia-common NO instead i got a nvidia-kernel-common,
nvidia-settings OK.
Edit2: Ok got nvidia-common too now.

Plus now that I installed thoes, when I open the nvidia x server, it gives me this error

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

and the command it suggests doesen't do anything too.
Also my desktop effects work nolonger, it is impossible to switch them on too...


Edit3:  Every game I try to run now crashes the computer after installing thoes thingys too.

Edit4: Uninstalled what I installed and everything is back to normal again, but still nothing is showing up on hardwere drivers.

---

### Post by okplayer02 on 2010-06-30
See you have an ATI graphic card not nvidia.

I would suggest you uninstall those nvidia packages that you were instructed to install:
```
sudo apt-get remove nvidia-current nvidia-current-modaliases nvidia-common nvidia-settings
```

then to make sure the correct driver is installed for your Ati card:
```
sudo apt-get install xserver-xorg-video-ati
```

after that

then logout and login.

run the command:
```
glxinfo
```

this will show whether the 3d graphics are enabled on your machine meaning you did install the correct drivers. You should see one line that says 

Direct Rendering: Yes

then finally try to enable the special effects

---

### Post by DutchLoki on 2010-07-03
> **dino99 said:**
> into a console, run:

sudo rm -f /etc/X11/xorg.conf

goto synaptic and check that: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings are installed

then reboot and check again that nvidia-current is activated (system admin hardware driver)

Did the same, works here to. I did however remove any existing nvidia driver before installing from synaptic.

---

