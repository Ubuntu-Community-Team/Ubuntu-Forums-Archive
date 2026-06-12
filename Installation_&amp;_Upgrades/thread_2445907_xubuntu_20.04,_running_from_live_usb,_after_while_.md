---
title: "xubuntu 20.04, running from live usb, after while can't click on anything"
date: 2020-06-22
forum: Installation &amp; Upgrades
---

### Post by roadcone2 on 2020-06-22
I am running xubuntu v18 on an ancient Dell with no issue. Just tried out v20.04  from live usb. Left music playing via bluetooth earphones and all seemingly well. But when I try to click pause using keyboard touch pad nothing happens. Discover than although the track pad moves the cursor, highlight focus is not working and nothing that would normally be clickable or dragable works (can't access menu, nor pause, close or click-drag to move or resize windows). Music continues to play fine. Tried the same usb on a not-so-old Asus and then on a new PC Specialist (think it is a badged Cleeve) and all three behave the same. So unlikely it is computer related. Can you offer any advice please or do you need more information from me?

---

### Post by TheFu on 2020-06-23
Just a guess, ...  perhaps the available RAM used for temporary storage is full?

Either do a real install or setup a flash boot that has an overlay file system that can be written, patched, maintained.  mkusb can do that. An 8GB flash drive can make a huge difference.  Flash storage has a limited number of writes, so beware that running an OS off it is abusive for the flash storage and will reduce the life for that storage.  I only use flash for emergency needs, perhaps running a system for a few days while some replacement storage is being shipped.  I've burned through about 10 flash drives and SDHC flash storage over the years due to the write limits.  One 64G name-brand flash drive was worn out in just over 1 year. Beware.

But really the correct answer is to do a real install into a 25G SSD or spinning HDD.  Extra storage will be needed for data, especially if you keep media files on that same storage.

People with full installs don't see this behavior, do they?

---

