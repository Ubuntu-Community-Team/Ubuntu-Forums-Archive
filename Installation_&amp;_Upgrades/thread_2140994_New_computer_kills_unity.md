---
title: "New computer kills unity?"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by knowledge_is_power on 2013-05-01
Hey, I just built a new computer, it is composed of the following:
a gigabyte GA-H61N-USB3 socket LGA1155 mini ITX board: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128526](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128526)
a pentium G2020 Ivy bridge LGA 1155 CPU: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16819116886](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819116886)
a OCZ Vertex Plus OCZSSD2: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16820227956](http://www.newegg.ca/Product/Product.aspx?Item=N82E16820227956)
and 4 gb of cosair RAM: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16820145278](http://www.newegg.ca/Product/Product.aspx?Item=N82E16820145278)

heres the wierd stuff: computer POSTS fine, boots 12.04 live CD fine, but after install, either compiz or unity causes my GUI to lock up, and not always in the same way.

It always works after I log in.
Usually after 2 or 3 clicks and animations, it crashes.
When it crashes, it does one of two things:
1) window decorations freeze: I am unable to click on anything, alt+tab, move windows, change windows, open close windows, etc. I CAN USE THE KEYBOARD INSIDE A WINDOW THATS CURRENTLY ACTIVE.

2) text input freezes: being linux this is actually worse. I can switch windows OK (animations are non existent or slow) and click things, but I cannot use the keyboard.

1 happens more often than 2. When 1) happened, I goto ctrlaltf1 and killall -KILL compiz and go back and it works for a couple more clicks of the mouse (sometimes up to five or six!)

I thought maybe it was a SSD problem, but I ran a read/write benchmark on it and it passed no problem. 

any suggestions? my current course of action is to 1) try ubuntu 13.10. 2) try ubuntu 12.04 LTS i386 version 3) try 13.10 i386 version.

---

### Post by 2F4U on 2013-05-01
I would suspect the graphics card? Is this an integrated card which comes with the processor? Maybe the graphics effects are too much for the card or the graphics drivers don't support the GPU well. If I were you, I would try something that places less demand on the card, such as Xubuntu or Lubuntu. 12.04 LTS may also be a good option to try.

---

### Post by ajgreeny on 2013-05-01
If you're using the ivybridge integrated graphics you should be fine with unity, as far as I'm aware.

I have an i5-3570K cpu with HD4000 graphics which runs unity fine, though I don't use it, much preferring Xubuntu to Ubuntu now.

---

### Post by knowledge_is_power on 2013-05-01
I had the same thought, and one of my ideas was to disable compiz. however, It would seem that is no longer possible with unity?
ajgreeny is using same ivybridge, so maybe that's not the problem.

2F4U: I am trying to use 12.04 LTS, as I don't want to have to worry about updating. Maybe I will try Xubuntu if the other attempts don't pan out.

---

### Post by grahammechanical on 2013-05-01
Regarding this statement

