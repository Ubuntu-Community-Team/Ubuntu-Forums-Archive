---
title: "Changes not saved on USB stick"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by boerenjos on 2010-12-30
I have a Xubuntu 10.10 (Merkat) installed on boot-able usb drive.
This is working fine , however changes on e.g. timezone settings, accounts created in thunderbird are not stored on the USB stick? Who can help me? KR Jos B :popcorn:

---

### Post by mcduck on 2010-12-30
When you created the USB drive did you check the option to use remaining space for persistence file?

If not, it's just the same as a regular Live-CD and no settings are saved. There's nothing to save them to.

edit: of course if you 
made and actual, normal install to the drive then your settings *should* be saved.

---

### Post by C.S.Cameron on 2010-12-30
Startup Disk Creator from the Ubuntu Live CD and Universal from Pendrivelinux.com have persistence options UNetbootin does not.

All Ubuntu pendrive methods can be made persistent by adding casper-rw and/or home-rw partitions and editing the text.cfg or syslinux.cfg file.

---

### Post by boerenjos on 2010-12-30
Hi , please to meet you. I am a newbie.  I can't remember exactly the settings when I installed the USB stick. I used USB creator. In the attached file i captured the settings from gparted. Everything looks fine?

---

### Post by C.S.Cameron on 2010-12-30
Plug your stick into a running computer and see if there is a file named casper-rw, This is is where persistent changes are saved.
If not, run Startup Disk Creator again and select some Stored in reserved extra space.

---

### Post by boerenjos on 2010-12-30
Thx, guys for the tips and tricks. The problem is solved. Have a nice day and a good turnaround of the year.
See you once again. Bye:p

---

