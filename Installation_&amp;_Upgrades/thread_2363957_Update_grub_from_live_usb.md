---
title: "Update grub from live usb"
date: 2017-06-16
forum: Installation &amp; Upgrades
---

### Post by Ausghostdog on 2017-06-16
Reinstalling windows,[COLOR=#111111][FONT=Ubuntu]

So I was able to install Ubuntu 17.04 after I changed the install grub option to nomodeset. Now that the system is installed trying to boot I see a purple splash screen followed by the above error again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]During install I did take the option to install drivers as needed during install thinking this might help the issue but sadly did not.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have read that if I hold shift after bios splash that it should give me the grub editor but all I got was the purple screen followed by the error.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I also tried loading into the live usb and editing the grubfile there for the harddrive that has ubuntu installed but updating grub using sudo update-grub gives /usr/sbin/grub-probe: error: failed to get canonical path of aufs
[/FONT][/COLOR]http://imgur.com/a/yY7CC

---

### Post by Bashing-om on 2017-06-16
Ausghostdog; Hello;

nouvea error - Not a grub issue .

Bet we install the proprietary - nvidia - driver .. all will be good . 
Can you boot to the login screen at this time ?
If so, what results with key combo ctl+alt+F1 -
terminal ? then log into the system with user name and passwird .

Next is to know the hardware we are to match for the graphic's driver .
post back the output of terminal command:
```

lspci -vnn | grep -i VGA

```

[INDENT][INDENT]that interface between the hardware/operating system
[INDENT][INDENT][INDENT]a driver
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ausghostdog on 2017-06-16
Hi, no I can not even get a login sreen, after the bios screen I get a purple screen for a short time and then the error starts and nothing else happens.

---

### Post by Bashing-om on 2017-06-16
Ausghostdog; Well ...

A UEFI machine ?

It is then the escape key that grub looks for .
As soon as the firmware splash screen clears, spam the escape key . Be aware in UEFI there is but a 3 second window of opportunity .

Back up - regroup 
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT]

---

