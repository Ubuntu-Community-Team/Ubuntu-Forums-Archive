---
title: "Screen brightness acting crazy on RC."
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by francsal on 2009-10-24
I´m not so sure if this is an issue specific to the RC but I just find it out. Whenever I try to adjust the brightness of my screen (MSI U120, running Kubuntu, but problem manifest itself on GNOME, too) it goes crazy, and it keeps "adjusting" itself (changing the brightness constantly, without any input from me). Also, the problem seems to happen whenever I try to manually adjust the brightness of whenever I unplug the AC cord and start running on batteries. Also, it doesn´t alway recognize when the AC cord is plugged or unplugged....

Any ideas?

Thanks in advance.

Frank.

EDIT: My PC uses an Intel 950 graphics card. I tried unchecking the "Let PowerDevil manage screen powersaving" but it still acts like crazy, changing the brightness non stop, up an down....

---

### Post by happyhamster on 2009-10-24
Yes, there are a zillion brightness bugs open at the moment it seems. For me, everything works sort of fine until xserver-xorg-video-intel 2:2.9.0-1ubuntu1. Downgrading to 2:2.8.1-1ubuntu3 makes the brightness applet and such work normally. This is on a laptop with GM45 video though.

You don't have the same card, but if you want to test, download the 2:2.8.1-1ubuntu3 driver from here:
[https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel/+builds](https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel/+builds)
Make sure you get the right one for your archictecture (i386 or AMD64), and you won't need the dbg package. In a terminal, navigate to where the driver was downloaded, and install like this:

sudo dpkg -i drivername

Next, restart the xserver by pressing ctrl-alt-backspace (if enabled*) or by rebooting. In case you decide you want this older driver version to remain installed, then you have to tell Synaptic to lock that package (else update-manager will keep telling you to update it). Go to System-->Administration-->Synaptic Package Manager and search for the driver. Select it, and click the Package menu option at the top of the page. Tick the "Lock version" option. Done.
If you want to upgrade the driver, untick the "Lock version" option, and let update manager do its stuff, or run "sudo apt-get update && sudo apt-get upgrade".

More info:
[https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel](https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel)

BTW, the current driver also appears to work fine with a 2.6.32 kernel (again, at least it does on my laptop).

Good luck.


* to enable the old keyboard shortcut to kill the xserver, go to System-->Preferences-->Keyboard-->Layouts-->Layout Options-->Key sequence to kill the X server.

---

### Post by Zorael on 2009-10-24
gnome-power-manager needs to be patched to listen to the HAL property laptop_panel.brightness_in_hardware. The repos have a fixed powerdevil (for KDE) as of yesterday or so, but you still need to add a HAL fdi rule to make that property be true for your screen. The necessary hal package (hal-info) has't been updated yet, and probably won't before release (according to debfx on #kubuntu-devel). The fix is very preliminary.

To be added to /usr/share/hal/fdi/information/10freedesktop (before </device> </deviceinfo>);
```
    <match key="info.category" string="laptop_panel">
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix_ncase="micro-star">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="U100;U-100">
          <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
        </match>
      </match>
    </match>
```
After a reboot, the following command should output the following;
```
$ lshal | grep brightness
  laptop_panel.brightness_in_hardware = true  (bool)
```
Then you need version 4:4.3.2-0ubuntu6 or later of kdebase-workspace (current version at time of writing is -0ubuntu7).

That works for a U100, you may need to change the fdi match line to say **contains_outof="U120;U-120"** for a U120. Perhaps another identifier needs to be used, if all Wind models experience the same issue.


On a similar note, can your screen dpms suspend/standby/off? As in, sleep? Mine just wakens immediately, and I believe it's a related issue. The following command should make the screen sleep for 5 seconds.
```
$ xset dpms force off; sleep 5; xset dpms force on
```
Chime in if it doesn't for you either.

---

### Post by francsal on 2009-10-25
Thank you both for the extremely detailed tips!!! Unfortunately, neither fixed the problem. I sort of "fixed" it by disabling the keyboard based shortcuts to modify the brightness (Fn-F4 and Fn-F5). Obviously, now if I want to modify the brightness, I have to do it via the power management icon.

Thanks, again!!

Cheers!

Frank.

---

