---
title: "Dvorak keyboard layout not added at login"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-23
After selecting Dvorak UK keyboard layout during install, the login screen defaults to UK qwerty. I can add Dvorak at the login screen, but it still only accepts Qwerty. Second login will accept Dvorak and will accept Dvorak as default from 3rd login onwards.

But Dvorak should have been default 1st time round.

Any one else? Is there a bug reported?

---

### Post by durand on 2009-07-23
With me, I can set the Dvorak UK layout and it lets me use it but the next time I have to login, it forgets that I'm using dvorak uk. Making it system wide doesn't work either..

If you post a bug, could you add the link to this thread?

---

### Post by phenest on 2009-07-23
In fact, Gnome isn't using Dvorak at all, even though I selected it during install. I had to set it up manually.

---

### Post by durand on 2009-07-23
Well I started using dvorak a long time after installation so I can't really say much there. It's definitely a bug if it doesn't work when its been set as the system default. I think I'll report that unless you've already done that?

---

### Post by phenest on 2009-07-23
I've just installed alpha 3 and selected UK Dvorak during install. But after installation, Qwerty has been setup instead. Dvorak needed to be added manually for both login and apps.

I will report a bug.

---

### Post by phenest on 2009-07-23
[Bug 403680]("https://bugs.launchpad.net/ubuntu/+bug/403680")

---

### Post by phenest on 2009-07-28
How do I setup a UK Dvorak layout for the console? I have it done in X.

---

### Post by durand on 2009-07-28
> **phenest said:**
> How do I setup a UK Dvorak layout for the console? I have it done in X.

I'd like to know that as well.

---

### Post by phenest on 2009-07-28
I tried:
```
sudo dpkg-reconfigure console-setup
```
...which works, but doesn't survive a reboot.

---

### Post by Tomy on 2009-09-28
> **phenest said:**
> I've just installed alpha 3 and selected UK Dvorak during install. But after installation, Qwerty has been setup instead. Dvorak needed to be added manually for both login and apps.

I will report a bug.

I just installed alpha 6+ (9/24 daily) and have the same problem with US Dvorak.

I added the Keyboard Indicator to the panel and have dvorak selected there. My tty's are using dvorak. The login screen is qwerty. 

How do I change my login screen to dvorak? I tried adding a keyboard section to xorg.conf. This **did not** work:

```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbVariant"    "dvorak"
EndSection

```Where does the xserver get it's keyboard settings from now that xorg.conf is no longer used??

---

### Post by durand on 2009-09-28
Did you try the Apply Systemwide option in keyboard settings? I can't remember if that worked for me bit it's worth a shot.

---

### Post by Tomy on 2009-09-28
> **durand said:**
> Did you try the Apply Systemwide option in keyboard settings? I can't remember if that worked for me bit it's worth a shot.

Thanks, but did not work. Still wondering where gdm gets the keyboard setting from.

---

