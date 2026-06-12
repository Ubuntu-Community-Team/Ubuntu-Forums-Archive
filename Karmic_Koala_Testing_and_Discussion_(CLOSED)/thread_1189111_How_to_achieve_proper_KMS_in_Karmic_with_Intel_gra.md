---
title: "How to achieve proper KMS in Karmic with Intel graphics"
date: 2009-06-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-06-16
First of all, the modprobe method (i915.modeset=1) doesn't allow for early KMS initialization nor proper Plymouth.

If you want non-text Plymouth and earlier KMS, this is the guide for you.

**Configuring KMS on  Karmic the Debian way**

* Make sure you are booting the  2.6.30-2 kernel (or newer) and are using the -intel driver 2.7.99.1 or  later (note that UXA is enabled by default) or a newer -intel from the  xorg-edgers PPA.

* To enable KMS  on i915 hardware, just add the following lines to /etc/initramfs-tools/modules  : 
# Enable Kernel Modesetting
intel_agp
drm
i915 modeset=1

* And regenerate  your initramfs: 
# update-initramfs -k `uname -r` -u

At the next boot, the kernel should be handling  modesetting.

---

### Post by ghindo on 2009-06-16
How stable has KMS been on Intel hardware?

---

### Post by handaxe on 2009-06-16
> **ghindo said:**
> How stable has KMS been on Intel hardware?

see [http://ubuntuforums.org/showthread.php?t=1189068](http://ubuntuforums.org/showthread.php?t=1189068)

The table in this link  [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)   seems to show that most others are OK, but it varies. I suspect most of that testing was with the earlier 30-8 kernel.

HA

---

### Post by Starks on 2009-06-16
> **ghindo said:**
> How stable has KMS been on Intel hardware?
Pretty good aside from a few documented issues.


[LIST]
[*]RandR is broken for fullscreen games
[*]xv Overlay missing
[*]Lack of xv vsync
[*]Pageflipping absent (fix due for 2.6.31)
[*]Plymouth doesn't want to cooperate all the time (Plymouth's fault mostly)
[/LIST]

---

### Post by ghindo on 2009-06-17
Gave it a shot, it borked my system.  After GRUB, my display just turns off entirely.  I'm not sure, but it looks like it might be this bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/388032](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/388032)

I'll meddle more when I get off from work :)

---

### Post by karlrt on 2009-06-17
stupid question perhaps, but i never tried to enable KMS on karmic because i have a i965 grafics controller, not the i915 allways mentioned in ubuntu howtos.

however i use kms fith the new fedora and it works (until now) quite good, so, my question is, can i just change the 1 to the 6 in your tutorial and this will enable kms for me? im more and more unshure about it :)

---

### Post by DBO on 2009-06-17
i915 is the name of the kernel module, not your video card. Just leave the tutorial as is.

---

### Post by Zorael on 2009-06-18
I've been running with kms for a good while now, and it's working better for me than userspace mode-setting does. With ums, X fails to redraw after a vtswitch (bug#[21647](https://bugs.freedesktop.org/show_bug.cgi?id=21647)), whereas with kms vtswitching is safe and snappy. I don't run Plymouth, so can't comment on that.

I do get bug#[20867](https://bugs.freedesktop.org/show_bug.cgi?id=20867) though, but I get that with ums as well so doesn't seem to be kms-related.

> **Starks said:**
> [LIST]
[*]RandR is broken for fullscreen games
[*]xv Overlay missing
[*]Lack of xv vsync
[*]Pageflipping absent (fix due for 2.6.31)
[*]Plymouth doesn't want to cooperate all the time (Plymouth's fault mostly)[/LIST]
How can I test whether xv vsync and pageflipping works? (So I can check after compiling new kernels and updating drivers.)


