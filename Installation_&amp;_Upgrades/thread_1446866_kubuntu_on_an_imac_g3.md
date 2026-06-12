---
title: "kubuntu on an imac g3"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by gwvenus on 2010-04-04
Hi Everyone,
I've just been given an imac g3 slot load and it seemed like a good idea to install kubuntu on it. the install went pretty smooth but I have some issues.
When I check the display settings the only choice I have is 800x600, I have no real color and the refresh rate is 186hz. I've googled until my eyes are sore and can't find any solutions. I did find a script but I have no idea how to install it. 
This is the script I found:

EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "CCEusecTimeout" "100000"
#Option "UseFBDev" "true"
EndSection

Can I use this script and if so how do I install it? Is there a command line I can use to back up and restore the old script in case I make a mistake? I'm pretty much still a noobie but I'm a linux fanboy all the way! If anyone has the time they would have to hold my hand and walk me through the process. I couldn't even figure out how to install this script as root. The imac uses an ati rage card. Maybe there is an easier way? Any suggestions would be greatly appreciated!!
Thanks Again,
Gary

---

