---
title: "The answer about &quot;Error opening /dev/wacom &quot;"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by zhuomingliang on 2006-06-20
if you're using aiglx,maybe have this issue,just like me

> cann't find  Xserver&#65306;/usr/bin/Xorg-air[COLOR="Red"]:0 :0[/COLOR] -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
> 
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success

this /etc/X11/gdm/gdm.conf-custom file is
> [server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air:0
flexible=ture


what'is wrong ?

why cann't find  Xserver&#65306;/usr/bin/Xorg-air[COLOR="Red"]:0 :0[/COLOR] -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

because it should be /usr/bin/Xorg-air[COLOR="Red"]:0[/COLOR] -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Modify 
command=/usr/bin/Xorg-air:0

just like this

> command=/usr/bin/Xorg-air
and it is OK.

sorry , my poor english](*,)

---

### Post by slack42 on 2007-01-20
Hi ,  I was looking at my gdm log and I noticed that I was getting a similar message to the one you posted. I went to the file you said that you edited to correct it and I don't have server-aiglx section but I still get that same message in the error logs.

 (EE) xf86OpenSerial: Cannot open device /dev/wacom

 I have xgl install  , I installed it because I wanted to try out beryl. If I create a sections server-xgl and put it the same way you have it would that get rid of the error message in my log file? I also don't have a /dev/wacom directory and don't know if I'm suppose to have it or not or what's even suppose to be in it. I am using ubuntu edgy and I have a ATi 9600 video card using restricted drivers witch seem to work. 

I stumbled on this because I was having another issue ( with beryl ) and so I was poking around in the logs to find a solution and that's how I came across your post. I don't know if this will solve my problem but I was just curious about how to get rid of that error message. 

Thanks

---

### Post by linear on 2007-01-20
That error, I believe, is due to entries in /etc/X11/xorg.conf - if you don't have a Wacom tablet, there are lines in xorg.conf that you can comment out.

(If you do have a Wacom tablet, and wacom-tools installed, then the path is wrong anyway - should be /dev/input/wacom.)

---

### Post by slack42 on 2007-01-21
Thanks, I don't have a tablet and I have tried to comment out that section in xorg.conf but then when I restart x it crashes. And I get that error message saying that x couldn't start. Can I just add the line /dev/input/wacom or will that cause more problems because I don't have a tablet?

---

### Post by linear on 2007-01-21
I think you'll get the same "Cannot open device" errors. You could just leave xorg.conf alone and ignore them.

---

### Post by jobox on 2007-04-09
I suspect you may have missed a little something is you still get errors after commenting out the wacom device sections.
If youlook towards the end of your xorg.conf you will find those devices beeing included in the server section aswell. commenting those out will remove the errors fromyourlog. If that doesn't solve it youare most likely editing the wrong file.

---

