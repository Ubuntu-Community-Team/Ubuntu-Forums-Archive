---
title: "nVidia driver problem"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by J86 on 2007-01-08
I'm having trouble getting the drivers for my GeForce TI 4200 working. When I use the "nv" driver I can get into the X windows but openGL isn't working. glxgears gives me this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I can't get into the X windows at all with the nvidia driver. It says something about the "kernel module does not appear to be receiving interrupts". I've been messing with it forever and I can't find any solution on Google. ](*,)   I'm about to give up. Please help, and also, I'm really new to this Linux thing so please bear with me.

---

### Post by tommcd on 2007-01-08
First back up your xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak). Then install nvidia-glx from synaptic. Then run "sudo nvidia-xconfig" in terminal. Restart X (hit CTRL + ALT + backspace). You should get the nvidia splash screen prior to login. Then run glxgears.
EDIT: I'm prety sure your card is supported by the driver in the repos. Can anyone conirm this?

---

### Post by tommcd on 2007-01-08
Yes, your card is supported by nvidia-glx:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28nvidia%29)
Hope this helps.

---

### Post by J86 on 2007-01-08
This is still not working. Now that I installed with the synaptic I'm getting a different error message.

---

### Post by po0f on 2007-01-08
J86,

[quote=J86]... Now that I installed with the synaptic I'm getting a different error message.[/quote]

How did you install it before?  You didn't download the *.bin from the NVIDIA site and install it that way, did you?  If you did, this might require some work to get fixed.

It might help knowing what the error is.  Can you even get X to come up now?

---

### Post by tommcd on 2007-01-08
Did the nvidia-glx successfully install from synaptic?
Did you then run 'sudo nvidia-xconfig?
When you restarted X (or rebooted) did you see the nvidia splash screen? If not, and assuming nvidia-glx successfully installed, type 'gksudo gedit /etc/X11/xorg.conf' in terminal. Scroll down to the "driver" section. Make sure the driver says "nvidia" and not "nv". Also in the device section (I think that is where it's at, I'm at work now so I can't check) if you have 'load dri' or 'load GLcore' in there comment them out (ie, put a # in front of). Then save and exit. Restart X or reboot.  You should get the nvidia splash screen.
EDIT: oh, I hope you did not install the driver from nvidia before doing what I suggested. You did not mention that. Did you, and what error are you getting now?

---

### Post by J86 on 2007-01-08
(see post below)

---

### Post by J86 on 2007-01-08
> **po0f said:**
> J86,
How did you install it before?  You didn't download the *.bin from the NVIDIA site and install it that way, did you?

I downloaded the .run from nVidia's website and installed it that way.

> **po0f said:**
> It might help knowing what the error is.  Can you even get X to come up now?

Yes. Like I said before, it works when I use "nv". Its when I try to use "nvidia" that X doesn't work. Instead of telling me that the "driver is not receiving interrupts" it is now telling me that there was an "error running install command for nvidia"

> Did the nvidia-glx successfully install from synaptic?

I don't know. There were no error messages.

> Did you then run 'sudo nvidia-xconfig?

Yes.

> When you restarted X (or rebooted) did you see the nvidia splash screen?

No

> If not, and assuming nvidia-glx successfully installed, type 'gksudo gedit /etc/X11/xorg.conf' in terminal. Scroll down to the "driver" section. Make sure the driver says "nvidia" and not "nv". Also in the device section (I think that is where it's at, I'm at work now so I can't check) if you have 'load dri' or 'load GLcore' in there comment them out (ie, put a # in front of). Then save and exit. Restart X or reboot. You should get the nvidia splash screen.

I only get an error screen with nvidia. With nv, X starts but there is no openGL.

---

### Post by tommcd on 2007-01-08
You should not have the nvidia-glx from the repos and the driver from nvidia's website installed together. I'm sorry but I did not know you had already installed nvidia's driver. 
Go here:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)
And scroll down to the section "HOW TO UNINSTALL THE DRIVER (FROM METHOD 2)" This will uninstall the driver from nvidia. Then  do "sudo apt-get --purge remove nvidia-glx " This will get rid of the driver from the repos. Then reboot into recovery mode and do "sudo dpkg-reconfigure xserver-xorg" from recovery terminal. Then do "startx" This should get you a clean xorg.conf. The go ahead and follow the directions I gave you in my first post. The driver from the repos should be fine for your card.
Sorry I gave you this trouble. Let me know if this works.

---

### Post by tommcd on 2007-01-08
To uninstall nvidia's driver do this:
sudo sh NVIDIA-Linux-x86-1.0-8776-pkg1.run --uninstall
Edit the command to reflect the name of nvidia's driver you downloaded.

---

### Post by J86 on 2007-01-08
I did all that and it is still telling me there was an "error running install command for nvidia"

---

### Post by tommcd on 2007-01-08
Did you successfully uninstall the nvidia driver from nvidia's web site. Then did you reconfigure X with 'sudo dpkg-reconfigure xserver-xorg'? If so, and assuming you can boot to the GUI ok, then just use the driver from synaptic (nvidia-glx). That driver should work fine. It is all I use on my nvidia 6200 and 6600.
If you really want to use the driver from nvidia's web site then you should follow "method 2" as discussed here:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
A very detailed tutorial for the driver from synaptic is under "section 1".
If you use the driver from nvidia you will have to completely remove the driver from synaptic. You should not have both of them together.
Again, I'm sorry, but I did not know you had already ran the driver from nvidia before I told you to install the driver from synaptic. Please follow the guide I linked to. It is very good.

---

### Post by J86 on 2007-01-09
(see next post)

---

### Post by J86 on 2007-01-09
(next post) (where is the delete post option?)

---

### Post by J86 on 2007-01-09
Method 1 seemed to install fine but now I'm back to the "kernel driver interrupt" problem

---

### Post by J86 on 2007-01-13
Well, I've given up and reinstalled Windows XP. After I installed an ATI card and it wouldn't work either I decided that I'd had enough. The driver for both these cards work with a couple clicks in Windows and besides that, they actually work at all.

---

### Post by moonS on 2007-01-14
With the last update os restricted modules nvidia-glx is broken on my machine.

I own the same card and i fix the problem adding this line to sources.list and upgrading my distro:

deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable-9631


Does anobody know if ubuntu will fix the restricted drivers??

---

### Post by tommcd on 2007-01-15
Well, that is one repository that I have never sen before.
I'm curious, how did you find it? a google search?
I hope the OP is still subscribing to this thread.

---