I guess Overlay not showing up in the output of xvinfo shows that it isn't in yet.
```
$ xvinfo                                                        
X-Video Extension version 2.2                                                        
screen #0                                                                            
  [B]Adaptor #0: "Intel(R) Textured Video"                                              
[/B]    number of ports: 16                                                              
    port base: 63                                                                    
    operations supported: PutImage                                                   
    supported visuals:                                                               
      depth 24, visualID 0x21                                                        
    number of attributes: 3                                                          
      "XV_BRIGHTNESS" (range -128 to 127)                                            
              client settable attribute                                              
              client gettable attribute (current value is 0)                         
      "XV_CONTRAST" (range 0 to 255)                                                 
              client settable attribute                                              
              client gettable attribute (current value is 0)                         
      "XV_SYNC_TO_VBLANK" (range -1 to 1)                                            
              client settable attribute                                              
              client gettable attribute (current value is 1)                         
    maximum XvImage size: 1920 x 1088                                                
    Number of image formats: 5                                                       
      id: 0x32595559 (YUY2)                                                          
        guid: 59555932-0000-0010-8000-00aa00389b71                                   
        bits per pixel: 16                                                           
        number of planes: 1                                                          
        type: YUV (packed)                                                           
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x434d5658 (XVMC)
        guid: 58564d43-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```

---

### Post by Amaranth on 2009-06-18
Xv Overlay is incompatible with compositing and this cannot be fixed. You really don't want Overlay if you use compiz.

---

### Post by Zorael on 2009-06-18
> **Amaranth said:**
> Xv Overlay is incompatible with compositing and this cannot be fixed. You really don't want Overlay if you use compiz.
I run KDE so I wouldn't use compiz anyway.

Nitpicking aside, I usually don't run with compositioning at all; effects bog down my somewhat underpowered netbook.

---

### Post by jerrylamos on 2009-06-18
Whoopee.  With KMS modeset=1 as in the top of the thread, this intel i845g 2 gHz Celeron takes 47 seconds to do GtkPerf (downloaded from Synaptic).  With driver "vesa" it takes 29 seconds.  Vesa is fully 18 seconds faster than KMS.

KMS
GtkPerf 0.40 - Starting testing: Thu Jun 18 20:35:12 2009
GtkEntry - time:  0.25
GtkComboBox - time:  9.19
GtkComboBoxEntry - time:  5.43
GtkSpinButton - time:  2.49
GtkProgressBar - time:  3.96
GtkToggleButton - time:  2.46
GtkCheckButton - time:  1.09
GtkRadioButton - time:  1.37
GtkTextView - Add text - time:  1.86
GtkTextView - Scroll - time:  1.98
GtkDrawingArea - Lines - time:  1.79
GtkDrawingArea - Circles - time:  9.44
GtkDrawingArea - Text - time:  5.42
GtkDrawingArea - Pixbufs - time:  0.52
 --- 
Total time: 47.27

"vesa"
GtkPerf 0.40 - Starting testing: Thu Jun 18 20:42:01 2009
GtkEntry - time:  0.23
GtkComboBox - time:  5.65
GtkComboBoxEntry - time:  3.79
GtkSpinButton - time:  1.14
GtkProgressBar - time:  0.84
GtkToggleButton - time:  0.99
GtkCheckButton - time:  0.62
GtkRadioButton - time:  0.91
GtkTextView - Add text - time:  1.96
GtkTextView - Scroll - time:  1.36
GtkDrawingArea - Lines - time:  2.01
GtkDrawingArea - Circles - time:  3.94
GtkDrawingArea - Text - time:  4.81
GtkDrawingArea - Pixbufs - time:  0.26
 --- 
Total time: 28.54

What is KMS supposed to do for me besides slow down GtkPerf?

Thanks, Jerry

p.s. That much performance difference is fully felt on the desktop however I don't have a stopwatch on my fingers.

---

### Post by psyke83 on 2009-06-18
> **jerrylamos said:**
> Whoopee.  With KMS modeset=1 as in the top of the thread, this intel i845g 2 gHz Celeron takes 47 seconds to do GtkPerf (downloaded from Synaptic).  With driver "vesa" it takes 29 seconds.  Vesa is fully 18 seconds faster than KMS.


Can you disable KMS and test the intel driver performance again? That will isolate the performance hit (or lack thereof) from KMS.

Also note that Karmic doesn't really have the latest components that may affect KMS performance (Mesa and libdrm2). The xorg-edgers packages may yield better results.

---

### Post by SKLP on 2009-06-19
Interesting. Too bad my intel laptop just stopped working...

---

### Post by psyke83 on 2009-06-19
Jerry,

I forgot to mention - your benchmark is worthless if you left compiz enabled for the KMS/intel case, as it becomes more a benchmark of opengl than anything else.

