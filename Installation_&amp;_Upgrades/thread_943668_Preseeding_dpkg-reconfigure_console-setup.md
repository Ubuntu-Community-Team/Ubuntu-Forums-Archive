---
title: "Preseeding dpkg-reconfigure console-setup"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by cilkay on 2008-10-10
Hello,

I am striving to have a totally hands-off installation using preseeding. I have considered other alternatives like DRBL/Clonezilla, FAI, and kickstart and have rejected them because preseeding seems to be the preferred Debian/Ubuntu way of integrating with the Debian Installer (d-i).

If I specify en_US as the locale, the installation will work fine. However, if I specify en_CA, the first time I attempt to log into the console, the keyboard mapping will be incorrect and I'll see multiple diamonds for every keystroke. Typing blindly does not work. To work around this, I log in remotely via ssh and then run "dpkg-reconfigure console-setup" to set up the console and then I can log in via a local console. This is not a desirable situation given the requirement to do hands-off installations.

I have tried the following in my preseed file but it has not made any difference. I extracted the values below using debconf-get-selections on a system that I had installed manually. Any ideas on how I can do away with the need to reconfigure the console manually after a preseed installation?

```
# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i console-setup/variantcode string
d-i console-setup console-setup/variant select USA
d-i console-setup console-setup/charmap select UTF-8
d-i console-setup console-setup/toggle select No toggling
d-i console-setup console-setup/compose select No compose key
d-i console-setup console-setup/fontsize-text select  16
d-i console-setup console-setup/optionscode string
d-i console-terminus console-terminus/new_file_names note
d-i console-setup console-setup/layout select  USA
d-i console-setup console-setup/detect detect-keyboard
d-i console-setup console-setup/detected note
d-i console-setup console-setup/codesetcode string Lat15
d-i console-setup console-setup/dont_ask_layout error
d-i console-setup console-setup/modelcode string pc105
d-i console-setup console-setup/ask_detect boolean true
d-i console-setup console-setup/altgr select No AltGr key
d-i console-setup console-setup/ttys string /dev/tty[1-6]
d-i console-setup console-setup/model select Generic 105-key (Intl) PC
d-i console-setup console-setup/fontsize-fb select 16
d-i console-setup console-setup/switch select No temporary switch
d-i console-setup console-setup/codeset select # Latin1 and Latin5 - western Europe and Turkic languages
d-i console-setup console-setup/toggle select  No toggling
d-i console-setup console-setup/fontface select VGA
d-i console-setup console-setup/fontsize string 16

```

---

