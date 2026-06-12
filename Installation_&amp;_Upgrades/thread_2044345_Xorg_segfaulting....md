---
title: "Xorg segfaulting..."
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by ghat on 2012-08-19
hi

I have X crashing. How do I get more information on the crash...

I have 
```

ii  xserver-xorg                                   1:7.6+12ubuntu1                                   X.Org X server
ii  xserver-xorg-core                              2:1.11.4-0ubuntu10.7                              Xorg X server - core server

```

```

[ 49442.231] (**) NVIDIA(0):     device DELL 2007FP (DFP-1) (Using EDID frequencies has
[ 49442.231] (**) NVIDIA(0):     been enabled on all display devices.)
[ 49747.454]
Backtrace:
[ 49747.455] 0: /usr/bin/Xorg (xorg_backtrace+0x26) [0x7f7dfe738846]
[ 49747.455] 1: /usr/bin/Xorg (0x7f7dfe5b0000+0x18c6ea) [0x7f7dfe73c6ea]
[ 49747.455] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f7dfd8d6000+0xfcb0) [0x7f7dfd8e5cb0]
[ 49747.455] 3: /usr/bin/Xorg (doListFontsWithInfo+0x16a) [0x7f7dfe5ff33a]
[ 49747.455] 4: /usr/bin/Xorg (ProcessWorkQueue+0x21) [0x7f7dfe602ad1]
[ 49747.455] 5: /usr/bin/Xorg (WaitForSomething+0x65) [0x7f7dfe735af5]
[ 49747.455] 6: /usr/bin/Xorg (0x7f7dfe5b0000+0x4e5f2) [0x7f7dfe5fe5f2]
[ 49747.456] 7: /usr/bin/Xorg (0x7f7dfe5b0000+0x3d7ba) [0x7f7dfe5ed7ba]
[ 49747.456] 8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f7dfc76b76d]
[ 49747.456] 9: /usr/bin/Xorg (0x7f7dfe5b0000+0x3daad) [0x7f7dfe5edaad]
[ 49747.456] Segmentation fault at address 0x7f7f6cfb13b0
[ 49747.456]
Caught signal 11 (Segmentation fault). Server aborting
[ 49747.456]
Please consult the The X.Org Foundation support
         at http://wiki.x.org

```

I checked /var/crash/ but apport does not seem to be collecting information...

Ghat
PS: This is relating to my upgrade from lucid to precise... 

> 
PS:
I can reproduce the problem specifically. Apparently if I run any app which scans the fonts directories, it fails.
initially the problem was with nxclient, but stracing that lead to some gsfonts dir, so I checked xfontsel, and that 
too crashes the Xorg. I have since purged the gsfonts, but I still have the problem. 
IT CRASHES EVEN IF I DO A /etc/init.d/networking restart FROM A XTERM !!


---

### Post by tommcd on 2012-08-19
Crashes of the X server would be listed in **/var/log/Xorg.0.log**.
Errors in the Xorg.0.log start with **EE**.
A quick way to check for errors in the Xorg.0.log is to run the command:
```
/var/log/Xorg.0.log | grep -i ee
```
Any line that starts with **EE** is an error. Warnings can usually be ignored.

I always do clean installs of Ubuntu. I never do dist-upgrades, and I never have problems. 
Clean installs of Ubuntu are the best and easiest way to avoid problems like this.

---

### Post by ghat on 2012-08-19
> **tommcd said:**
> Crashes of the X server would be listed in **/var/log/Xorg.0.log**.
Errors in the Xorg.0.log start with **EE**.
A quick way to check for errors in the Xorg.0.log is to run the command:
```
/var/log/Xorg.0.log | grep -i ee
```
Any line that starts with **EE** is an error. Warnings can usually be ignored.

I always do clean installs of Ubuntu. I never do dist-upgrades, and I never have problems. 
Clean installs of Ubuntu are the best and easiest way to avoid problems like this.


