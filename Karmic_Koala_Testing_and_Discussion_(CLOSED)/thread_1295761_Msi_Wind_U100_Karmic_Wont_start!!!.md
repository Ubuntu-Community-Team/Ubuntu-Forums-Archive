---
title: "Msi Wind U100 Karmic Wont start!!!"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tech721 on 2009-10-19
OK i installed karmic through windows and it installs fine but i keep getting this message black screen grub beta and that all it goes to is there any way to bypass that?

---

### Post by frieder83 on 2009-10-20
I can confirm this problem. During booting of the live-cd (beta) the screen goes black startup stops. Seems to be a problem with the GMA driver.

---

### Post by Dragonbite on 2009-10-20
What do you mean by "install through Windows"?  Do you mean Wubi?

---

### Post by tech721 on 2009-10-21
> **Dragonbite said:**
> What do you mean by "install through Windows"?  Do you mean Wubi?

yea in wubi even in virtual os does the same

---

### Post by Mauriciobc on 2009-10-22
I can confirm the same thing is happening to me!
It loads everything than just get to a black screen!

---

### Post by frieder83 on 2009-10-23
Problem is not solved in Karmic RC. :( Only the mouse is shown on a black ground...

Does someone has a workaround?

---

### Post by Mauriciobc on 2009-10-23
Not yet. I can't even acess terminal screen with alt+F1.

With the final release, i got this message: 

> this is normally some bug in some application using the D-BUS library. Process 2358: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending !=NULL" failed in file dbus-pending-call.c line 596.

---

### Post by eldutcho on 2009-10-23
I had it booting and installed on mine. It was horrible buggy, the display constantly flickered if I touched the fn+brightness keys. That was 2 weeks ago though, it may have been fixed. I'll try it out when the official release comes, I'm too busy with school to test anymore

---

### Post by Zorael on 2009-10-23
My Wind (Advent 4211) works nicely, but it's installed on its own partition and not through Wubi nor via virtualization.


Sort of off-topic;
> **eldutcho said:**
> I had it booting and installed on mine. It was horrible buggy, the display constantly flickered if I touched the fn+brightness keys. That was 2 weeks ago though, it may have been fixed. I'll try it out when the official release comes, I'm too busy with school to test anymore

That bug has been tracked down ([https://bugs.launchpad.net/bugs/415023](https://bugs.launchpad.net/bugs/415023)), currently awaiting a patched hal-info package to hit the repos.

For KDE, if you manually apply that patch (to the HAL fdi file for laptop screens), and upgrade kdebase-workspace to 4:4.3.2-0ubuntu6 or later (which includes a patch to listen to the changes the HAL patch did), it'll work.

gnome-power-manager likely needs to be similarly patched before the fdi patch will make any difference.

[quote=Felix Geyer (debfx)]I'm not sure why my patch doesn't fix the issue with gnome-power-manager but it seems to work with KDE powerdevil (once a patch to respect the brightness_in_hardware property has been uploaded).

The MSI Wind seems to send brightness up/down key events on every brightness change and that's exactly what brightness_in_hardware=true indicates.[/quote]

```
kdebase-workspace (4:4.3.2-0ubuntu7) karmic; urgency=low

  * Update kubuntu_101_brightness_fn_keys_and_osd.diff to use the same OSD as
    kmix (LP: #458963):
    - Reverts the addition of an untranslated string
    - Reduces U/I impact of this late change
    - Updated patch thanks to Felix Geyer

 -- Scott Kitterman <scott@kitterman.com>  Thu, 22 Oct 2009 18:09:50 -0400

kdebase-workspace (4:4.3.2-0ubuntu6) karmic; urgency=low

  * Add kubuntu_101_brightness_fn_keys_and_osd.diff to enable brightness
    Fn keys when they aren't handled by the hardware and add an OSD
    for brightness changes

 -- Felix Geyer <debfx-pkg@fobos.de>  Sat, 17 Oct 2009 13:19:34 +0200
```


edit:
```
[22:28] <debfx> *[...]* the hal-info patch probably won't make it into karmic final
```

---

### Post by The Cog on 2009-10-25
> **frieder83 said:**
> Problem is not solved in Karmic RC. :( Only the mouse is shown on a black ground...

Does someone has a workaround?

Same problem with an Advent 4211 - a UK MSI wind clone. The live USB installer stick gives a black screen, and can't switch to a tty conlole. Starting in safe graphics mode instead gives a scrambled unreadable screen like a monitor that lost horiz sync. Can switch to a tty console but can't see the text.

However, if you choose to install rather than to try Ubuntu without touching the hard disk, the installer works fine. After installing, Karmic boots fine, so I think the problem is just something to do with the installer CD/stick.

---

### Post by Zorael on 2009-10-25
> **The Cog said:**
> Same problem with an Advent 4211 - a UK MSI wind clone. The live USB installer stick gives a black screen, and can't switch to a tty conlole. Starting in safe graphics mode instead gives a scrambled unreadable screen like a monitor that lost horiz sync. Can switch to a tty console but can't see the text.
Curious; WFM. I'm writing this from a Kubuntu live usb created with unetbootin, which booted without hitches. Brightness is still borked, of course, and I expect the USB subsystem to go down if I toggle the camera.

Perhaps it's an Ubuntu-specific bug? (ie KDE works)

---

