---
title: "Can't Play DVDs"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by adds2one on 2006-08-27
Hello,

In the last month I have installed Ubuntu on my Dell laptop and on my Dell desktop. I also used Automatix and installed all the support for non-free DVD  codecs and other multimedia codecs. 

I can play DVDs no problem on my laptop but when I try to play DVDs on the desktop, whatever player I try to use starts to open and then closes right away. I have tried to play DVDs with movie player and mplayer and experience the same thing. 

I am at a loss as to how to trouble shoot this and have had no luck with google.

Anyone have some advice for me. Watching DVDs on my desktop is key to having Ubuntu on this machine.

Thanks

---

### Post by adds2one on 2006-08-27
I ran Totem from the command line and tried to open a DVD (several actually, some originals and some copies) and this is the output I get in the terminal:

```
(totem:15195): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(totem:15195): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)
libdvdnav: Using dvdnav version 1.1.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdd mounted on /media/cdrom-1 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/fiona/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000129
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000313e
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 97 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

Here is the relevant line from /etc/mtab

```
/dev/hdd /media/cdrom-1 udf ro,nosuid,nodev,uid=1000,gid=1000,umask=007,iocharset=utf8 0 0

```

and there is no mention of /dev/hdd in /etc/fstab

Is it just that this drive isn't mounted?

Please help!

---

### Post by adds2one on 2006-08-28
This is the error output I get when I try to use mplayer:

```
91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000129
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000313e
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 3.0 (3f)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

```

Can anyone help me?

---

