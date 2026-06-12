---
title: "Ubuntu 10.10 hangs at /scripts/init-bottom during boot"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by BlackAdderDK on 2011-08-25
Hi

The story is as follows.

I have a Lenovo TP W520 with a Nvidia Quadro 2000M (with support for Optimus)!

I've tried to use the open-source optimus driver (Bumblebee), but found to many issues I had to deal with. (both on 11.04 and 10.10) - therefore I've accepted the lesser batterytime... and choosed to run with "discrete" option in BIOS - setting Nvidia only mode!

I can't use the 11.04, as I need iFolder (and can't get it to work with this edition, by the way I see the following problems on 11.04 too) - as a result I am using 10.10 (64-bit).

I have installed the Nvidia proprietary driver, and when attached to my dockingstation (connected to an switchbox) the laptop boots fine every time! But out of the dock, the laptop hangs at "running /scripts/init-bottom" during boot!

To resolve this I've [**tried ****this **]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")(used the "nomodeset" option)... after this, it pass the "running..." every 4-5 time

After this I tried to upgrade the driver as [**described here**]("http://www.multimediaboom.com/how-to-install-nvidia-display-driver-260-19-36-in-ubuntu-10-10-maverick/")... this may have helped - a tinytiny bit

Last effort was to add "TPPS/2 IBM TrackPoint (MatchIsPointer "on")" and "AT Translated Set 2 keyboard (MatchIsKeyboard "on")" to "/usr/share/X11/xorg.conf.d/10-evdev.conf" according to [**this **]("http://maarten.hondelink.com/index.php/No_Keyboard/mouse_when_upgrading_from_9.04_to_10.04_%28linux_Mint_7_upto_9%29")... now it boot's fine every time... but at login, the login-box disappears and everything freezes! But if I choose "Safe Mode" i can login.

I'm a hopeless newbie with Ubuntu, and I'm fresh out of ideas - please help!#-o

by the way... I was thinking about trying the OpenSouce 3D driver I've seen in 11.04 - but I can't find it to 10.10 - anyone? :confused:

regards
'Adder

---

### Post by BlackAdderDK on 2011-08-26
Hmmmm... correction - It passed the "/scripts/init-bottom" ALMOST every time... :(

I see a lot post in google with similar problems... can it be true - is it a well known problem never dealt with??

anyone?

---

### Post by BlackAdderDK on 2011-09-08
We'll... guess I have to reply on my own question then :)

I have found an acceptable solution:

I have edited "/usr/share/X11/xorg.conf.d/10-evdev.conf", and added the following:

> Section "InputClass"
        Identifier "TPPS/2 IBM TrackPoint"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "AT Translated Set 2 keyboard"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
    Identifier     "Power Button"
    MatchProduct   "Power Button"
    Option         "Ignore" "on"
EndSection

Section "InputClass"
    Identifier     "Video Bus"
    MatchProduct   "Video Bus"
    Option         "Ignore" "on"
EndSection

Section "InputClass"
    Identifier     "Sleep Button"
    MatchProduct   "Sleep Button"
    Option         "Ignore" "on"
EndSection

Section "InputClass"
    Identifier     "Integrated Camera"
    MatchProduct   "Integrated Camera"
    Option         "Ignore" "on"
EndSection

Section "InputClass"
    Identifier     "ThinkPad Extra Buttons"
    MatchProduct   "ThinkPad Extra Buttons"
    Option         "Ignore" "on"
EndSection

Section "InputClass"
    Identifier     "Lid Switch"
    MatchProduct   "Lid Switch"
    Option         "Ignore" "on"
EndSection
Furthermore I edited the "/etc/default/grub"
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

was changed to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi nomodeset"

(just remember to run "update-grub" after this)

Not sure both is needed, it might be able to work with the boot-options only... 

I have changed the driver back to the "standard" proprietary Nvidia Driver within Ubuntu 10.10, and in the BIOS the "discrete" option is choosed... and all is good - furthermore I have had a blast using ***[COLOR=Blue][disper]("http://willem.engen.nl/projects/disper/")[/COLOR]*** - so great a tool!

---

