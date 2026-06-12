---
title: "appletouch.fdi on karmic?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stephana on 2009-10-03
Hi,

I've installed Karmic Beta on my Macbook 4.1, but appletouch is not working. I've tried to create appletouch.fdi in /etc/hal/fdi/policy/ like in Jaunty, but nothing happend.

Does anyone know how to get this working?

greetz from germany, stephana

---

### Post by hotfigs on 2009-10-10
The driver seems to work fine for me, as the two finger right click bit works fine, but the appletouch.fdi configuration is ignored. Macbook 2,1

---

### Post by hanzomon4 on 2009-10-10
maybe [sudo modprobe appletouch]

---

### Post by hotfigs on 2009-10-11
lsmod | grep appletouch shows that it is loaded. Interestingly, it does seem that hal is loaded my appletouch.fdi, but the settings aren't being used. When I do a hal-device I get this:

```
39: udi = '/org/freedesktop/Hal/devices/usb_device_5ac_21b_noserial_if1_logicaldev_input'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.touchpad' } (string list)
  input.device = '/dev/input/event8'  (string)
  input.product = 'appletouch'  (string)
  input.x11_driver = 'synaptics'  (string)
  info.subsystem = 'input'  (string)
  input.product = 'appletouch'  (string)
  input.x11_driver = 'synaptics'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'appletouch'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5ac_21b_noserial_if1_logicaldev_input'  (string)
  input.x11_options.SHMConfig = 'true'  (string)
  input.x11_options.VertEdgeScroll = 'false'  (string)
  input.x11_options.HorizEdgeScroll = 'false'  (string)
  input.x11_options.VertTwoFingerScroll = 'true'  (string)
  input.x11_options.HorizTwoFingerScroll = 'false'  (string)
  input.x11_options.VertScrollDelta = '20'  (string)
  input.x11_options.RTCornerButton = 'false'  (string)
  input.x11_options.RBCornerButton = 'false'  (string)
  input.x11_options.LBCornerButton = 'false'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  input.x11_options.TopEdge = '0'  (string)
  input.x11_options.LeftEdge = '0'  (string)
  input.x11_options.RightEdge = '1100'  (string)
  input.x11_options.BottomEdge = '800'  (string)
  input.x11_options.FingerLow = '5'  (string)
  input.x11_options.FingerHigh = '15'  (string)
  input.x11_options.TapButton1 = '0'  (string)
  input.x11_options.TapButton2 = '0'  (string)
  input.x11_options.TapButton3 = '0'  (string)
  input.x11_options.LTCornerButton = 'false'  (string)
  input.x11_options.ClickFinger1 = '1'  (string)
  input.x11_options.ClickFinger2 = '3'  (string)
  input.x11_options.ClickFinger3 = '2'  (string)
  input.x11_options.MinSpeed = '0.25'  (string)
  input.x11_options.MaxSpeed = '2.5'  (string)
  input.x11_options.AccelFactor = '0.15'  (string)
  input.x11_options.PalmDetect = 'true'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input10/event8'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5ac_21b_noserial_if1'  (string)
  info.category = 'input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5ac_21b_noserial_if1'  (string)
```

So I guess either there must be something wrong with either this configuration (which worked fine on jaunty) or the way this config is picked up by HAL?

---

### Post by hotfigs on 2009-10-11
I've found a solution: install **gpointing-device-settings**. As far as I can tell, it's a replacement for gsynaptics. It lets you configure the touchpad via a GUI and has an option to enable two finger scrolling.

---

### Post by hotfigs on 2009-10-12
Does anyone know what configuration files are used now? What is the replacement for appletouch.fdi?

I've fixed two finger scrolling (btw it also is an option in System -> Preferences -> Mouse), but now the two-finger right click doesn't work :P

---

