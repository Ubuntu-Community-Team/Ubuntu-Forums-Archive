---
title: "Fresh Ubuntu-mate install-nvidia drivers don't update display"
date: 2016-12-10
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2016-12-10
3rd try at installing Ubuntu-mate correctly. I've updated Nvidia drivers using the Software & Updates >Other driver settings
  Also added an additional PPA [http://ppa.launchpad.net/graphics-drivers/ppa/xbuntu](http://ppa.launchpad.net/graphics-drivers/ppa/xbuntu) xenial main
  to get the very latest driver 375.20


  I've applied changes and rebooted, but no change. My resolution is still wrong.(low resolution, wrong format) What do you need to do to make the driver's update your display?

[ATTACH=CONFIG]272649[/ATTACH][ATTACH=CONFIG]272650[/ATTACH]

---

### Post by #&amp;thj^% on 2016-12-10
Show us what card you have...with:
```
inxi -G
```
[s]And have you rebooted after install Nvidia?[/s]
Yes I see that you have.

---

### Post by ubuntini2 on 2016-12-10
OP<br>
ok,on reboot enabled Fast boot, Disabled Secure Boot in UEFI-BIOS, now my display is correct. But why? I though Nividia drivers worked fine in secure boot?

---

### Post by #&amp;thj^% on 2016-12-10
So all is good then?
I will try and answer the best I know how to. "Secure Boot in UEFI-BIOS"
This has security benefits, but as you've seen, it also has problems. If a third-party driver is not signed with a cryptographic key that the Ubuntu version of the Linux kernel recognizes as valid, it won't be loaded. This mostly impacts the closed-source Nvidia and AMD/ATI video drivers, but there are other drivers that can be affected, too.

Note that there should be pretty good Nvidia support using such drivers; your system probably fell back to sub-optimal drivers because it thought that the closed-source drivers were available.

---

