---
title: "Logitech UltraX - Chinese keyboard tilde character"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by fnjordy on 2006-08-23
I have a Traditional Chinese varient of the Logitech UltraX Keyboard, model no: Y-SX49.  I can configure the Keyboard Preferences to this keyboard model but the tilde key only generates a grave character.  I have "U.S. English" selected as the layout as no Chinese layouts are available to choose.

Here's a link to the keyboard:

[http://www.outletpc.com/c6454.html](http://www.outletpc.com/c6454.html)

All the media keys work as expected.

(edit) fixed.  Manually update /etc/X11/xorg.conf keyboard device to use the following:

```

Section "InputDevice"
        Identifier      "Logitech UltraX Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "logiultrax"
        Option          "XkbLayout"     "us"
EndSection

```

---

### Post by rlreich on 2006-08-23
[http://doc.gwos.org/index.php/DapperGuide#How_to_install_Chinese_Input_Method_.28SCIM.29]("http://doc.gwos.org/index.php/DapperGuide#How_to_install_Chinese_Input_Method_.28SCIM.29") I found this site with the following instructions. I hope it helps you.

 How to install Chinese Input Method (SCIM)

    * Read General Notes
    * Read How to add extra repositories
    * Read How to install Extra Fonts 


file.pngCode:

sudo apt-get install scim sudo apt-get install scim-chinese sudo apt-get install scim-config-socket sudo apt-get install scim-gtk2-immodule sudo apt-get install scim-tables-zh wget -c [http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz](http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz) sudo tar zxvf fireflysung-1.3.0.tar.gz -C /usr/share/fonts/truetype/ sudo chown -R root:root /usr/share/fonts/truetype/fireflysung-1.3.0/ sudo fc-cache -f -v


    * System -> Preferences -> SCIM Input Method Setup
    * To activate SCIM 


file.pngCode:

Press 'Ctrl + Space'

---

