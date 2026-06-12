---
title: "Nvidia 169 glx-extension remains on system blocking ATI gl-driver!!"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by perixx on 2008-01-26
Please Help!

I had changed my graphic cards, trying out a 6800XT with standard and newest (169) drivers - got both working. 

Then I disabled the Nvidia restricted driver in the manager and went over to re-install my X1950 GT again (with 8.01 driver)... I was trying and tinkering around, even reverting to the standard Xubuntu fglrx drivers (7.34). But the direct rendering and OpenGL wouldn't just come back.

After some examinating, I finally think I found the culprit: according to /var/log/Xorg.0.log, in
> usr/lib/xorg/modules/extensions there's a symlink named 'libglx.so' that's still pointing to the 'libglx.so.169.09'-Nvidia OpenGL-driver.

I've done following without success: ```
'sudo dpkg-reconfigure xserver-xorg'
```
I tried to remove Nvidia drivers with 'Envy' and manually by purging all Nvidia stuff with ```
sudo apt-get remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings --purge
```
I re-installed ```
linux-restricted-modules-generic and restricted-manager 
```... no go.

What can I do to get rid of the Nvidia trash??

perixx

---

### Post by perixx on 2008-01-27
Someone reading this that has an idea..?

perixx

---

### Post by perixx on 2008-01-28
In the /var/log/Xorg.0.log I found out, that there's still the Nvidia 169.09 glx-extention in the system. Since I got nothing much to lose, I thought, why not be a little experimental?

I found > /usr/lib/xorg/modules/extensions/libglx.so (Symlink to)
/usr/lib/xorg/modules/extensions/libglx.so.169.09 (Nvidia stuff) - probably the main culprit. It's not being replaced by ATI's driver, so I decided to rename and replace it with the live-CD's version (obviously Xorg/Xvesa version):
> libglx.so and libGLcore.so.

After building the ATI 8.452.1 .deb packages and installing them again (first fglrx-kernel-source, xorg-driver-fglrx-dev, then xorg-driver-fglrx + amdcccle), the installation output would say: > starting atieventsd: error while loading shared libs: libGL.so.1 - no such file!
Realizing that there's another Nvidia piece of crap lying around ```
/usr/lib/libGLcore.so.1 (Symlink to)
/usr/lib/libGLcore.so.169.09
```, I renamed the last one as well + removed and re-installed ATI drivers again. 

At least I've got **MESA** back again, so I **MUST** be on the right track!?! :]

Doing ```
sudo apt-get update
sudo depmod -a
sudo aticonfig --initial --input=/etc/X11/xorg.conf
restart now
``` brought me here, where I am now... the last thing I can think of now is the (in)famous```
sudo dpkg-reconfigure xserver-xorg
```, which I got stuck now with not knowing how to determine my USB-mouse!!! ACK...
:roll:

perixx

---

### Post by DRPend on 2008-01-28
> **perixx said:**
> In the /var/log/Xorg.0.log I found out, that there's still the Nvidia 169.09 glx-extention in the system. Since I got nothing much to lose, I thought, why not be a little experimental?

I found  - probably the main culprit. It's not being replaced by ATI's driver, so I decided to rename and replace it with the live-CD's version (obviously Xorg/Xvesa version):
.

After building the ATI 8.452.1 .deb packages and installing them again (first fglrx-kernel-source, xorg-driver-fglrx-dev, then xorg-driver-fglrx + amdcccle), the installation output would say: 
Realizing that there's another Nvidia piece of crap lying around ```
/usr/lib/libGLcore.so.1 (Symlink to)
/usr/lib/libGLcore.so.169.09
```, I renamed the last one as well + removed and re-installed ATI drivers again. 

At least I've got **MESA** back again, so I **MUST** be on the right track!?! :]

Doing ```
sudo apt-get update
sudo depmod -a
sudo aticonfig --initial --input=/etc/X11/xorg.conf
restart now
``` brought me here, where I am now... the last thing I can think of now is the (in)famous```
sudo dpkg-reconfigure xserver-xorg
```, which I got stuck now with not knowing how to determine my USB-mouse!!! ACK...
:roll:

perixx

By USB mouse do you mean the protocol?.  I was wondering if your xor.conf file was using the correct driver id? ATI cards tend to be a bit off on this and you may have gotten the PCI ID listed under the Dirver ID setting.  If you need the mouse protocol try using mdetect

---

### Post by perixx on 2008-01-29
Thanks for your help, but I installed and used 'mdetect', but I can't make sense of the few hundrets of messages like these: > Opening device tty0...
Opening device .initramfs...


With > I was wondering if your xor.conf file was using the correct driver id? ATI cards tend to be a bit off on this and you may have gotten the PCI ID listed under the Dirver ID setting. Iguess you're referring to this:
```
Section "Device"
.
.
BusID "PCI:1:0:0"
``` That's what it always was like...

perixx

---

### Post by perixx on 2008-01-30
**Allright**, 

**how to recover from NVIDIA latest drivers to ATI standard the hard way / SUMMARY**: :-D

I thought I'd have to reinstall and uninstall the Nvidia card all over again, in order to get rid of that damn Nvidia-glx-extension for xorg; fortunately, there was no need for this! I still haven't got the latest ATI driver working, but the standard, restricted 'fglrx' drivers (7.34) work again !! :)

Here's how I finally made a safe landing - since I don't know WHICH steps exactly led to success (most probably the remaining Nvidia '.so.169' drivers), I'll write down all of them, in case someone got similar problems:

1) In /var/log/Xorg.0.log, there was reference to the OpenGL glx-extension 'libglx.so', still pointing to the 'libglx.so.169.09'-Nvidia:
> /usr/lib/xorg/modules/extensions/libglx.so (Symlink to)
/usr/lib/xorg/modules/extensions/libglx.so.169.09 (Nvidia stuff)
- probably the main culprit. It's not being replaced by ATI's driver, so I decided to rename and replace it with the live-CD's version (obviously Xorg/Xvesa version):
> libglx.so and libGLcore.so

2) I've done following without success:
```
sudo dpkg-reconfigure xserver-xorg
```

3) I tried to remove Nvidia drivers with 'Envy' and, to make it sure, manually by purging all Nvidia stuff with ```
sudo apt-get remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings --purge
```

4) I reinstalled without success: ```
linux-restricted-modules-generic and restricted-manager
```

5) After building the ATI 8.452.1 .deb packages and installing them again (first fglrx-kernel-source, xorg-driver-fglrx-dev, then xorg-driver-fglrx + amdcccle), the installation output would say: > starting atieventsd: error while loading shared libs: libGL.so.1 - no such file! 

6) Realizing that there was another Nvidia piece of crap in: > /usr/lib/libGLcore.so.1 (Symlink to)
/usr/lib/libGLcore.so.169.09 I renamed the last one as + removed and re-installed ATI drivers again 
>> MESA soft-rendering back again!

7) I did ```
sudo apt-get update
sudo depmod -a
sudo aticonfig --initial --input=/etc/X11/xorg.conf
restart now
``` >> same result, only MESA OpenGL.

8] Executed ```
sudo dpkg-reconfigure xserver-xorg
``` >> still, only MESA works. USB mouse-protocol was unknown, I messed up my mouse; remedy was to replace faulty mouse options in xorg.conf with backup values (I guess "Emulate3Buttons" "true" was bad, apart from the protocol): 
Non-working mouse setup after 'dpkg-reconfigure':
>  Option          "Device"                "/dev/**psaux**"
        Option          "Protocol"              "**PS/2**"
        Option          "ZAxisMapping"          "4 5"
        Option          **"Emulate3Buttons"       "true"**
Old, yet working mouse setup in xorg.conf backup file:
>  Option         "Device" "/dev/input/**mice**"
    Option         "Protocol" "**[B][COLOR="Blue"]Im[/COLOR]**PS/2[/B]" **[COLOR="Blue"]EDIT:[/COLOR]** Actually, only the the marked characters need to be added, to get the mousewheel working again - everything else doesn't seem to matter.

9) After fixing the mouse, deinstalling the ATI 8.01 driver with: ```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```, disabling ATI restricted drivers in the Restricted Drivers Manager and removing all 'fglrx' packages completely with Synaptic, to be on the safe side, 

10) I enabled the ATI RESTRICTED DRIVERS in the Restricted Drivers Manager, which installed the v.7.34 flgrx-drivers again. Then ```
 sudo mousepad /etc/default/linux-restricted-modules-common
