---
title: "Touchpad and wireless problems after Intrepid upgrade"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by bipco on 2008-11-13
Hello

I've upgraded to Intrepid 64-bit on a Lenovo R61, via a fairly tortuous process (had to do a new install of Hardy, then upgrade, as I couldn't get any of the installers I tried to work).

I have two current problems:

1. Wireless is not working at all - the network panel control thing says "wireless is disabled". Wired network is working fine. Seems the built-in wireless is not being detected.

2. I can't configure the touchpad - the option in the mouse control panel is not there anymore, and I can't get the synaptics touchpad control to work. It says it needs SHMConfig enabling. I've followed the instructions here: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) for doing this via an fdi file, but it makes no difference.

Both of these were working fine "out-of-the-box" in Hardy

Any others with similar, or with fixes?

Thanks

Warren

---

### Post by sukhhari on 2008-11-13
Try install with Ubuntu Recovery Mode and select option with dpkg missing packages and hopefully with will be correcting your problem, this problem since upgrading from Ubuntu 8.04 to Ubuntu 8.10.

:confused:

---

### Post by bipco on 2008-11-13
Thanks for the suggestion, but not sure what the procedure is - do you mean use an install CD or do this from within the installed system? If the CD, which one - I had a look at the desktop installer and couldn't see anything for Recovery Mode. I've got the alternate installer as well.

Also. how do I know which packages I'm missing, or will it just fix any that it finds?

Thanks

Warren

---

### Post by sukhhari on 2008-11-14
Start your Computer in Ubuntu Recovery Mode means

1. While booting please select Ubuntu Recovery mode to fix the problems.

2. Let Connect Network Cable ( Internet Connection / Broadband Connection ).

3. In Recovery Mode - Select damaged packages to re-configure for fixing the problems.

Once all above steps completed successfully, now you can go back to your normal startup.

Regards
Harish
:KS

---

### Post by sukhhari on 2008-11-14
Sorry onething missed.

DON'T USE YOUR INSTALLATION CD / DVD.

BOOT WITH INSTALLTED SYSTEM ONLY AND THEN SELECT RECOVERY MODE.

---

### Post by forsola on 2008-11-14
Hi,

I had the same problem with the touchpad in my lenovo after upgraded. With this new release touchpad can be configure via HAL.

So what you have to do is edir /etc/X11/xorg.conf and just leave this lines:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "False"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
EndSection

Whitout any reference to synaptics. After that restart the X (/etc/init.d/gdm restart) and it will be working.

To control the preference of the touchpad forget about to use gsynaptics any more. For now on you can use: gnome-mouse-properties.

Best,

Ferran

---

### Post by bipco on 2008-11-17
Thanks both for the info - although dpkg said nothing was broken, Recovery Mode did seem to fix the wireless (though I haven't got a network here to test it as yet). However, the touchpad is still not fixed - the references to synaptics are already commented-out in xorg.conf, and I tried setting up SHMConfig via HAL as described above. Still no touchpad tab in Mouse preferences and Touchpad control won't launch due to the SHMConfig problem.

Warren

---

### Post by bipco on 2008-11-18
Correction on the wireless - it works OK if I have wireless enabled at boot (there is a hardware switch), but doesn't work if I switch it on after boot. However, Bluetooth seems to work either way.

Warren

---

