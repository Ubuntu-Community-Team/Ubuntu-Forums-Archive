---
title: "Karmic Koala and Mythtv 0.21"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by richard.e.morton on 2009-09-30
Hi,

Mythtv is on the verge of releasing its next major version; it's a favulous use of opensource software and is an incredibly powerful TV system for homes. It's a little complex to setup though.

0.22 will be incompatible with 0.21. Jaunty has 0.21; it is planned that Karmic will only come with 0,22. Most people run in mixed OS environments; most people cant spend the time to upgrade their entire system overnight; it takes a bit of time.

Here's the short question; can we have 0.21 packages on Karmic please? I have got around it; the reasons and method follow... this way at least people can upgrade over a slightly longer period changing OS then changing Myth over a few days or weeks rather than having no TV at all; many of us use Myth as the only TV - we dont even use actual DVDs anymore - we just buy, rip and store-disc.

thanks

Rich

I recently had a problem; I have successfully been using MythDora5 on a SP13000 board. I installed this some time ago but sometime after its release. I used to tend to keep my systems up to date; so even from first use the system was not a off-the-cd installation.

Recently the harddisc was making noises and grub started complaining -
it was time to rethink the system. I wanted it quieter (the hard disc
was the last moving component in the system). I decided to install
onto a USB drive.

I installed MythDora5 off the cds I have floating around, and after
some playing I got it installed but it didn't quite work; despite my
copious notes I couldnt get XvMC to work and it was dead slow to use.

I ended up with MythDora5 as the then as current mythbuntu wouldn't
work with XvMC and this seemed to be supported by other Via users. I
tried a few distros with no luck.

I did a bit of research recently and the issue is fixed in a recent
kernel. I cant remember the kernel version exactly but I think it is
2.6.30 where this is fixed and this is in Karmic.

However Karmic doesn't have Myth.21 packages and wont have. 0.22 is
going into Karmic but 0.22 is not compatible in a
multi-system/multiversion envrionment ( eg backend with 0.21 /
frontend on 0.22).

So I needed the fix in the Kernel which is going into Karmic but there
is no myth 0.21 packages. Further research showed that compiling the
patched kernel for Jaunty was fraught with issues (and no tutorial for
completing the task while a few requests for help still pending).

Before I start with what I did; the setup I am about to describe is
not a supported installation and there will be very few users with
this arrangement. Not only that but I am no Linux expert and what I
have done maybe completely the wrong way to solve my problem...

I installed Karmic Xubuntu Alpha6 on a 4gb usb stick (i used a
standard Xubuntu Karmic installation and partition layout. Once
installed I removed apps that were irrelevant for this systems purpose
or administration; openoffice, gimp etc).

Then I downloaded a few deb files for mythtv from the Jaunty packages
website; I needed 0.21 and went for version: 0.21fixes19961 of
libmyth, mythtv-common and mythtv-frontend for the base system and
appropriate versions (as suggested on the webpage) of Mythmusic,
mythvideo and mythgallery.

gdebi-gtk wouldnt install them and there are reports on the web
regarding this but; but sudo dpkg -i <packagename> works fine.
install libmyth then mythtv-common, then myth-frontend, and finally the plugins.

The installer moaned about some chmod chown actions it wasnt permitted
to complete due to them already being mounted onto the backend at this
point - which was a mistake so at this point you should mount the
backend drives as you would with mythtv frontends normally.

I had to update the /etc/X11/XvMCConfig file to libXvMCVIAPro.so (for
the SP13000 MB). add the myth user into the mythtv group.
restartX/reboot

I then successfully got the mythtv frontend system configured as
standard using slim is typical but i setup a different (purely XvMC)
playback profile to ensure XvMC was used (I hope - otherwise this
little passively cooled system will bake).

My only two issues remaining are
1 getting X to stick to a resolution I want; it keeps detecting on
startup and that (a) 1900x1200 and the display adapter can output - it
pans with mouse movement above 1600x1200; and (b) is the right aspect
ratio for the monitor; I have to set it manually on each start up to
1440x900
2getting rid of the OSD for the volume control in XFCE4.

The system runs Myth at 1440x900 with BBC2 (high bitrate SD DVB-T uk
transmission) playing with Myth using 25-35% cpu.

Boot times of the system are long (minutes) but once running there is
only long delays loading setup modules/pages. All "user" areas of the
system are acceptably responsive - even with our 250+ recorded shows
and preview video.

I hope that explanation helps someone else or it will create a
discussion on more elegant methods.

Rich

---

