---
title: "Mouse Not Detected"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by nj_86 on 2006-08-04
Hi,
I'm a windows user and i want to shift to linux.Well i was really excited when i got the Ubuntu 6.06 CD from shipit.com.So i decided to install it.Now the problem is that my mouse does not work.I can see the cursor but its stuck in the middle of the screen.With Great difficulty(rather by fluke) i nstalled it using the key board while randomly testing all the keyboard shortcuts.I've got a logitech 3 button ball mouse which is around 5 yrs.So plz help me with my mouse problem.Alo i do not know how to get the terminal screen using the keyboard to use the commands.Plz help.
Regards

---

### Post by moma on 2006-08-04
Is your mouse connected to Serial port?,  PS2 port?,  USB port?
Maybe you need a new mouse?

---

### Post by nj_86 on 2006-08-04
Its a serial mouse.Sorry forgot to mention it.

---

### Post by nj_86 on 2006-08-04
I mean its connected to COM2 -Serial port.

---

### Post by moma on 2006-08-04
Try to load sermouse.ko kernel module.

Unload it first
$ [COLOR="Green"]sudo modprobe -r mousedev [/COLOR]  # This may not exist.
$ [COLOR="Green"]sudo modprobe -r sermouse[/COLOR]

Load the module for serial mouse
$ [COLOR="Green"]sudo modprobe -vv sermouse[/COLOR]

Test your mouse
-------------------

If it does not work, then check if there's life in the wire. (ttyS0 = Com1, ttyS1 = Com2).
$ [COLOR="Green"]cat /dev/ttyS1[/COLOR]
or 
$ [COLOR="Green"]cat /dev/input/mice[/COLOR]
And move the mouse pointer. You should see droppings of the mice.
----------------------------------------------

Check also your /etc/X11/xorg.conf file.   Study the InputDevice section for mouse.
The Option "Device" should be "/dev/ttyS1" or possibly "/dev/input/mice".

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol"  "???"   <---- ------ How this should be?  
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection
```
Restart X-server if you change your /etc/X11/xorg.conf. Just press CNTR + ALT + BACKSPACE.

---

### Post by nj_86 on 2006-08-04
Hi,
I'm sorry,but i do not know the keyboard shortcut to load the terminal/sermouse.ko kernel module.Plz help
Regards

---

### Post by moma on 2006-08-04
Start Terminal program from Applications -> Accessories menu. 

Or press CNTR + ALT + F1 to activate text console, login and enter the commands there.
"nano" is a good text editor if you need that.

---

### Post by nj_86 on 2006-08-04
Hi,
Sorry again,But how do i access the Applications->Accessories menu,without the mouse?Its so difficult with the keyboard.

---

### Post by nj_86 on 2006-08-04
Hi,
how do i goto /etc/X11/xorg.conf using the command prompt?(Using Alt+CTRL+F1) when i type dir it shows only 2 folders example and my user name.
Regards

---

### Post by moma on 2006-08-05
$ [COLOR="Green"]cd /etc/X11[/COLOR]

or use "nano" editor. Sudo gives you admin rights.
$ [COLOR="Green"]sudo nano /etc/X11/xorg.conf[/COLOR]
----

CNTR + ALT + F7 returns you to the GUI.

Notice: ALT + F1 brings you into the main-menu in GNOME.

---

### Post by nj_86 on 2006-08-05
Hi,
Thanks for being patient :) Well i could edit the xorg.conf and this line showed  Option "Protocol"  "Explorer PS/2",I did everything u said.My mouse works fine in Windows XP.So what do i change in the protocol line?
Regards

---

### Post by nj_86 on 2006-08-05
Hi,
moma thanks a lot for the help.I've fixed it :D :D  after reading through [http://www.ubuntuforums.org/showthread.php?t=196502](http://www.ubuntuforums.org/showthread.php?t=196502) and following yossman's advice.thanks for the help.Linux seems to be so diff from Windows.
Regards

---

