---
title: "804x86::Microsoft Wireless optical mouse 2.0 issue"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by xerman on 2008-06-09
Hello there

Since update to 804x86, mouse has been behaving a bit weird. When scrolling down, mouse produces the scroll down feature, but:

1- When scrolling up through the mouse wheel, instead of scrolling through the window, the right-click menu appears. No scroll up is possible.

2- Modifying xorg.conf in:
[INDENT]Emulate three button mouse[/INDENT]
from "true" to "false" does not make any difference.

Keyboard and mouse are the "Microsoft Wireless Comfort Desktop" with:
[LIST=1]
[*]Wireless comfort keyboard 1.0A
[*]Wireless optical mouse 2.0
[/LIST]

Any help will be much apreciated.
regards
Xermán

---

### Post by dstew on 2008-06-09
Some have got that setup working by using a USB-to-PS/2 adapter, and plugging into the PS/2 computer socket...

---

### Post by xerman on 2008-06-12
> **dstew said:**
> Some have got that setup working by using a USB-to-PS/2 adapter, and plugging into the PS/2 computer socket...

Hello dstew, 

The keyboard and mouse are plugged into the ps2 socket through a KVM switch to handle desktop and server computers.

Behavior is weird though as sometimes seems to work fine, and sometimes seems to work completely chaotic.


When using the keyboard and mouse in the server (ubuntu server 704-64) also through the KVM switch there is no issue at all. The issues just take place in the 804x86 desktop machine.

---

### Post by dstew on 2008-06-12
How does it work if you bypass the KVM switch, an plug it directly into the PS/2 socket?

---

### Post by xerman on 2008-06-18
Hello dstew,

I haven't had time to check the KVM bypass yet. But I've noticed since last updates that besides the weird movement of mouse I experience new issues.

As a sum up:

1- When logging into gnome, the pointer goes crazy all acros the screen clicking and doing whatever. This happens even if I keep my hands at my back.
The effects can be: a new folder on the desktop; rearrange desktop icons; screenlets appear moved; bottom panel changes position; new panels are created; some preferences are open. 
All these effects I've noticed up to today just in 804x86. This does not happen on 704_64 server.

2- After today's update: the mouse does not respond to clicks when it should. I might left-click to select something, and could need up to 6 left-clicks to get the left-click on. Same with right-click. Almost the same with scroll (maybe the same, as turning the wheel could be understood as 6 clicks in a row)

All these just happens on the desktop machine, does not happen on the server, also using the same Keyboard-Mouse through the KVM.

I'm starting to think is something related with updating from 710. I might try to install from scratch 804x86. A clean install could help, besides other issues not mouse-keyboard related.

The weird thing is that with LiveCD does not present any issue at all. So could be some config inherited from 704 to 710 and then to 804.

Regards. As soon as I can bypass the KVM I'll write down the experience.

Xermán

---

### Post by xerman on 2008-11-07
Hello there:

Today i bypassed the KVM tired of the issue to find out that the issue is still there. So seems is not related to the KVM thing, but to something deeper.

If i choose other window manager, compiz, metacity or kWin the response of Keyboard-mouse still is the same chaotic behavior.

The chaotic behavior relates also to noise as this machine is same as home (but home has IDE DVDRW while this has SATA, so i can not write DVD nor CD at work, but can at home), and here ACPI-APM works, while not at home. So seems from update to 804 some things got messed up, and some things stay working. And fresh install of 804 (home) got some things messed up and other working, but not the same things as the update process.

This issues decrease stability of overall system to recommend ubuntu to non-poweruser users. 

Regards

Xermán

---

### Post by xerman on 2008-11-21
Hello there:

Problem was solved in the following way:

Change Microsoft Wireles Optical Mouse and Multimedia Keyboard. Now I use a Logitech Wireless desktop EX, through KVM and no problems at all.

So the issue seems to be with MS Desktop Combo and hardware recognition by ubuntu. So seems somethings still need to be tuned to get to production machines.

Will check the MS keyboard on 810-64b machines if have time this weekend and post any issues as soon as have time.
(So better not use MS Desktop Combo through PS2, or do not buy MS Desktop Combos)


Regards.
Xermán.

PS: i might be getting old too fast, as since changed Desktop keyboard and mouse overall performance seems to have increased a few. At least responsivenes.... maybe my eyes are suffering from restrain... who knows...

---

### Post by xerman on 2008-12-04
Hello again...

I've been noticeing issues lately on this computer with the Logitech EX desktop.

Everything seemed to work fine, mouse, keyboard... until I unplugged Wacom tablet to take home. Since I unplugged Wacom tablet mouse works when it feels like working. So everytime i turn on computer, mouse is usless until i get into gnome desktop, and from there i restart computer using keyboard, as no mouse/no pointer on the screen.

Besides when trying to use wacom tablet in Inkscape and Gimp, I've noticed the following issues:
1- using mouse and switch to use tablet seems to work fine and can use tablet pen and buttons, though not correctly mapped. Should need a Global Settings Preference for Tablets inside Preferences. And if want to modify in each program, do inside.

2- when switching back to mouse mouse becomes useless as Wacom pen bindings are remapped to mouse so behaviour of mouse becomes erratic.

So seems there is an issue with the layer P'n'P for input devices and when 2 input devices are plugged produces missbehaviour in config files that will remain when unplug the devices.

---

