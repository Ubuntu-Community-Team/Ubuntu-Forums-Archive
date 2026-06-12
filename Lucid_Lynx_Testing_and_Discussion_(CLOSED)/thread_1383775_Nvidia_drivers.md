---
title: "Nvidia drivers?"
date: 2010-01-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brottman on 2010-01-17
What is going on with the nvidia drivers? I can't get the drivers to work right. They are installed, and the Hardware Drivers say they are activated but not in use.

---

### Post by buzzmandt on 2010-01-17
same problem here, 
had to use the drivers from nvidia.com

---

### Post by ronacc on 2010-01-17
are you sure your nvidia driver is not active ? system>administration>hardware drivers SAYS my Nvidia driver "nvidia _current" is activated but NOT in use , however it most certainly is in use , Also on my sys nvidia-settings crashes on startup but there seem to be no ill effects , compiz is working fine .

---

### Post by cariboo on 2010-01-17
I get the same thing as ronacc, everything works as it should. According to Nvidia X  Server Settings I'm using the 190.53 drivers. The driver in synaptic is now called nvidia-current.

---

### Post by vishalrao on 2010-01-17
btw, looks like a good useability move to call it "current" for those who cant figure out that "highest version is (probably) better"

---

### Post by kahumba on 2010-01-17
Folks, the issue with Nvidia's drivers is a known issue, please refer to its official solution at:
[http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues]("http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues")

but bear in mind there's a typo on that page and no one is willing to fix it.
Instead of "nvidia-config", it should say "nvidia-xconfig".

---

### Post by hikaricore on 2010-01-17
Using the nvidia configuration tool is a moot point if the damn packages don't work to begin with.
Installing the binary blob works perfectly, any of the packages seem to build properly with dkms but X bombs out and gives a slew or strange errors.

The alpha issues list includes the following:
> * Because of the new alternatives system, the nvidia installer from NVIDIA's website currently doesn't work. 
This is completely inaccurate.

---

### Post by Ibidem on 2010-01-17
Just helped my brother with installing NVIDIA drivers on Fedora 12, which *seems* to be pretty close to where Lucid is;
saw tons of X errors until following this instruction:
To use the default initrd, but disable the nouveau driver, edit /etc/grub.conf and add the following to the end of the line(s) starting with 'kernel': 
  rdblacklist=nouveauBut that's assuming that nouveau is being loaded.  If it is, the error will be some complaint about /path/to/nvidia.ko not being found.

