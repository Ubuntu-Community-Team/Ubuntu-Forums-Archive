---
title: "Corrupt Bios after running LIVE Boot"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by geyids on 2024-08-06
Hello Forums,

I have an old Fujitsu P956/E90 which I tried to install Ubuntu 24.04. Before completing the installation, the computer froze and on reboot I could not get it to boot any more. I can't even reach the BIOS settings page. Only the Fujitsu logo displays and after a minute the computer restarts and goes on forever. Any ideas on what could be the problem? Could it be an old hardware problem?

---

### Post by euol on 2024-08-06
You can try doing a hard reset by powering off and holding the power button for 30 seconds. Also make sure that it is not caused by some external devices (USB drives, printers, etc.) by unplugging them. And yes it could be an old hardware problem.

---

### Post by geyids on 2024-08-06
I already tried that. Tried removing all peripherals, even changed the RAM slot but still didn't get through. Is there an explanation of what might have happened? I tried a live session on a different machine of the same model without installing and it also broke.

---

### Post by ajgreeny on 2024-08-06
I presume from what you've said so far that the machine will not even boot from a live USB.
However, just in case you can get it to do so, please show us the hardware from running terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by yancek on 2024-08-06
>  I tried a live session on a different machine of the same model without installing and it also broke. 				

You need to be more informative and post some details if you actually want help.  So, what 'broke'.  The information in your initial post seems like a hardware problem but you don't give much for detail so if you can't gather the information requested in post 4, at least give some basic info on the machine age and hardware as best you can.

A Linux iso/usb is not going to modify your BIOS other than to write an entry to it to boot so what happens when you try to access the BIOS?

---

### Post by hedgehog123 on 2024-08-06
There is a German forum thread where one had the same problem with a Q956 ([https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/](https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/)).
Solution was a recovery of the BIOS which is a bit complicated:
- Download admin pack from Fujitsu website
- Download USB creation tool from Fujitsu website
- Create bootlable USB stick with the creation tool and copy the admin pack to the root directory of the USB stick
- Set mainboard jumper to boot into recovery mode
- Start PC with connected USB stick

---

### Post by geyids on 2024-08-07
> **ajgreeny said:**
> I presume from what you've said so far that the machine will not even boot from a live USB.
However, just in case you can get it to do so, please show us the hardware from running terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Unfortunately I cannot get to any of the menu's, it freezes on the flash logo screen and after a minute it reboots and repeats the process indefinately. I can't get to bios settings either

---

### Post by geyids on 2024-08-07
> **yancek said:**
> You need to be more informative and post some details if you actually want help.  So, what 'broke'.  The information in your initial post seems like a hardware problem but you don't give much for detail so if you can't gather the information requested in post 4, at least give some basic info on the machine age and hardware as best you can.

A Linux iso/usb is not going to modify your BIOS other than to write an entry to it to boot so what happens when you try to access the BIOS?

What broke is the second computer of the same model that I tried out running a live boot (without installation). The machine is Fujitsu P956/E90 around 6years old. I've been installing new versions of Ubuntu without any problems in the past.

---

### Post by geyids on 2024-08-07
> **hedgehog123 said:**
> There is a German forum thread where one had the same problem with a Q956 ([https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/](https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/)).
Solution was a recovery of the BIOS which is a bit complicated:
- Download admin pack from Fujitsu website
- Download USB creation tool from Fujitsu website
- Create bootlable USB stick with the creation tool and copy the admin pack to the root directory of the USB stick
- Set mainboard jumper to boot into recovery mode
- Start PC with connected USB stick

That you for shedding some light, I will use a translator hope it helps get somewhere

---

### Post by tea for one on 2024-08-07
Have a look at rEFInd
You can Install rEFInd on a USB stick temporarily to see if it offers any improvement. 
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File

One of the options is "Reboot to Computer Setup Utility" i.e. your UEFI settings.

Edit: If rEFInd on a USB doesn't boot, then it looks like a Fujitsu firmware problem.

---

### Post by hedgehog123 on 2024-08-07
> **geyids said:**
> That you for shedding some light, I will use a translator hope it helps get somewhere

Just ask here if you need some help to understand the thread.

---

### Post by geyids on 2024-08-15
> **hedgehog123 said:**
> There is a German forum thread where one had the same problem with a Q956 ([https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/](https://www.computerbase.de/forum/threads/fujitsu-q956-mainboard-gebrickt-nach-live-linux-boot.2204146/)).
Solution was a recovery of the BIOS which is a bit complicated:
- Download admin pack from Fujitsu website
- Download USB creation tool from Fujitsu website
- Create bootlable USB stick with the creation tool and copy the admin pack to the root directory of the USB stick
- Set mainboard jumper to boot into recovery mode
- Start PC with connected USB stick

This worked out for me, had to download the admin package from the Fujitsu support website for my correct desktop, cleated the boot disk, searched for a manual for jumper configuration to change the machine to bios recovery mode so as to boot from the USB. Follow the directions on the manual, started the machine, a number of beeps with a blank screen then it restarted with the message revocery complete and some instructions to restore the machine to original state and that was all. Thank you everyone for your time

---

