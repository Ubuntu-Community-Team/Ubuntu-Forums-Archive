---
title: "Mouse does not work in Hardy / 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by zannyo on 2008-04-26
After upgrading to Hardy/8.04, the mouse now no longer works.  The cursor is sitting in the middle of the desktop screen and does not move.  The mouse is a two-button wheel mouse that plugs in.  The relevant section of our /etc/X11/xorg.conf file reads:

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/mouse"
Option "ZAxisMapping" "4 5 7 8"
Option "Emulate3Buttons" "no"
Option "Buttons" "3"
EndSection

In order to get the X server to start in the first place, we had to fix a problem with the nvidia drivers by installing nvidia-xconfig and changing the entry in the xorg.conf file from nvidia to nv.  

Thank you for your help.

---

### Post by Dr_A on 2008-04-26
I have the same problem (aside of the bit getting X to work). I've tried rebooting, tried a different mouse device to no effect.

---

### Post by Jolly Roger on 2008-04-27
i have this same issue as well. the mouse not working that is. i have had no problems with getting the x server to work. 

i upgraded my gutsy install only to find out that in hardy my mouse is unusable. the cursor just sits in the middle of the screen not moving.

i would really love to figure out the solution to this because i've been forced to use windows for now...i'm not too happy about having to do that.

---

### Post by Vermind on 2008-04-27
Hello,
after my upgrade to Hardy, my X did not even start. Apparently evdev is now something too complicated for users to worry about, and the new X makes some evdev options in the xorg.conf illegal, in favour of a hotplug system for these devices. The illegal options were not documented, or automatically commented out in my xorg.conf, however, and hence, it didn't start.
I also had to modify my mouse entry in order to get it working in Hardy. Apparently, the Option "Protocol" "auto" line is now required.

Here is my mouse config:
```
Section "InputDevice"
    Identifier     "Configured Mouse2"
    Driver         "mouse"
    Option         "Protocol"       "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 7 6"
    Option         "ButtonMapping" "1 2 3 8 9 10 11 12"
EndSection
```

I enabled the hotplug multibutton mouse (horizontal wheel, more than the usual 3 buttons and wheel) by adding a file called /etc/hal/fdi/policy/10-x11-input.fdi, with the content:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <!-- FIXME: Support tablets too. -->
    <match key="info.capabilities" contains="input.mouse">
      <merge key="input.x11_driver" type="string">mouse</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>
<!-- Vermind: This wrecks havoc on any international keyboards! Especially on laptops.-->
<!--    <match key="info.capabilities" contains="input.keys">-->
      <!-- If we're using Linux, we use evdev by default (falling back to
           keyboard otherwise). -->
<!--      <merge key="input.x11_driver" type="string">keyboard</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
             string="Linux">
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>-->
  </device>
</deviceinfo>
```

Note that this is the file /usr/share/doc/hal/examples/10-x11-input.fdi with the keyboard section removed, since it breaks keyboard on my laptop. For example up arrow becomes printscreen and other interesting stuff.

After adding the file, restart hal (sudo /etc/init.d/hal restart) and the X server by for example zapping it with Ctrl-Alt-Backspace.

My nvidia driver works flawlessly. I install it using the official nvidia installer ( [nvidia 32-bit]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") or [nvidia 64-bit]("http://www.nvidia.com/object/linux_display_amd64_169.12.html") for 64-bit), and my little script. This needs to be done in a TTY (non-X terminal, Ctrl-Alt-F1, F2, ...). Note that the official nvidia driver fails to load if the Ubuntu loading command is used, or if the Ubuntu nvidia module overrides it.

If one uses the official driver, one has to reinstall it every time the kernel is updated. Your Ubuntu does not know about custom kernel drivers, so You have to update them Yourself.

To use the official driver, one needs to comment out the nvidia line in /etc/modprobe.d/lrm-video, to change the loading of the nvidia driver back to normal:
```
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
```

And to stop overriding it with the Ubuntu-supplied version of the driver, one needs to disable nvidia modules in /etc/default/linux-restricted-modules-common:
```
DISABLED_MODULES="nv nvidia_new"
```

To go back, just change these as they were.

After these prerequisites are done, one can proceed to install the nvidia driver with the official installer, for example NVIDIA-Linux-x86-100.14.19-pkg1.run. The installer requires one has build-essential and linux-headers installed. On Ubuntu machines with restricted modules in use, the nvidia driver does not install correctly if the restricted drivers overlay (/lib/modules/kernel-version/volatile) is not unmounted first. The nvidia installer also fails to start if an X server is running, since it needs to unload the current nvidia driver. This is what I use my script for:

```
#!/bin/bash

arch=x86 # change to x86_64 for 64-bit
#nver=169.12
nver=100.14.19 # change nver according to Your driver version
nvi=NVIDIA-Linux-$arch-$nver-pkg1.run # change to pkg2 for 64-bit
sudo killall -s TERM gdm Xorg # two kills to make sure 
sudo killall -s TERM gdm Xorg # safe mode X is killed
sudo umount /lib/modules/`uname -r`/volatile
sudo ./$nvi -a -n; # accept license do not ask to download precompiled stuff
```

I run this script once after each kernel update,
when I notice X does not start.

I had other problems with Hardy too. Those had to do with the kernel not booting because of missing mdadm.conf entries, and a keybinding problem in the compiz scale plugin.

---

### Post by zannyo on 2008-04-27
Thank you, Vermind!  
We took your advice, and the mouse works now.  I am very glad not to have to become an expert in using keyboard hotkeys.

---

### Post by ykram on 2008-04-28
You forgot the /dev/input/mouse :)

---

### Post by alexitosrv on 2010-04-28
Thank you very much !

My mouse also did stop completely for no apparent reason, and with the changes to the /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/input/mice"
        Option          "CorePointer"
EndSection

Everything came back to normal!


Thank you guys!.

---

