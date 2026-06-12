---
title: "Cant Get rid of GRUB2 Boot Menu - Ive Tried Everything!"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by secondsystem on 2011-01-18
I have a simple single drive, single OS (Ubuntu 10) setup.  I've removed my boot recovery and ram test, so that there is only one possible kernel/os to boot off of.  I've set my GRUB_DEFAULT=0.  GRUB_HIDDEN_TIMEOUT=0.

 I've even tried part 11 from [here]("http://ubuntuforums.org/showthread.php?t=1287602")

This is a server, and I need it to reboot after a power outage.  I'm not able to get the countdown at the boot menu either.  What is going on here?

---

### Post by garvinrick4 on 2011-01-18
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
***GRUB_TIMEOUT=10*** 

[LIST]
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG] This instruction defers to the **GRUB_HIDDEN_TIMEOUT** unless **GRUB_HIDDEN_TIMEOUT** is commented (#). If **GRUB_HIDDEN_TIMEOUT** is active, the **GRUB_TIMEOUT** only operates once, and if, the menu is displayed. 
[*]Setting this value to -1 will cause the menu to display until the user makes a selection. 
[*]The  GRUB 2 menu is hidden by default unless another OS is detected by the  system. If there is no other OS, this line may be commented out unless  the user changes it. To display the menu on each boot, uncomment the  line and use a value of 1 or higher.
[/LIST]

---

### Post by secondsystem on 2011-01-18
> **garvinrick4 said:**
> [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
***GRUB_TIMEOUT=10*** 

[LIST]
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG] This instruction defers to the **GRUB_HIDDEN_TIMEOUT** unless **GRUB_HIDDEN_TIMEOUT** is commented (#). If **GRUB_HIDDEN_TIMEOUT** is active, the **GRUB_TIMEOUT** only operates once, and if, the menu is displayed. 
[*]Setting this value to -1 will cause the menu to display until the user makes a selection. 
[*]The  GRUB 2 menu is hidden by default unless another OS is detected by the  system. If there is no other OS, this line may be commented out unless  the user changes it. To display the menu on each boot, uncomment the  line and use a value of 1 or higher.
[/LIST]

This yields the same result, unfortunately.

---

### Post by garvinrick4 on 2011-01-18
#purge grub and reinstall:
#There is some setting that is over ridding default if one OS and
commenting out does not do it.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by garvinrick4 on 2011-01-18
##After you work on /etc/default/grub you are updating grub aren't you.
```
sudo update-grub
```

---

### Post by secondsystem on 2011-01-19
Thanks, that has worked.  I simply uninstalled and reinstalled through the Synaptic package manager.   I have an idea of what was causing the error.  I think in struggling to get grub2 configured in the first place, I mistakenly configured one of the interior partitions for grub.  So in my case grub2 was probing not only /dev/sda but also /dev/sda1.  

Grub2 has a gui for the initial setup apparently, and I was asked to put a check next to sda and sda1.  I left sda1 unchecked and everything was good from that point on.  Its easy enough to bugger this stuff up when running off of a usb boot disk.

---

