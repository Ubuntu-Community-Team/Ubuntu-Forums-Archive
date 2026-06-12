---
title: "My experiences on Ubuntu 10.04 The Lucid Lynx"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Meneer Jansen on 2010-07-15
I'd like to share my experiences on installing the newest version of Ubuntu at the time of writing: ver. 10.04 "The Lucid Lynx". As you will know there are some teething probs. like there is with every thing that is new. ([topic]("http://ubuntuforums.org/showthread.php?t=1469475")).

**Old Nvidia card & Compiz**
Out of the box it don't work. I removed as much Nividia nad Nouveau stuff as possible with Synaptic. I then installed only the Nvidia 96 driver. Simple. 
To get Compiz and Xorg working optimally I added an *"/etc/X11/xorg.conf"* file. Xorg is said to work without one, but that is not true for old and exotic cards.
```

Section "ServerFlags"
  Option       "AllowMouseOpenFail"
EndSection

Section "Module"
  Load         "glx"
  Load         "dbe"
  Load         "v4l"
  Load         "freetype"
  Load         "type1"
  Load         "extmod"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "pc104"
  Option       "XkbRules" "xfree86"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "7"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImExPS/2 Logitech Explorer Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
        Identifier "Monitor[0]"
        ModelName "Generic Monitor"
        Option "DPMS"
        HorizSync 30-70
        VertRefresh 50-160
EndSection


Section "Screen"
  Identifier   "Screen[0]"
  Device       "Device[0]"
  Monitor      "Monitor[0]"
  DefaultDepth 24
  SubSection "Display"
    Depth      24
    Modes      "800x600" "1280x960" "1280x1024" "1280x800" "1152x864" "1280x768" "1024x768" "768x576" "640x480"
    Virtual    1280 960
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "800x600" "1280x960" "1280x1024" "1280x800" "1152x864" "1280x768" "1024x768" "768x576" "640x480"
#Virtual screensize. Beware: physical screen size cannot be larger!
    Virtual    1280 960
  EndSubSection
EndSection

Section "Device"
  Identifier   "Device[0]"
  Option       "NoLogo" "True"
  BoardName    "GeForce2 MX/MX 400"
  BusID        "1:0:0"
  Driver       "nvidia"
  Option       "CIOverlay"
  Option       "usevnc" "no"
  Option       "TVStandard" "PAL"
  Option       "TVOutFormat" "PAL"
  #Option       "NvAGP" "2"
  #Option       "NvAGP" "0"
  #Option       "NvAGP" "3"
  #Option       "NvAGP" "1"
  Screen       0
  VendorName   "NVidia"
# For Compiz-Fusion? Shoud this be in another Section?
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
#For Compiz?
  Option "Composite" "Enable"
EndSection

```
The options that do magic for Compiz are:
```

Section "Device"
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection

```
You may also want to remove your videocard from the black list.

**TV card**
My TV card is based on an saa7134 chip and works fine out of the box in Lucid. However, audio via the PCI bus so it can be captured by Alsa is broken. The saa7134 will not load. (I filed a [bug](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/603536)). I can listen to TV via the jack output.