My system yields these results (a rough outline from memory, as I don't have the logs to hand): 
[LIST]
[*]unmaximized: 16 seconds
[*]unmaximized with xcompmgr: 15 seconds
[*]unmaximized with compiz: 20 seconds
[*]maximized window: 17 seconds
[*]maximized with xcompmgr: 26 seconds
[*]maximized with compiz: 35 seconds
[/LIST]

Tested without KMS, as it causes a system freeze upon boot.

---

### Post by jerrylamos on 2009-06-19
> **psyke83 said:**
> Jerry,

I forgot to mention - your benchmark is worthless if you left compiz enabled for the KMS/intel case, as it becomes more a benchmark of opengl than anything else.


ubuntu blacklists compiz for my i845 and i830 pc's.  Compiz hangs these pc's since early Intrepid and still doesn't work so ubuntu intrepid, jaunty, and karmic blacklist compiz for them.

There's some explanation of GtkPerf in Synaptic.  I just used it because it is downloadable by everybody directly from Synaptic and easy to run.  The Phronix site has a pile of video performance programs however I haven't seen a common selection of which to run.  Glxgears is flakey I only use it to test function.

I've been trying KMS for a while with Intel graphics turning it on and off etc.  I can tell when it is on because when I do Ctrl-Alt-F1 the kernel screen has a smaller graphics font.  With KMS off it's the old tty dot printer type font.  KMS performance is about the same modeset = 1 or modeset = 0 on the IBM ThinkCentre i845g and IBM Thinkpad R31 i830.

Jerry

---

### Post by Sarvatt on 2009-06-22
You might as well be comparing performance with glxgears using gtkperf as your benchmark jerrylamos :P in no way do x11perf or gtkperf demonstrate any kind of real world performance differences as you can see by your comparison with vesa.

---

### Post by jerrylamos on 2009-06-22
> **Sarvatt said:**
> You might as well be comparing performance with glxgears using gtkperf as your benchmark jerrylamos :P in no way do x11perf or gtkperf demonstrate any kind of real world performance differences as you can see by your comparison with vesa.

When GtkPerf shows slower performance so does everything I do on the desktop.  This shows up on my 1.0 gHz Celeron Thinkpad R31 laptop and on my 2.0 gHz Celeron ThinkCentre tower.  My faster Thinkpad T40 ATI Radeon laptop and 3.3 gHz Celeron Compaq ATI Radeon tower tend to mask the differences because fast vs. faster is not as noticeable as slow vs. slower.

When linux is running reasonably, like on the Thinkpad R31 with Jaunty or Karmic with Option Tiling "false", it is comfortably usable for internet, Office, mail, etc. even small window video.  The ThinkCentre is annoyingly slow with default Karmic intel driver; with jaunty it was just fine.  Now with Karmic "vesa" it does "ordinary desktop usage" just fine.  With the intel driver default I get way ahead on the keyboard and I'm not that fast a typer.

The Since I don't have a stopwatch on my fingers I use GtkPerf because it puts a number on what I detect using the pc.

If there are some better benchmarks, let me know.

I assume most developers have high end pc's so they wouldn't notice much of a change; judging from entries in Launchpad, Bugzilla, and Ubuntu Forums there's lots of us ordinary users out there that do notice a difference.

Jerry

---

### Post by psyke83 on 2009-06-22
> **jerrylamos said:**
> When GtkPerf shows slower performance so does everything I do on the desktop.  This shows up on my 1.0 gHz Celeron Thinkpad R31 laptop and on my 2.0 gHz Celeron ThinkCentre tower.  My faster Thinkpad T40 ATI Radeon laptop and 3.3 gHz Celeron Compaq ATI Radeon tower tend to mask the differences because fast vs. faster is not as noticeable as slow vs. slower.

When linux is running reasonably, like on the Thinkpad R31 with Jaunty or Karmic with Option Tiling "false", it is comfortably usable for internet, Office, mail, etc. even small window video.  The ThinkCentre is annoyingly slow with default Karmic intel driver; with jaunty it was just fine.  Now with Karmic "vesa" it does "ordinary desktop usage" just fine.  With the intel driver default I get way ahead on the keyboard and I'm not that fast a typer.

The Since I don't have a stopwatch on my fingers I use GtkPerf because it puts a number on what I detect using the pc.

If there are some better benchmarks, let me know.

I assume most developers have high end pc's so they wouldn't notice much of a change; judging from entries in Launchpad, Bugzilla, and Ubuntu Forums there's lots of us ordinary users out there that do notice a difference.

Jerry

Tiling now works correctly on 855GM chipsets (at least without KMS), so you no longer need to disable it.

See: [http://anholt.livejournal.com/41132.html](http://anholt.livejournal.com/41132.html)

I'm not certain, but you may need to use the xorg-edgers drivers in Karmic until mesa/libdrm etc. in our repository catch up.

---

### Post by jerrylamos on 2009-06-23
> **psyke83 said:**
> Tiling now works correctly on 855GM chipsets (at least without KMS), so you no longer need to disable it.


Tiling works O.K., just with tiling GtkPerf runs 64 seconds on this IBM Thinkpad R31 i830 1gHz Celeron, while "Tiling" "false" runs in 50 seconds.  The tiling code slows this pc down for this type of function.

I say Tiling works because when it was broken glxgears display was screwed up on this Thinkpad.  Now glxgears displays properly, true or false.

Jerry

---

### Post by psyke83 on 2009-06-23
> **jerrylamos said:**
> Tiling works O.K., just with tiling GtkPerf runs 64 seconds on this IBM Thinkpad R31 i830 1gHz Celeron, while "Tiling" "false" runs in 50 seconds.  The tiling code slows this pc down for this type of function.

I say Tiling works because when it was broken glxgears display was screwed up on this Thinkpad.  Now glxgears displays properly, true or false.

Jerry

Does tiling show this performance regression when KMS is disabled? I can't test it myself as KMS refuses to work on my laptop (855GM chipset as well).

---

### Post by Ani on 2009-06-23
2.6.30-10-generic kernel has KMS enabled by default.

---

### Post by eTM_ on 2009-06-23
... yes in -10, and it does not work at all for me.

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	Identifier "DELL 2405FPW"
	VendorName "DEL"
	ModelName "DELL 2405FPW"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 30-81
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 170 MHz
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1920x1200"	# vfreq 59.950Hz, hfreq 74.038kHz
		DotClock	154.000000
		HTimings	1920 1968 2000 2080
		VTimings	1200 1203 1209 1235
		Flags	"-HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection

---

### Post by eTM_ on 2009-06-23
I appended "nomodeset" in grub.conf.

Looks like this now:

linux /boot/vmlinuz-2.6.30-10-generic root=UUID=xxxxxx-xxx-xxx-yours-xxx ro quiet splash nomodeset

Switches it off when it is not working for you.

---

### Post by Sarvatt on 2009-06-23
If you dont have an /etc/X11/xorg.conf you will need to add this to it to use KMS until the fbdev fix gets added to xserver.

Section "Device"
        Identifier "intel"
        Driver "intel"
EndSection

This doesn't apply if you are using xorg-edgers though, I've already added the fix needed in there and things should work fine.

---

### Post by jerrylamos on 2009-06-25
I'm not sure what KMS is for on intel video graphics?
i830 Thinkpad R31 boots to blackscreen. nomodeset in kernel line turns off KMS boots O.K.
i845 ThinkCentre 2.0 gHz Celeron works O.K. but Noticeably slower than generic video driver vesa, for example GtkPerf from Synaptic:
```

06/24/09 karmic 2.6.30.10.10				
karmic.i845_________	 vesa	 KMS=1	   KMS_slower
Entry_______________		0.22	0.26	18%
ComboBox____________		5.55	9.25	67%
ComboBoxEntry_______		3.84	5.52	44%
SpinButton__________		0.85	2.5	194%
ProgressBar_________		0.82	3.97	384%
ToggleButton________		0.95	2.47	160%
CheckButton_________		0.60	1.10	83%
RadioButton_________		0.87	1.35	55%
TextView-Add-text___		1.93	1.83	-5%
TextView-Scroll_____		1.29	1.97	53%
DrawingArea-Lines___		2.11	1.83	-13%
DrawingArea-Circles_		4.15	9.81	136%
DrawingArea-Text____		4.77	5.53	16%
DrawingArea-Pixbufs_		0.26	0.51	96%
				
Total_time__________		28.24	47.92	70%

```
Progress bar in particular visibly drags across the screen....

?  Launchpad bug # 382017

Jerry

---

### Post by Zorael on 2009-06-25
Put it in code tags to get a monospaced font.
```
abc       def        ghi
---       ---        ---
jkl       mno        pqr
stu       vwx        yz!
```

---

