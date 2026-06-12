---
title: "Lenovo ThinkPad T410s Compatibility"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by undoIT on 2010-02-11
Has anyone ordered the ThinkPad T410s and put Ubuntu on it? I'd like to know how compatible it is. I will be buying this as my next laptop (primary laptop that I use for work 8-12 hours a day) as long as I can get *buntu running properly on it. Currently, only models with the integrated graphics are available. I'm holding out for the switchable graphics.

Another question, do any owners of the T400s have problems with the switchable graphics? Is there a way to switch from integrated to discrete with software or is this only possible the bios?

---

### Post by jimirn on 2010-03-30
**Right now the hardware issues with Lenovo T410s and Ubuntu Lucid (10.04 latest updates) are**:
- Sound card is not detected, but manual workaround possible: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538383)
- Wlan not working properly, I have several crashes every day:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539733)
- Left mouse button stops working after disconnecting/reconnecting AC-powersupply (both trackpoint and touchpad) - I dont know why this happens ?
- The Fn-button and most F-shortcuts dont work (dont know if this is normal with other Lenovo laptops)

---

### Post by undoIT on 2010-04-17
I'm testing out Kubuntu 10.04 and have the latest bios installed (1.11). Here's a list of the issues I'm having:

1. Sound card not detected, easy fix as mentioned
2. Suspend to RAM not working properly, second time causes system to reboot.
3. TrackPoint sensitivity cannot be permanently adjusted, as mentioned here: [http://ubuntuforums.org/showthread.php?t=1454452](http://ubuntuforums.org/showthread.php?t=1454452)
4. Most function keys seem to be working. The only one that doesn't appear to be working properly is the key to switch between laptop screen and external monitor.
5. Multi-touch is not working for TrackPad :(  I was really hoping for two finger scroll and right click. Perhaps there is a hack, but this seems to be an issue with the T400s as well. Hopefully a Synaptic driver update is coming.

I do not have the issue where left mouse button stops working. Tested several times. Also, the wireless hasn't given me any trouble (Intel Ultimate-N 6300) although I haven't tested it for an extended period of time yet.

Another issue which may just be figuring out how to configure, is that the brightness setting is not remembered between reboots. The power daemon always sets the brightness to the profile level, rather than remembering the level I had adjusted using the Fn keys.

---

