---
title: "unviewable screen after installation"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by Jason_Lovett on 2005-06-09
I have install 5.04 64bit but when i boot into it the first time i get strange display i can't see anything apart for random coloured pixels, my monitor can handle the resolution, what should i do?

system specs:

amd athlon 64 3000+
Nvidia 6600GT
Via K8T800 mobo
80GB Sata
40GB IDE
old packard bell monitor
onboard sound.

thanx

---

### Post by sethmahoney on 2005-06-09
Sounds like some changes to xorg.conf are in order, though I'm not sure what to recommend.  I'd search the forum for hints on monitor issues and xorg.conf.

One other question: Have you used other versions of Ubuntu successfully, or other Linux distros?

---

### Post by Jason_Lovett on 2005-06-09
I have use suse linux 9.2 and mepis which worked fine, Mandrive same prob and this is the only ubuntu install i have tried. Could it be a issue with the 64bit version?

---

### Post by sethmahoney on 2005-06-09
Could be.  Another possibility is that its xorg specific, though I wouldn't think that would make sense...  Do you know offhand if suse and mepis use xorg or xfree86?

Also, are you getting just a few random pixels here and there or a sort of weird wiggley arc-shaped blur that strains your eyes when you look at it (sorry, don't quite know how to describe it)?

---

### Post by Jason_Lovett on 2005-06-10
Mepis uses xfree86 and suse uses x.org (6.8.1). not much help really.

I going to download the 32bit version and try that.

---

### Post by Jason_Lovett on 2005-06-11
would trying Kubuntu make any differnce?

---

### Post by Xian on 2005-06-11
[QUOTE=Jason_Lovett]I have install 5.04 64bit but when i boot into it the first time i get strange display i can't see anything apart for random coloured pixels, my monitor can handle the resolution, what should i do?[/QUOTE]
Compare what your monitor specs are to what is listed in the _example_ "Monitor" section of the /etc/X11/xorg.conf file listed below. Make any appropriated changes where required. This is a nice [How-To](http://www.advogato.org/person/robertc/diary.html?start=35) on getting your DisplaySize setup.

```
Section "Monitor"
        Identifier	      "COMPAQ 7500"
        Option	      "DPMS"
        HorizSync        30-70
        VertRefresh    50-140
        DisplaySize     312 234
EndSection
```

---

### Post by Jason_Lovett on 2005-06-11
what is xdpyinfo and how do i run it coz it cant get a good pic on the screen?

---

### Post by Xian on 2005-06-11
[QUOTE=Jason_Lovett]what is xdpyinfo and how do i run it coz it cant get a good pic on the screen?[/QUOTE]
It's just a terminal command. You can run it from any prompt.
Then just look at the output.

```
$ xdpyinfo
```

Here's mine: 

```
$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    60802000
X.Org version: 6.8.2
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x300001b, revert to Parent
number of extensions:    33
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    FontCache
    GLX
    LBX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation
default screen number:    0
number of screens:    1

screen #0:
  print screen:    no
  dimensions:    1024x768 pixels (313x235 millimeters)
  resolution:    83x83 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32

</snip>
```

---

### Post by Jason_Lovett on 2005-06-11
well when it boots it get the unviewable screen and i press ctrl + alt + F1 to get the promt but all the text is unreadable it looks like each letters is made of 2 monochrome verticle pixels. I would not be able to read the output.

---

### Post by mingus on 2005-06-12
Perhaps I missed something in this thread . . . but you have a corrupted display immediately after you boot and before you get to the login screen, right?  If so, the X server has not been loaded yet, and the problem may be with framebuffer and/or the ability to read the video card.

First, just try disabling the vesa framebuffer - at your grub boot menu, edit the kernel argument, adding to the end of the line:

vga=normal

or if that doesn't work:

video=vga16:off

---

### Post by Jason_Lovett on 2005-06-12
well i get the boot sequence the after that has finished i get the currupt display, i will try what you said soon

---

### Post by mingus on 2005-06-12
too be clear . . . when you hit enter to boot, first you will see a few lines of text which is grub executing boot command and calling the kernel, it is after these that the boot sequence actually begins.  Then you should see a couple of lines and "Starting Ubuntu"; do you see this?  Or do you get farther, another 10 lines or so you should see something about "vesafb" or "vga"; this is the video driver being loaded.  
Or is it still farther down in the sequence, and can you see where?

Of course, you should be booting in recovery mode now to get the kernel echo.

---

### Post by Jason_Lovett on 2005-06-12
what is meant be  > kernel echo ?
because i'm relitively new to linux.

---

### Post by mingus on 2005-06-12
sorry for talking geek, it's a programmer term . . . the text messages you see displayed as the kernel starts the system are called an "echo", that is, it is replying back to you with what you asked it to do.

---

### Post by Jason_Lovett on 2005-06-13
i have tried the xdpyinfo command suggested in the recovery mode, but it says it is not a useable command

---

