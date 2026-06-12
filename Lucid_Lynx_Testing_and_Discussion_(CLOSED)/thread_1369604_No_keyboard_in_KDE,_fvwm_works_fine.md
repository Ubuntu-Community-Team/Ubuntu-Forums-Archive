---
title: "No keyboard in KDE, fvwm works fine"
date: 2010-01-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by slakkie on 2010-01-01
Hello to all,

I have somewhat of a problem. I use KDE but now I cannot do anything because I've seem to lost my keyboard. I'm able to login and i'm able to switch to a VT when I'm not logged in. As soon as I login and KDE is started I lose my keyboard. I've started fvwm and my keyboard works without any issue. 

I'm troubleshooting the issue on Debian testing/unstable btw

I've tried downgrading to testing, it seems to help a bit. The keyboard is responding, but slow, I need to press a key for at least 2/3 seconds and then the input is registered. 

I found this error in my .xsession-error log file: [http://pb.opperschaap.net/138](http://pb.opperschaap.net/138)
I grepped 'keyboard' in my Xorg.0.log and this is what it returned:
```

(II) Cannot locate a core keyboard device.
(II) Initializing built-in extension XKEYBOARD
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) config/hal: Adding input device ACPI Virtual Keyboard Device
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event10"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) ACPI Virtual Keyboard Device: Close
(II) AT Translated Set 2 keyboard: Close
(EE) XKB: No components provided for device Virtual core keyboard
(II) Video Bus: Configuring as keyboard
(II) Video Bus: Configuring as keyboard
(II) config/hal: Adding input device ACPI Virtual Keyboard Device
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event10"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) Sleep Button: Configuring as keyboard
(II) Power Button: Configuring as keyboard
(II) ACPI Virtual Keyboard Device: Close
(II) AT Translated Set 2 keyboard: Close
(EE) XKB: No components provided for device Virtual core keyboard
(II) Video Bus: Configuring as keyboard
(II) Video Bus: Configuring as keyboard
(II) config/hal: Adding input device ACPI Virtual Keyboard Device
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event10"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) Sleep Button: Configuring as keyboard
(II) Power Button: Configuring as keyboard

```

Does anyone have an idea what could be happening, how to mitigate/solve the issue?

---

### Post by VMC on 2010-01-01
In checking your log file, I would be grasping at straws, but create new user and see if it persists. Changing keyboards appears to be not the issue , since you can use it on another distro. Is this a usb or plugin type keyboard. Any special keys on it?

---

### Post by slakkie on 2010-01-02
It appears to be something with my .kde dir. I removed my .kde dir and logged in and it now works again, on my Debian and Ubuntu install.

I want my old profile back since it heavily customized but with keyboard support. Anyone has a clue which config file is responsible for the keyboard bit in KDE?

---

