---
title: "Joysticks/joypads/etc information needed for Ubuntu 8.10 and later"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Loïc2 on 2008-10-20
Hi,

In Ubuntu 8.10 Intrepid Ibex and due to changes in Xorg, each model of joystick needs a special .fdi file to be used properly. Ubuntu 8.10 doesn't ship with these files, and thus your joystick shouldn't be working anymore (instead, it should move the mouse cursor, sometimes preventing the use of the mouse until you unplug the joystick).

Since each joystick model is different, in order to provide these fdi files we need users to provide a little information about their joystick model - else your joystick may never be supported in Intrepid.

If you are the owner of a joystick (or any game input device, joypad, dance mat, etc...), can borrow somebody's joystick for 5 minutes or can go to a friend that has a joystick, you would be a great help if you could check if your joypad is on [this list]("https://help.ubuntu.com/community/Joystick_lshal_outputs_done"), and if not follow the instructions at [https://help.ubuntu.com/community/Joystick_lshal](https://help.ubuntu.com/community/Joystick_lshal)

If you are on a mailing list or forums where the users might be happy to help Ubuntu's gaming, you can also politely direct them to this post in the forums (I'm already sending this to the ubuntu-devel-discuss and ubuntu-users mailing lists).

Please note that I'm not an Ubuntu developer, just been an Ubuntu user for a while ;)
I'll monitor this thread for a while, feel free to post any question or suggest any improvements to the wiki or the launchpad bug.
Thanks in advance,
Loïc

---

### Post by Loïc2 on 2008-10-20
Update : 
According to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203/comments/78](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203/comments/78) Ubuntu 9.04 may not need this, and since Ubuntu isn't going to provide the fdi files for 8.10, basically the lshal output is only necessary to tell the name of the info.product information.

To summarize, you can try to create the fdi file for your device, using this model:

---
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="PRODUCT ID OF YOUR JOYSTICK">
      <merge key="input.x11_driver" type="string"></merge>
    </match>
  </device>
</deviceinfo>
---

by replacing PRODUCT ID OF YOUR JOYSTICK by the name of the device reported by lshal (see [https://help.ubuntu.com/community/Joystick_lshal](https://help.ubuntu.com/community/Joystick_lshal) on how to do it easily). Then give any name to the fdi file (preferably the name of your device) and copy it in /etc/hal/fdi/policy 

I'll try that in the next few days for a few joystick I have, then we can attach the fdi files to each device in the list at [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done).

[COLOR="Blue"]Edit: tried that, it didn't work. You still have to add specific lines for your joystick buttons and axis, not just change the info.product information. However, there's already 2 fdi files for joysticks/pads that are reported working on the list ( [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) ), covering 3 models. Hope the other models can be figured out too.[/COLOR]

---

### Post by tghe-retford on 2008-10-22
> **Loïc2 said:**
> [COLOR="Blue"]Edit: tried that, it didn't work. You still have to add specific lines for your joystick buttons and axis, not just change the info.product information. However, there's already 2 fdi files for joysticks/pads that are reported working on the list ( [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) ), covering 3 models. Hope the other models can be figured out too.[/COLOR]
Out of the two joypads I could test (Mad Catz PC CON I own and Logic3 USB Gamepad (JP260) I borrowed tonight) both worked without the need to add any specific lines for buttons or axis, testing with jstest and the joystick module in KDE4 system settings, all buttons and axis worked perfectly. I can finally play my games with my joypad. The fdi files for both those joypads are now available on the Joystick lshal outputs done page.

According to this bug report, the problem seems to only affect AMD64 systems: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951)

I just hope some fix is implemented for 8.10's release, though that bug report suggests otherwise (probably not implemented until 8.10.1).

---

### Post by endesign on 2008-10-23
Thanks for the info Loic! Wondered why my mouse was doing crazy dances now and again. I followed your guide and submitted files for the Logitech Force 3D Pro to launchpad. Hopefully it will mean that sometime down the line I can reconnect it without doing mouse tug of war!:lolflag:

---

### Post by dustint83 on 2008-10-24
simply adding some lines to your xorg.conf will fix your joysticks, any model or brand. there is no need to code specific files for every joystick. what if someone decided to go buy a new one? with this method it will still be configured with no need for a sperate .fdi

first, add this

> Section "ServerFlags"
    Option         "AutoAddDevices" "False"
EndSection

then

> Section "InputDevice"
    Identifier     "Configured Joystick"
    Driver         "joystick"
    Option         "Device" "/dev/input/event5"
EndSection

where "Device" is the input port your joystick is connected to

restart X and enjoy

---

### Post by JayBee808 on 2008-10-24
dustint83's xorg.conf modification works great.

Do we still need to submit lshal outputs for the bug report?

---

### Post by Loïc2 on 2008-10-24
dustint83's solution works indeed, but it means loosing input hotplug support when adding :
```
Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection 
```

If these lines are enough and don't break anything on your setup, then it's ok for you to use them.

However, 

```
Section "InputDevice"
Identifier "Configured Joystick"
Driver "joystick"
Option "Device" "/dev/input/event5"
EndSection 
```

isn't necessary for many joysticks (I tried 5 of them before starting the thread), and can cause problems (i.e. some users reported the ```
Option "AutoAddDevices" "False"
``` didn't work for them, but it ended up they added the Section "InputDevice" too, and that was the cause of their problem. I'm not on their setup to check, but 
```
Option "Device" "/dev/input/event5"
```
isn't a great way to keep things working, since the joystick won't always be on event5, it can be on different event# depending on what is plugged in your system. That means the user will have to adjust manually xorg.conf each time the joystick won't be on event5, which isn't something I'd advise users to do.

You could point to /dev/input/js0 (just chack your joystick appears as js0 but that's the case most often. And with two joysticks plugged? Well, you'll go back to editing xorg.conf again.

In versions of Ubuntu older than Hardy, I'd have advised editing xorg.conf, even though it's not something we should require our users to do. However, with recent X releases manual editing of xorg.conf is getting more and more risky. For example, with the Option "AutoAddDevices" "False", my keyboard switched from French (my layout) back to English in X, and changing it back in dpkg-reconfigure was no help at all for X. So try this solution in the meantime, but that's an advice that's only possible on a personnal basis, not as a "end all be all" solution.

However, on i386 Intrepid joysticks should work fine, that problem is on amd64, and supposedly will be fixed by updates - so getting lshal output isn't necessary anymore. However, nobody tried the supposed fix in Intrepid yet, and there's only one developer's word saying we'll get an update, so better safe than sorry. Getting the lshal output isn't going to hurt, it's easy to do, and it's a safety in case Ubuntu devs won't/can't/forget to fix the problem.

---

### Post by kforum on 2008-10-25
> **Loïc2 said:**
> Update : 
According to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203/comments/78](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/274203/comments/78) Ubuntu 9.04 may not need this...

why? 
are they planing on creating fdi auto generators?(that perhaps should already exist anyway.^^;

or what?

---

### Post by Loïc2 on 2008-10-25
Now, hal will detect that the peripheral plugged in is a joystick, and won't pass it to evdev at all. I think it's already working like that in i386, and the bug in amd64 should be fixed. I'm doing iso testing at the moment, and since the release is next week I might just wait for the updates instead of opening a PPA and building fixed packages, but somebody else already built a patched package for Intrepid amd64 and says the fix works (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13) ). So if it gets into -updates everything will be ok if the user has an internet connection.

---

