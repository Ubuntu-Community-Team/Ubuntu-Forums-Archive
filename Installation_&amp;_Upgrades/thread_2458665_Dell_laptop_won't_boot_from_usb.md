---
title: "Dell laptop won't boot from usb"
date: 2021-03-01
forum: Installation &amp; Upgrades
---

### Post by petersonlevi88-j on 2021-03-01
I have a Dell Inspiron 15-3565 with bios version 1.10.1 and I cannot seem to boot Ubuntu on USB. I used unetbootin. I have a current Windows 10 install and I want to dual boot. I read somewhere that maybe my bios won't boot anything gtp, not sure if this is, but I would really like some help please. I've tried disabling secure boot, fastboot and even tried legacy mode. It only gives me USB storage option, but if I select it, it says failure to load. I might add that my bios is Aptio setup utility American Megatrends Inc if that matters

---

### Post by yancek on 2021-03-02
I'm not sure why your usb won't boot but one thing you could easily try is software other than unetbootin, ventoy, rufus or some other.  Have you ever booted a usb from this computer?  How old is it?

---

### Post by petersonlevi88-j on 2021-03-02
I have never tried before. We purchased the laptop 3 years ago came with Windows 7. It was purchased new. I will try other software for creating the USB and I'll try creating a disc iso too and report back my results. Windows has made my laptop painfully sluggish even with an upgraded SSD

---

### Post by SeijiSensei on 2021-03-02
I suggest using Rufus on a Windows machine to make the USB device.  [https://rufus.ie/](https://rufus.ie/)  A machine that new probably requires GPT.

---

### Post by ActionParsnip on 2021-03-02
F12 is usually the bottom to press on Dell systems to bring up the one time boot menu. If this is to ONLY have Ubuntu on then I recommend disabling UEFI/Secureboot and so on.

---

### Post by petersonlevi88-j on 2021-03-02
I used rufus and was able to boot the usb. Attempting install now. Thank you for the rufus suggestion. It appears to be installing alongside Windows. I'll update upon results

---

### Post by petersonlevi88-j on 2021-03-02
I'm doing a dual boot as I plan on keeping Windows. I wanted Linux as a second os for general use as Windows has become painfully slow

---

### Post by tea for one on 2021-03-02
Have you read the info contained here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

By the way, Windows 7 support ended in January 2020.

---

### Post by petersonlevi88-j on 2021-03-02
> **SeijiSensei said:**
> I suggest using Rufus on a Windows machine to make the USB device.  [https://rufus.ie/](https://rufus.ie/)  A machine that new probably requires GPT.

> **ActionParsnip said:**
> F12 is usually the bottom to press on Dell systems to bring up the one time boot menu. If this is to ONLY have Ubuntu on then I recommend disabling UEFI/Secureboot and so on.

> **tea for one said:**
> Have you read the info contained here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

By the way, Windows 7 support ended in January 2020.

I don't have Windows 7. I have Windows 10. The laptop originally came with 7, but was offered a free update to 10.

---

### Post by petersonlevi88-j on 2021-03-02
So, the install froze on the final install step where you select the partitions. I rebooted in graphics safe mode and attempted to install again, but no longer gives me the option to install alongside Windows. Apparently it did create some partitions, but froze. Are there any guides on how to proceed with manual partitions so as to keep Windows?

---

### Post by tea for one on 2021-03-02
Can you boot into Windows 10 and supply the info from:-

System Information > System Summary > BIOS mode > UEFI (or BIOS)?

---

### Post by petersonlevi88-j on 2021-03-02
It's not showing that in Windows settings, but in my bios I'm in UEFI mode. Secure boot is enabled. When I created the USB iso with rufus, I selected the default which was UEFI. I was able to boot the USB and run Ubuntu live. I went through the install steps and chose install alongside Windows and got to the final screen where you select partitions. I chose the auto settings and clicked continue. I waited for 20 minutes, but it never left that screen so I shut it down and rebooted the USB and chose graphics safe mode to attempt again. It no longer showed the option to install alongside Windows. It was either custom it erase disk. Upon choosing custom it showed unlabeled partitions that has apparently been partially created from Ubuntu. I have very basic experience doing manual partitions, but I have no clue how to do a manual with the Windows alongside it. I've only done manual partitions with a blank drive

---

### Post by tea for one on 2021-03-02
Before going any further, it is essential to know how Windows 10 (originally 7) is installed.

[https://www.easyuefi.com/resource/check-windows-is-booted-in-uefi-mode.html](https://www.easyuefi.com/resource/check-windows-is-booted-in-uefi-mode.html)

---

### Post by petersonlevi88-j on 2021-03-02
Update. I have successfully installed Ubuntu alongside Windows 10. I was reading another article and opened up disk management through command line and was planning on shrinking partition, but it notified me there were errors on the windows partition, so I fixed and rebooted and decided to try again with Ubuntu before proceeding forward. It then again offered me the option to install alongside Windows.

---

### Post by petersonlevi88-j on 2021-03-02
And thank you for the link, I was already aware of that. I'm in UEFI and I created the USB Ubuntu using rufus and selected UEFI install for it's creation on USB

---

### Post by tea for one on 2021-03-02
This seemed to be a combination of two problems.

Creating the USB device - Rufus was the solution
Using Windows tools to fix Windows partition errors

Nevertheless, it's good to read about successful results.

Please mark the thread as solved [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by zebra2 on 2021-03-03
I don't have a Dell, but given that most bios follow a pattern 
Make a bootable USB and place it in the USB slot 
Open the Bios and select Boot Order (or something similar).
Move USB to the first boot position.
Save and Exit and reboot.

If you don't have a bootable USB plugged in it may not give you the option since the bios won't give an option for what is not there. 
After you boot and install and then reboot with the USB removed your Bios may remove the USB boot option and return to default.

The settings are different from one bios to another but this is what I have on my Lenovo systems.

---

### Post by ajgreeny on 2021-03-03
I am pretty sure that Windows 7 was always installed in BIOS mode, not UEFI, and if you upgraded from 7 to 10 your Windows 10 will, I think, now be using BIOS mode and msdos partitions, not gpt.

So if you have now installed Ubuntu in UEFI mode you may have problems related to that as it is more or less essential that both OSs use the same mode.

If you can boot to the live Ubuntu USB please use gparted and show us a screenshot of what partitions that sees.  Failing that, and assuming you can boot to Windows, use the Disk Management utility from that to show partitions; it is not as good as gparted but may give us better information than we have now.

---