The section of the error above is from Xorg.0.log...
I guess "clean" install is what is missing, as I did a debootstrapped ubuntu-minimal install, and then added to it..

Unfortunately, I guess this is the worst release I have seen from canonical, in relation to the earlier ones,... Unity etc is great for folks who want to move to Linux from OSX or Windows, but for hardcore guys like us who have been using Unix for 15+ years, its pretty crap...  I just like the standard GNOME and some like KDE, they should have release which is rock-solid with only GNOME+KDE and anything new like Unity, should be independent... The release is out since April, and is still not as stable... sometimes I feel like gong back to debian...

Ghat

---

### Post by ghat on 2012-08-19
UPDATE:...

I moved back to the stable latest kernel on 12.04

Linux desktop 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Please refer [post=12180208] this post on how my xorg.conf [/post]looks.... 

I am using the newer 3XX nvidia drivers, to achieve what I want, and with that it is plain simple crashing. If I move back to the ubuntu default version drivers, I cannot rotate the displays within twinview, and if I remember right I was not able to rotate them the earlier way using 2 separate X-screens, and Xinerama.

Ghat
> 
The new segfault in Xorg.0.log
```

[  1739.795]
Backtrace:
[  1739.796] 0: /usr/bin/Xorg (xorg_backtrace+0x26) [0x7f5353203846]
[  1739.796] 1: /usr/bin/Xorg (0x7f535307b000+0x18c6ea) [0x7f53532076ea]
[  1739.796] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f53523a1000+0xfcb0) [0x7f53523b0cb0]
[  1739.796] 3: /usr/bin/Xorg (doListFontsWithInfo+0x16a) [0x7f53530ca33a]
[  1739.796] 4: /usr/bin/Xorg (ProcessWorkQueue+0x21) [0x7f53530cdad1]
[  1739.796] 5: /usr/bin/Xorg (WaitForSomething+0x65) [0x7f5353200af5]
[  1739.796] 6: /usr/bin/Xorg (0x7f535307b000+0x4e5f2) [0x7f53530c95f2]
[  1739.797] 7: /usr/bin/Xorg (0x7f535307b000+0x3d7ba) [0x7f53530b87ba]
[  1739.797] 8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f535123676d]
[  1739.797] 9: /usr/bin/Xorg (0x7f535307b000+0x3daad) [0x7f53530b8aad]
[  1739.797] Segmentation fault at address 0x7f7bcfc4dea0
[  1739.797]
Caught signal 11 (Segmentation fault). Server aborting
[  1739.797]

```

The crash is caused with I use xfontsel..



> 
QUESTION....

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/304.32-0ubuntu4](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/304.32-0ubuntu4)

What does this mean...
```

Changelog
nvidia-graphics-drivers (304.32-0ubuntu4) quantal; urgency=low

  * debian/rules:
    - Disable support fo X ABI 13 since the driver doesn't
      seem to work well with the new X.
 -- Alberto Milone <email address hidden>   Fri, 17 Aug 2012 18:50:05 +0200

```

How do I disable it ? I am trying to use this in Precise, not Quantal... 



---

### Post by ghat on 2012-08-20
OK...

So there is some issue with my xorg.conf, which I cannot tell at this point.. 

I let the NVIDIA 302.* (and later/now 304.*) driver do all the setting up (ie removed the xorg.conf, and let it take the defaults) 

with that, I don't see any crash... at least the known ways to crash it..

Next I just added this line to my
/etc/gdm/Init/Default
```

[ -x /usr/bin/xrandr ] && \
     /usr/bin/xrandr --output DVI-I-2 --pos 0x400 --output DVI-I-3 --pos 1920x0 --rotate left


```

just before the last line/[FONT="Courier New"]exit0[/FONT]

With that, I do get the rotation I wanted, and it does not crash...

If I dig out the correct config, I will post it on the other [post=12183215]thread of the xorg.conf [/post]

Ghat

---

