---
title: "Mouse Clicks Unresponsive After Ubuntu 14.04 LTS Upgrade"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by ken40 on 2014-09-01
I just upgraded from Ubuntu 12.04 LTS to 14.04 LTS. After I upgraded I discovered that the launcher and window menu bars (File Edit View Search Tools Documents Help ) are responsive to left and right Logitech wireless optical mouse clicks, but icons within a window are not responsive unless the Shift, Ctrl, Alt  or Microsoft  key is held while the mouse button is pressed. For example, in the gedit text editor  Open Save Undo and other icons only respond to mouse clicks when one of the &#8220;augmenting&#8221; keys is pressed at the same time. Also, the same issue occurs when attempting to select text or move the cursor within the gedit window. This is not limited to gedit, it is consistent across all applications (LibreOffice, Firefox, etc.). All windows seem to behave this way.  The arrow keys and Enter do work. 

 '**cat /proc/bus/input/devices** ' shows the following information for the mouse
 
```

 I: Bus=0003 Vendor=046d Product=c50e Version=0111 
 N: Name="Logitech USB RECEIVER" 

 P: Phys=usb-0000:00:1d.2-1/input0 
 S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input5 
 U: Uniq= 
 H: Handlers=mouse0 event2  
 B: PROP=0 
 B: EV=20017 
 B: KEY=ffff0000 0 0 0 0 0 0 0 0 
 B: REL=143 
 B: MSC=10 
 B: LED=ff00
 
```

 And '**xev**' shows the following information when left and then right mouse buttons are pressed:


  
 ```

ButtonPress event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36146604, (32,30), root:(464,876),

state 0x14, button 1, same_screen YES


EnterNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36146058, (32,30), root:(464,876),

mode NotifyGrab, detail NotifyInferior, same_screen YES,

focus YES, state 276



KeymapNotify event, serial 37, synthetic NO, window 0x0,

keys: 4294967225 0 0 0 32 0 0 0 0 0 0 0 0 0 0 0

0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0



ButtonRelease event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36146716, (32,30), root:(464,876),

state 0x114, button 1, same_screen YES



ButtonPress event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36148812, (32,30), root:(464,876),

state 0x14, button 3, same_screen YES


EnterNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36146716, (32,30), root:(464,876),

mode NotifyGrab, detail NotifyInferior, same_screen YES,

focus YES, state 1044



KeymapNotify event, serial 37, synthetic NO, window 0x0,

keys: 4294967225 0 0 0 32 0 0 0 0 0 0 0 0 0 0 0

0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0



ButtonRelease event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36148940, (32,30), root:(464,876),

state 0x414, button 3, same_screen YES

```

 The following information is captured from '**xev**' while holding the left Shift key and the left and then the right mouse buttons are pressed:

 

 ```

KeyPress event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36150159, (32,30), root:(464,876),

state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,

XLookupString gives 0 bytes:

XmbLookupString gives 0 bytes:

XFilterEvent returns: False



ButtonPress event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36150532, (32,30), root:(464,876),

state 0x11, button 1, same_screen YES



EnterNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36150160, (32,30), root:(464,876),
mode NotifyGrab, detail NotifyInferior, same_screen YES,
focus YES, state 273


KeymapNotify event, serial 37, synthetic NO, window 0x0,

keys: 4294967225 0 0 0 0 0 4 0 0 0 0 0 0 0 0 0

0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0



ButtonRelease event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36150636, (32,30), root:(464,876),

state 0x111, button 1, same_screen YES



LeaveNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36150532, (32,30), root:(464,876),

mode NotifyUngrab, detail NotifyInferior, same_screen YES,

focus YES, state 17



ButtonPress event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36151116, (32,30), root:(464,876),
state 0x11, button 3, same_screen YES



EnterNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36150636, (32,30), root:(464,876),

mode NotifyGrab, detail NotifyInferior, same_screen YES,

focus YES, state 1041


KeymapNotify event, serial 37, synthetic NO, window 0x0,

keys: 4294967225 0 0 0 0 0 4 0 0 0 0 0 0 0 0 0

0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0



ButtonRelease event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36151244, (32,30), root:(464,876),

state 0x411, button 3, same_screen YES


LeaveNotify event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x0, time 36151116, (32,30), root:(464,876),

mode NotifyUngrab, detail NotifyInferior, same_screen YES,

focus YES, state 17



KeyRelease event, serial 37, synthetic NO, window 0x4200001,

root 0x2b9, subw 0x4200002, time 36151535, (32,30), root:(464,876),

state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,

XLookupString gives 0 bytes:

XFilterEvent returns: False

```

---

### Post by ken40 on 2014-09-02
I tried this command based on another article I found:

xinput

Here is the output:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB RECEIVER                   	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=8	[slave  keyboard (3)]

```

---

### Post by ken40 on 2014-09-05
I created an Ubuntu 14.04 LTS DVD bootable image and booted from it. The mouse worked fine in all situations. Does anyone have any idea about how my upgrade could have gotten messed up? Are there any packages I could try to reinstall to address the issue? Is there a way to reinstall 14.04 and leave my data intact?

---

