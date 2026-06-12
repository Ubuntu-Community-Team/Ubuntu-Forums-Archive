---
title: "W10 doesn't boot anymore"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by keit14 on 2016-09-16
Hi everyone
I just installed Lubuntu in my pc and W10 doesn't boot anymore

I have 3 partition (C: for W10. D: just for media.  And I created a new one ( E: )  for Lubuntu (actually I needed another one for swap) 

In GRUB I can select Ubuntu/Advance option for Ubuntu/Windows 10

But if I select Windows 10 the pc shows this symbol (_)  for less than a second and then restart. 

I tried with "boot repair" but after using it if I try to boot W10 says "invalid license" 

I had to reinstall GRUB and now I'm back in the beginning (after select W10 in GRUB just restarts) 

Sorry for my English, I'm from Venezuela

Thanks for your time

---

### Post by Bucky Ball on 2016-09-16
> **keit14 said:**
> I tried with "boot repair" but after using it if I try to boot W10 says "invalid license"

Is it an unlicensed version? 

Boot to Lubuntu, open a terminal and;

```
sudo grub-install /dev/sda
```

Reboot and try Windows. If still not working, Boot Repair will create a bootinfo summary. Launch Boot Repair, choose for it to create that, at the end it will provide you with a link to the output, post that here. Thanks.

*** Very important point: Whatever mode Windows is installed in, UEFI or legacy, Ubuntu *_must_* be installed in the same mode. This may be your issue.

---

### Post by keit14 on 2016-09-16
> Is it an unlicensed version? 

I think it is, I just downloaded the ISO from Microsoft and installed it 

> 
Boot to Lubuntu, open a terminal and;

```
sudo grub-install /dev/sda
```

Reboot and try Windows. If still not working, Boot Repair will create a bootinfo summary. Launch Boot Repair, choose for it to create that, at the end it will provide you with a link to the output, post that here. Thanks.


I did it and nothing change, this is the info [http://paste2.org/DzacIZgN](http://paste2.org/DzacIZgN)

> 
*** Very important point: Whatever mode Windows is installed in, UEFI or legacy, Ubuntu *_must_* be installed in the same mode. This may be your issue.

I'm not sure about that, how can I know that? I don't even know what UEFI or legacy means for this things.

By the way, UEFI boot has been always disabled in BIOS.

This is my first time trying to do something with GNU/Linux and I'm really confuse with everything, sorry about that

Thanks again for your time and taking care for my issue

---

### Post by keit14 on 2016-09-27
> **Bucky Ball said:**
> Is it an unlicensed version? 

Boot to Lubuntu, open a terminal and;

```
sudo grub-install /dev/sda
```

Reboot and try Windows. If still not working, Boot Repair will create a bootinfo summary. Launch Boot Repair, choose for it to create that, at the end it will provide you with a link to the output, post that here. Thanks.

*** Very important point: Whatever mode Windows is installed in, UEFI or legacy, Ubuntu *_must_* be installed in the same mode. This may be your issue.

Sorry for bother you again, but actually I don't know how to see if Ubuntu/Windows is on legacy/UEFI and how to fix it. Do you or anyone know how?

Thanks

---

### Post by yancek on 2016-09-27
The boot repiar output you posted indicates you are using MBR to boot and not UEFI.   It also indicates you did not select the suggested repair.  Have you since tried that?  You have Grub installed to the MBR which is correct.  You also have the correct Grub code as well as an entry for windows in the Grub boot menu (grub.cfg file) on sda6 where Ubuntu is installed.  The problem is that you also somehow have Grub installed on sda1 which is your windows boot partition.  That should never happen as it probably has overwritten windows boot code rendering the system unbootable (windows anyhow).

If you haven't tried the suggested repair, you could try that.
If you have tried the suggested repair and it still won't boot windows, you would probably need the windows installation DVD and select the Repair option to repair the windows boot loader.  If that fails, it might be simpler to re-install windows to the same partition.  Make sure you have either a backup or do not use the partition (D) you use for your media as it will then be overwritten.

---

