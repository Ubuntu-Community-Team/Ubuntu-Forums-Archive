---
title: "Windows Installer wont work?"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by zRW8b6z on 2013-10-05
I'm at my wits end. I've tried installing through various ways but it just won't work. I'm using windows XP and at this point I don't care if I can dual boot anymore. Could someone please just show me how to install it? It would be a huge help! Oh at my computer can't boot from USB it can only boot from the CD drive. I really want to enjoy ubuntu!!
Tell me if you need anymore editional information about my computer

---

### Post by The Cog on 2013-10-05
These two links should help:
[http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Come back here if you have further questions.
And welcome top the forums.

---

### Post by zRW8b6z on 2013-10-05
That says I need the desktop CD I've tried burning the iso to a cd and rebooting my computer but it didn't work. I even changed the BIOS. Thanks for the welcome :)

---

### Post by zRW8b6z on 2013-10-05
Help? :(

---

### Post by grahammechanical on 2013-10-05
It did not work? How did it not work? Please explain what you see happening on the screen. Oh, What do you mean by "Windows installer?" Are you trying to install Ubuntu inside XP using Wubi.exe? There is lots of information about your machine that you could supply. The hardware specification. The version of Ubuntu. At this point we do not even know if your machine has a DVD drive. Ubuntu ISO images are now too large to fit on a standard CD disk. There could be any number of reasons why it does not work. How can we know?

Regards.

---

### Post by zRW8b6z on 2013-10-05
Okay so the installer works fine (I'm using this one [http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)) but when it reboots I don't get any option to boot up ubuntu, even if I go to the boot menu. I'm trying to use ubuntu 12.04. I've downloaded it onto a 4GB DVD and it didn't work. I do have a DVD drive.
Thanks for trying to help me resolve this issue. I appreciate it.

---

### Post by hakuna_matata on 2013-10-05
> **zRW8b6z said:**
> ....even if I go to the boot menu.
Boot menu of windows XP ? In windows XP run "msconfig.exe" and configure "boot.ini" section. Check if timeout limit is more than 0 seconds and if there is an entry for ubuntu.

edit: Sample for boot.ini with wubi menu entry (last line):
```
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP"
C:\wubildr.mbr = "Ubuntu"
```

edit2: There is no need to burn a desktop CD/DVD for installing with wubi (windows installer), but there is also no need to use wubi.

---

### Post by zRW8b6z on 2013-10-06
> **hakuna_matata said:**
> Boot menu of windows XP ? In windows XP run "msconfig.exe" and configure "boot.ini" section. Check if timeout limit is more than 0 seconds and if there is an entry for ubuntu.

edit: Sample for boot.ini with wubi menu entry (last line):
```
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP"
C:\wubildr.mbr = "Ubuntu"
```

edit2: There is no need to burn a desktop CD/DVD for installing with wubi (windows installer), but there is also no need to use wubi.


Thank you so much!! You don't know how grateful I am. I have another question though, how do you install things like skype, google chrome, and minecraft on ubuntu?

---

### Post by BlinkinCat on 2013-10-06
> **zRW8b6z said:**
> Thank you so much!! You don't know how grateful I am. I have another question though, how do you install things like skype, google chrome, and minecraft on ubuntu?

Hi,

You should start a new thread with descriptive heading for each question in the most appropriate forum.

Cheers - :p

Edit: If this thread has been resolved, you should mark it as solved using the thread tools at top of page.

---

