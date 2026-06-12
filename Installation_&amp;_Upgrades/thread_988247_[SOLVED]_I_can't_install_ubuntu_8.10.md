---
title: "[SOLVED] I can't install ubuntu 8.10"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by seek1 on 2008-11-20
Hi all,
i don't have cd or floppy or usb or network tottaly
and i'd like to install ubuntu from my HD i have an ISO file and i'd like to install it but not sure how to do that :confused:
note: i don't need to install it inside windows i need it beside windows.

any comments will be appreciated :)

---

### Post by icanfly0307 on 2008-11-20
Follow [this]("http://ubuntuforums.org/showthread.php?t=28948") HOWTO. It's got excellent detail on how to do it from within Windows. 

BE SURE TO BACK UP ALL DOCUMENTS BEFORE ATTEMPTING THIS!!!

---

### Post by seek1 on 2008-11-21
> Follow this HOWTO. It's got excellent detail on how to do it from within Windows. 

BE SURE TO BACK UP ALL DOCUMENTS BEFORE ATTEMPTING THIS!!!

not help me they are talking about installation using internet 
so i need other method and what about alternate cd
could i do install for it from my hd without any removeable media or network connection!!!

note: i don't need to install it inside windows i need it beside windows.
thanks in advance

---

### Post by jimreynold2nd on 2008-11-21
I have an idea:
1) Create a FAT32 partition of 2GB on your hdd using one of the Windows partitioning tools (Windows' built-in disk management, Paragon partition manager, Partition magic, etc)
2) Follow one of those guides:
    [http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/](http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/) (xubuntu); [http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/](http://www.pendrivelinux.com/2008/11/05/usb-xubuntu-810-persistent-install-windows/) (kubuntu); [http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/](http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/) (ubuntu);

**But** instead of doing everything from the USB stick, you do those from the new FAT32 partition (remember to run the boot setup script as Administrator in Windows).
THIS WILL RENDER YOUR COMPUTER TO BOOT INTO THE NEW LIVE PARTITION AT BEST BY REPLACING WINDOWS' MBR WITH **SYSLINUX** (it's the script's purpose), AND MAY RENDER YOUR COMPUTER UNBOOTABLE AT WORST. Hence the warning of not running the script from the same HDD with Windows and stuffs.

Reboot. With your luck, you will be able to boot into Ubuntu Live. Do installation from there as you would from the Live CD.

---

### Post by seek1 on 2008-11-21
you mean make a bootable partition
but how??? i can't boot from it 
i have copy the contents of iso to it
but don't know how to boot it

---

### Post by sarahGarry on 2008-11-21
Here is what you need to do


[http://www.sizlopedia.com/2008/10/31/install-ubuntu-810-usb-flash-drive/](http://www.sizlopedia.com/2008/10/31/install-ubuntu-810-usb-flash-drive/)

---

### Post by seek1 on 2008-11-21
Solved
@jimreynold2nd
thank you so much man it's worked and i can boot it from my hd and ima installing it now

@sarahGarry
thank you too

i appreciate your comments people thanks all

---

### Post by seek1 on 2008-11-21
can you help me?
after installing ubuntu and after i install nvidia packages 
i change my screen resolution and after reboot 
screen resets to default again 
i try this topics but not helped any way 
[http://ubuntuforums.org/showthread.php?t=828384](http://ubuntuforums.org/showthread.php?t=828384)
[http://ubuntuforums.org/showthread.php?t=557935](http://ubuntuforums.org/showthread.php?t=557935)

btw i'm using Geforce fx 5200
cheers

---

### Post by icanfly0307 on 2008-11-21
Please mark your thread as SOLVED and start a new thread for your screen problem.

---

