---
title: "[Mouse Drivers] Corsair Katar"
date: 2016-08-05
forum: MINT
---

### Post by Runedog48 on 2016-08-05
Hello, my mouse is a 'Corsair Katar', and supports adjustable DPI, a light which can flash at different intervals ( so fancy ) and that's about it. Unfortunately, I can only configure it on Windows, and the configuration does not save when I switch over to Linux. The mouse works fine ( DPI is adjustable via the button, basic mouse operations work, but profiles are not editable ). I plan on trying to develop a driver for the device to make it work correctly. From what I've read so far I need to write the driver, and an application to control the mouse ( adjust the DPI profiles, etc. ). I don't have any prior experience with developing drivers, I planned on writing a basic driver and using it to debug/reverse engineer the mouse and hope I'm able to manipulate it so it works correctly. I do have skills with programming ( C++, C#, etc. ), but I lack skills with Linux I'm gonna need a lot of help with this project, and it's probably a bit out of my league currently, but I'm willing to give it a shot. Any help would be appreciated, I'm not even that sure on where to start. 

I was hoping that I'd be able to use a pre-existing driver and modify it to include the extra functionality. I've been trying to poke around in terminal to see what driver is currently being used for the device.

Mouse Related Information
[Logs]("http://pastebin.com/i1UVrtUW")

LSUB
[Output]("http://pastebin.com/yHdk02mh")

I've used a debugging program on Windows to retrieve the communications going to and from the mouse. [Here]("http://pastebin.com/ZBKipdCF") is what I've found so far.

---

