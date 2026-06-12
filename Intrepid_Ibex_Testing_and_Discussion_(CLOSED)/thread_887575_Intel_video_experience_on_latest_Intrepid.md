---
title: "Intel video experience on latest Intrepid"
date: 2008-08-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nIRV on 2008-08-12
Running with the latest Intrepid packages, I've noticed the x intel video driver became quite unstable. Since the latest intel driver 2.4.0 update:

- The bottom 1/4 of screen is flashing while logging in gnome and loading applications ([Bug 256142](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/256142))

In particular, it's now very difficult to successfully view video/dvd:
- Viewing videos while compiz is activated always kills video and system
- With compiz deactivated, videos can be played but sometimes screen corruption appears and leads to same video/system freeze. ([Bug 256820](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820))

Lastly, bugs that have been affecting my system since I moved to Intrepid +/- 1 month ago:
- Screen artifacts in usplash while ubuntu loads
- Boot will often result in blank screen after usplash, failing to display GDM
 
Anybody else running on intel video noticed these degradations? Bug numbers?

---

### Post by yelo3 on 2008-08-12
I have the same problems you described. If you find a solution please tell me!
Thanks

---

### Post by TheMono on 2008-08-13
Ditto. Furthermore, xrandr won't allow me to use a second monitor (this is off my eee 901 laptop) at a resolution of more than 1024x1024, when I know under XP that people have much higher resolutions going on the exact same hardware.

---

### Post by SunnyRabbiera on 2008-08-13
Intrepid is still alpha so any issues wont surprise me right now

---

### Post by nIRV on 2008-08-13
> **SunnyRabbiera said:**
> Intrepid is still alpha so any issues wont surprise me right now

Absolutely right; this thread would probably serve developers and intrepid testers if people could link problems to known bugs... Let's start.

Flickering of bottom 1/4 screen using intel drivers
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/256142](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/256142)

---

### Post by napsy on 2008-08-13
Intel video problems:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820)

---

### Post by nIRV on 2008-08-13
> **napsy said:**
> Intel video problems:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820)

thanks napsy, added bug url to list

---

### Post by stef70 on 2008-08-13
This is not specific to ubuntu.

The problem is discussed in the thread "Xf86-video-intel-2.4.0" at

[http://lists.freedesktop.org/archives/xorg/2008-July/thread.html](http://lists.freedesktop.org/archives/xorg/2008-July/thread.html)

and

[http://lists.freedesktop.org/archives/xorg/2008-August/thread.html](http://lists.freedesktop.org/archives/xorg/2008-August/thread.html)

---

### Post by hexion on 2008-08-13
Same problem here.
I couldn't even start gnome (no image) until the last updates on the kernel.

---

### Post by napsy on 2008-08-13
It would be good if someone tries this:
> 


Thank you for the log and configuration. However, more information is needed to deal with your crash:

Is there a file called /etc/X11/core after the crash? If so, please execute the command

sudo gdb /usr/bin/Xorg /etc/X11/core

and attach the backtrace here. If it's not there please try the following steps:

find the process ID (pid) of Xorg:

pgrep Xorg

Then start gdb and attach to that process:

sudo gdb /usr/bin/Xorg

(gdb starts up and gives you its (gdb) prompt)

(gdb) attach <the process ID you found above>
(gdb) cont

Now do what you need to make the X server crash. Or, if the problem is that the X server is locked up and doesn't react, stop it with ctrl-C. Now get a backtrace:

(gdb) backtrace full

Please attach the backtraces here.



And report back to bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256820)

---

### Post by OutOfReach on 2008-08-13
Phew, so I'm not alone!
I also have the bottom 1/4 of the screen flickering when starting applications, and everything else you listed.
Just today actually, the gdm failed to start, luckily the recovery option in GRUB saved me (:)).

---

### Post by mknudsen on 2008-09-01
Same problem here (flickering), had no problems playing stuff in totem though,

---

### Post by damoxc on 2008-09-02
Fix has been released in the latest updates just so people are aware.

---

### Post by mc4100 on 2008-09-02
> **damoxc said:**
> Fix has been released in the latest updates just so people are aware.
Yay, it's fixed! 

... I'm noticing improvements in video playback, too :)

---

### Post by zombiepig on 2008-09-02
With the flickering display problem fixed, intel video is working fantastic on intrepid. Textured video is behaving nicely, even with fullscreen videos, and all the compiz effects that caused problems in hardy (blur, water, etc..) all work perfectly now!

---

### Post by mc4100 on 2008-09-02
> **zombiepig said:**
> With the flickering display problem fixed, intel video is working fantastic on intrepid. Textured video is behaving nicely, even with fullscreen videos, and all the compiz effects that caused problems in hardy (blur, water, etc..) all work perfectly now!
Let's just hope they don't break it, now that it works so well, lol.

---

### Post by damoxc on 2008-09-02
> **zombiepig said:**
> With the flickering display problem fixed, intel video is working fantastic on intrepid. Textured video is behaving nicely, even with fullscreen videos, and all the compiz effects that caused problems in hardy (blur, water, etc..) all work perfectly now!

Blur works for you?

Does that include alpha blur?

---

### Post by zombiepig on 2008-09-03
> **damoxc said:**
> Blur works for you?

