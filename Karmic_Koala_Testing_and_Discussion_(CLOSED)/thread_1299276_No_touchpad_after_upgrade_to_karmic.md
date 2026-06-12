---
title: "No touchpad after upgrade to karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alinux-lb22 on 2009-10-23
Hi
I got not touchpad on my toshiba laptop after upgrading to karmic, and the system settings dont show a touchpad in the mouse section.

Regards

---

### Post by jbrown96 on 2009-10-23
Check your /etc/X11/xorg.conf file and for touchpad settings. ```
cat /etc/X11/xorg.conf
``` see if you have a section similar to > Section "InputDevice"

    # generated from default
    Identifier     "Mouse0" 
    Driver         "mouse"  
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"  
EndSection 
If not, let's add it. 
1) backup xorg.conf ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
2) Edit the file ```
sudo gedit /etc/X11/xorg.conf
``` You said system settings, which usually mean KDE. If you are using kde, then replace gedit with kate. Copy in my mouse section and then logout. See if it's working now.

If it's still not, do you have a regular usb mouse you can try?

---

### Post by alinux-lb22 on 2009-10-24
I did try it 

strangely X did not start claiming there is no EndSection statement although you included it and so did I.

---

### Post by Zorael on 2009-10-24
Does 'xinput list' list it?
```
$ xinput list | less
```
Or perhaps 'xinput list | grep -i pad'.

---

### Post by alinux-lb22 on 2009-10-24
"Virtual core pointer"  id=0    [XPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 0
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 0
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=2    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Power Button (FF)"     id=3    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Power Button (CM)"     id=4    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"AT Translated Set 2 keyboard"  id=5    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"PS/2 Mouse"    id=6    [XExtensionPointer]
       Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Macintosh mouse button emulation"      id=7    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"USB Optical Mouse"     id=8    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 7
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
               Min_value is -1
                Max_value is -1
                Resolution is 1

---

### Post by jaansson on 2009-10-25
Hello! I've actually got the same problem after upgrading from 9.04 to 9.10 BETA. The touchpad basicly doesn't respond at all. On another installation, I upgraded from 9.04 -> 9.10 ALPHA, which was no problem. I tried those tricks, but unfortunately without any luck. I've got a HP 6735s, in case that would be of any use what so ever :P 
Also, is there any way to get to the network connections thing without a mouse? Because without internet, I have to boot in to vista if my tries fails, which takes quite some time. Otherwise I'll see if I can get my hands on some mouse.

---

### Post by CommonClone on 2009-10-25
I am having the same problem.  I upgraded from 9.04 to 9.10.  When I rebooted after the installation, I had no touchpad.  It didn't even work in gdm.  I have openbox installed, and I have no touchpad in openbox either.  I plugged in a USB optical mouse, and it works fine.  I would really like to get my touchpad working again.

---

### Post by jaansson on 2009-10-25
Ahhh! Simple fix that worked for me:

Remove linux-image-2.6.28-15-generic, or similar. It was overriding the 2.6.31 kernel image, preventing a lot of stuff from starting. Pretty obvious thing, and I actually think that the same thing has happened to me before :mad: That's probably what got me onto this track.

Hope the same thing works for you guys!

(It probably even says that you should do this somewhere, just that I was ignorant enough to miss it :P )

---

