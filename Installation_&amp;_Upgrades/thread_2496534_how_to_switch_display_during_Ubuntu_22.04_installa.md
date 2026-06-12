---
title: "how to switch display during Ubuntu 22.04 installation?"
date: 2024-04-02
forum: Installation &amp; Upgrades
---

### Post by fox8171 on 2024-04-02
i'm installing 22.04 in a J1900 CPU motherboard.
the motherboard has LVDS, VGA and HDMI.
however the LVDS is defected, dont show image. then i use VGA for display.

But after "try or install Ubuntu", the VGA display shows picture as a "secondary display"
now i can not continue.
how to make VGA "primary display" during the installation?
pls help, thanks

---

### Post by TheFu on 2024-04-02
Change the primary display setting in the BIOS.

---

### Post by fox8171 on 2024-04-02
it doesnt work. i already select only VGA display in BIOS. but when it gets into ubuntu screen, VGA still shows picture as secondary screen.

---

### Post by fox8171 on 2024-04-03
i tried to edit the boot parameter as picture below.

also i tried these:
video=LVDS-1:d
video=LVDS-0:d
video=LVDS-0:d video=vga-0:e
video=LVDS-0:d video=LVDS-1:d video=vga-0:e video=vga-1:d

none works. the VGA still shows as secondary display.

---

### Post by fox8171 on 2024-04-06
anyone has any clue?

---

### Post by MAFoElffen on 2024-04-07
The correct syntax for the 'video' boot parameter would be
```

video=VGA-1:1920x1080@60

```
Using a port name (case matters in the name) & res mode that the BIOS see from Grub using either the modes listed by 'vbeinfo' (Legacy BIOS) or 'videoinfo' (UEFI BIOS).  That will set the mode of the display.

What you are looking for is setting the precedence order of the frame buffers, which are in use at boot, from the boot loader. Look at Section 5.3 of this, from the Doc's: [https://tldp.org/HOWTO/BootPrompt-HOWTO-5.html](https://tldp.org/HOWTO/BootPrompt-HOWTO-5.html)
> 
5.3 The `video=vc:...' Argument

A number, or a range of numbers (e.g. video=vc:2-5) will specify the first, or the first and last frame buffer virtual console(s). The use of this option also has the effect of setting the frame buffer console to not be the default console. 

I think that is what you are looking for.

But that says frame buffers and not ports. So I am thinking more along the lines of trying(?)
```

video=VGA-1:1 video=HDMI-1:2 video:LVDS-1:5

```
*** I am looking into this. May edit this later, based on what I find.

---

### Post by MAFoElffen on 2024-04-07
I'm thinking the better 'option' is 'map' ([https://www.kernel.org/doc/Documentation/fb/fbcon.txt](https://www.kernel.org/doc/Documentation/fb/fbcon.txt))
> 
3. fbcon=map:<0123>

        This is an interesting option. It tells which driver gets mapped to
        which console. The value '0123' is a sequence that gets repeated until
        the total length is 64 which is the number of consoles available. In
        the above example, it is expanded to 012301230123... and the mapping
        will be:

        tty | 1 2 3 4 5 6 7 8 9 ...
        fb  | 0 1 2 3 0 1 2 3 0 ...

        ('cat /proc/fb' should tell you what the fb numbers are)

    One side effect that may be useful is using a map value that exceeds
    the number of loaded fb drivers. For example, if only one driver is
    available, fb0, adding fbcon=map:1 tells fbcon not to take over the
    console.

    Later on, when you want to map the console the to the framebuffer
    device, you can use the con2fbmap utility.

4. fbcon=vc:<n1>-<n2>

    This option tells fbcon to take over only a range of consoles as
    specified by the values 'n1' and 'n2'. The rest of the consoles
    outside the given range will still be controlled by the standard
    console driver.

    NOTE: For x86 machines, the standard console is the VGA console which
    is typically located on the same video card.  Thus, the consoles that
    are controlled by the VGA console will be garbled.

[https://superuser.com/questions/122173/change-linux-consoles-default-monitor](https://superuser.com/questions/122173/change-linux-consoles-default-monitor)

So along the lines of 'video=map:<0123>' (example: video=map:1)...whichever of those corresponds to the port you want used. Which is going to be found through playing with that parameter on your own hardware

---

