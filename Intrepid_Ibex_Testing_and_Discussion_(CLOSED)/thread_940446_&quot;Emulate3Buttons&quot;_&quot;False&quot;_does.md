---
title: "&quot;Emulate3Buttons&quot; &quot;False&quot; does not work."
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by snick525 on 2008-10-07
I am unable to get the Option on the Xorg.conf

```
Option  "Emulate3Buttons" "False"
```

to work.

Any help would be greatly appreciated.

Here is my full xorg.conf right now, I have changed almost every option you see.

```
Section "InputDevice"
        Identifier      "Logitech G7"
        Driver          "mousedev"
        Option          "Protocol"      "mousedev"
        Option          "Dev Name"      "Logitech Optical USB Mouse"
        Option          "Dev Phys"      "usb-0000:00:0b.0-6/input0"
        Option          "Device"        "/class/input/input5"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5 7 8"
        Option          "Emulate3Buttons" "false"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

---

### Post by wgrant on 2008-10-07
You shouldn't really have any input device configuration in xorg.conf any more. There are a couple of different methods now. See the Input Configuration section of [this document](https://wiki.ubuntu.com/X/Config) for details. The xinput and hal methods have their pros and cons.

---

### Post by snick525 on 2008-10-07
> **wgrant said:**
> You shouldn't really have any input device configuration in xorg.conf any more. There are a couple of different methods now. See the Input Configuration section of [this document](https://wiki.ubuntu.com/X/Config) for details. The xinput and hal methods have their pros and cons.

Thanks!

---

