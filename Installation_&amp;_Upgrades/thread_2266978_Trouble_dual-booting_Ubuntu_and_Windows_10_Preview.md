---
title: "Trouble dual-booting Ubuntu and Windows 10 Preview"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by eschand on 2015-02-26
I just built my first PC and installed Windows 10 Technical Preview. Now, I want to dual boot Ubuntu with Windows 10, but I am running into a problem.

What I have done so far:
- Created partition on my SSD for Ubuntu in UEFI format
- Used Unetbootin to create a live USB to boot Ubuntu from
- Went into BIOS and made UEFI: USB first boot option

Now, when I boot using the UEFI: USB as first option I am brought to a screen of options: "Try Ubuntu before installing", "Install Ubuntu", etc. Upon first boot I selected Install Ubuntu and was brought to a black screen. The second boot I pressed "e" and changed "quiet splash" to "nomodeset", this brought me to an error page telling me that Windows is in hibernation and needs to be shut down fully AND NTFS partition not safe. I went through a complete shutdown of Windows and tried process again and the same thing happened.

If you have any comments or suggestions please help!

---

### Post by Mark Phelps on 2015-02-26
Windows 10 uses the same "new" form of hibernation introduced in Win8; that is, when you "shut down" Windows, it keeps all the partitions that were open still mounted, thereby preventing accessing them from another OS.  To prevent that, you have to go into Windows 10 and disable "FastStartup".  That is NOT the same as "fast boot".

---

### Post by oldfred on 2015-02-26
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

UEFI may also have a fast boot setting, which you want to turn off or set a delay if possible. The fast boot stops UEFI from scanning hardware on every reboot as it usually does not change. But it may not give you enough time to get into UEFI from whatever key your system uses. They assume you get into UEFI from Windows but if Windows is damaged then you have just about no way to get into UEFI to fix things.

---

### Post by eschand on 2015-02-27
I turned off Fast Startup and still having the same problem

---

### Post by oldfred on 2015-02-27
What motherboard & what video card?
Some have specific issues.

---