**Sunbird/Lightning**
I wanted a calendar/schedule in Thunderbird. The "official" pluging on Mozilla's site is supposed to work with Lucids Thunderb. version, but it don't. Luckily our beloved forum had the solution ([topic](http://ubuntuforums.org/showthread.php?t=1463762&highlight=lightning+lucid&page=2) and [download link]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/")).

**GDM2Setup and Ubuntutweak**
These two apps are important if you want to change the way Lucid boots. See this [site]("http://myubuntublog.wordpress.com/2010/05/21/things-to-do-after-installing-lucid-lynx-10-04/") on how to install them. You can edit the loginscreen (GDM) with them too.

**Bloody Plymouth, bootsplash, Grub etc.**
Enough had been said about the all new but not improved way Lucid (and probably other Linuxes) boots. First there is Grub that does not show itself unless it is [forced](http://www.linuxquestions.org/questions/ubuntu-63/no-boot-splash-with-ubuntu-lucid-10-04-lts-805171/) to by editing "**/etc/default/grub**". Then there is Plymouth that takes over the booting process by loading Linux and showing a splash screen that can be turned into a screen in which you see all the important messages fly by. On my computer the screen says black w/ a blinking cursor for quite some time before a graphic bootsplash takes over. Some people have that sort of problem too and a [popular solution]("http://reformedmusings.wordpress.com/2010/05/01/corrupt-bootsplash-fix-in-ubuntu-lucid-10-04-lts/") that did not work for me is:
```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit

```
There are not many nice themes available yet and the ones that do have some color in them do not display well on my PC because they seem to need 24 bit colors, and they do not seem to be available on my PC at boot time (weird!). So I chose "simply line" (a growing progress indicator). I used The Gimp to edit the two pictures it uses to draw the progress indicator. It looks a bit niver now.
Switch Plymouth theme:
```
sudo update-alternatives --config default.plymouth
```
Then:
```
sudo update-initramfs -u
```
After Plymouth, GDM takes over. That one is of new version too so my themes and tweks didn't work anymore. Use above mentioned GDM2Setup and UbuntuTweak to alter GDM's login screen to your liking.

**Turning KMS (kernel mode seting) off**
If your vid.crd. gives you trouble then turning KMS offmay help ([https://wiki.ubuntu.com/CharlieKravetz/TipsAndNotes#Turning](https://wiki.ubuntu.com/CharlieKravetz/TipsAndNotes#Turning) KMS off):
# ATI Radeon:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

# Intel:
echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf

# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

```
update-initramfs -u
```


**Gdesklets**
If you want to use them instead of Cairo-docks screenlets then do the following to fix the [bug]("http://ubuntuforums.org/showthread.php?t=1524976") in it: edit the file "/usr/lib/gdesklets/utils/ErrorFormatter.py"
```

# 09/08/09:per  article=http://forums.opensuse.org/applications/409465-fix-gdesklets.html
#def  _new_imp(name, globs = {}, locls = {}, fromlist = []):
def  _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):

```

**GTK1 apps better look**
I still use some antique GTK1 apps like xmms, Turboprint 1.96 and Xdialog (= graphic dialog boxes via a shell script). But GTK1 look ugly! The Industrial engine and theme from way bach when make it look much, much better! 
I used the following trick: I installed the gtk-engines from Ubuntu ver. 6 'Dapper' (download from the Ubuntu site whil its still there!!). It needs two dependencies from that repo. Libglib1.2 and libgtk1.2. I could install Turboprint 1.96 from a "source" tarball. I compiled the gtk-theme-switcher from source code to use the command "switch" to switch GTK1 theme to Industrial. If the fonts of the Industrial theme are too large then i use the following trick: 
> 
1. Copy, as root, the file /etc/gtk/gtkrc.iso-8859-13 to "/etc/gtk/gtkrc.iso-8859-1". Notice that this file does not exist and the omission of the "3". 

2. Open it and change all references to "13" into "1" (just like you did to for the filenname).

3. Open a GTK1 app (like XMMS, XMGrace etc.) and check. It works!

4., If that still don't work try: set LC_CTYPE and LC_NUMERIC locales to something reasonable in .bashrc ("export LC_CTYPE=C" for example).


---

### Post by Meneer Jansen on 2010-07-16
**Watch DVD's**
Aaargh. It's still only sort of "semi" legal to play DVD's. Still! Bluray has almost made DVD's obsolete and still this legal war. So you'll still have to resort to a little trick to get a good working *libdvd*. See:
[https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)

**XBMC**
I use my PC as a Mediacenter with XBMC. However, since *libcdio* is bugged in version 0.81 (0.80 still worked) is does not let cd's and dvd's pop up properly anymore. [Workaround]("http://forum.xbmc.org/showthread.php?t=77251") in the XBMC forum.

Good Heavens, what a lot of bugs and issues in Lucid!

---

### Post by Meneer Jansen on 2010-07-17
**Play DTS-CD's**
I used to do this w/ XMMs before it depicated. Then in Ubuntu 9 Banshee did the trick and now only Mplayer works. Luckily there's a nice graphical front end to Mplayer in Lucid: gnome-mplayer. To play DTS-CD's you need a soundcard that does NOT upsample 44.1 kHz to 48 kHz and the following Mplayer option (set it in gnome-mplayer):
```

-ao alsa:device=hw=0.2

```
Or on the command line:
```

mplayer -ao alsa:device=hw=0.2 -afm hwac3

```
Note: 
"-ao" means Audio Output
"alsa:" means use Alsa
"hw=0.2" means first physical device (number 0), output number 2 (on my card digital out (AC3 etc.) is number 2, 0 is PCM).

From the mplayer man page:
> 
Play DTS-CD with passthrough:
       mplayer -ac hwdts -rawaudio format=0x2001 -cdrom-device /dev/cdrom cdda://
       You can also use -afm hwac3 instead of -ac hwdts.  Adjust  &#8217;/dev/cdrom&#8217;
       to  match  the CD-ROM device on your system.  If your external receiver
       supports decoding raw DTS streams, you can directly play it via cdda://
       without setting format, hwac3 or hwdts.


---