Does that include alpha blur?

Focus blur definitely works, I'm not quite sure how to properly use alpha blur. Does I need to be using murrine w/ transparent widgets to utilize it?

---

### Post by plun on 2008-09-03
> **zombiepig said:**
> Does I need to be using murrine w/ transparent widgets to utilize it?

The Dust theme got a manual for latest Murrine svn
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme)

Application list
[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)

"Official" works directly, plugins are really easy to enable.

Brand-new themes using newest engine.
[http://www.cimitan.com/murrine/node/125](http://www.cimitan.com/murrine/node/125)

Carbon is the most amazing theme I have used....:)

---

### Post by damoxc on 2008-09-03
> **zombiepig said:**
> Focus blur definitely works, I'm not quite sure how to properly use alpha blur. Does I need to be using murrine w/ transparent widgets to utilize it?

You just need to check the alpha blur box, and set the window type to the same as focus blur. But I don't recommend doing so, as my screen goes all black and screwed up.

---

### Post by avb on 2008-09-03
im still waiting for a new kernel. Con with 2.6.27-2 i can boot mine lenovo X61 only from second time. First time im getting always corrupted usplash theme and then boot just hangs.

---

### Post by vikrant82 on 2008-09-04
The flickering has improved a bit, but its still there for me on launching some applications. 

Previously a lot of flickering was happening on mouse movement as well which seems to have gone.

---

### Post by andrewabc on 2008-09-04
Is anyone using intel g965?

I'm waiting for the next alpha to be released to test.

I've rarely gotten compiz to work good. Everything works fine, but the CPU usage is around 40% when scrolling a webpage, and very high for other basic stuff. This has been documented since 7.10 release.
I'm hoping Intrepid works better.

---

### Post by ntetreau on 2008-09-04
> **andrewabc said:**
> Is anyone using intel g965?

I'm waiting for the next alpha to be released to test.

I've rarely gotten compiz to work good. Everything works fine, but the CPU usage is around 40% when scrolling a webpage, and very high for other basic stuff. This has been documented since 7.10 release.
I'm hoping Intrepid works better.

I am on intel 965 and compiz works well (i needed to uncheck unredirect fullscreen in the Compiz manager "General" tab for the screensaver to work safely).  With that said, I do get 40% cpu usage when I scroll non-stop, it is unfortunate but not a show stopper for me.

---

### Post by 01ago on 2008-10-10
> **damoxc said:**
> You just need to check the alpha blur box, and set the window type to the same as focus blur. But I don't recommend doing so, as my screen goes all black and screwed up.

How did you recover from that? I cannot do anything after my screen went black:(:(




Add: I solved it myself! Alt+F2, type metacity --replace   :)

---

### Post by muzzamo on 2008-10-14
Well i'm getting very slow/buggy video in totem. Quite often (maybe 70% of the time) the video is simply black, otherwise it is slow.

Switching to vlc or xine fixes the problem, so I wonder if its a totem bug, gstreamer bug, or intel bug.

My xorg.conf after upgrading from hardy is very simple, it seems to be the intrepid failsafe one. Compiz is working so I assume the intel driver is loaded.
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by wgrant on 2008-10-14
> **muzzamo said:**
> Well i'm getting very slow/buggy video in totem and vlc. Quite often (maybe 70% of the time) the video is simply black, otherwise it is slow.

My xorg.conf after upgrading from hardy is very simple, it seems to be the intrepid failsafe one. Compiz is working so I assume the intel driver is loaded.

That's the normal Intrepid xorg.conf - you don't need one at all any more. Pretty much everything is autodetected properly now.

---

### Post by muzzamo on 2008-10-14
> **wgrant said:**
> That's the normal Intrepid xorg.conf - you don't need one at all any more. Pretty much everything is autodetected properly now.
OK.

How do you tell which video driver is actually loaded now, and what version etc?

---

### Post by ShirishAg75 on 2008-10-14
> **muzzamo said:**
> OK.

How do you tell which video driver is actually loaded now, and what version etc?

one way which I know is using xvinfo but its not the best one I guess.

---

### Post by muzzamo on 2008-10-14
> **ShirishAg75 said:**
> one way which I know is using xvinfo but its not the best one I guess.

My xvinfo says that its a 

```

  Adaptor #0: "Intel(R) Video Overlay"

```

I assume thats the correct one to be using...

---

### Post by mordanda on 2008-10-14
I'm getting spotty performance in Kubuntu 8.10 as well.  All the desktop effects work fine, but when there's constant motion on the screen (DVD, hulu, h.264 avi) the video hitches for a split second every 5 seconds.

I have a Dell D620 with an Intel 945GM video chip.  the driver loaded is the xserve-xorg-video-intel driver.

Does anyone have a solution?

D

---

### Post by adam on 2008-10-15
mordanda:  Go to System Settings. Open Service Manager (from the advanced tab), and shut off "Detecting RANDR (monitor) changes".

---

### Post by mordanda on 2008-10-16
Cool, that got rid of the studdering.  Now is only it would properly detect that the laptop lid is closed, turn that screen off and display on the external monitor that would be great.  I can change those settings manually but then I also have to resize the Taskbar to take up the rest of the screen.

Got any magic for that? :)

D

---

