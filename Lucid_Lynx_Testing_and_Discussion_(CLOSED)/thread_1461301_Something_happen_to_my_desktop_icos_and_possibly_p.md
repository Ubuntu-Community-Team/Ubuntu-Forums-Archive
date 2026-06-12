---
title: "Something happen to my desktop icos and possibly plymoute"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-24
when i turn off my computer last night (where i am is 9:26 am) i noticed that the ubuntu logo of Plymouth have grown substantially  i thought it might be just a resolution problem 
but when i turned on the computer now i saw that the icons on desktop are huge how can i fix it?

i have attached a picture my screen resolution is 1920x1080 but changing it did fixed the icons size nor does changing a theme.

---

### Post by aviramof on 2010-04-24
if ubuntu would have recognize my motorolve v3x phone i would have shown you Plymouth logo he's hugh like size 40 i think something made it grow like this i thought maybe it's the dev version of google chrome i installed last night because it shortcut disappeared from application-internet show i removed it but it didn't fixed the problem.

---

### Post by aviramof on 2010-04-24
Pictures of Plymoute logo:

---

### Post by MacUntu on 2010-04-24
I see nothing wrong here.

---

### Post by aviramof on 2010-04-24
Can't you see that the ubuntu logo is hugh?
 
it was much smaller in the past.

---

### Post by BrokeMahPC on 2010-04-24
Difficult to tell with such a close up photo - could we see it with the whole monitor included too? Also try to keep your hand still when taking the photo - that image is blurred and streaky.

---

### Post by BrokeMahPC on 2010-04-24
Here's my Plymouth - 22" monitor

---

### Post by aviramof on 2010-04-24
Now Plymouth logo has stopped appearing at all all i see is the purple screen.

But take a look at the circles at my previous pictures there much bigger then they should be and so is the text.

i have installed now all Plymouth themes including reinstalling ubuntu-logo will see how it goes.

is there a way to check it without restart?

UPDATE:
i restarted and i still can't see ubuntu logo only empty purple screen and i don't want to try other themes right now because i might not be able to enter ubuntu later.

---

### Post by BrokeMahPC on 2010-04-24
Could we have photos of the whole screen including the monitor?

---

### Post by aviramof on 2010-04-24
it would have been easier if ubuntu would have recognize my Motorola v3x or what ever phone in order to give you a picture i need to enter windows but i don't think that a picture would help it's just an empty purple background.

---

### Post by BrokeMahPC on 2010-04-24
Well going into windows will only take you a few minutes - I'm sure you can get us a picture - even if it's just the purple screen it would be useful. Can we also have one of plymouth on shutdown? But we need to see the whole monitor.

---

### Post by aviramof on 2010-04-24
i did what i can but it's not easy to capture 24 inch screen with phone camera.
 
it's the same in boot and restart.

---

### Post by Kirk M on 2010-04-24
> **BrokeMahPC said:**
> Difficult to tell with such a close up photo - could we see it with the whole monitor included too? Also try to keep your hand still when taking the photo - that image is blurred and streaky.

