---
title: "Keyboard problem (3rd level choose key)"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-08-08
The "key to choose 3rd level" function does not work with all applications on my Macbook Pro. I can create a "@" if I press the "Left Win + L" in gnome-terminal
but it does not work in firefox/evolution/gedit.

xev tells me:

```
KeyPress event, serial 32, synthetic NO, window 0x3a00001,
    root 0x77, subw 0x0, time 6157726, (-178,240), root:(455,614),
    state 0x0, keycode 133 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x3a00001,
    root 0x77, subw 0x0, time 6159254, (-178,240), root:(455,614),
    state 0xc0, keycode 46 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XmbLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False

``` ... that looks good ... everything ok ... but only for gnome-terminal ... other Gnome applications do not recognize this combination.

Isn't the keyboard layout a general setting for all programs?

My keyboard configuration:

```
rschmitt@macbook:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "de", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "evdev", "apple_laptop", "de", "mac", "lv3:lwin_switch"
``````
rschmitt@macbook:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [de    mac]
 options = [lv3    lv3:lwin_switch]
 model = apple_laptop

```

---

### Post by phenest on 2009-08-08
Yep. Same problem here. Have you reported it?

---

### Post by wayne_cat on 2009-08-08
ok ... I'm not the only one ...  thank you for confirming this problem ... I will file a bug report.

Link to the bug report will be added to this thread.

---

### Post by wayne_cat on 2009-08-08
bug report for this problem:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/410876](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/410876)

---

### Post by phenest on 2009-08-08
I know I confirmed this bug, but I'm getting different results in a VM. I originally tested this in a regular install. In the VM, it works. I may ignore those results, and go by the results I found in the regular install.

I just need to reboot, switch OS, test, and report. Bear with me.

---

### Post by wayne_cat on 2009-08-08
> **phenest said:**
> I know I confirmed this bug, but I'm getting different results in a VM. I originally tested this in a regular install. In the VM, it works. I may ignore those results, and go by the results I found in the regular install.

I just need to reboot, switch OS, test, and report. Bear with me.

Seems to be related to GTK ... I do not have this problem with "Non-Gnome" applications. It works in:

- xterm 
- konsole 
- OpenOffice 
- konqueror 
- Arora

all started in Gnome ... quite confusing

---

### Post by qzio on 2009-09-11
i have same kind of problem. Bumping this thread. Anyone knows a solution?

---

