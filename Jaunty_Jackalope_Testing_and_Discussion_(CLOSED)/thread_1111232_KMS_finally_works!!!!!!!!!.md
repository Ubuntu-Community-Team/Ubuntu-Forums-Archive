---
title: "KMS finally works!!!!!!!!!"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xtoudi on 2009-03-30
**Info:**
Jaunty 9.04 amd64 - up2date (30 march 2009).
my gfx: 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

So ... today I read on 
[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=8dabcc40747bfd478f296728741240241698f165](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=8dabcc40747bfd478f296728741240241698f165)

[I]..."Tiling fixes, third setmaster
Hopefully this concludes the fixes necessary to deal with the various combinations of kernel and user level tiling. We have several cases to handle: 
1) KMS (kernel handles all tiling) 
2) UMS w/memory management + kexec fencing (kernel handles all tiling) 
3) UMS w/memory mangement but no kexec fencing (userland handles tiling) 
4) UMS w/o memory management (userland handles tiling) "...[/I]
[B][COLOR="Green"][SIZE="4"]
**Here we go:**[/SIZE][/COLOR][/B]

1. Compiling the new version of kernel 2.6.29 

**Extremly important:** 
 * Don't compile any framebuffer-driver in the kernel, but framebuffer-support itself (section Frame buffer hardware drivers). Everything in this section should looks like this:
```
#
# Frame buffer hardware drivers
#
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
...
...
...
```

 * Turn on (compile into kernel):
```

CONFIG_DRM_I915=y
CONFIG_DRM_I915_KMS=y
```
 * theese should be set too
```
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL=y
```
* and Framebuffer Console support
```
CONFIG_FRAMEBUFFER_CONSOLE=y
```


Obviously don't ask me how to compile kernel - you have to know that or google knows.

3. Take 'git clone' of the latest version of xf86-video-intel driver and compile it:
[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/)

