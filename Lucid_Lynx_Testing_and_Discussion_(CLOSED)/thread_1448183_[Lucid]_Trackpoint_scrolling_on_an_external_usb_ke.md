---
title: "[Lucid] Trackpoint scrolling on an external usb keyboard"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whtvr on 2010-04-06
Hi,

I was playing around with Lucid beta1 and it looks pretty good so far. The only thing I couldn't figure out is how to enable middle mouse button scrolling on an [COLOR=DarkRed][external usb keyboard.]("http://shop.lenovo.com/SEUILibrary/controller/e/gbweb/LenovoPortal/en_GB/catalog.workflow:item.detail?GroupID=38&Code=55Y9041&current-category-id=E9ADAEB6787146E29B78400A33E7FE8A&&hide_menu_area=yes")[/COLOR]

On karmic I was able to enable that functionality using the [COLOR=DarkRed][fdi configuration file for HAL]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Configuration_using_udev_and_HAL").[/COLOR] Since afaik there is no HAL in lucid I had to use gpointing-device-settings which works fine for the trackpoint on the laptops internal keyboard but not on the above mentioned external keyboard hooked up to the laptop via usb port on the dockingstation. I do not see this device on the list in gpoint-device-setting and frankly, was unable to find any meaningful reference to the so called ["DevKit method"]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Configuration_using_DevKit").

If anybody has an idea what to do with this problem I would be grateful for help.

Thanks

---

### Post by whtvr on 2010-04-08
Ok, let me rephrase the question in a more general way - how can I do whatever gpoint-device-setting does using a command line and/or a configuration file? As per my previous post, gpoint-device-setting does not seem to recognize my keyboard (it only list the internal trackpoint and a usb mouse).

I can use the external keyboard fine and the trackpoint along with mouse buttons also work ok but I cannot enable middle mouse scrolling emulation.

Once again, thanks a lot for your help.

---

### Post by Killigrew on 2010-04-08
Hi

Put the folling lines in a script file:
```
xinput set-prop 'TPPS/2 IBM TrackPoint' "Evdev Wheel Emulation" 1
xinput set-prop 'TPPS/2 IBM TrackPoint' "Evdev Wheel Emulation Button" 2
xinput set-prop 'TPPS/2 IBM TrackPoint' "Evdev Wheel Emulation Timeout" 200
```for TPPS/2 IBM TrackPoint you should put in the name of your keyboard pointing device.

greetings :)

---

### Post by whtvr on 2010-04-08
a related issue: [https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754)

---

