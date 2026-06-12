---
title: "Wacom tablets in Ubuntu guide/howto"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Loïc2 on 2008-10-20
I've updated the [Community wiki documentation]("https://help.ubuntu.com/community/Wacom") and [the example xorg.conf files]("https://help.ubuntu.com/community/WacomTroubleshooting") for Ubuntu 8.10 Intrepid Ibex, but the guide is also geared towards each Ubuntu release starting with Ubuntu 6.04 Dapper Drake.

This thread is the forum side of the wiki, if you have questions or want to add information to the guide but are not sure you'll be able to keep it clean and simple.

Basically for any Ubuntu release, always check first on [The Linux Wacom Project]("http://linuxwacom.sourceforge.net/") if the version of the linux wacom driver you have in your distribution  supports your model of tablet - use System>Administration>Synaptic Package Manager or ```
dpkg -p wacom-tools  | grep Version
```
If it supports it, on releases older than Ubuntu 8.10, you only need to edit your /etc/X11/xorg.conf as in the wiki - you save time and run less risks to mess up your configuration. If it doesn't support your model and you can't upgrade to a more recent version, use the "Specific cases" part of the guide (many different contributors).

In Ubuntu 8.10 Intrepid Ibex, due to changes in Xorg, old methods aren't enough. Basically, if you can do with using only the stylus (you'll get pressure support and tilt, plus the side buttons in Gimp), a simple file copy is needed. Else, you need to add lines in /etc/X11/xorg.conf following [these example files]("https://help.ubuntu.com/community/WacomTroubleshooting"). However, with the move away from using xorg.conf, it's becoming harder not to hose X (unless you reuse an old xorg.conf and try just adding the ["AutoAddDevices" "False" Option]("https://help.ubuntu.com/community/WacomTroubleshooting").

In Ubuntu 9.04, the first solution will hopefully allow the use of all the input devices (since it's the direction Xorg is headed to).

[COLOR="Blue"]In your posts, please specify the model of your Wacom tablet, and the Ubuntu version you're using. And if you feel like being really nice, say if the wacom driver version you have on your system is supposed to support your model of tablet ;)[/COLOR]

---

### Post by mesilliac on 2008-10-25
Thanks for the info :). One useful thing I found is that in the default setup (hotplugging but no eraser) you can set the options for the wacom driver by creating a custom .fdi file and copying it to /etc/hal/fdi/policy/. Here's mine as an example, setting the TPCButton and KeepShape options to "on".

/etc/hal/fdi/policy/mytabletrules.fdi
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_options.TPCButton" type="string">on</merge>
	<merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by oldsoundguy on 2008-10-25
I have My Intuios 3 working fairly well in Gutsy, but has anyone been able to get the actual airbrush tool to work?  Rather than using brushes would prefer to use the tool itself if at all possible.

(still does not work as well as in Windows on Photo Shop, but that could be an issue with GIMP in Linux and not Wacom.)

---

### Post by MacUntu on 2008-10-25
I don't have a file /usr/share/doc/xserver-xorg-input-wacom/10-wacom.fdi and my tablet (Bamboo) works like it should after copying that file (stylus + hotplug) out of the box.

---

### Post by mesilliac on 2008-10-25
Looks like the 10-wacom.fdi file is enabled by default now, so the file copy is no longer necessary :)

@oldsoundguy:
I'm not sure how to get a more realistic airbrush effect, but when I use the airbrush tool in GIMP I normally select a fuzzy brush and turn the opacity and rate way down.

---

### Post by twisted_steel on 2008-10-25
My fdi file is located in /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi.  I didn't see this thread before I set up my tablet, which didn't do anything after install.  I just modified my xorg.conf file to make it look like I had it configured during Hardy.

Here is my modified xorg.conf.  Don't mind my settings for getting dual monitors to work with xrandr.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "ButtonsOnly"   "on"
        Option          "USB"           "on"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection      "Display"
                Virtual 3360 1050       # 1680 x 2 = 3360
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "pad"           "SendCoreEvents"
EndSection
```

Interestingly enough, having the Wacom tablet plugged in during the RC install caused it to crash X before the installation could finish.  I had to leave it unplugged so I could finish.  I have a Graphire 4 (USB).

Here is the bug in case anyone comes across this post: [link]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/288991")

---

### Post by oldsoundguy on 2008-10-25
> **mesilliac said:**
> 

@oldsoundguy:
I'm not sure how to get a more realistic airbrush effect, but when I use the airbrush tool in GIMP I normally select a fuzzy brush and turn the opacity and rate way down.

That is what I am using now .. a brush effect in GIMP.

A very good friend gave me the actual airbrush tool for Wacom as a gift a while back, and I found it really neat to use in Photo Shop on Windows.  Just would like to see it migrate to Linux in the near future.  Granted, not much demand as it is an expensive little bugger and most do not have it.  But still and all, would be nice to have EVERYTHING Wacom work in Linux.
(but not the end of the world if it does not work right now as I can switch between computers if I really want to use the airbrush)

---

### Post by mesilliac on 2008-10-29
I just edited the wiki - most wacom tablets should work out-of-the-box in ubuntu 8.10 now, although only the stylus will work (i.e. not the eraser, mouse or pad buttons) without manually editing xorg.conf.

---

