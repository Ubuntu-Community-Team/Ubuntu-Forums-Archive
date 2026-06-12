---
title: "Latest 14.04 LTS update failure"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by newbutol on 2014-12-11
Dec 11 accepted the latest 14.04LTS update. After restaring the OS all icons for installed apps including icons for devices attached to the cpu disappeared. Tried recovery options at boot time with no success. Re-installed previous update with no success. Opened dashboard dragged all app icons to unity side board. They stuck. Upon a re-boot they went missing again. All that remains oin the icon list is - "dashboard", "firefox", Libre Office writer, spreadsheet and presentaion", "software center", "amazon", "settings" and an icon for a "ghost" device I have not connected in a while. Normally I have 3 external HD drives attached via USB. Even when attached they are not displayed as an icon nor do they show up in the nautilus list of devices.

Can anyone assist me in determinig what went wrong and how I can recover to a prior state.

THank You.

---

### Post by pfeiffep on 2014-12-12
Enter the grub menu by holding the shift key down during a power up start - this should enable you to choose a prior Kernel from which to boot.

---

### Post by newbutol on 2014-12-12
Thank you for the reply. I tried that (hold shift key during GRUB boot). I got the same results. 

[LIST]
[*]Strangely, I can go to dashboard, drag my app icons to the unity bar menu and they will stick and execute.
[*]I went into the disk management app and mounted the external drives that way. They still don't show up on the side bar. They do appear in the nautilus list.
[*]If I move something to trash and empty trash the icon for trash does not respond
[*]When I reboot all it reverts back to the original problem.
[*]I went to advanced options at grub menu. clicked on a previous version and still have same problem.
[/LIST]

Not sure where to go from here. I really don't want to do a clean reinstall unless absolutely required.

---

### Post by MAFoElffen on 2014-12-12
Try:
```

sudo apt-get install --reinstall gnome-icon-theme-full

```
That will trigger the theme icons to reattach...

---

### Post by newbutol on 2014-12-12
Thank you. I will give that a try.

It appears that the OS will not recognize my external drive mounted on a multi-USB external bar. Just tried to make ISO for clonezilla. Can mount the cd/dvd drive but the burning software (brasero) doesn't see it.

---

### Post by newbutol on 2014-12-12
Tried that and still no success. I think I will just replace the OS with a freash verision. I hope no one else has this issue. It is quite frustrating.

---

### Post by kmkwood on 2014-12-12
I had a problem with the Dec. 11 update, too.  I lost the screen functions -- no graphical interface at all.  I can ssh in from a non-ubuntu linux, and everything is running fine.  I took pfeiffep's suggestion and booted the 3.13.0-40 kernel.  I'm back in business.

---

### Post by newbutol on 2014-12-12
I think I did the grub boot wrong. When do I hold the key down during the boot process or right after before the grub menu appears?

---

### Post by newbutol on 2014-12-12
Folks,

It seems that I have a bigger problem. It appears, coincindentally that my hard drive is failing. I believe this is the root cause of my problem. Consequently I must purchase a new one. Thank you for all your assistance. I will close this thread....

---

