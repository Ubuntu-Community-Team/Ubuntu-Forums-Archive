---
title: "Unable to pair Bluetooth mouse"
date: 2020-11-17
forum: Installation &amp; Upgrades
---

### Post by dgtangman on 2020-11-17
I have been running Ubuntu Mate 18.04 on a Lenovo Yoga 920-13IKB. I want to try out Ubuntu Desktop 20.10. I downloaded the ISO and built a USB boot drive; it boots into a desktop successfully. When I try to pair my Bluetooth mouse by bringing up the Bluetooth Settings display and turning on Bluetooth, it says it's searching for devices. When I then press the pairing button on the mouse, the mouse shows up in the Settings display marked as "Not set up". If I click on the entry for the mouse, "Not set up" changes to the Busy icon for a while, then the mouse disappears from the display and it goes back to searching for devices. From what I can gather using bluetoothctl it looks like the mouse has been recognized as a pointing device, but I may be reading too much into its output, and bluetoothctl is no more able to pair with the mouse than the graphical interface was.

Anyone have any thoughts on ways to get around this? At the moment I'm stuck - I don't have a spare hub, and the laptop only has one type A USB port, so the Bluetooth mouse is my only available option for testing with the live "CD". And I should add that I use the same mouse with 18.04 on that laptop with no issues.

**Edit: **I have now tried the same test on 20.4.1. It fails rather more immediately: When the mouse identifies itself to the laptop an entry for the mouse flashes up in the Bluetooth Settings display. It lasts for only a fraction of a second before it disappears and the interface goes back to searching for devices. In bluetoothctl there is no discernable delay between the message announcing the mouse as a new device and the subsequent message announcing that the device has been deleted.

---

