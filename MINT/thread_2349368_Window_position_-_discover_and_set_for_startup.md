---
title: "Window position - discover and set for startup"
date: 2017-01-13
forum: MINT
---

### Post by Kevin McCready on 2017-01-13
Is there a way to discover the windows position of a window already opened?

Then I want to start my program at that position each time.

Here's what I have now:
```

vlc /home/k/Documents/deafvids/playlist.m3u

```

My system:
Kernel: 4.4.0-21-generic i686 (32 bit) 
Desktop: MATE 1.14.1
Distro: Linux Mint 18 Sarah

---

### Post by vasa1 on 2017-01-13
The *xprop* and *xwininfo* commands and the *wmctrl* program provide window details. *wmctrl* may not be present by default.

Making rules for how a program's windows should be sized and placed depends on the program and the window manager. Some programs allow a --geometry option.

---

### Post by Kevin McCready on 2017-01-14
Thanks for that. xwininfo gave me:
Window id: 0x360000d "g66.mp4 - VLC media player"

  Absolute upper-left X:  797
  Absolute upper-left Y:  29
  Relative upper-left X:  3
  Relative upper-left Y:  29
  Width: 1120
  Height: 1020
  Depth: 24
  Visual: 0x326
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x360000c (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +797+29  -3+29  -3-31  +797-31
  -geometry 1120x1020-0+0

I tried to construct a command with --geometry but I kept getting an error: syntax error near unexpected token `newline'

Here's what I tried for the latest error:
```

vlc /home/k/Documents/deafvids/playlist.m3u --geometry=<[1120[x1020][0:0]>

```

Hoping to get help constructing the --geometry command

---

### Post by vasa1 on 2017-01-14
Whether --geometry is possible depends on the application. It looks like vlc doesn't accommodate --geometry. See [http://manpages.ubuntu.com/manpages/xenial/en/man1/vlc.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/vlc.1.html)

---

### Post by Kevin McCready on 2017-01-14
I found something which might help. 

Window properties:
      --width <integer [-2147483648 .. 2147483647]> 
                                 Video width
          You can enforce the video width. By default (-1) VLC will adapt to
          the video characteristics.
      --height <integer [-2147483648 .. 2147483647]> 
                                 Video height
          You can enforce the video height. By default (-1) VLC will adapt to
          the video characteristics.
      --video-x <integer [-2147483648 .. 2147483647]> 
                                 Video X coordinate
          You can enforce the position of the top left corner of the video
          window (X coordinate).
      --video-y <integer [-2147483648 .. 2147483647]> 
                                 Video Y coordinate
          You can enforce the position of the top left corner of the video
          window (Y coordinate).

But when I tried different commands it always seemed to open in the same wrong place.

---

### Post by Kevin McCready on 2017-01-16
Bump

---

