---
title: "Alt Gr key doesn't work any more after upgrade to 6.10"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by BioGeek on 2006-12-01
Hi all,

I upgraded to Ubuntu 6.10 via: ```
sudo gksu "update-manager -c"
```

Everything seems to work fine, except that my Alt Gr key doesn't work anymore. I have a [Belgian keyboard layout]("http://www.language-keyboard.com/layouts/belgian_french_keyboard500.jpg"), so that means that I can't type characters as the at-sign, backslash, hash, tilde, pipe, the euro-sign and opening and closing square brackets. I use Gnome as a desktop environment.

I tried a solution given in [this thread]("http://ubuntuforums.org/showthread.php?t=107077"):
```

sudo apt-get install xkeycaps
xkeycaps
```
Where I selected:
[LIST]
[*]vendor: PC
[*]keyboard: '105 key wide Delete tall Enter'
[*]Layout: 'XFree86 Belgian'
[/LIST]
Then I saved the results:
```
echo "xmodmap .xmodmap-'uname -n'" >> .bashrc
```

But that didn't help either. Neither does the command ```
setxkbmap be
```

In /var/log/Xorg.0.log I find the error message:
```
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
```

Does anyone know a solution to this problem? Thanks in advance.

---

### Post by digeratess on 2006-12-02
I've done 3 fresh Edgy installs and all had this issue, so it's not a quirk. I use a standard US keyboard, so I'm not sure how this will work for other layouts, but here's what I did to fix it.

    * System > Preferences > Keyboard > Layout Options > Third Level Choosers
    * Tick anything other than Press Right Alt key to choose 3rd level
    * Untick Press Right Alt key to choose 3rd level

---

### Post by BioGeek on 2006-12-02
Hi digeratess,

Thanks for your reply, but that didn't help either :( 

Anything else I can try?

The output of [xprop -root | grep XKB]("http://ubuntuforums.org/showthread.php?t=296483") gives me:
XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "be", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "be", "", "eurosign:e,altwin:meta_alt,lv3:rwin_switch"

I guess the problem lies in the  "lv3:ralt_switch" part. 


And gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd gives:
 layouts = []
 model = 
 overrideSettings = false
 options = [eurosign    eurosign:e,altwin       altwin:meta_alt,lv3     lv3:rwin_switch]

Thanks in advance.

---