[Here's the guide]("http://rpmfusion.org/Howto/nVidia#head-205aab6f190d363e3915c0fa2e0681fc392aaeb6") for Fedora 12; that one line is probably the only relevant one.

All the errors go in ~/.xsession-errors...

Ibidem

---

### Post by mc4man on 2010-01-17
I would think that the best first step, as noted in post 6 is to follow the simple instr.'s which should work for most nvidia adapters. (before chasing mods or other methods

Quite simple just - 
open synaptic, search nvidia, install nvidia-current which should install a few other packages including nvidia-settings

After install run
sudo nvidia-xconfig and then restart

That's it, don't bother with system -> admin -> 'hardware drivers

Then if desired install compiz-config-settings-manager and enable/disable what you wish, no need to go to system -> pref. -> appearance -> visual effects to enable effects

You can even try on a live cd, worked quite well here with GeForce 8400M GS on a laptop

before
> ubuntu@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
ubuntu@ubuntu:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

After
> ubuntu@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"
    number of ports: 32
buntu@ubuntu:~$ glxinfo
name of display: :2.0
display: :2  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4


Nothing set in system -> pref. -> appearance -> visual effects.,( all radio buttons are empty) but settings in compiz are possible  as in screen (rotate cube - scroll on desktop

---

### Post by turbostd on 2010-01-18
I did all that and x doesn't start :( I get the following error. Card is an on board 6150LE.

```
EE) Jan 18 18:43:44 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jan 18 18:43:44 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jan 18 18:43:44 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
```

only thing I see in kern.log that may be relevant is:

```
Jan 18 08:16:45 c521 kernel: [   14.407873] nvidia: module license 'NVIDIA' taints kernel.
```

---

### Post by mc4man on 2010-01-19
@kahumba

> but bear in mind there's a typo on that page and no one is willing to fix it.

Thanks for heads up, been taken care of - was actually 2 places - release notes and known issues page

---

### Post by sinedanat on 2010-03-06
Thanks a lot!

But it didn't work for my system - I tried 1001 ways to solve this problem.
And this link in Russian really helped me - 
[http://www.shatlovsky.ru/2009/11/20/nvidia-v-ubuntu-reanimaciya/](http://www.shatlovsky.ru/2009/11/20/nvidia-v-ubuntu-reanimaciya/)

1. Remove all concerning "nvidia":
$ [COLOR=#c20cb9]**sudo**[/COLOR] dpkg --get-selections | [COLOR=#c20cb9]**grep**[/COLOR] nvidia | [COLOR=#c20cb9]**grep**[/COLOR] -v deinstall | [COLOR=#c20cb9]**awk**[/COLOR] [COLOR=#ff0000]'{print $1}'[/COLOR] | [COLOR=#c20cb9]**xargs**[/COLOR] [COLOR=#c20cb9]**sudo**[/COLOR] apt-get remove

2. Check it:
$ [COLOR=#c20cb9]**sudo**[/COLOR] dpkg --get-selections | [COLOR=#c20cb9]**grep**[/COLOR] nvidia | [COLOR=#c20cb9]**grep**[/COLOR] -v deinstall

3. Install only needed packages:
$ [COLOR=#c20cb9]**sudo**[/COLOR] apt-get [COLOR=#c20cb9]**install**[/COLOR] nvidia-glx[COLOR=#000000]-185

4. Load module nvidia and check it:
$ [/COLOR][COLOR=Black][COLOR=#c20cb9]**sudo**[/COLOR][/COLOR] modprobe nvidia
[COLOR=#000000]$ [/COLOR][COLOR=Black][COLOR=#c20cb9]**sudo**[/COLOR][/COLOR] lsmod | grep -i nvidia
[COLOR=#000000]
5. Make configuration file xorg.file in /etc/X11/xorg.conf  
$ [/COLOR][COLOR=Black][COLOR=#c20cb9]**sudo**[/COLOR][/COLOR][COLOR=#000000] nvidia-xconfig

6. Reboot.
[/COLOR]
Useful links:
[http://www.shatlovsky.ru/2009/11/20/nvidia-v-ubuntu-reanimaciya/](http://www.shatlovsky.ru/2009/11/20/nvidia-v-ubuntu-reanimaciya/)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html](http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html)

My system:
Ubuntu 10.04 (Lucid Lynx) Alpha 3 + XFX Nvidia 9500GT + FOXCONN  P9657AB-8EKRS2H + Intel Pentium D 925
  [URL="https://wiki.ubuntu.com/LucidLynx"]
[/URL]

---

### Post by Uncle Spellbinder on 2010-03-06
> **brottman said:**
> What is going on with the nvidia drivers? I can't get the drivers to work right. They are installed, and the Hardware Drivers say they are activated but not in use.

Same here. But desktop effects (compiz) are working perfectly even though in hardware drivers I get "activated but not in use."

:-?

---

### Post by ratcheer on 2010-03-06
It is a bug. I will look it up if anyone needs me to. The driver is obviously in use, as the Nouveau driver does not do advanced effects. Since the effects are working, the driver is working.

Tim

---

### Post by blakamin on 2010-03-06
> **ratcheer said:**
> It is a bug. I will look it up if anyone needs me to. The driver is obviously in use, as the Nouveau driver does not do advanced effects. Since the effects are working, the driver is working.

Tim
Thanks Tim, handy to know what drivers are in use sometimes when things say they aren't... and the Nouveau driver does't do advanced effects.

[[IMG]http://img709.imageshack.us/img709/1434/screenshot2lv.png[/IMG]](http://img709.imageshack.us/i/screenshot2lv.png/)

(quite hard to get a shot of that)

---

### Post by Uncle Spellbinder on 2010-03-06
> **ratcheer said:**
> ...the Nouveau driver does not do advanced effects...

I've read (and seen) effects working just fine using the  Nouveau driver. Seen a video on another forum and seen statement here on this forum to that effect.

---

### Post by ratcheer on 2010-03-06
> **Uncle Spellbinder said:**
> I've read (and seen) effects working just fine using the  Nouveau driver. Seen a video on another forum and seen statement here on this forum to that effect.

I have heard that, too. But if I am using Nouveau and I try to change Visual Effects from None, it informs me that I must install the proprietary restricted drivers in order to do so. Then, when I install them, it works.

Tim

---

### Post by tunin on 2010-03-06
I have tried the instructions on the Lucid known bugs post and from post #12 in this thread.
From Xorg log:
> (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

From Jockey log:
> 2010-03-06 15:03:27,179 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-03-06 15:03:27,200 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-03-06 15:03:27,204 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-03-06 15:03:27,206 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriver from name FglrxDriver
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/fglrx.py", line 16, in __init__
    raise SystemError, 'does not currently work with X.org 1.7'
SystemError: does not currently work with X.org 1.7

I have been logging in with the low graphics option to tinker with things.  I can't seem to find it in the log files, but in the last log in I saw an error message about not being able to determine what resolution my monitor is.  This is understandable since I am using a small flat screen tv for my monitor. 

As things are currently, I have the 96 driver installed (after trying the 173 as in post 12).  It shows the driver as being active but not used.  Everything seems to be working normally as it did before the update (as far as effects go).  The resolution is a bit strange (everything is a bit larger), but I assume that comes from the option selected at boot.  Also the order of applets was shuffled for some reason.  So things are running, but still not right.  I'll have to do some more searching and tinkering to see if I can get mine to go back to normal.

---

