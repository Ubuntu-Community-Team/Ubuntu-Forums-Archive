---
title: "TTY resolution in 11.10"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by The Bird Man of Alcatraz on 2012-02-02
Hi all,
I've followed several tutorials without success; as far as I am aware, all of them were for older Ubuntu versions.

I've modified /etc/default/grub and /etc/grub.d/00_header

The only hex code that's produced some sort of visible difference is the one for 8-bit 1200x800, which ended up running off the screen.  I'm hoping to get it working with 1280x1024 at any number of bits.  1650x1050 would be ideal.  I'm using the Nvidia driver.

Thanks for any ideas

```
$ sudo hwinfo --framebuffer
[sudo] password for peter: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.oklx5b9oyeA
  Hardware Class: framebuffer
  Model: "NVIDIA GF104 Board - 10410000"
  Vendor: "NVIDIA Corporation"
  Device: "GF104 Board - 10410000"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xd5000000-0xd5dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by MAFoElffen on 2012-02-05
> **The Bird Man of Alcatraz said:**
> Hi all,
I've followed several tutorials without success; as far as I am aware, all of them were for older Ubuntu versions.

I've modified /etc/default/grub and /etc/grub.d/00_header

The only hex code that's produced some sort of visible difference is the one for 8-bit 1200x800, which ended up running off the screen.  I'm hoping to get it working with 1280x1024 at any number of bits.  1650x1050 would be ideal.  I'm using the Nvidia driver.

Thanks for any ideas

```
$ sudo hwinfo --framebuffer
[sudo] password for peter: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.oklx5b9oyeA
  Hardware Class: framebuffer
  Model: "NVIDIA GF104 Board - 10410000"
  Vendor: "NVIDIA Corporation"
  Device: "GF104 Board - 10410000"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xd5000000-0xd5dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
It's sad that no one has answered this already (2 days).  My apologies.

If you could backoff your /etc/grub.d/00_header to it's original settings... Then bring up your /etc/default/grub to make changes there...

