---
title: "How to select English (US) keyboard layout when preseeding with Ubiquity."
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by arto7177 on 2013-04-05
I am attempting to automate an install of the Ubuntu 12.10 LiveCD (on a  USB). The Installer will do everything except automatically pick a  keyboard layout. Below is the portion of my preseed3.cfg that should  select the language and keyboard layout. Ubiquity will correctly install  everything, It just requires that I choose a keyboard layout before it  will proceed. Is English (US) the correct argument (I have also tried USA, en, and English) or is there another preseed option which selects the layout.
```

ubiquity    languagechooser/language-name   select  English
ubiquity    countrychooser/shortlist    select  US 
ubiquity    time/zone   select  America/Los_Angeles 
ubiquity    debian-installer/locale select  en_US.UTF-8 
ubiquity    localechooser/supported-locales multiselect en_US.UTF-8 
ubiquity    console-setup/ask_detect    boolean false 
ubiquity    console-setup/layoutcode    string  us
ubiquity    console-setup/modelcode string  SKIP
ubiquity    keyboard-configuration/variant  select  English (US)
ubiquity    keyboard-configuration/layout   select  English (US)
ubiquity    keyboard-configuration/model    select  Generic 105-key (Intl) PC
ubiquity    console-keymaps-at/keymap   select  us
ubiquity    keyboard-configuration/xkb-keymap   select  us
console-setup   console-setup/layoutcode    string  us
console-setup   console-setup/layout    select  U.S. English
console-setup   console-setup/variantcode   select  U.S. English
```

Here is the portion of my menu which launches the installer and loads preseed3.cfg into the initrd. My understanding is that I may need an argument which specifies the layout before ubiquity actually launches. I do not know which argument to use if one is needed.

```

label unattended menu label ^Unattended Installation kernel /casper/vmlinuz append cdrom-detect/try-usb=true file=/cdrom/preseed/preseed3.seed boot=casper automatic-ubiquity initrd=/casper/initrd.lz quiet  splash noprompt  ---
```

If anyone also knows a location where I can find all the arguments which can be used in the preseed, [https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt](https://help.ubuntu.com/12.04/installation-guide/example-preseed.txt) does not contain them all I might be able to solve this problem.

---

### Post by dino99 on 2013-04-05
similar blogpost; maybe you'll find the answer : [http://www.mybinarylife.net/2011/07/ubuntu-1104-custom-ubiquity-installer.html](http://www.mybinarylife.net/2011/07/ubuntu-1104-custom-ubiquity-installer.html)

---

### Post by grahammechanical on 2013-04-05
What you are doing is way beyond my skill set. So, all I can give is another pair of eyes. From the link that you give I see this:

> 
# Keyboard selection.# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
#d-i keyboard-configuration/modelcode string pc105d-i 
keyboard-configuration/layoutcode string us
# To select a variant of the selected layout (if you leave this out, the
# basic form of the layout will be used):
#d-i keyboard-configuration/variantcode string dvorak

And from the link provide by dino99 I see this:

> [FONT=Arial]# Detect keyboard layout?[/FONT]
[FONT=Arial]keyboard-configuration console-setup/ask_detect boolean false[/FONT]
[FONT=Arial]keyboard-configuration console-setup/detected note[/FONT]
[FONT=Arial]keyboard-configuration  keyboard-configuration/model select Generic 105-key (Intl) PC[/FONT]

I compare it with your arguments and I see a difference:

> ubiquity console-setup/ask_detect boolean false
ubiquity console-setup/layoutcode string us
ubiquity    console-setup/modelcode string  SKIP

It may be just nothing. Regards.

---

### Post by arto7177 on 2013-04-06
I just want to say I figured it out. As i suspected I did need to add another argument to the append in my text menu.  I stumbled onto this blog post [http://sshrootat.blogspot.com/2011/04/preseeding-ubuntu-natty-1104.html](http://sshrootat.blogspot.com/2011/04/preseeding-ubuntu-natty-1104.html) after posting. I added bother [FONT=Courier New]keyboard-configuration/layoutcode=us and [/FONT][FONT=Courier New]console-setup/ask_detect=false[/FONT]. My final append ended up looking like. ```
append cdrom-detect/try-usb=true file=/cdrom/preseed/preseed3.seed [FONT=Courier New]keyboard-configuration/layoutcode=us and [/FONT][FONT=Courier New]console-setup/ask_detect=false[/FONT] boot=casper automatic-ubiquity initrd=/casper/initrd.lz quiet  splash noprompt  ---
```
I am not sure if [FONT=Courier New]console-setup/ask_detect=false[/FONT] is needed, but I put it in just to be sure.

---

