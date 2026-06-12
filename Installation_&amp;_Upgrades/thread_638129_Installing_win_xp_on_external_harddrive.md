---
title: "Installing win xp on external harddrive"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by doppis on 2007-12-11
There is probably an easy solution to this but I figured this is the right place to get info.  I have a dell 1420n, 7.04 comes pre installed and I want to buy an external harddrive and put windows xp on it.  I was wondering what would be the steps to do this correctly and have an option at boot up to boot to my internal hd or external.  I need xp for my visual basic work and schooling, any help would be great!

---

### Post by src2206 on 2007-12-13
You can always create a partition in your main HDD (I am not sure though whether DELL allows that) and then install XP in that partition. You will need to reinstall Ubuntu's GRUB to use it back though as Windows GRUB is not that friendly to other OSes as Ubuntu's or you can edit the boot.ini file in Windows to put a choice in XP's Boot Loader.

BTW, I would have preferred to ask your question in a Forum dedicated to Windows rather than to Linux. :)

---

### Post by logos34 on 2007-12-13
After installing xp on the usb drive, you'll need to add a windows entry to grub menu.lst, [with mapping.]("http://www.users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

---

### Post by doppis on 2007-12-13
ok thankyou, I will give it a shot after christmas and post my results.

---

### Post by doppis on 2007-12-25
Well i formatted my new 320 gig simpletech and the windows xp files were copied to it, after I rebooted it said the windows/system32 hal.dll was missing or corrupted.  I have tried a couple things to see if I could get it to work but no luck.

---

