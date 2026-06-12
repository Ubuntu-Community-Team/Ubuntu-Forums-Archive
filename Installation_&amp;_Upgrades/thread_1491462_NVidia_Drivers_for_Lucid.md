---
title: "NVidia Drivers for Lucid"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-23
Looking for some input.
Do you think if I do an upgrade from 9.1 to 10.04 and then add i915.modeset=0 ( works with the live CD) to the boot sequence and then load the proprietary NVidia drivers from sys/admin/hardware drivers, that I'll get full screen resolution.
BTW if I don't use the modeset=0 I get a blank screen after update reboot.

---

### Post by wojox on 2010-05-23
You have to use nomodeset for nvidia.

i915.modeset=0 is for intel.

---

### Post by Silvertones on 2010-05-23
> **wojox said:**
> You have to use nomodeset for nvidia.

i915.modeset=0 is for intel.

So far I've just experimented with the live CD. When the purple screen comes up I hit the space bar, choose the language,press F6,press ESC, add any of the following after splash:
```
i915.modeset=0
``````
i915.modeset=0 xforceintel
``````
i915.modeset=0 xforcevesa
```So what SHOULD I be putting in that line.

---

### Post by wojox on 2010-05-23
When you press F6 scroll down to **nomodeset** and hit the space bar to select it and then you can install.

---

### Post by oldfred on 2010-05-23
I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

---

### Post by Silvertones on 2010-05-24
Did you get full resolution from your monitor?

---

### Post by dino99 on 2010-05-24
on our side all is fine, and you have to try with your config to know about trouble if any.

its good also to add this ppa to your synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by wojox on 2010-05-24
> **Silvertones said:**
> Did you get full resolution from your monitor?

Not really because you haven't installed the driver yet. It should default to 800x600. then you activate the driver reboot and run:

```
gksudo nvidia-settings
```

---

### Post by enaction on 2010-05-24
> **oldfred said:**
> I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

:) This fixed the blank screen after initial grub load perfectly.  THANK U

---

### Post by Silvertones on 2010-05-24
My first upgrade went south because I didn't read the release notes so I  reinstalled Karmic.
I did the upgrade today from the Alternate CD and it was flawless. All I  needed to do is add the "nomodeset" to the boot line. Then I did the  NVdia upgrades from sys/admin/hardware. Then the other updates.
My network is running without touching it, dialup works everything.:smile:
Nice work.

---

