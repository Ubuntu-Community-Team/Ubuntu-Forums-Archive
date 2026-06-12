---
title: "problem of using SmartBootManager"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by qiushiwang on 2006-06-28
For some reason, I can not boot from my CDROM, so I use SmartBootManager to boot from CDROM.
But when I boot from the floppy, I can not find the "menu option with CDROM in it". What should I do?
Thanks.

---

### Post by confused57 on 2006-06-28
What options do you see when you boot from the SBM floppy?  I've used it on an old computer of mine and it has an option to boot from CD in SBM.
Did you burn the sbm file "as an image" to floppy using rawrite?

---

### Post by qiushiwang on 2006-06-28
[QUOTE=confused57]What options do you see when you boot from the SBM floppy?  I've used it on an old computer of mine and it has an option to boot from CD in SBM.
Did you burn the sbm file "as an image" to floppy using rawrite?[/QUOTE]

Yes, I did use rawrite to make the floppy.
The menu I see has " quit to BIOS, reboot, boot from harddisk, boot from hd0-1, boot from hd0-5 ". I tried every option, some lead to Windows, some lead to a boot error.What should I do?
Thanks for your help.

---

### Post by confused57 on 2006-06-28
Here's the guide I used to create a SBM floppy:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

I don't know why your menu doesn't give you the option of booting from your CD drive.  I've made a couple of SBM floppies and they both give that option.

---

### Post by qiushiwang on 2006-06-28
[QUOTE=confused57]Here's the guide I used to create a SBM floppy:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

I don't know why your menu doesn't give you the option of booting from your CD drive.  I've made a couple of SBM floppies and they both give that option.[/QUOTE]

Yes, I made the floppy according to that document..

---

### Post by confused57 on 2006-06-28
If you have Windows installed, what happens when you insert the Ubuntu CD into your drive in Windows?

Make sure to set your floppy drive as the first boot option.  What I do is insert both the floppy and the Ubuntu CD when I start my computer, then the SBM floppy boots & gives me the option to boot from the CD drive.
If that doesn't work, I don't really know what's different with your system.
Good luck with it.

---