``` and enabled restricted fglrx module again with ```
# DISABLED_MODULES="fglrx"
``` (commenting it out).

11) Made sure that xorg.conf had some vital settings: ```
.
.
Load    "dri"
        Load    "extmod"
        Load    "glx"
        Load    "dbe"
        Load    "vbe"
.
.
Section "Extensions"
        Option          "Composite"     "0"
EndSection
Section "DRI"
        Mode    0666
EndSection
# Section "ServerFlags"
#    Option         "AIGLX" "on"
# EndSection
```
Restarted system. **[COLOR="DarkGreen"]OpenGL/direct rendering WORKS AGAIN[/COLOR]** !!! 8)

12) **WHEW!!** I'm considering this one as 'SOLVED', though only standard fglrx (7.34), BUT..(!)

perixx

---

### Post by perixx on 2008-02-02
It seems that I was a little prematurely... I could but install the 7.34 drivers from the repos again, but none other (newer) drivers won't install properly anymore - Nvidia crap is remaining on system and won't vanish :(

FGLRX won't install in /usr/share/ati - only 'amdcccle'. In /usr/lib/xorg/modules/extensions, there's a libglx.so symlink to Nvidia crap. In /usr/lib, there's libGL.so.1 symlinking to Nvidia crap. In /var/log/Xorg.0.log there are traces of 'libnvidia-tls.so.1'. In spite of I even reinstalled and deinstalled the Nvidia card completely again - manually and with Envy...

HECK, what's all that Nvidia stuff still doing on my system:confused:

perixx

perixx

---

### Post by perixx on 2008-02-03
Somehow I seem to got rid of the Nvidia trash, at last!!

I did, however, delete the questionable files I could find by hand and reinstall nearly my complete underlying linux-architecture: linux-kernel-common, linux-kernel-generic, xorg, Mesa, xubuntu-desktop.... and a lot more.

Then I've installed ATI 7.11 driver over and over (including manually compiling the kernel-module) several times. Obviously, all visible traces of #@!?&! **NoVidia** are gone now, except for some remaining wrong symlinks, which I've deleted by hand, the one's I could find, that is. Those might well be the cause for my installation problems with the ATI drivers, I guess, which still won't work!

perixx

---