Info:
Latest version of xf86-video-intel required libdrm 2.4.6 which you should compile too.
[http://cgit.freedesktop.org/mesa/drm/](http://cgit.freedesktop.org/mesa/drm/)

4. Like stays in README the only section which should be important in xorg.conf is:
```

Section "Device"
      Identifier "intel"
      Driver     "intel"
EndSection

```
...but without xorg.conf should works too.

That's all!! 

No need any special commands with your kernel/boot like: i915.modeset=1 - NOTHING like that - it works with default settings!

**_What I've got??_**

Boot/UPSLASH with highres - in my case is 1280:800 (16:10).
Extremly fast VT switching - very cool and very nice
... and rest of KMS goods ...

---

### Post by gnomeuser on 2009-03-30
If anyone wants this without the compiling and configuration. Also for Radeon and GeForce 8 series cards. On the 31th (tomorrow as of posting) Fedora 11 Beta will ship with all of this.

To activate on nvidia cards pass nouveau.modeset=1 in grub, for ATI and Intel it should be on by default (except selected Radeon cards for various reasons).

Additional information can be found here:
[https://fedoraproject.org/wiki/Features/IntelKMS](https://fedoraproject.org/wiki/Features/IntelKMS)
[https://fedoraproject.org/wiki/Features/NouveauModesetting](https://fedoraproject.org/wiki/Features/NouveauModesetting)
[https://fedoraproject.org/wiki/Features/NouveauAsDefault](https://fedoraproject.org/wiki/Features/NouveauAsDefault)
[https://fedoraproject.org/wiki/Features/Radeon3DUpdate](https://fedoraproject.org/wiki/Features/Radeon3DUpdate)
[https://fedoraproject.org/wiki/Features/XserverOnePointSix](https://fedoraproject.org/wiki/Features/XserverOnePointSix)
[https://fedoraproject.org/wiki/Features/DRI2](https://fedoraproject.org/wiki/Features/DRI2)

There will be LiveCDs so it is non destructive if you just want to see if it works (if it doesn't please file bugs and the talented developers will fix it right up).

---

### Post by tjeremiah on 2009-03-30
wait, so would this benefit me? (graphic card is in sig)

---

### Post by xens on 2009-03-30
someone know if nvidia planed to support KMS into their binary driver?

---

### Post by amano on 2009-03-30
Why do you need it in the binary driver? Most benefits will be at boot time and at that point the binary blob isn'T loaded.

---

### Post by Therion on 2009-03-30
***OMG!!!! FINALLY!!!***




Uhhh...  What's a KMS?

---

### Post by xtoudi on 2009-03-30
> **amano said:**
> Why do you need it in the binary driver? Most benefits will be at boot time and at that point the binary blob isn'T loaded.

I do not agree!! having the mode-setting done in the kernel allows for a cleaner and richer boot process, improved suspend and resume support, and more reliable VT switching - it's very fast withount any changing resolution! 

And why in the binary driver? Because - maintenence of KMS there is in driver :)

---

### Post by xens on 2009-03-30
> **amano said:**
> Why do you need it in the binary driver? Most benefits will be at boot time and at that point the binary blob isn'T loaded.

So I've missed something... I thought the driver must support KMS to use it

---

### Post by gaspard.leon on 2009-03-30
> **Therion said:**
> ***OMG!!!! FINALLY!!!***




Uhhh...  What's a KMS?


Kernel-based Mode Setting

Basically it means the kernel can set graphics modes instead of only the drivers.
So you can do seamless graphical boot, and quick VT (Virtual Terminal) switching.

Without this kernel change, we would be stuck with the usual flickery graphical boot that flicks back and forth between modes and looks ugly, and VT switches that take a while... However, last I heard KMS is only supported by some intel chipsets in practice...

please correct me if other chipsets can use this.

---

### Post by xtoudi on 2009-03-30
> **gaspard.leon said:**
> Kernel-based Mode Setting

Basically it means the kernel can set graphics modes instead of only the drivers.
So you can do seamless graphical boot, and quick VT (Virtual Terminal) switching.

Without this kernel change, we would be stuck with the usual flickery graphical boot that flicks back and forth between modes and looks ugly, and VT switches that take a while... However, last I heard KMS is only supported by some intel chipsets in practice...

please correct me if other chipsets can use this.

There is a project called Plymouth (FEDORA) - with that you can use any nice boot with animations in high resolution - but no KMS probably, because without any support of NVidia or AMD there is no chance to take a real adventages with that - only nice boot screen like in Plymouth;-)
Another problably is that there will be Plymouth in Karmic Koala.
And full support of KMS finally will exist in Karmic Koala - or if you do this youself with kernel 2.6.29 in JJ:).

If you want to train with this (Plymouth) in JJ you should read this:
[http://ubuntuforums.org/showthread.php?t=1083584&highlight=plymouth](http://ubuntuforums.org/showthread.php?t=1083584&highlight=plymouth)

---

### Post by MacUntu on 2009-03-30
> **gaspard.leon said:**
> please correct me if other chipsets can use this.

Have you read gnomeuser's posting? #-o

Latest official "something" (wouldn't call it news) from Nvidia that I know about (11.11.2008):

[QUOTE=AaronP]
The last time I talked to the developers working on it, they told me that the hooks necessary to implement kernel modesetting were exported to GPL modules only, and therefore are not usable by the NVIDIA driver. On the other hand, that was a while ago and I haven't looked at it since. If the kernel developers are willing to work with us to make kernel modesetting possible for NVIDIA GPUs, then we'll look into it.[/QUOTE]

---

### Post by Starks on 2009-03-30
I'm gonna see if I can trick kernelcheck into compiling a kernel with non-broken KMS support.

Wish me luck!

---

### Post by MacUntu on 2009-03-31
> **gnomeuser said:**
> To activate on nvidia cards pass nouveau.modeset=1 in grub

That's an unknown boot parameter. Coaster disc. :-(

---

### Post by xtoudi on 2009-03-31
> **MacUntu said:**
> That's an unknown boot parameter. Coaster disc. :-(

It's because you kernel doesn't support KMS. And I don't know if Fedoras kernel support this - and NVidia cards.

---

### Post by zekopeko on 2009-03-31
> **gnomeuser said:**
> If anyone wants this without the compiling and configuration. Also for Radeon and GeForce 8 series cards. On the 31th (tomorrow as of posting) Fedora 11 Beta will ship with all of this.

To activate on nvidia cards pass nouveau.modeset=1 in grub, for ATI and Intel it should be on by default (except selected Radeon cards for various reasons).

Additional information can be found here:
[https://fedoraproject.org/wiki/Features/IntelKMS](https://fedoraproject.org/wiki/Features/IntelKMS)
[https://fedoraproject.org/wiki/Features/NouveauModesetting](https://fedoraproject.org/wiki/Features/NouveauModesetting)
[https://fedoraproject.org/wiki/Features/NouveauAsDefault](https://fedoraproject.org/wiki/Features/NouveauAsDefault)
[https://fedoraproject.org/wiki/Features/Radeon3DUpdate](https://fedoraproject.org/wiki/Features/Radeon3DUpdate)
[https://fedoraproject.org/wiki/Features/XserverOnePointSix](https://fedoraproject.org/wiki/Features/XserverOnePointSix)
[https://fedoraproject.org/wiki/Features/DRI2](https://fedoraproject.org/wiki/Features/DRI2)

There will be LiveCDs so it is non destructive if you just want to see if it works (if it doesn't please file bugs and the talented developers will fix it right up).

so when Fedora releases its beta my 8600GTS should work if i add the relevant boot parameter? and i should get the plymouth experience with the livecd?

---

### Post by MacUntu on 2009-03-31
> **xtoudi said:**
> It's because you kernel doesn't support KMS. And I don't know if Fedoras kernel support this - and NVidia cards.

That's from the Fedora Beta gnomeuser was referring to.

---

### Post by xtoudi on 2009-03-31
> **MacUntu said:**
> That's from the Fedora Beta gnomeuser was referring to.

Summary - I don't know ... this is JJ thread and I wrote howto do this with JJ :). But ofcourse you can try play with Fedora.

---

### Post by gnomeuser on 2009-03-31
> **MacUntu said:**
> That's an unknown boot parameter. Coaster disc. :-(

I should have explained further, grub does not understand it but when time comes to load the nouveau module it will. The error is harmless and your cd is likely fine.

---

### Post by gnomeuser on 2009-03-31
> **zekopeko said:**
> so when Fedora releases its beta my 8600GTS should work if i add the relevant boot parameter? and i should get the plymouth experience with the livecd?

Yes, it should work.

At the test day, at least one person tested with a similar card and everything worked (note the test day livecd is not the exact same as the beta one - there are a few newer packages on there for the purposes of testing)

[https://fedoraproject.org/wiki/QA/Test_Days/2009-03-26](https://fedoraproject.org/wiki/QA/Test_Days/2009-03-26)

*edit*

This goes for everyone with an nvidia card, go to the page above and see if someone tested with a card of your model. If there are bugs check if they were closed after the bug day in which case a Fedora 11 Beta install plus updates should work. KMS currently only works for GeForce 8 series cards but support will be expanded.

---

### Post by gnomeuser on 2009-03-31
> **xens said:**
> someone know if nvidia planed to support KMS into their binary driver?

No, if they did that the driver would become derived work from the kernel and thus definitely subject to licensing under GPLv2. This is something nvidia does not want to do so you will not get KMS on their driver, look to nouveau for these features. It will not do 3D yet but Red Hat has a guy working full time on this driver as well as many others on the related X stack. I would wager a year or so from now we will have decent 3D on nvidia using Free Software thanks to these investments.

---

### Post by MacUntu on 2009-03-31
Seems I misinterpreted your GeForce 8 hint.

> Unfortunately, the kms support for nouveau that'll be in F11 only covers GeForce 8 and higher chipsets.

But I agree, this thread is about Jaunty, let's stop hijacking it.

---

### Post by xtoudi on 2009-03-31
> **MacUntu said:**
> Seems I misinterpreted your GeForce 8 hint.


That's not my hint. So far kernel 2.6.29 KMS supports only Intel chipsets.

---

### Post by Zorael on 2009-04-01
Managed to get it running on my netbook with intel graphics. Switching to VTs is fast and they show up in native resolution, but glxgears' fps is roughly cut in half with UXA and KMS compared to non-KMS EXA.

Important note is that you have to add --prefix=/usr to autogen.sh, or it'll install the libraries to /usr/**local**/lib.

edit: And stuff goes bad if I don't explicitly define driver "intel" and option "accelmethod" "uxa" in xorg.conf.

---

### Post by gnomeuser on 2009-04-01
> **MacUntu said:**
> 
But I agree, this thread is about Jaunty, let's stop hijacking it.

I thought the thread was about KMS, I merely provided a non destructive means of trying this out without the compiling that also covered more video cards. I feel that is entirely relevant.

---

### Post by xens on 2009-04-01
> **gnomeuser said:**
> No, if they did that the driver would become derived work from the kernel and thus definitely subject to licensing under GPLv2. This is something nvidia does not want to do so you will not get KMS on their driver, look to nouveau for these features. It will not do 3D yet but Red Hat has a guy working full time on this driver as well as many others on the related X stack. I would wager a year or so from now we will have decent 3D on nvidia using Free Software thanks to these investments.

thank you for the explanation! this license issue really sucks, hope one day nvidia open their driver or help the nouveau developpers...

---

### Post by Starks on 2009-04-01
afaik, you need to modprobe the driver with the modeset options.

example: *modprobe i915 modeset=1*

---

### Post by xtoudi on 2009-04-01
> **Starks said:**
> afaik, you need to modprobe the driver with the modeset options.

example: *modprobe i915 modeset=1*

If the kernel is build with KMS compiled in (CONFIG_DRM_I915=y and CONFIG_DRM_I915_KMS=y) than there is no need to add any additional options.

and wrong example, should be:

i915.modeset=1 at kernel line (menu.lst)

but like I said it's not needed, kernel default in that case is KMS. The rest is on the xf86-video-intel side (with KMS support too).

---

### Post by zika on 2009-04-01
> **gnomeuser said:**
> If anyone wants this without the compiling and configuration. Also for Radeon and GeForce 8 series cards. On the 31th (tomorrow as of posting) Fedora 11 Beta will ship with all of this.

To activate on nvidia cards pass nouveau.modeset=1 in grub, for ATI and Intel it should be on by default (except selected Radeon cards for various reasons).

Additional information can be found here:
[https://fedoraproject.org/wiki/Features/IntelKMS](https://fedoraproject.org/wiki/Features/IntelKMS)
[https://fedoraproject.org/wiki/Features/NouveauModesetting](https://fedoraproject.org/wiki/Features/NouveauModesetting)
[https://fedoraproject.org/wiki/Features/NouveauAsDefault](https://fedoraproject.org/wiki/Features/NouveauAsDefault)
[https://fedoraproject.org/wiki/Features/Radeon3DUpdate](https://fedoraproject.org/wiki/Features/Radeon3DUpdate)
[https://fedoraproject.org/wiki/Features/XserverOnePointSix](https://fedoraproject.org/wiki/Features/XserverOnePointSix)
[https://fedoraproject.org/wiki/Features/DRI2](https://fedoraproject.org/wiki/Features/DRI2)

There will be LiveCDs so it is non destructive if you just want to see if it works (if it doesn't please file bugs and the talented developers will fix it right up).
do You have any knowledge or whatever when Ubuntu will get a descent radeon driver for rv635(ATI) (HD3650) ...?

---

### Post by gnomeuser on 2009-04-01
> **zika said:**
> do You have any knowledge or whatever when Ubuntu will get a descent radeon driver for rv635(ATI) (HD3650) ...?

Since Ubuntu unlike Fedora doesn't upgrade drivers and software very aggressively post release I suspect you will have to wait for 9.10. Alternatively, you might be able to find a PPA that will supply an unsupported driver upgrade. 

That being said, today is the test day for Radeon 3D in Fedora. If you want to help out and see if your own card is well supported then:

[http://fedoraproject.org/wiki/Test_Day:Radeon_2009-04-01](http://fedoraproject.org/wiki/Test_Day:Radeon_2009-04-01)

There is a downloadable liveCD with all the things you need, plus a set of test cases. If you run into problems please file bugs, the relevant developers are available all day for nothing but this. Alternatively look down the list and see if anyone has tested a card like yours to see the current status.

I should note that doing this, regardless of your feelings about Fedora will help get a driver into Ubuntu quickly. The better shape it is in today, the better it will be when it comes time to merge or request an update.

---

### Post by zika on 2009-04-02
> **gnomeuser said:**
> Since Ubuntu unlike Fedora doesn't upgrade drivers and software very aggressively post release I suspect you will have to wait for 9.10. Alternatively, you might be able to find a PPA that will supply an unsupported driver upgrade. 

That being said, today is the test day for Radeon 3D in Fedora. If you want to help out and see if your own card is well supported then:

[http://fedoraproject.org/wiki/Test_Day:Radeon_2009-04-01](http://fedoraproject.org/wiki/Test_Day:Radeon_2009-04-01)

There is a downloadable liveCD with all the things you need, plus a set of test cases. If you run into problems please file bugs, the relevant developers are available all day for nothing but this. Alternatively look down the list and see if anyone has tested a card like yours to see the current status.

I should note that doing this, regardless of your feelings about Fedora will help get a driver into Ubuntu quickly. The better shape it is in today, the better it will be when it comes time to merge or request an update.

the situation seems to be very similar: (quote) **(3D will not work for Fedora 11 with r600 or r700 cards - anything in the Radeon HD 2xxx, HD 3xxx, or HD 4xxx series: if you have one of these cards, mark this test as N/A in the results table)**...
I have HD 3650 (rv635) ... :)

nevertheless I will try CD today just for fun of it ...

p.s. boy, for user that is the totally the same ... glxgears is ~15% better but that's it. I could not find compiz (is there a compiz in Fedora?) ... I will just investigate if "my" main apps are there ... Kile, Tex, R, etc. ...

what is the **real** difference ... ?

p.p.s. I've spent an hour playing with Fedora. the only thing I wish I have brought with me to Ubuntu after reboot were wallpapers. **(is that possible and how)** not enough for me to convert ... :) I know, liveCD experience is not worth of judgment but I do not have time to install it as a third OS. or, ... :) 
____________________________________________________________________
he who has two ladies looses his soul but he who has two homes looses his head ...

---

### Post by PatrickVogeli on 2009-04-02
kms definitely sound nice, but the setup didn't work too well here. I installed the intel git driver and git libdrm, but after that, trying to view a fullscreen movie crashed the laptop. I suppose unstable drivers and such stuff have those things... no big problem though, reverting was easy.

Once that's finished, boot up will look a lot better: the streched ubuntu logo isn't quite a beatiful thing. Great widebuntu theme exists and, quite of, solves the problem!

---

### Post by antistress on 2009-04-08
du we really need to compile the kernel for that ?
what about [that way to do]("http://tuxce.blogspot.com/2009/03/activer-kms-sur-arch-linux.html") ?

---

### Post by Cybah on 2009-04-11
> **xtoudi said:**
> **_What I've got??_**

Boot/UPSLASH with highres - in my case is 1280:800 (16:10).
Extremly fast VT switching - very cool and very nice
... and rest of KMS goods ...

Great, thanks... I've now got this working, too. One issue is the long period where the screen is blank during boot, which is a bit disconcerting the first time around! I see the Ubuntu splash screen and the progress bar gets to about 25%, screen blanks until the GDM login screen appears. Anyone else experiencing this?

It's also worth double-checking that CONFIG_FRAMEBUFFER_CONSOLE=y in the kernel config. For some reason, mine ended up being changed to =m the first time, so I had to modprobe fbcon or change the mkinitramfs settings... was most likely me messing around in make menuconfig.

Now if only I could get VSync to work properly... but that's another matter.

---

### Post by Cybah on 2009-04-11
Oh yeah, and is it normal for this to happen with KMS?

$ driconf 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen "0" is not direct rendering capable.

---

### Post by xtoudi on 2009-04-13
> **Cybah said:**
> Oh yeah, and is it normal for this to happen with KMS?

$ driconf 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen "0" is not direct rendering capable.

Yes ... I've noticed that too ...

And the previous problem:

> I see the Ubuntu splash screen and the progress bar gets to about 25%, screen blanks until the GDM login screen appears. Anyone else experiencing this?

I don't know if I understood but mine splash is ok, there is no blanks - everything goes fine. And there is a little pause (black screnn) between splash and gdm login.

---

### Post by loomsen on 2009-04-14
Thats actually why KMS exists isnt it ^^

---

### Post by xtoudi on 2009-04-14
I've compiled kernel 2.6.30-rc1 in the same way, DRM 2.4.6 and xf86-video-intel-2.6.99.902 (also 2.6.99.901) and still works :-).
There are problems with latest git clone of xf86 (info: "Turn on front buffer tiling in KMS") ... but most important is that is still progress.

---

### Post by Starks on 2009-04-14
> **antistress said:**
> du we really need to compile the kernel for that ?
what about [that way to do]("http://tuxce.blogspot.com/2009/03/activer-kms-sur-arch-linux.html") ?
Debian and Ubuntu don't use mkinitrd. We use mkinitramfs and thus that procedure doesn't work.

---

### Post by Cybah on 2009-04-14
> **xtoudi said:**
> Yes ... I've noticed that too ...

When I get some time, I'll try to learn a bit more about the relationship between KMS, the intel video driver, DRM and DRI. I've noticed a few utilities which now don't quite work as expected, while trying to track down non-working vertical sync.

I'm also suffering from the performance regression discussed in various places, even after modifying the kernel to disable the GEM functionality.

> **xtoudi said:**
> I don't know if I understood but mine splash is ok, there is no blanks - everything goes fine. And there is a little pause (black screnn) between splash and gdm login.

Hmmm, I wonder why it's different. I'm following the latest Jaunty updates, running on the i945GM chipset. You?

---

### Post by xtoudi on 2009-04-14
> **Cybah said:**
> When I get some time, I'll try to learn a bit more about the relationship between KMS, the intel video driver, DRM and DRI. I've noticed a few utilities which now don't quite work as expected, while trying to track down non-working vertical sync.

I'm also suffering from the performance regression discussed in various places, even after modifying the kernel to disable the GEM functionality.
Hmmm, I wonder why it's different. I'm following the latest Jaunty updates, running on the i945GM chipset. You?

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
And latest JJ updates too.

---

### Post by Sarvatt on 2009-04-14
I have KMS enabled libdrm and xserver-xorg-video-intel drivers up in my PPA incase it's useful to anyone else.

[https://launchpad.net/~sarvatt/+archive/ppa](https://launchpad.net/~sarvatt/+archive/ppa)

You might want to mention that disabling PAT in the kernel config or booting with nopat helps a good deal, right now its really buggy with PAT enabled. 2.6.30-rc2 has some useful drm fixes as well.

---

