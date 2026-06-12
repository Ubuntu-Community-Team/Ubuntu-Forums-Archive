---
title: "Xp and Ubuntu netbook dual boot hell!"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by smoker_dave on 2010-07-08
Hey,
 
I have done quite a bit of reading around already. Seems a few people have similar problems but never exactly the same as me..
 
I have a netbook running Windows XP as standard. There is also a recovery partition which came from the factory.
 
In the past I installed Ubuntu (I think 9.something) from USB key and all worked fine. However my XP became corrupted and I needed to do a repair on it. After this, Ubuntu became removed from the boot select menu.
 
Since then, Ubuntu has become updated to 10.04, which I now cannot install.
 
The Live CD tells me there is a "file IO error" and simply stops installation at around 70%.
 
I did manage to get into Ubuntu from a Live USB using Wubi. However when I chose to install Ubuntu to a Harddrive, the option to "install side by side" was missing.
 
After reading on the forums, I did a chkdsk /f on Windows and tried again. Now my liveUSB does not show a boot menu!
 
When I select to boot from USB stick, the screen goes blank with a flashing cursor. Ctrl+alt+dlt reboots.
 
I'm really lost here! It seems when I fix one problem, another problem arises!
 
Also when trying to instal Ubuntu within Windows, the process goes through to 100% and asks me to reboot. When I do so, the option for Ubuntu does show in the boot menu. However when I select it, I get an error "Windows boot failed: file wubildr.mbr and status: 0xc00000f - something is corrupt".
 
Please help me! I have been teased with Ubuntu and now I am not allowed to use it however I try!

---

### Post by smoker_dave on 2010-07-09
No replies! Great Support!
 
I have made a second liveUSB stick, checked md5 sum.
 
I deleted the old ubuntu partitions, used partition magic within windows to reclaim them into my windows partition and did a fresh instal.
 
This worked nicely. I was into Ubuntu all working fine.
 
Now Ubuntu decides to do an automatic update, and another big head ache.
 
After the update, my display is madly blinking. Only the desktop image is shown, no menus. The screen flicks between that and a grey box with arrows on it.
 
there is a black cross in the middle of the screen and no mouse.
 
I could get into low graphics mode, again with no mouse. I could not modify the graphics settings from within this emergency boot menu. Clicking the option did nothing!
 
Really great...
 
Anyway, I went through the process again (delete and reclaim partition, reinstall from usb). But this time I dissabled automatic updates.
 
Maybe my system is not secure but at least it is stable.
 
In all the years of Windows, there has never been an "update" which completely f-cked my system and forced me to format and reinstall.
 
You really expect me to concider Ubuntu as my main system? For working and saving important files?
 
You must be joking!
 
See you around.

---

