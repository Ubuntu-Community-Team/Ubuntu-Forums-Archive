---
title: "Can only boot into recovery mode after upgrading to 14.04LTS"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by Goettschwan on 2014-09-16
Hi, 
after having upgraded my machine to 14.04LTS I cannot boot anymore. The boot ssd disc is correctly recognized by the bios, and most of the time grub loads the selection screen for what to boot. 
If I choose "normal boot" then I get a black screen and a waiting blinking cursor. Pressing enter moves the cursor a row down. I have waited quite some time and nothing happens. If I press ctrl alt delete I can just barely see an [elapsed time] message that goes too fast away to read it but then the machine reboots. My machine has no dual boot, ubuntu only. I have two harddisks in the machine, one ssd for booting and parts of home, and one big normal harddisk for the rest.

If I choose "select operation system / last kernel : recovery mode" then there is a 3 in 4 chance the machine starts. This I can see early on, if while booting the list of "[elapsed time] message" changes appearance at a certain point then I come to the "recovery mode" prompt, where I can select "resume" and boot normally. The OS will function normally then in every way, I have no other problems on the machine. If the appearance/font does not change at that point, the boot list will continue, take some time, and then fall back to grub rescue prompt because it doesn't find a bootable disc. 

I have seen on this forum that there are quite a lot of people with similar problems, and tried some of the solutions provided as for example boot-repair. This did not really help it changes nothing about my problem. 

I am unsure what info is needed from my machine. Please advise. I understand terminal commands and such.

---

### Post by Bucky Ball on 2014-09-16
When at the blinking cursor, what happens when you press control+alt+F!? Do you get the dialogue to log in in a CLI (like a big terminal)? If so, log in and:

```
sudo startlightdm
```

... from memory (use Xubuntu myself which is a different command, depending on the set up). That may at least get you to a desktop where we can have a closer look.

---

### Post by Goettschwan on 2014-09-16
No, sorry. pressing control+alt+F just displays ^[^F and I can do it as much as I want. I just tried five reboots though, and the first two succeded in normal boot mode. 
The third, I selected choose kernel : latest kernel (normal mode), and that one hang. the two attemps after that hang, too, with normal boot. 

Is there a boot log or crash log that I could look up, where you can see the last ubuntu boot up and until it failed?

---

### Post by Bucky Ball on 2014-09-16
control+alt+**F1**

---

### Post by Goettschwan on 2014-09-16
Ah, sorry, misread the command due to typo. 
But no, pressing ctrl+alt+F1 does nothing. 
I tried typing some commands, nothing happens at all, it is as if I am writing into a void.

---

### Post by Bucky Ball on 2014-09-16
Oops, sorry. My bad. Have corrected. ;)

---

### Post by Goettschwan on 2014-09-16
Yes, as stated ctrl+alt+F1 has no effect. Is there a log in ubuntu I could check for progress while booting? I ran Suse som years ago and I remember that the progress throught boot was saved in some file there.

---

### Post by Bucky Ball on 2014-09-16
Logs are kept in /var/log.

---

### Post by Goettschwan on 2014-09-16
Can't really see anything unusual there but then again I am unsure where to look for what. I have a boot-repair summary at this link [http://paste.ubuntu.com/8359939/](http://paste.ubuntu.com/8359939/)

---

### Post by Bucky Ball on 2014-09-17
You seem to have grub installed in the MBR of sdb as well as sda. Unsure why as you don't appear to have a Ubuntu install on there. Could be the machine is attempting to boot from sdb. No OS, though. :-k

---

### Post by Goettschwan on 2014-09-18
Interesting. The default setting in boot repair is "install grub into all disks except USB". My latest attempt with boot repair before the link i posted was "purge grub from all disks" and "reinstall grub only into sda". 
Funny, that seemed to go flawless but in reality didn't function. 
I see there is a boot flag on sdb, too. I will remove this, there is only one bootable OS partition on the machine.

---

### Post by Goettschwan on 2014-09-18
I removed "quiet splash" from the grub menu. The empty space I was writing into is the waiting cursor while the system starts. Due to the annoying error with the non detected boot disc in grub this sometimes takes an eternity to start. 
I also used gparted to remove the boot flag from the documents partition on sdb. 
When restarting, all of sidebar and top menu was gone, the system did not react anymore to ctrl+alt+t or alt+F2, all window decorations were gone and I tried several solutions from elsewhere in this forum that did jack all. 
I am on the guest account in my machine now, which functions perfectly fine, and I have decided to reinstall 14.04 as I am slightly fed up. 
Thank you for your help!

---

### Post by Goettschwan on 2014-10-12
Just to lock this, the problem was the SSD disk failing. It broke completely since and cannot be accessed or found by the SATA controller. I am now on another SSD disk with a fresh install.

---

