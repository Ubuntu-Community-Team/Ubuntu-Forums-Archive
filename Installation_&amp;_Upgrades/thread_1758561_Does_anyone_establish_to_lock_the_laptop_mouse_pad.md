---
title: "Does anyone establish to lock the laptop mouse pad"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by jao_madn on 2011-05-14
Hi,

I just wondering if someone in the linux specifically ubuntu community accomplish on locking the mouse pad built in in the laptop just like in the windows where you can Fn+lock if im not using it and using a usb mouse instead. mine is an asus laptop.

Thanks for any reply..

---

### Post by jao_madn on 2011-05-15
Below is the procedure i used to accomplished my objective:

1. issue command #xinput list
output: 
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                   id=15    [slave  keyboa
```2. Determine touchpad mouse ID in my case i had two mouse the USB mouse and the touchpad. the touchpad is > ImPS/2 Logitech Wheel Mouse                 id=13    [slave  pointer  (2)] 3. Disable the touchpad using id 13 in the above result. Issue this command to disable
```
xinput set-int-prop 13 "Device Enabled" 8 0
```4. To enable back again the touchpad change the value of 0 to 1 in the above command like this one.```
xinput set-int-prop 13 "Device Enabled" 8 **1**
```5. The disable  command well be reset upon reboot. to make it easy to me i used alias like ```
alias moff='xinput set-int-prop 13 "Device Enabled" 8 0' ---> disable
alias mon='xinput set-int-prop 13 "Device Enabled" 8 1' ---> enable
``` or create keyboard shortcut its up to you..

My laptop is ASUS U30JC


Thanks for reading.

---

