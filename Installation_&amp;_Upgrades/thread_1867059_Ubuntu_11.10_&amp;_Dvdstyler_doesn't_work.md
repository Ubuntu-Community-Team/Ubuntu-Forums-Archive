---
title: "Ubuntu 11.10 &amp; Dvdstyler doesn't work"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by kk2en on 2011-10-22
I Updated my pc to Ubuntu 11.10 and now Dvdstyler doesn't work.

Any ideas?

Thanks, Ken

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

ken@ken-K53E:~$ dvdstyler

(dvdstyler:4020): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dvdstyler:4020): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dvdstyler:4020): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dvdstyler:4020): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(dvdstyler:4020): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4020): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4020): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4020): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[mp3 @ 0x9f56320] Header missing
[mpeg4 @ 0xa1d9b40] Invalid and inefficient vfw-avi packed B frames detected
[mp3 @ 0xa22f000] Header missing
[mpeg4 @ 0xa246ee0] Invalid and inefficient vfw-avi packed B frames detected
Output #0, dvd, to '/tmp/dvd-tmp/menu1-0.mpg_bg.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 2 channels, s16, 64 kb/s
[ac3 @ 0xa31b740] Specified sample_fmt is not supported.
Segmentation fault

---

### Post by Rattus Norvegicus on 2011-10-22
I almost get the same error with Unity on 11.10 (dvdstyler 1.8.3), and I have even tested it with a mpeg video wich it succeded in 11.04, just to make sure it wasn't the video that was corrupted:

> (dvdstyler:3534): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3534): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3534): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3534): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[mpeg @ 0xa215b20] max_analyze_duration reached
[mpeg @ 0xa1d5800] max_analyze_duration reached
[mpeg @ 0xa1a1920] max_analyze_duration reached
Output #0, dvd, to '/tmp/dvd-tmp/menu1-0.mpg_bg.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 2 channels, s16, 64 kb/s
[ac3 @ 0xa35e8e0] Specified sample_fmt is not supported.
Segmentation fault

But there is another problem when running dvdstyler in Gnome Shell.
When ever I try to add a button to the menu, the program crashes with this error:

> (dvdstyler:2097): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2097): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2097): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2097): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
Segmentation fault

And if I try to enter the menu properties or even delete the menu, the program crashes with this error:

> (dvdstyler:3573): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3573): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3573): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:3573): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[mpeg @ 0x9388240] max_analyze_duration reached
[mpeg @ 0x90974a0] max_analyze_duration reached
Segmentation fault


I really hope someone has an idea how to fix these serious problems, because dvdstyler is without a doubt the best software to create DVD's in linux.

---

### Post by hantms on 2011-10-23
Just want to add I have the same problem.

> I really hope someone has an idea how to fix these serious problems, 
> because dvdstyler is without a doubt the best software to create DVD's in 
> linux.

