---
title: "Lucid 64 in qemu: mouse movement yields high cpu usage"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lavinog on 2010-03-20
I am testing Lucid in a qemu vm.  About a month ago everything was fine.
I went about a month without updating, and last night I updated to the beta (over 300M of updates)

Now there doesn't seem to be any video acceleration...Moving the mouse causes high cpu usage, and makes the system pretty difficult to use.
I then wiped my vm, and reinstalled from the beta iso and got the same results.

The commands I have tried:
```

kvm -m 1024 Lucid_64.qcow2
kvm -m 1024 Lucid_64.qcow2 -vga std

```
both yield the same results.
I also tried a Karmic vm and everything still works...so it must be a recent update in Lucid that caused this.

I would like to file a bug report, but I am not sure what package to file it under.
Any ideas where to start?

Edit: The same thing occurs with lucid 32bit.

---

### Post by lavinog on 2010-03-27
Any ideas?
I guess I just need to file a bug report.

---

### Post by lavinog on 2010-03-30
I compared my Xorg.0.conf between lucid and karmic, and the main difference is lucid is using a VMWARE mouse:
```

(II) config/udev: Adding input device "AT Translated Set 2 keyboard" (/dev/input/event2)
(**) "AT Translated Set 2 keyboard": always reports core events
(**) "AT Translated Set 2 keyboard": Device: "/dev/input/event2"
(II) "AT Translated Set 2 keyboard": Found keys
(II) "AT Translated Set 2 keyboard": Configuring as keyboard
(II) XINPUT: Adding extended input device ""AT Translated Set 2 keyboard"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device "ImExPS/2 Generic Explorer Mouse" (/dev/input/event3)
(II) LoadModule: "vmmouse"
(II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
(II) Module vmmouse: vendor="X.Org Foundation"
	compiled for 1.7.5, module version = 12.6.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) VMWARE(0): VMMOUSE module was loaded
(II) VMWARE(0): vmmouse is available
(**) "ImExPS/2 Generic Explorer Mouse": always reports core events
(**) Option "Device" "/dev/input/event3"
(**) "ImExPS/2 Generic Explorer Mouse": ZAxisMapping: buttons 4 and 5
(II) XINPUT: Adding extended input device ""ImExPS/2 Generic Explorer Mouse"" (type: MOUSE)
(**) "ImExPS/2 Generic Explorer Mouse": (accel) keeping acceleration scheme 1
(**) "ImExPS/2 Generic Explorer Mouse": (accel) acceleration profile 0
(II) VMWARE(0): VMMOUSE DEVICE_INIT
(II) VMWARE(0): VMMOUSE DEVICE_ON
(II) VMWARE(0): vmmouse enabled
(II) config/udev: Adding input device "ImExPS/2 Generic Explorer Mouse" (/dev/input/mouse1)
(II) VMWARE(0): vmmouse is available
(**) "ImExPS/2 Generic Explorer Mouse": always reports core events
(**) Option "Device" "/dev/input/mouse1"
(**) "ImExPS/2 Generic Explorer Mouse": ZAxisMapping: buttons 4 and 5
(II) XINPUT: Adding extended input device ""ImExPS/2 Generic Explorer Mouse"" (type: MOUSE)
(**) "ImExPS/2 Generic Explorer Mouse": (accel) keeping acceleration scheme 1
(**) "ImExPS/2 Generic Explorer Mouse": (accel) acceleration profile 0
(II) VMWARE(0): VMMOUSE DEVICE_INIT
(II) VMWARE(0): VMMOUSE DEVICE_ON
(II) VMWARE(0): vmmouse enabled
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event1)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/event1"
(II) "Macintosh mouse button emulation": Found 3 mouse buttons
(II) "Macintosh mouse button emulation": Found relative axes
(II) "Macintosh mouse button emulation": Found x and y relative axes
(II) "Macintosh mouse button emulation": Configuring as mouse
(**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
(**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
(**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
(**) "Macintosh mouse button emulation": (accel) acceleration profile 0
(II) "Macintosh mouse button emulation": initialized for relative axes.
(II) VMWARE(0): vmmouse enable absolute mode
(II) VMWARE(0): vmmouse enable absolute mode

```

karmic:
```

(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.

```

Anyone have any ideas?

---

### Post by lavinog on 2010-03-30
errr...no direct rendering:
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

I was almost certain I checked this before though.

---

### Post by lavinog on 2010-03-30
Ok I didn't change anything and direct rendering works now?  Go figure...
EDIT: Ok now I get the direct rendering thing...if I use ctrl-alt-T to open a terminal I get no DRI, but if I use the terminal in the menu, I get DRI.  I came across a bug report about it.
EDIT2: here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388)
removing compiz fixed the direct rendering: No message, but now I am back to square one.
I think I am going to try a fresh install...I am still not sure where to file the bug...I am thinking that xorg would be appropriate package since /usr/bin/X is the process using all of the resources...but there are numerous bug reports claiming X is the cause of high cpu usage when it isn't...I don't want to jump the gun on this.

---

### Post by lavinog on 2010-04-01
Woohoo. I am on the right track.  Removing xserver-xorg-input-vmmouse fixes the issue.
Also looking at the changelog:
```

xserver-xorg-input-vmmouse (1:12.6.5-2ubuntu3) lucid; urgency=low

  * debian/patches/enable-detect-in-kvm.patch: add iopl() back so
    vmmouse_detect will work in kvm again.
 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>   Fri, 05 Mar 2010 09:53:29 -0500

```
That is about the time the issue started, but I find a package to downgrade to 1:12.6.5-2ubuntu2 to test this.
At least I know where to file the bug report now.
edit: Bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/553081](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/553081)

---

