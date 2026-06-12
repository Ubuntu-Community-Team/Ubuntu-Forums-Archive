---
title: "Cannt access Bios after installing Ubuntu"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by rockvilla on 2013-02-21
I have bought new Lenovo G580 laptop with no OS.
Then installed ubuntu 12.10 64bit.
Its runs very nicely but while booting if I press F2, it gives me screen to boot into "Ubuntu" and "Advance options of Ubuntu".
I cannot access bios menu. I want to access bios menu to enable virtual threading option for Virtualbox

When I ran Boot repair it gave this [www.http://paste.ubuntu.com/1698702](www.http://paste.ubuntu.com/1698702)

---

### Post by dino99 on 2013-02-21
which is the required key to access bios on that laptop ?
if you get the grub menu by holding F2 (should be "shift" key) then the key does not follow the standard way (reaffected)

[http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169](http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169)

---

### Post by ajgreeny on 2013-02-21
I don't think this has anything to do with Ubuntu installation; I suspect you are pressing the wrong key.

Perhaps F2 just gives you boot device options (when there are device options to choose from) and does not get you into the BIOS.  What does your machine manual tell you?

Google suggests that holding "B" at boot may work or F12 or F!, but this model seems to haver some problems with the UEFI mode booting, so I'm not at all sure.  Perhaps contact with Lenovo is called for.

---

### Post by dino99 on 2013-02-21
> **ajgreeny said:**
> I don't think this has anything to do with Ubuntu installation; I suspect you are pressing the wrong key.

Perhaps F2 just gives you boot device options (when there are device options to choose from) and does not get you into the BIOS.  What does your machine manual tell you?

Google suggests that holding "B" at boot may work or F12 or F!, but this model seems to haver some problems with the UEFI mode booting, so I'm not at all sure.  Perhaps contact with Lenovo is called for.

i've posted the link above to explain what to do; that netbook has an uefi/gpt firmware, so the issue.

---

### Post by rockvilla on 2013-02-21
None of the keys work for bringing up bios menu :(
and I am newbie in linux so I am not understanding much mention in the link : [http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169]("http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/td-p/890169")

Can any one explain me better?

---

### Post by oldfred on 2013-02-21
Did you turn fast boot off in Windows. That setting is to speed boot boot. And it also seems to not let you directly into UEFI/BIOS except from Window boot menu.

       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

    [http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

       Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

---

### Post by rockvilla on 2013-02-21
> **oldfred said:**
> Did you turn fast boot off in Windows. That setting is to speed boot boot. And it also seems to not let you directly into UEFI/BIOS except from Window boot menu.

       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

    [http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

       Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

none of those solutions work and they are just suggestions, no concrete solution is mentioned :( I don't know why this problem is appearing!! If I install Ubuntu again will this problem get solved?

---

### Post by dino99 on 2013-02-21
> **rockvilla said:**
> none of those solutions work and they are just suggestions, no concrete solution is mentioned :( I don't know why this problem is appearing!! If I install Ubuntu again will this problem get solved?

ubuntu is not the first problem to work around first. You need to read and understand what Oldfred said in the post above about Windows boot option.
This is the only thing to pay attention right now.

---

### Post by rockvilla on 2013-02-21
I am not having Windows on laptop. It has only Ubuntu 12.10 installed and it runs well. But I cannot access bios at booting. I want to enable Vt-x feature in bios for Virtualbox

---

### Post by oldfred on 2013-02-21
I do not see it in your system, but some now have this entry in grub.

```
        ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup

 }
### END /etc/grub.d/30_uefi-firmware ###    
```

---

### Post by Mark Phelps on 2013-02-21
> **rockvilla said:**
> none of those solutions work and they are just suggestions, no concrete solution is mentioned :( I don't know why this problem is appearing!! If I install Ubuntu again will this problem get solved?

The following (from Dino99's link) looks like a "concrete solution" to me:


```
But now I have been able to to display the BIOS.
press F12 during POST -> Press the TAB from the [boot menu] -> [App Menu]
--- App Menu -------------
| 1. Diagnostic Splash |  <- Normally there is only No.1.
| 2. Setup                       |  <- Item to display the BIOS.
| 3. Diagnostic Splash |  <- Item No.1 is a duplicate.
```

---