> [COLOR=#000000]3) try 13.10 i386 version.[/COLOR]

You are six months away from 13.10. Perhaps you are thinking of the development branch. Well, the code for Saucy Salamander (13.10) is being built on the code from Raring Ringtail (13.04). If fact the two code bases are still very much the same. Have you tried a different video driver? You will find them in System Settings>Software & Updates>Additional Drivers tab.

Regards.

---

### Post by oldfred on 2013-05-01
I saw this in another thread, but I have nVidia.

 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by knowledge_is_power on 2013-05-01
yep, my bad, I meant 13.04.
nothing shows up under additional drivers, which is new to me, but I've always used AMD/ati graphics.

oldfred: output I get is:

Vendor: Intel open source tech center
Renderer: Mesa DRI Intel(R) Ivybridge desktop
OpenGL version: 3.0 Mesa 9.0

Just tried to boot a 13.04 live USB I made on my laptop in 11.04, and I got nothing. initial splash, then everything goes dark: keyboard, mouse, screen, activity light on USB drive.. and I have to hard power off.

when I "sudo shutdown now" from the installed 12.04, It halts while asking all processes to terminate giving a bunch of errors for different threads (they are all modem manager) reading something along the lines of:

modem-manager: could not get the system bus. Make sure message bus deamon is running. Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory.

I wonder if it is related. maybe just a bad install because of faulty flash memory? I would use a dvd, but my dvd drive is on an PATA ribbon, which my tiny board does not have a connector for.

---

### Post by knowledge_is_power on 2013-05-01
This is the wierdest thing I have ever seen. different parts of the UI do not respond at various times. Sometimes I cannot move windows, sometimes I can, sometimes I can't use the mouse, sometimes I can't use the keyboard, sometimes one or another thing comes back (without a reboot). i am low on ideas. is it at all possible that there is damaged hardware, but my computer still boots properly? is ubuntu still packaged with memtest86?

Edit: memtest checked out fine, h/w reports line up with all specs. 
installed gnome
gnome seems to work fine - is this just because it's more stable? (i might note it has enabled comosting that works just fine)
Xorg crashed about 5 minutes after login. gnome barely missed a beat.
still mystified, but now im satisfied its not h/w

Well. I reinstalled 12.04 LTS, tested the flash drive, md5'd everything i could, UI still mostly non-functional. I switched to Unity 2D based on my experience with gnome, and it worked basically fine! I installed compizconfig-settings, dicked around with some settings, went back into 3d, changed some more stuff, and it appears to work ok now, with just the occasional Xorg crash to hold me back. shut down fine with no halts.

**Based on the fact that it's compiz, Xorg, or Unity, what logs would make sense to look in for startup errors? **

OK I checked /var/log/boot.log and no problems, checked /var/log/Xorg.0.log and no problems. but then I remembered I had killed X after the UI lockup thing happened upon startup and logged back in to find it working again, so I checked /var/log/xorg.0.log.old and found the following at the end:

> [    25.157] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
**[   115.748] (EE) **
[   115.748] (EE) Backtrace:
[   115.748] (EE) 0: /usr/bin/X (xorg_backtrace+0x34) [0x7fa84c4bd644]
[   115.748] (EE) 1: /usr/bin/X (0x7fa84c308000+0x1b9599) [0x7fa84c4c1599]
[   115.748] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fa84b62e000+0xfcb0) [0x7fa84b63dcb0]
[   115.748] (EE) 3: /usr/bin/X (0x7fa84c308000+0x6b2e7) [0x7fa84c3732e7]
[   115.748] (EE) 4: /usr/bin/X (0x7fa84c308000+0x16d258) [0x7fa84c475258]
[   115.748] (EE) 5: /usr/bin/X (0x7fa84c308000+0x166d2f) [0x7fa84c46ed2f]
[   115.748] (EE) 6: /usr/bin/X (mieqProcessDeviceEvent+0x204) [0x7fa84c49e224]
[   115.748] (EE) 7: /usr/bin/X (0x7fa84c308000+0x4ced5) [0x7fa84c354ed5]
[   115.748] (EE) 8: /usr/bin/X (DisableDevice+0xb8) [0x7fa84c3565a8]
[   115.748] (EE) 9: /usr/bin/X (0x7fa84c308000+0x4eab2) [0x7fa84c356ab2]
[   115.748] (EE) 10: /usr/bin/X (0x7fa84c308000+0x44165) [0x7fa84c34c165]
[   115.748] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fa84a2b476d]
[   115.748] (EE) 12: /usr/bin/X (0x7fa84c308000+0x444b1) [0x7fa84c34c4b1]
[   115.748] (EE) 
[   115.748] (EE) Segmentation fault at address 0xd0
[   115.748] 
Fatal server error:
[   115.748] Caught signal 11 (Segmentation fault). Server aborting
[   115.748] 
[   115.748] (EE) 

which looks like it was testing refresh rates and crashed on 67.5kHz?
Edit: nope, it looks like the new log hit the 1152x864"x0.0  108.00 modeline and finished up.
that segfault must have happened after successful login. Must have been caused by something else breaking it.
which points to my GUI freeze shortly after successful login.

I still dont understand.

---

### Post by knowledge_is_power on 2013-05-02
I have found this thread:
[http://www.flyingpenguin.com/?p=17668](http://www.flyingpenguin.com/?p=17668)
Which describes my problem almost perfectly.
however, the suggestion is to upgrade kernel to 3.5.0-27.43... because it is old.

> scoob@scoob-9:~/.config/autostart$ uname -a
Linux scoob-9 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Why would a bugfix get REMOVED in a kernel revision?

---