Yes. :(

---

### Post by Jimmmac1 on 2011-10-25
Hi all

Has anyone got an answer to this yet?  Has anyone tried to contact the developer? Thanks.

Jim

---

### Post by kk2en on 2011-10-26
It looks like it has been posted at the DVDSTYLER forum.

No answers there either.....


[http://sourceforge.net/projects/dvdstyler/forums/forum/318795/topic/4772017](http://sourceforge.net/projects/dvdstyler/forums/forum/318795/topic/4772017)

---

### Post by TedMerrill on 2011-11-07
dvdstyler as installed as part of Ubuntu 11.10 segfaults soon
after being told to "burn" (actually, while it is building the
files to go on dvd), soon after emitting message to stdout:

Specified sample_fmt is not supported.

I tried downloading from [http://www.dvdstyler.org](http://www.dvdstyler.org) / sourceforge
version 2.0 but it proved difficult to get to compile.
So instead i compiled version 1.8.4.3 after some difficulty.
This works great for my application, which is making dvds from
mpeg video files that are already use dvd-appropriate codecs and settings.

Here are some steps of getting to compile:

Install a whole bunch of packages.
Some of these can be determined by missing files complained about
by "./configure" and a few don't cause obvious problem until "make"
(especially "flex" and "bison").
Sorry i don't have a complete list!
Here are the packages that i downloaded during that period, 
from /var/log/dpkg.log :

dvdisaster
dvdisaster-doc
dvdstyler-data
libwxsvg0
dvdstyler
libxine1-bin
libxine1-misc-plugins
libxine1-x
libxine1-console
libxine1
libxine1-ffmpeg
xine-ui
wx2.8-headers
libwxbase2.8-dev
libwxgtk2.8-dev
libart-2.0-dev
libwxsvg-dev
libgnutlsxx26
libavahi-common-dev
libdbus-1-dev
libavahi-client-dev
libavahi-glib-dev
libidl-dev
liborbit2-dev
libpopt-dev
libbonobo2-dev
libgail-dev
libgnomecanvas2-dev
libcanberra-dev
libgconf2-dev
libgpg-error-dev
libgcrypt11-dev
libtasn1-3-dev
libgnutls-dev
libsepol1-dev
libselinux1-dev
libgnomevfs2-dev
libgnome2-dev
libbonoboui2-dev
libexif-dev
libgnome-keyring-dev
libgnomeui-dev
orbit2
texlive-fonts-recommended
texlive-latex-base
texlive-latex-recommended
texlive
texlive-bibtex-extra
preview-latex-style
texlive-pictures
texlive-latex-extra
texlive-math-extra
texlive-extra-utils
dblatex
gir1.2-gudev-1.0
lacheck
latex-xcolor
pgf
latex-beamer
libudev-dev
libgudev-1.0-dev
libgudev1.0-cil-dev
texlive-generic-recommended
texlive-pstricks
prosper
ps2eps
texlive-font-utils
texlive-fonts-recommended-doc
texlive-latex-base-doc
texlive-latex-extra-doc
texlive-latex-recommended-doc
texlive-pictures-doc
texlive-pstricks-doc
tipa
xmlto
libjpeg62-dev
libgd2-xpm-dev
m4
bison
flex

There may of course be other dependencies to packages that i had
already downloaded previously.

Download wxsvg-1.1.2 from [www.dvdstyler.org](www.dvdstyler.org) and do ./configure && make
&& make install (puts files in /usr/local/lib).
(The one that is part of ubuntu 11.10 is too different!).

Download DVDStyler-1.8.4.3 from [www.dvdstyler.org](www.dvdstyler.org) and make a number
of source code modifications:

Change PKT_FLAG_KEY to AV_PKT_FLAG_KEY in all places used.
Change AVERROR_NUMEXPECTED to AVERROR(EINVAL) in all places used
except see below.
Change FF_COMPLIANCE_INOFFICIAL to FF_COMPLIANCE_UNOFFICIAL in all places.

DVDStyler-1.8.4.3/src/mediaenc_ffmpeg.cpp :
#include <libavcodec/avcodec.h> 

DVDStyler-1.8.4.3/src/mediatrc_ffmpeg.cpp :
#include <libavcodec/avcodec.h> 
Comment out declaration of av_vsrc_buffer_add_frame2()
    and comment out where it is used...  this will probably break something
    but if you're lucky it will be something you aren't using!
In wxFfmpegMediaTranscoder::PrintError(), 
    comment out cases for AVERROR_NUMEXPECTED and AVERROR_NOFMT.
Change 
    big_picture.pict_type = 0;
to
    big_picture.pict_type = (enum AVPictureType)0;

Hope i didn't leave out too much above!
cd to the DVDStyler-1.8.4.3 directory and do
./configure && make && make install

---

### Post by Jimmmac1 on 2011-11-09
Hi Ted

Thanks for the response.  Boy, that is a lot of stuff to do.  Is there a similar to DVD Styler out there that is supported?   Or at least has someone to contact? I also tried installing 2.0 but gave up after a while.  DVD Styler is a nice program to work with, and I was wondering if there is a similar out there that will take it's place.  Unless someone can contact the developer. Thanks.

Jim

---

### Post by theteapatriot on 2011-11-16
> **Jimmmac1 said:**
> Hi Ted

Thanks for the response.  Boy, that is a lot of stuff to do.  Is there a similar to DVD Styler out there that is supported?   Or at least has someone to contact? I also tried installing 2.0 but gave up after a while.  DVD Styler is a nice program to work with, and I was wondering if there is a similar out there that will take it's place.  Unless someone can contact the developer. Thanks.

Jim
I dual boot. Had to install it on Win 7 (exe avail. at sourceforge dvdstyler page). Sucks I had almost stopped using Win. Now it will be the other way around, as this is what I use most. I hate supporting the eugenicist Bill Gates. I pass out educational movies, for free to those who do not have the internet.

---

### Post by voodoostevie on 2011-11-21
I am not getting the segmentation faults and other errors (most likely because there was an update added to the ubuntu repos not too long ago).

What is happening with my install of DVDStyler is I will get the project set to write to ISO only with no preview and start it. The encoding process hangs and the program basically locks up so you can't cancel unless you force-quit. 

I noticed there was some issues with melt libraries for KDEnlive (which is what I use for video editing) which they recommended trying the Sunab PPA (ppa:sunab/kdenlive-release) seen [here]("http://www.kdenlive.org/forum/ubuntu-1110-wont-run-kdenlive-mlts-sdl-module-not-found"). This fixed a MLT issue I was having with KDEnlive however DVDStyler is still hanging during the transcribe/encoding process.

---

### Post by Rattus Norvegicus on 2011-11-30
I just got tired of waiting for a solution to this bug, so tonight I went back to Natty, and DVDStyler worked again.

But after I installed Gnome Shell on Natty, DVDStyler crashes again with the same error as in Oneiric :(

So now I have to choose between the usage of DVDStyler or Gnome Shell... but I want both :(

---

### Post by gordintoronto on 2011-11-30
It might not have as many features, but devede is an alternative. Spend a few minutes in the help text before you get carried away.

devede makes an ISO, then you can use Brasero to actually burn the DVD.

---

### Post by Rattus Norvegicus on 2011-12-02
I reinstalled 11.10 again plus Gnome Shell, and now DVDStyler only crashes when I try to add menu button, edit the menu or add movies.
But creating iso-files works on old projects.

Then I tried to log into Gnome Classic and EVERYTHING works i DVDStyler there, so it seems like it is only in Gnome 3 there is a problem with DVDstyler.

---

### Post by satanselbow on 2011-12-02
May or may not be related but replacing the repo version of ffmpeg (with the latest pulled from git) fixed segmentation faults in winFF and dvdstyler for me under gnome-shell ;)

---

### Post by LewisTM on 2011-12-19
Works fine under Xubuntu 11.10. I ran into a dvdauthor error while building the DVD structure but fixed it by changing the launcher command to
```
env VIDEO_FORMAT=NTSC dvdstyler
```
Of course change to PAL if you have a European DVD player

---

### Post by LewisTM on 2011-12-21
> **LewisTM said:**
> Works fine under Xubuntu 11.10. I ran into a dvdauthor error while building the DVD structure but fixed it by changing the launcher command to
```
env VIDEO_FORMAT=NTSC dvdstyler
```
Of course change to PAL if you have a European DVD player
Ah well that was a bit premature.

It works well for short clips. I did experience crashing with a typical sized movie.

Seems like the problem stems from transcoding. I can see that as it progresses, DVD Styler's memory usage increases slowly, perfectly following the size of the transcoded .vob file and reaching several Gigs. It eventually gets killed by Linux for being to fat.

I could feed it predigested mpeg2/AC3 files but that would defeat the purpose of the software.

---

