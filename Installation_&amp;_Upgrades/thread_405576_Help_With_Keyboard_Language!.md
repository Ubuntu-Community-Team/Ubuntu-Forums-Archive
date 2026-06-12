---
title: "Help With Keyboard Language!"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by xe1ufo on 2007-04-09
Dear Friends:

I had a wonderfully working Ubuntu 6.06 install. Then I got the bright idea of upgrading to 6.10. I have everything working fine (Samba server, etc.) EXCEPT I cannot get the Keyboard Language select to work. I am trying to make my keyboard Spanish from Spain.  I get the following notice:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
(This gives me this: _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "es", "es", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "es", "es", "lv3:ralt_switch")

- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
(This gives me this:
 layouts = []
 model = pc105
 options = [lv3 lv3:ralt_switch,grp_led grp_led:num,altwin      altwin:alt_super_win]
 overrideSettings = true)

Thanks in advance for any help!

Dr. Steve, central old Mexico
:confused:

---

### Post by zorkerz on 2007-04-10
Oh man i had a similar problem reciently. Im going to try and remember how i fixed it / a link to what helped me. If youve already soled this please let us know how.
Hopefully i will be back.  

I think it had to do with xorg.conf and/or one other xkb config file.

---

### Post by zorkerz on 2007-04-10
Ok here is what i think may help.

Check /etc/default/console-setup for **XKBLAYOUT="dvorak,us"**

and /etc/X11/xorg.conf for       ** Option         "XkbLayout" "dvorak,us"**

These should i believe both be the same in your case probably replace my dvorak,us with "spanish" (or maybe spain).

Don't forget to back up these files before you change them but i think this should get ride of the error.

Note: this may be gnome specific

Hope this helps let us know.

---

### Post by zvacet on 2007-04-11
[https://help.ubuntu.com/community/LocaleConf]("https://help.ubuntu.com/community/LocaleConf")

---

### Post by xe1ufo on 2007-04-11
Hey, Zorkers:

Thanks for your ideas!  But it didn't work.


Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"es"

Steve, central old Mexico

---

### Post by zvacet on 2007-04-11
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way")

---

### Post by xe1ufo on 2007-04-17
I certainly appreciate everybody's ideas!!! But alas... still no working Spanish keyboard.
SOOOOO FRUSTRATING!!!

Here is my latest error report --- 
---------------------------------------------------
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by zorkerz on 2007-04-17
Sorry to hear no solution yet.
if i remember right my problem was slightly different but it caused me to get the same error.
Here is the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/90311") not sure it will really help but i have no other ideas for you at this time.

hope you find something

---

### Post by xe1ufo on 2007-04-25
Dear Friends:

After trying everything suggested by everybody, and not having success, I got a wild idea.  I did an online upgrade from Ubuntu 6.10 to Ubuntu 7.04 Feisty.  ALL PROBLEMS RESOLVED!!

Thanks to everybody for their kind input!

Dr. Steve, central old Mexico.:)

---

