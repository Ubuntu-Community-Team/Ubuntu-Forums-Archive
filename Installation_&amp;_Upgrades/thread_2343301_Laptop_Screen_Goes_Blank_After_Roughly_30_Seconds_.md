---
title: "Laptop Screen Goes Blank After Roughly 30 Seconds Of No Mouse Movement"
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by davismatthers on 2016-11-15
I'm a novice at Linux/Ubuntu. I installed Kubuntu and have configured  the Power Management and Display And Monitor settings appropriately.  I've installed Caffeine, and have tried multiple times to prevent the  screen from going blank. I've followed other articles and tried  disabling the Screen Blanking feature. I've also disabled all the power  saving options.


  **Issue: **After 31 seconds of not moving the mouse, even if multimedia -  including web-based multimedia - is still playing, the screen goes  blank. Please give me very specific instructions when referring to the  Terminal commands and their respective directories. 


  Thank you in advance.


  **Troubleshooting performed: **
mv ~/.kde ~/.kde.old 
mv ~/.cache ~/.cache.old 
mv ~/.local ~/.local.old 
mv ~/.config ~/.config.old 
shutdown -r now 
Disabled Hardware Acceleration in Firefox and Chromium 
 rm ~/.local/share/kscreen  
sudo killall sddm 
Tried New Sessions

  **xset -q revealed the following: **
xset -q Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off     03: Compose:     off    04: Kana:        off    05: Sleep:       off     06: Suspend:     off    07: Mute:        off    08: Misc:        off     09: Mail:        off    10: Charging:    off    11: Shift Lock:  off     12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  600    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled


  **Some Specs:** Kubuntu 16.10 KDE Plasma Version 5.7.5 KDE Frameworks Version 5.26.0 Qt Version 5.6.1 Kernel Version 4.8.0-27-generic OS Type 64-bit Dell Latitude E5410

---

### Post by davismatthers on 2016-11-15
Also ran: 

xset -dpms xset s noblank

grep -iA2 vga 00:02.0 VGA compatible  controller: Intel Corporation Core Processor Integrated Graphics  Controller (rev 02)         Subsystem: Dell Core Processor Integrated  Graphics Controller         Kernel driver in use: i915

---

