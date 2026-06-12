---
title: "Grub trouble... Windows 7 + Karmic"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by Loge on 2009-12-31
Hi everyone,

for a while now, I've been using a dual boot setup of Windows 7 and Ubuntu. I upgraded to Karmic Koala, but stopped using Ubuntu when, after a clean Windows 7 install, grub disappeared.
Today, I wanted to boot into ubuntu again. So, I made a Live USB thumbdrive. Then, in the terminal, I followed the instructions for recovering grub 2 - this might have been my mistake, as I was possibly using grub 1 still, having only upgraded Ubuntu.
Anyway, now, when I restart, I get a command line interface for grub 1.97 or so. There is no menu.lst, and my boot.cfg seems to be completely empty, too. When I try "update-grub", it just tells me "cannot find a device for /".
I'm writing this off the live-drive, and am pretty clueless as to what to do. To make matters more annoying, I am currently not at home and have not brought my Windows 7 DVD with me - I probably should have been more careful...
Is there a way of fixing my grub?

Thanks a tonne,

Loge

---

### Post by darkod on 2009-12-31
I'm not sure if it will work because you probably only had grub1, but try the procedure to reinstall grub2 from here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look at number 2) Using Ubuntu 9.10 live cd. And do both sets of commands, also for missing grub.cfg, because you say yours is empty.
I'm puzzled why menu.lst doesn't exist at least though.

---

### Post by Loge on 2009-12-31
Hi darkod,

thanks a lot! Well, it didn't quite work out. I followed the instructions, and everything worked without an error.
Now, I have a menu.lst which looks very nice and complete; however, despite following all instructions, I have no grub.cfg! I tried the procedure again, but it still won't appear...
What can I do?

Thanks a lot,

Loge

---

### Post by darkod on 2009-12-31
Did you try to reboot and check if it will work? Since grub1 was not upgraded I'm not exactly sure whether grub.cfg needs to appear.
It might work like this too.

---

### Post by phillw on 2009-12-31
Ah,

you 'upgraded' to 9.10 -- if you still have Grub Legacy, then you'll want to pop over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And use the Section on **pre** 9.10

Or, you could put Grub2 on -- it's quite painless and is covered in this excellent Wiki --> [https://help.ubuntu.com/community/Grub2#Installation](https://help.ubuntu.com/community/Grub2#Installation)

Regards,

Phill.

/edit - Ooosp, Soz, darkod - I mis-read your time stamp - I'll leave the OP in your more than capable hands !!

---

### Post by Loge on 2009-12-31
> **darkod said:**
> Did you try to reboot and check if it will work? Since grub1 was not upgraded I'm not exactly sure whether grub.cfg needs to appear.
It might work like this too.
I have, and it still gives me the dreaded command prompt :-(
Is there anything else I could try?

Thanks in advance!

---

### Post by Loge on 2009-12-31
Just a quick update: Grub works now that I've managed flags in GParted to set my Linux sda to boot...
There is no entry for Windows at the moment - what do I have to do for that?
At the moment, I'm quite happy in ubuntu, though :-)

Thanks for the help!

---

