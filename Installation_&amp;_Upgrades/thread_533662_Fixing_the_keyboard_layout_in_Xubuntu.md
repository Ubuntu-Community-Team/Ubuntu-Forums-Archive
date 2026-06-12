---
title: "Fixing the keyboard layout in Xubuntu"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by jgb2185 on 2007-08-24
I am working to resurrect an older PC (HP Pavilion 8660c, 533 mHz, 128 MB RAM) with Xubuntu. I think I have misconfigured the keyboard. The hardware is an old IBM 105-key (model 3923).

The keyboard section of **xorg.conf** that was generated during installation is
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
EndSection
```

The apostrophe key (and the quote mark accessed with Shift) do not appear on screen unless I press them twice. Some other keys show the same behavior.

I have tried commenting out the **XkbVariant** line, as well as leaving it active but changing it to 
```
        Option          "XkbVariant"    ""
```

or

```
        Option          "XkbVariant"    "nodeadkeys"
```

None of these changes has had any effect after a reboot.

I'd like to solve this by editing **xorg.conf**. Can anyone supply the proper configuration, please?

Thanks...

JGB

---

### Post by kwiwii on 2007-08-27
Cant you go to System > Preferences > Keyboard?

---

### Post by zoobave on 2007-08-27
boot your your machine in single user mode and give

```
# X  -configure
```

and replace the old  xorg.conf file to the new one

---

### Post by jgb2185 on 2007-09-02
> Cant you go to System > Preferences > Keyboard?

I've tried, but nothing I do seems to have much effect on the apostrophe issue. Also, I'd like to learn how to fix an issue of this sort in xorg.conf.

> replace the old xorg.conf file to the new one

This results in the minimalist keyboard section here:
```
Section "InputDevice"
    Identifier   "Keyboard0"
    Driver  "kbd"
EndSection
```

I substituted this in my [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file, and changed the keyboard identifier in ServerLayout to match. Then I restarted X with Ctrl-Alt-Backspace.

To my amazement, all the keys on the PC keyboard work. Many thanks, zoobave.

I'd like to follow up, though: 

1) What, if any, additional parameters would I want to add for the IBM keyboard I described at the start of this thread?

2) Is it possible to re-run the text-mode X setup script that runs during Xubuntu installtion, without re-installing the entire OS?

Thanks...

JGB

---

### Post by jdier on 2007-09-19
I had the same problem here and followed instructions, worked well.  To clarify a bit:

I did not "boot your your machine in single user mode" and "# X  -configure"

Instead I just 

```
sudo mousepad /etc/X11/xorg.conf
```

then replaced the keyboard section with this:

```

Section "InputDevice"
    Identifier   "Keyboard0"
    Driver  "kbd"
EndSection

```

then changed the server section so it read like this:

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Keyboard0"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

then restarted X with Ctrl-Alt-Backspace and all was good.

Hope this is helpful.

Jim

---

