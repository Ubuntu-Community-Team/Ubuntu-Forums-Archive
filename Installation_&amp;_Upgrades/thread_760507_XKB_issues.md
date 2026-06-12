---
title: "XKB issues"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by JediKnight on 2008-04-20
I live in Greece and I want to use at least two keyboard layouts, USA and GR

When I installed Ubuntu I had no problem, I installed the locales and could write perfectly with both layouts and switch between them

However I wanted to experiment a bit with visual effects and had some tamperings with layout files. I can't remember what I changed and how

No whenever I login to Gnome, I get that infamous window 'Error activaiting XKB configuration. It can happen under various circumastances' etc etc etc

It then says to include the following results in a report

```
xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us,gr", "101", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us,gr", "101", ""
```

```
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	101,gr]
 model = 
 options = [grp	grp:alt_shift_toggle]
 overrideSettings = true
```

I don't like particularly the '[us	101,gr]' line... I have seen from other configurations that it should be something like [us,gr] while the 'model =' line should include something like 'pc101' or 'pc104'. But I don't know how to change these. I haven't found them in any ascii configuration files.

however I still can switch between the two layouts, although not with the keyboard shortcuts, but only by clicking the Kb indicator on the lower right, which is not very convenient at all!!! I tried to fix the problem by right-clivking on the indicator and go to the preferences, but whenever i make a change, the same warning window pops up again, and all changes I make aren't applied

OTOH I have discovered this command 
```

setxkbmap -model pc104 -layout us,gr -variant 101 -option -option grp:alt_shift_toggle
```

which makes everything work fine... whenever I type it as soon as I log in to Gnome, I can thenceforth switch the layouts with my preferred key combination (alt-shift). But this seems only to 'divert' the real problem rather than actually solving it... or else I could include this command in a startup script.

---

### Post by unutbu on 2008-04-20
Edit /etc/X11/xorg.conf. Find the "InputDevice" stanza for your keyboard:
It should look something like this:

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
...
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us,gr"
    Option 	   "XkbVariant"	"101"
    Option 	   "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection
```

Log out and the log back in to make the change take effect.

---

### Post by JediKnight on 2008-04-24
I solved it... By using the gconf-editor (the key answer to my question) I fixed the sytactic problem. I restarted Gnome and the warning was no more!! Yey!! Yet it still didn't recognise the keyboard shortcut for changing the layout but no problem, I right-clicked on the icon (still no warnings) and set it up myself

It was not a matter of xorf.conf... thanks anyway

---