You posted the results of "hwinfo --framebuffer", which I feel is half of what you need. The other half is the results of "hwinfo --monitor"... Then you have what your video card is capable of displaying AND what modes your monitor is capable of (it's a balance).

Then you add a vga switch to the boot line... For instance, in your data above, take the resolution: "Mode 0x031a: 1280x1024 (+2560), 16 bits"... with translates to 1280x1024x16 (WIDTHxHEIGTHxDEPTH), Linux VESA MODE of hex 0x031a or decimal 794.

In /etc/default/grub, goto the line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```And change it to 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=0x31a"

```OR
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=794"

```Then go down to the line:
```

#GRUB_GFXMODE=640x480

```And change it to 
```

GRUB_GFXMODE=1280x1024x16

```Save and exit, then do
```

sudo update-grub

```To pick up those changes. That will the resolution of the Grub menu and the virtual terminal sessions.

Another way to do it is to use setupcon (look at the man setupcon) or manually edit /etc/default/console-setup... You can reset your console fonts, font point size, width and heigth... to do the same thing from a different perspective... sort of like this extract:
```

# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT="no"

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP="UTF-8"

# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET="Lat15"

# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16) and Fixed (sizes 13, 14, 15, 16 and 18).  Only when
# CODESET=Ethiopian: Goha (sizes 12, 14 and 16) and 
# GohaClassic (sizes 12, 14 and 16).
# Set FONTFACE and FONTSIZE to empty strings if you want setupcon to
# set up the keyboard but to leave the console font unchanged.
[COLOR=Red]FONTFACE="VGA"
FONTSIZE="8"
[/COLOR]
# You can also directly specify nonstandard font or console map to load.
# Use space as separator if you want to load more than one font.
# You can use FONT_MAP in order to specify the Unicode map of the font
# in case the font doesn't have it embedded.

# FONT='lat9w-08.psf.gz /usr/local/share/braillefonts/brl-08.psf'
# FONT_MAP=/usr/share/consoletrans/lat9u.uni
# CONSOLE_MAP=/usr/local/share/consoletrans/my_special_encoding.acm

# You can also specify a screen size that setupcon will enforce.  This can not
# exceed what the current screen resolution can display according to the size of
# the loaded font.
#
[COLOR=Red]SCREEN_WIDTH=132
SCREEN_HEIGHT=50
[/COLOR]
##<<File Goes On>>

```That should be enough info to get you started right? Tell me how it goes.

---

### Post by The Bird Man of Alcatraz on 2012-02-05
Thanks for the detailed response.  I restored both files to their original settings and then tried your suggestion with /etc/default/grub, but when booting up this shows up--
```
vga=794 is deprecated.  Use set gfxpayload=1280x1024x16,1280x1024 before linux command instead
```
along with 'press any key to continue.'  It then boots into the GUI normally.

One of the results of ```
sudo hwinfo --monitor
```
was
 ```
 Resolution: 1280x1024@75Hz
```.

I took a look at console-setup, but is the font face TerminusBold actually a different resolution?

What do you think?
Thanks

Update:
After working through this tutorial
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html#.Ty5FiVE3UXc](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html#.Ty5FiVE3UXc)

this prints out after selecting from the boot menu:
```
Error: unknown command 'recordfail'.
```
Other people have had this for a variety of problems with GRUB 2; I haven't found any cases of this relating to setting TTY resolution, in particular.

Another update:
I should mention that I've seen a number of suggestions to move over to an open-source driver like Nouveau, but I can't do this as I rely on support for Nvidia CUDA and the official Nvidia drivers.

---

### Post by MAFoElffen on 2012-02-05
> **The Bird Man of Alcatraz said:**
> Thanks for the detailed response.  I restored both files to their original settings and then tried your suggestion with /etc/default/grub, but when booting up this shows up--
```
vga=794 is deprecated.  Use set gfxpayload=1280x1024x16,1280x1024 before linux command instead
```along with 'press any key to continue.'  It then boots into the GUI normally.

One of the results of ```
sudo hwinfo --monitor
```was
 ```
 Resolution: 1280x1024@75Hz
```.

I took a look at console-setup, but is the font face TerminusBold actually a different resolution?

What do you think?
Thanks

Update:
After working through this tutorial
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html#.Ty5FiVE3UXc](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html#.Ty5FiVE3UXc)

this prints out after selecting from the boot menu:
```
Error: unknown command 'recordfail'.
```Other people have had this for a variety of problems with GRUB 2; I haven't found any cases of this relating to setting TTY resolution, in particular.

Another update:
I should mention that I've seen a number of suggestions to move over to an open-source driver like Nouveau, but I can't do this as I rely on support for Nvidia CUDA and the official Nvidia drivers.
1. I set both the "vga" switch and the GRUB_GFXMODE, which sets GRUB_GFXPAYLOAD_LINUX in the 00_header section before GRUB_CMDLINE_LINUX_DEFAULT hits with the vga switch...
 - a.) What did you modify in /etc/grub.d/00_header?
 - b.) My experience with the error's suggestion to you, is that message is wrong.  Experience of my trials and errors showed me that a "resolution" is not a valid value for gfxpayload. If I do "set gfxpayload=1280x1024" it errors and gets ignored. a valid value for gfxpayload is "keep"...
 - c.) The 3.x kernels still take vga=xxx and a valid parameter and value. The "ask" value was deprecated, but as far as I know, all other valid VESA Linux mode numbers are still valid.

2. recordfail is a generic Grub2 error that is usually either an invalid value or a syntax error.  recheck your /etc/default/grub or your /etc/grub.d/00_default.
 - a.) I don't know what you modified in 00_header, so...

3. "Terminus" is a fixed width console font. "Terminus Bold" is another fixed width console font... They are not "resolutions." If that is the font, it's point size can be changed in /etc/default/console-setup (Font and background colors can be echoed to the session thru escape codes)

4. Nouveau resolution, quality and performance is lacking. It does not support CUDA. I personally use the nvidia binaries and the CUDA toolkit.

If you really plan on spending a lot of time in console--> I do (6 personal servers and working on text-only distro) I also use Byobu.  Sort of like a multi-panel, multi-session session/screen manager for console.  

*** I forgot to ask/confirm... You're doing this for tty1-6 right?

---

### Post by The Bird Man of Alcatraz on 2012-02-07
Pardon the late response

Changes in 00_header
```

  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=1280x1024x16,1280x1024

```
I think you're exactly right about the error message.  Should I leave ```
set gfxmode = ${GRUB_GFXMODE}
``` as is?  The other, I'll change to 'keep.'

> 3. "Terminus" is a fixed width console font. 
Ah, I'm not going to change this then until the resolution is higher.

>  It does not support CUDA.
Good to know

I'll look into Byobu; so far, I've been using Screen.  Figured out the vertical split recently, which has come in handy.

TTY 1-6?  Changing the resolution for all would be great.

Thanks a bunch

---

### Post by MAFoElffen on 2012-02-08
> **The Bird Man of Alcatraz said:**
> Pardon the late response

Changes in 00_header
```

  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=1280x1024x16,1280x1024

```I think you're exactly right about the error message.  Should I leave ```
set gfxmode = ${GRUB_GFXMODE}
``` as is?  The other, I'll change to 'keep.'


Ah, I'm not going to change this then until the resolution is higher.


Good to know

I'll look into Byobu; so far, I've been using Screen.  Figured out the vertical split recently, which has come in handy.

TTY 1-6?  Changing the resolution for all would be great.

Thanks a bunch
From look at things, sounds good to me...

---

### Post by The Bird Man of Alcatraz on 2012-02-09
I get ```
error: unknown command 'recordfail'
``` after selecting the kernel from the GRUB menu.

I'm trying to roll everything back, now.  I've also run grub-update after each change.  It still boots, after hitting any key.

There's a particular function in 00_header that causes the GRUB timeout to deactivate if there is a 'recordfail.'  I could just comment it out, but that wouldn't fix the 'unknown command.'

---

Update:
Must have messed this up pretty well.

I've also tried ```
sudo grub-install
```

---

### Post by MAFoElffen on 2012-02-10
> **The Bird Man of Alcatraz said:**
> I get ```
error: unknown command 'recordfail'
``` after selecting the kernel from the GRUB menu.

I'm trying to roll everything back, now.  I've also run grub-update after each change.  It still boots, after hitting any key.

There's a particular function in 00_header that causes the GRUB timeout to deactivate if there is a 'recordfail.'  I could just comment it out, but that wouldn't fix the 'unknown command.'

---

Update:
Must have messed this up pretty well.

I've also tried ```
sudo grub-install
```
Please post your /etc/default/grub and /etc/grub.d/00_header files and maybe a fresh set of eyes can help?

---

### Post by The Bird Man of Alcatraz on 2012-02-11
I'd appreciate that.
I've added txt extensions so the attachment uploader will accept them.

---

### Post by MAFoElffen on 2012-02-11
> **The Bird Man of Alcatraz said:**
> I'd appreciate that.
I've added txt extensions so the attachment uploader will accept them.
/etc/default/txt. at the moment is generic.  Everything you tried is commented out so is not in effect.  I'll get back to what you tried in this file a little later...

Your 00_header looks to me... I can see what you were trying to do/which should have been done in /etc/default/grub.  That is the file where the environment variables for grub are set (re: GRUB_GXFMODE)... If you do as you tried, it would only work until the first update of grub... which that file wold then be overwritten, thats why they have the /etc/default/grub file.  Even if you change that line back, that 00_header file seems hosed to me.  It's missing a line 2 in the executable section, other lines from functions and whole functions are just missing... ??? One of which of what you needed to do what you wanted, function load_video().

You said you installed grub again, but if you didn't purge it before a reinstall, the old stuff is still there because it thinks it already has the latest version installed. 

*** So if you removed/purged grub, reinstalled grub fresh and clean... Look at section #12 of DRS305's tutorial:
 [GRUB2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

Then use your vga switch (vga=0x31a) and reset GRUB_GFXMODE=1280x1024x16, both in /etc/default/grub... That should correct and clean up the problems in your scripts.  Then those variables should get passed cleanly to the 00_header script. If all goes well there, then the linux_gfx_mode should be set to keep on it's own.

You can test this by going to the grub menu, press <c> to get to a GRUB prompt and enter in:
```

echo $linux_gfx_mode

```You shouldn't have to hardcode that.  If it is set to "text" instead, look at the syntax of your edits..

---

### Post by The Bird Man of Alcatraz on 2012-02-12
Fantastic, GRUB works again, now.

One additional thing; CUDA works no longer.  The executables in the CUDA SDK fail to find a CUDA device.  Any ideas?
This only happens when GRUB_CMDLINE_LINUX_DEFAULT is set to "text."  If I boot up into the GUI and hit Ctrl-Alt-F1 to drop into the CLI, CUDA works.

This really isn't necessary to fix; it would only be applicable in a cluster sort of setup, where CUDA enabled servers would have to boot up without keyboards or monitors.
---

Very oddly, I was never able to get 1280x1024x16 working; ```
sudo hwinfo --monitor
``` says that the monitor only accepts that resolution at 75 Hertz.  1024x768x8 works well, now, presumably at 60 Herz.  On a side note, I am running on a digital interface, if that makes any difference.  I think the analog input can accept a wider variety of resolutions.

Thanks so much

---

