---
title: "Which kernel to use in lucid?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by panache on 2010-03-30
Hi all,

In order to enable compositing in 9.10 (I have a Mobility Radeon HD2600 card), I had to use a newer kernel than the default kernel, and enable the xorg-edgers PPA. This worked fine and enabled me to get my wobbly windows on =) (see this thread: [http://ubuntuforums.org/showthread.php?t=1313828&page=5](http://ubuntuforums.org/showthread.php?t=1313828&page=5))

Then after an update (haven't been able to work out what) 3D just broke. Apparently other users experienced this also. So I tried a few other kernels to see if it would help. No joy. I then tried upgrading to the 10.04 beta 1, after hearing that the default ATI drivers in lucid enable 3D. No joy. More playing with kernel versions to see if it have an effect.

Here is an extract from my Grub menu, to show what kernels are installed ('howmany' is set to all):

```
title		Ubuntu lucid (development branch), kernel 2.6.33-020633-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.33-020633-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.33-020633-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.33-020633-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.33-020633-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.33-020633-generic

title		Ubuntu lucid (development branch), kernel 2.6.32-020632rc8-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-020632rc8-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-020632rc8-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-020632rc8-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-020632rc8-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-020632rc8-generic

title		Ubuntu lucid (development branch), kernel 2.6.32-020632rc6-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-020632rc6-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-020632rc6-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-020632rc6-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-020632rc6-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-020632rc6-generic

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-18-generic-pae root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-18-generic-pae
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic-pae (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-18-generic-pae root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-18-generic-pae

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-18-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-18-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-18-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-18-generic

title		Ubuntu lucid (development branch), kernel 2.6.32-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-17-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-17-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-17-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-17-generic

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-16-generic-pae
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic-pae (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-16-generic-pae root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-16-generic-pae

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-16-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.32-16-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.32-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.32-16-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.32-16-generic

title		Ubuntu lucid (development branch), kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu lucid (development branch), kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu lucid (development branch), kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro quiet splash vga=normal 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu lucid (development branch), kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=cc901491-9329-457a-baa5-5391c23047cf ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu lucid (development branch), memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

Booting into some of these gives me errors in the start up process - I assume because they are not optimized for lucid.

Now, I've been booting into 2.6.32-16-generic, because the LTS Tech Overview here ([http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)) suggests that the kernel to use in lucid is 2.6.32-16.25.

**Q1: Am I booting into the correct kernel?**
If it is true that the default open source drivers in lucid should allow for 3D, I want to make sure I am using the correct kernel before complaining that they don't work / investigating why they don't work...
If this isn't the correct kernel, what is? Will upgrades not function correctly because I have all these different kernels installed?

**Q2: If I am booting into the correct lucid kernel, can anyone point me to something about getting the default drivers to work?**

Sorry for long post! Let me know if anything is not clear. xorg.conf is attached in case it helps in resolving the drivers issue...

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card0"
	Driver      "fbdev"
	VendorName  "ATI Technologies Inc"
	BoardName   "M76 [Radeon Mobility HD 2600 Series]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Slim Odds on 2010-03-30
They update the kernel almost daily at this point.

---

### Post by panache on 2010-03-30
> **Slim Odds said:**
> They update the kernel almost daily at this point.

Sure - how do I stay up to date with these kernel releases? My understanding is that cos I've fiddled with which kernel I boot in to, I don't receive the update alerts for these kernels...

---

### Post by Slim Odds on 2010-03-30
> **panache said:**
> Sure - how do I stay up to date with these kernel releases? My understanding is that cos I've fiddled with which kernel I boot in to, I don't receive the update alerts for these kernels...

The update manager will recommend updates when they become available, which, during "*beta time*", is just about all the time.

There are ways to disable receiving updates about selected packages, but you would **not** want to do that during the beta **TEST** cycle.

This is a time when all kinds of things are being **fixed**. Therefore, if you want to use the beta, you should be ready to accept nearly constant disruption from updates of all kinds.

This is what goes on during a **huge** test phase where **millions of people** all other the world are finding and reporting issues which the Ubuntu developer attempt to address as best they can.

Ubuntu uses a time base release schedule, so there are many things to get fixed and cleaned up before the release date near the and of April.

If this type of thing is not for you, use should stick to the official releases. They are much quieter.

---

### Post by panache on 2010-03-31
Thanks for the response slim odds - I appreciate it.

I don't feel like I've uncovered what I'm wanting to know though - no doubt I haven't expressed myself clearly.

What I am wanting to do is ensure that I am booting into the current 10.04 beta 1 kernel, so that I can ensure that my experience of the beta is as it should be, and that any bugs I encounter can be accurately reported (that is, I don't want to be reporting bugs that occur solely because I'm booting into the wrong kernel).

I've installed so many different kernel versions trying to find a solution to my ATI drivers issue that I'm not sure anymore which kernel in my grub menu is the default 10.04 beta kernel.

I have the following kernels installed:
[LIST]
[*]2.6.33-020633-generic
[*]2.6.32-020632rc8-generic
[*]2.6.32-020632rc6-generic
[*]2.6.32-18-generic-pae
[*]2.6.32-18-generic
[*]2.6.32-17-generic
[*]2.6.32-16-generic-pae
[*]2.6.32-16-generic
[*]2.6.27-11-generic
[*]2.6.27-9-generic
[*]2.6.24-22-generic
[/LIST]

Are you able to tell me which is the current lucid kernel / which I should be booting into? Or, if the current lucid kernel isn't listed - what version should I download and install?

(If my above comments suggest that I'm labouring under some false understanding of the nature kernels / lucid let me know!)

---

### Post by Slim Odds on 2010-03-31
Whenever Ubuntu updates the kernel, it always makes that new kernel the default.

So if you don't manually change it during the boot process, you will always get the latest one.

---

### Post by andrewthomas on 2010-03-31
> **panache said:**
> 
I've installed so many different kernel versions trying to find a solution to my ATI drivers issue that I'm not sure anymore which kernel in my grub menu is the default 10.04 beta kernel.

Are you able to tell me which is the current lucid kernel / which I should be booting into? )

2.6.32-18-generic

---

### Post by Rob2687 on 2010-03-31
Why are you using the fbdev driver?

---

### Post by darco on 2010-03-31
I want to uninstall 32.14 but its also wants to uninstall the nouveua backport modules. I am using Nouveau so will this cause a problem? I just updated to the 32.18 kernel and its boots up fine.

thxs

---

### Post by zika on 2010-03-31
> **darco said:**
> I want to uninstall 32.14 but its also wants to uninstall the nouveua backport modules. I am using Nouveau so will this cause a problem? I just updated to the 32.18 kernel and its boots up fine.

thxsYou should have, for example, linux-backports-modules-nouveau-2.6.32-18-generic installed, and, then, You should be safe in removing linux-backports-modules-nouveau-2.6.32-14-generic (that is what is going on in Your case, I think, -14 kernel wants to drag down -14 backports with it), but, as I'm not Nvidia user myself take my word with caution... I do install kernels before they came complete with backports so, I do have to wait until new version of backports emerge to be able to remove previous version of kernel...

---

### Post by panache on 2010-03-31
> **Rob2687 said:**
> Why are you using the fbdev driver?

Indeed. Apparently this driver was selected when I upgraded to the beta. In 9.10 I had the "ati" driver selected. After reconfiguring xorg.conf with Xorg -configure, I'm using the "radeon" driver. 3D + compositing has been restored! (see [http://ubuntuforums.org/showthread.php?t=1313828&page=5](http://ubuntuforums.org/showthread.php?t=1313828&page=5))

**@ andrewthomas**
Thanks. I'll start booting into that and uninstall the other kernels (maybe leaving the 32-16 one just in case)

**@ slim odds**
thanks for your help!

---