I believe what you're seeing in the images is pretty much what aviramof is seeing minus the streaking as the Plymouth loading screen is the same size on my PC as is shown in aviramof's images (19" wide screen). In my case the problem lies with using the proprietary Nvidia driver (190.* but same with 185.* and 173). Using the new default Nouveau driver the Plymouth loading splash screen is much smaller and much sharper and the background is an even reddish purple.

I've also found that when using a proprietary video driver Plymouth will render differently with each boot (and shutdown). Sometimes there's nothing but a green flash, a bit of purple background and then the login screen. Other times there will be a 1 to 2 sec flash of the (huge-ish) Plymouth loading screen and then  the login, etc, etc. By what I've been reading, Plymouth is still not working correctly when using proprietary video drivers. This doesn't explain the enlarged desktop icons though

aviramof - Did you happen to change video drivers recently?

---

### Post by aviramof on 2010-04-24
no i did not i formated last night and installed the latest fglrx driver from jockey that was
released i think yesterday version 2:8.723.1-ubuntu3  before that there was  2:8.723.1-ubuntu2 and that it.

Here is some history from synaptic of the hours prior to thr shutting down the computer last night when i first noticed that there is a problem and in fact this is all the history up to that point because as i said i just formated 

```

Commit Log for Fri Apr 23 22:43:44 2010


updated:
acpi-support (0.134) to 0.136
base-files (5.0.0ubuntu18) to 5.0.0ubuntu20
bcmwl-modaliases (5.60.48.36+bdcom-0ubuntu2) to 5.60.48.36+bdcom-0ubuntu3
busybox-initramfs (1:1.13.3-1ubuntu10) to 1:1.13.3-1ubuntu11
busybox-static (1:1.13.3-1ubuntu10) to 1:1.13.3-1ubuntu11
desktopcouch (0.6.4-0ubuntu2) to 0.6.4-0ubuntu3
fglrx-modaliases (2:8.723.1-0ubuntu2) to 2:8.723.1-0ubuntu3
firefox (3.6.3+nobinonly-0ubuntu3) to 3.6.3+nobinonly-0ubuntu4
firefox-branding (3.6.3+nobinonly-0ubuntu3) to 3.6.3+nobinonly-0ubuntu4
firefox-gnome-support (3.6.3+nobinonly-0ubuntu3) to 3.6.3+nobinonly-0ubuntu4
gnome-keyring (2.92.92.is.2.30.0-0ubuntu2) to 2.92.92.is.2.30.0-0ubuntu3
gtk2-engines-murrine (0.90.3+git20100323-0ubuntu2) to 0.90.3+git20100323-0ubuntu3
hdparm (9.15-1ubuntu8) to 9.15-1ubuntu9
hunspell-en-ca (1:3.2.0-2ubuntu2) to 1:3.2.0-3ubuntu2
indicator-application (0.0.19-0ubuntu3) to 0.0.19-0ubuntu4
initramfs-tools (0.92bubuntu74) to 0.92bubuntu76
initramfs-tools-bin (0.92bubuntu74) to 0.92bubuntu76
language-pack-en (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-en-base (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-gnome-en (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-gnome-en-base (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-gnome-he (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-gnome-he-base (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-he (1:10.04+20100413.1) to 1:10.04+20100421
language-pack-he-base (1:10.04+20100413.1) to 1:10.04+20100421
language-selector (0.5.6) to 0.5.7
language-selector-common (0.5.6) to 0.5.7
launchpad-integration (0.1.34) to 0.1.35
libappindicator0 (0.0.19-0ubuntu3) to 0.0.19-0ubuntu4
libc-bin (2.11.1-0ubuntu6) to 2.11.1-0ubuntu7
libc-dev-bin (2.11.1-0ubuntu6) to 2.11.1-0ubuntu7
libc6 (2.11.1-0ubuntu6) to 2.11.1-0ubuntu7
libc6-dev (2.11.1-0ubuntu6) to 2.11.1-0ubuntu7
libc6-i686 (2.11.1-0ubuntu6) to 2.11.1-0ubuntu7
libgcr0 (2.92.92.is.2.30.0-0ubuntu2) to 2.92.92.is.2.30.0-0ubuntu3
libglib2.0-0 (2.24.0-0ubuntu2) to 2.24.0-0ubuntu4
libglib2.0-data (2.24.0-0ubuntu2) to 2.24.0-0ubuntu4
libgp11-0 (2.92.92.is.2.30.0-0ubuntu2) to 2.92.92.is.2.30.0-0ubuntu3
libgphoto2-2 (2.4.8-0ubuntu1) to 2.4.8-0ubuntu2
libgphoto2-port0 (2.4.8-0ubuntu1) to 2.4.8-0ubuntu2
libgtk2-perl (1:1.221-4ubuntu1) to 1:1.221-4ubuntu2
liblaunchpad-integration1 (0.1.34) to 0.1.35
liblaunchpad-integration1.0-cil (0.1.34) to 0.1.35
liblpint-bonobo0 (0.1.34) to 0.1.35
libmono-cairo2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-corlib2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-data-tds2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-i18n-west2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-posix2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-security2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-sharpzip2.84-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-sqlite2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-system-data2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-system-runtime2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-system-web2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono-system2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libmono2.0-cil (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
libpam-gnome-keyring (2.92.92.is.2.30.0-0ubuntu2) to 2.92.92.is.2.30.0-0ubuntu3
libparted0debian1 (2.2-5ubuntu4) to 2.2-5ubuntu5
libperl5.10 (5.10.1-8ubuntu1) to 5.10.1-8ubuntu2
mono-2.0-gac (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
mono-gac (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
mono-runtime (2.4.4~svn151842-1ubuntu3) to 2.4.4~svn151842-1ubuntu4
myspell-en-gb (1:3.2.0-2ubuntu2) to 1:3.2.0-3ubuntu2
myspell-en-za (1:3.2.0-2ubuntu2) to 1:3.2.0-3ubuntu2
nvidia-96-modaliases (96.43.14-0ubuntu13) to 96.43.17-0ubuntu1
parted (2.2-5ubuntu4) to 2.2-5ubuntu5
perl (5.10.1-8ubuntu1) to 5.10.1-8ubuntu2
perl-base (5.10.1-8ubuntu1) to 5.10.1-8ubuntu2
perl-modules (5.10.1-8ubuntu1) to 5.10.1-8ubuntu2
python-appindicator (0.0.19-0ubuntu3) to 0.0.19-0ubuntu4
python-desktopcouch (0.6.4-0ubuntu2) to 0.6.4-0ubuntu3
python-desktopcouch-records (0.6.4-0ubuntu2) to 0.6.4-0ubuntu3
python-launchpad-integration (0.1.34) to 0.1.35
python-pyinotify (0.8.9-1ubuntu1) to 0.8.9-1ubuntu2
python-ubuntuone-client (1.2.0-0ubuntu1) to 1.2.1-0ubuntu1
tzdata (2010h-1) to 2010i-1
tzdata-java (2010h-1) to 2010i-1
ubuntu-mono (0.0.17) to 0.0.18
ubuntuone-client (1.2.0-0ubuntu1) to 1.2.1-0ubuntu1
ubuntuone-client-gnome (1.2.0-0ubuntu1) to 1.2.1-0ubuntu1
xfonts-mathml (4) to 4ubuntu1
xserver-common (2:1.7.6-2ubuntu5) to 2:1.7.6-2ubuntu7
xserver-xorg-core (2:1.7.6-2ubuntu5) to 2:1.7.6-2ubuntu7
xserver-xorg-input-vmmouse (1:12.6.5-4ubuntu1) to 1:12.6.5-4ubuntu2
xserver-xorg-input-wacom (1:0.10.5-0ubuntu2) to 1:0.10.5-0ubuntu4
xserver-xorg-video-geode (2.11.7-3) to 2.11.8-4

Commit Log for Fri Apr 23 23:50:50 2010

installed:
nautilus-wallpaper (0.1-0ubuntu3)

Commit Log for Fri Apr 23 23:56:53 2010

updated:
mplayer (2:1.0~rc3+svn20090426-1ubuntu16) to 2:1.0~rc3+svn20100416-0lucid3
smplayer (0.6.8-2) to 0.6.9-1~lucid1

installed:
libdirac-decoder0 (1.0.2-2)
libggi-target-x (1:2.2.2-5ubuntu1)
libggi2 (1:2.2.2-5ubuntu1)
libgii1 (1:1.0.2-4)
libgii1-target-x (1:1.0.2-4)
libvdpau1 (0.3-2build1)
mplayer-skins (3)

Commit Log for Sat Apr 24 00:04:59 2010

completly removed:
gwibber
gwibber-service

Commit Log for Sat Apr 24 00:11:48 2010

installed:
transmission (1.92-0ubuntu2)
transmission-cli (1.92-0ubuntu2)

Commit Log for Sat Apr 24 00:14:10 2010

installed:
linuxdcpp (1.0.3-1)

Commit Log for Sat Apr 24 00:16:37 2010


updated:
empathy (2.30.0.1-0ubuntu3) to 2.30.0.1-1+ppa10.4+1
empathy-common (2.30.0.1-0ubuntu3) to 2.30.0.1-1+ppa10.4+1
libtelepathy-glib0 (0.10.1-1) to 0.11.2-1~ppa10.4+1
libvlc2 (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
libvlccore2 (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
linuxdcpp (1.0.3-1) to 1.1.0-0ubuntu1~bzr362~lucid1
nautilus-sendto-empathy (2.30.0.1-0ubuntu3) to 2.30.0.1-1+ppa10.4+1
skype (2.1.0.81-1) to 2.1.0.81-1
ubuntu-tweak (0.5.3-1~karmic1) to 0.5.4-0~20100423~lucid1
vlc (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
vlc-data (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
vlc-nox (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
vlc-plugin-pulse (1.0.5-2ubuntu3) to 1.1.0+svn20100331-git8b61de2~webupd8~lucid4
x264 (2:0.85.1448+git1a6d32-4) to 2:0.92.1510+svn20100331-git33d382a~webupd8~lucid1

installed:
geoclue (0.12.0-1~ppa10.04+1)
geoclue-hostip (0.12.0-1~ppa10.04+1)
geoclue-localnet (0.12.0-1~ppa10.04+1)
geoclue-manual (0.12.0-1~ppa10.04+1)
geoclue-yahoo (0.12.0-1~ppa10.04+1)
libchamplain-0.4-0 (0.4.3-1ubuntu1)
libchamplain-gtk-0.4-0 (0.4.3-1ubuntu1)
libgeoclue0 (0.12.0-1~ppa10.04+1)
libx264-83 (2:0.92.1510+svn20100331-git33d382a~webupd8~lucid1)
libxcb-shm0 (1.5-2)
libxcb-xv0 (1.5-2)

Commit Log for Sat Apr 24 01:13:01 2010


updated:
transmission (1.92-0ubuntu2) to 1.92+r10515-0ubuntu0~lucid
transmission-cli (1.92-0ubuntu2) to 1.92+r10515-0ubuntu0~lucid
transmission-common (1.92-0ubuntu2) to 1.92+r10515-0ubuntu0~lucid
transmission-gtk (1.92-0ubuntu2) to 1.92+r10515-0ubuntu0~lucid

Commit Log for Sat Apr 24 02:20:11 2010

installed:
pppstatus (0.4.2-10)

Commit Log for Sat Apr 24 02:21:19 2010

installed:
pppoe (3.8-3)

Commit Log for Sat Apr 24 02:21:52 2010

completly removed:
pppstatus


```and that it at that point i restarted and notice the Hugh Plymouth logo and the next morning the problem with the desktop icons you tell me what you think here could have caused this problem.

thanks in advance.

---

### Post by 4Orbs on 2010-04-24
Something you may want to try. Open the nvidia settings manager as root (gksudo nvidia-settings) and set both the resolution and refresh rate to auto. Click the button at the bottom to save settings to /etc/X11/xorg.conf then reboot. For me on Xubuntu, this reduced the size of the logo at bootup, but not at shutdown.

---

### Post by aviramof on 2010-04-24
gksudo nvidia-settings doesn't open nothing here i have an ati card maybe that is the reason.

---

### Post by nystire on 2010-04-24
You should be able to do the same thing from the ATI control panel.

---

### Post by aviramof on 2010-04-24
the problem with the logo has change many comments ago.

the logo is no longer big he simply doesn't exist anymore now.

---

### Post by 4Orbs on 2010-04-24
Have you activated the driver for your ATI card (if there is one available) in System>Hardware Drivers?

EDIT: Please disregard this, I see that you have activated it.

---

