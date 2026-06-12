---
title: "UEFI installation failed"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by rlgracia on 2013-05-06
I followed the instructions for installing ubuntu on a UEFI Windows 8 machine (HP ENVY dv7) and ubuntu failed to boot, it went strait to windows 8.  I then follow the boot repair instructions which led me to [http://paste.ubuntu.com/5634191](http://paste.ubuntu.com/5634191).  I then rebooted and the pc is dead.  It will not boot windows or ubuntu.  The message I get is "Selected Boot image did not Authenticate'.  Any help would be appreciated.

Thanks,

Ron

---

### Post by rlgracia on 2013-05-06
Problem solved.  I googled the boot message and discovered that I had to [COLOR=#000000][FONT=HPRegular] disable secureboot and enable legacy boot mode to get it to run.

Thanks,

Ron[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-06
It looks like you have installed the signed kernels and grub shim file with the Microsoft secure boot key. That should boot with secure boot on.
Some systems only boot Windows with secure boot on.
And you cannot boot Windows in legacy mode, but maybe able to in UEFI mode or secure boot off?

HP puts a lot of efi files into the efi partition. Some vendors put those into a separate maintenance partition. 
       Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by rlgracia on 2013-05-06
Ah, I see I have more worked to do.  I just saw the usual grub menu and booted into ubuntu.  I just tried Windows and it didn't boot.  I'll try some other stuff when I get a chance and let you know how it goes.

Ron

---

### Post by oldfred on 2013-05-06
Which boot entry are you using. Only the Boot-repair entry will work.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by rlgracia on 2013-05-07
I tried the boot-repair disk again, this time from my installed ubuntu.  This time it made some changes but when I rebooted I still got the same error.  Then I remember the secure boot setting. I know have 2 entries for Windows UEFI that both work, plus ubuntu and some other stuff that seems to be from HP.  Anyway it now works so you can mark this as solved.

Thanks,

Ron

---

### Post by oldfred on 2013-05-07
Glad it worked. :)

Post #5 has a link to some info on removing extra entries if you want.

---

