---
title: "Ubuntu 16.04 LTS 64bit - screen goes black every 15 seconds"
date: 2016-09-17
forum: Installation &amp; Upgrades
---

### Post by stefan_bahrens on 2016-09-17
I am completely at a loss. On a new installation of Ubuntu 16.04 LTS  64bit my laptop screen has started to go black every 15 seconds. If I  move the mouse or click then the display returns (I do not have to log  in). Because this happens every 15 seconds the laptop is essentially  unusable. It looks like screensaver behaviour but it could be anything. 

  If I type " sudo lshw -C video | grep product: " I get -

  product: Broadwell-U Integrated Graphics
product: GM108M [GeForce 940M]

  
If I type " sudo lshw -C video " I get -

  
*-display

     description: VGA compatible controller
   product: Broadwell-U Integrated Graphics
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 09
   width: 64 bits
   clock: 33MHz
   capabilities: msi pm vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
   resources: irq:44 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:4000(size=64)
  *-display UNCLAIMED

     description: 3D controller
   product: GM108M [GeForce 940M]
   vendor: NVIDIA Corporation
   physical id: 0
   bus info: pci@0000:08:00.0
   version: a2
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress cap_list
   configuration: latency=0
   resources: memory:f1000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
  If I type "xset s off" this seems to have no effect.
  If I type " gnome screensaver " I get - 
  ** (gnome-screensaver:5014): WARNING **: screensaver already running in this session
  If I type " xscreensaver " I get -
  The program 'xscreensaver' is currently not installed. You can install it by typing: sudo apt install xscreensaver
  If I type " xset -q " I get -
  [INDENT]   Keyboard Control:
      auto repeat:  on    key click percent:  0    LED mask:  00000000    XKB indicators:      00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off      03: Compose:     off    04: Kana:        off    05: Sleep:       off      06: Suspend:     off    07: Mute:        off    08: Misc:        off      09: Mail:        off    10: Charging:    off    11: Shift Lock:  off      12: Group 2:     off    13: Mouse Keys:  off    auto repeat delay:  500    repeat rate:  33    auto repeating keys:  00ffffffdffffbbf                          fadfffefffedffff                          9fffffffffffffff                          fff7ffffffffffff    bell percent:  50    bell pitch:  400    bell duration:  100   Pointer Control:
      acceleration:  5/1    threshold:  5   
Screen Saver:

      prefer blanking:  yes    allow exposures:  yes    timeout:  0    cycle:  0   Colors:

      default colormap:  0x22    BlackPixel:  0x0    WhitePixel:  0xffffff   
Font Path:

      /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins   
DPMS (Energy Star):   Standby: 0    Suspend: 0    Off: 0

      DPMS is Enabled   Monitor is On
 [/INDENT]  Needless to stay if I go to Settings > System Settings... and make  changes to "Brightness and Lock", "Power" or "Screen Display" this has  no effect on the problem. I don't know what to do. Any help would be  appreciated.

---

### Post by stefan_bahrens on 2016-09-17
I have solved this issue. I have no idea why the problem was triggered. I don't know what the problem actually was. I don't know why or how my solution works.

I guessed that the problem was arising because of Display Power Management Signalling, or DPMS. I guessed that DPMS had been turned on by something I'd installed and that it was operating at a default setting of 15 seconds. I guessed that DPMS was turning off the display through the X server after 15 seconds (a default value) of zero activity in order to "manage power". I opened a console and typed "xset -dpms". This turns off DPMS permanently, not just for the session. The problem promptly went away.

---

### Post by Swelch87 on 2016-11-15
THANK YOU!
I had this exact same issue with my 16.10 install. The only thing I could think would have caused it is Remmina as I just started using it the other day. I also don't know how or why this happened or worked, but I'm glad you solved it.

---

### Post by ehsanjfry on 2017-08-11
Thank YOU . You solve my problem too .
i had same problem with ubuntu 16.04.

---

### Post by alanr@unix.sh on 2017-09-11
Thanks much for solving it. I just had the same problem show up with 16.04 myself. Your solution fixed my problem too!  Thanks!

---

