---
title: "Upgraded to 20.04, now can't do full screen."
date: 2020-10-10
forum: Installation &amp; Upgrades
---

### Post by imaginashawn2 on 2020-10-10
Upgraded from 18.04 to 20.04 a couple days ago. Finally figured out the pointer trail problem but I'm stumped on getting my videos to play full screen (Youtube, Amazon Prime, etc.). When I click on the full screen icon, instead of going full screen, the player moves to the top left, in other words 1/4 screen. Any help would be greatly appreciated.

---

### Post by ActionParsnip on 2020-10-11
What is the output of:
```

sudo lshw -C display; lsb_release -a; uname -a

```

Thanks

---

### Post by imaginashawn2 on 2020-10-14
Thank you Action Parsnip for your input, it is greatly appreciated. I'm going to try your suggestion next but I wanted to thank you first in case I can't find my post again.

---

### Post by CelticWarrior on 2020-10-14
Please note the command above is to gather information about your hardware and Ubuntu release/kernel version, information that is missing and shouldn't be from the OP. It changes absolutely nothing.

---

### Post by imaginashawn2 on 2020-10-14
*-display:0               
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f7c00000-f7ffffff memory:e0000000-efffffff ioport:ecb0(size=8) memory:c0000-dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7b00000-f7bfffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
Linux imaginashawn-OptiPlex-780 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by imaginashawn2 on 2020-10-14
Got it Celtic Warrior thank you.

---

### Post by CelticWarrior on 2020-10-14
First of all make sure your system is fully updated:
```
sudo apt update && sudo apt full-upgrade
```

Reboot. Try again. Post results.

---

### Post by imaginashawn2 on 2020-10-14
I just noticed I never said that this problem is only in Firefox. I tried a couple other browsers and full screen works perfect. I tried removing Firefox, rebooting and installing Firefox. That worked for yesterday but today I get quarter screen again. Because of this, I'm thinking maybe it's got to do with Flash?

---

### Post by imaginashawn2 on 2020-10-16
I updated and the problem persist. Problem is only with Firefox so I deleted Firefox, rebooted and re-installed Firefox. Still same problem. Mozilla offers no solutions to this problem.

---

### Post by SeijiSensei on 2020-10-16
Reinstalling Firefox won't fix issues in your profile.  Close all instances of Firefox, then try this:

```

cd ~
mv .mozilla mozilla.old

```

Note the leading period.  Now start Firefox and try again.

---

### Post by imaginashawn2 on 2020-10-19
I reverted to old file in Mozilla as you suggested. The only thing that changed is it turned off DRM content. I turned it back on and went to Amazon Prime Videos and tried full screening a show there but same thing. I tried doing some upgrades manually like, graphics driver and flash. Both said they were already up to date. I wonder if it's something corrupt in my flash. I was thinking of removing it, restarting and installing it. What do you think? Worth a try or no. One more thing I forgot to mention yesterday, I've been getting an error message everytime I start the computer. It's a error detected by whoopsie. Don't remeber the whole string but the error code is 1899347. I couldn't find it.

---

### Post by imaginashawn2 on 2020-10-19
I think I've got it. The phasing out of flash is my problem. I just looked at my flash and the always on selection is gone. Probably happened when I upgraded Ubuntu. Only options now are never turn on and always ask. Guess I need to find another flash besides Adobe. Thanks for your help.

---

### Post by CelticWarrior on 2020-10-20
> [COLOR=#000000]Guess I need to find another flash besides Adobe. [/COLOR]

No, you need to move on with your life.
There is no other "Flash" and it's an old and obsolete technology about to be axed for good. Nothing (no website/service) important nowadays uses it, Youtube particularly moved to HTML5 almost a decade ago.

---

