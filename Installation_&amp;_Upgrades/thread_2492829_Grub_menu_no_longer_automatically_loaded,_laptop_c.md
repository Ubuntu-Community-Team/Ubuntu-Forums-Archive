---
title: "Grub menu no longer automatically loaded, laptop crashes after using UEFI boot menu"
date: 2023-11-24
forum: Installation &amp; Upgrades
---

### Post by camielcastillo on 2023-11-24
Dear community members,

I have a laptop running Windows 10 and Kubuntu side by side. Until a couple of weeks ago, my laptop would automatically go to the Grub menu and start Kubuntu when I powered on my laptop. Then my laptop crashed, and since that time, the grub menu does not load anymore. Also, when I pull up my boot menu through F12, I see the option of booting my Linux partition, but when I choose that I hear my disk spin down and my laptop restarts. I have as such for a couple of weeks been doomed to use Windows rather than my preference Kubuntu.

I am able to boot from a live USB using the UEFI boot menu, and ran a boot-repair analysis. The outcome can be found on pastebin here; [https://paste.ubuntu.com/p/qG7TsxYzwD/](https://paste.ubuntu.com/p/qG7TsxYzwD/)

Can anybody help me restore my boot process to the way it was?

Thansk and with kind regards,

C

---

### Post by tea for one on 2023-11-24
> **camielcastillo said:**
> Until a couple of weeks ago, my laptop would automatically go to the Grub menu and start Kubuntu when I powered on my laptop. Then my laptop crashed, and since that time, the grub menu does not load anymore. 
When your device crashed, were you using Kubuntu?
```
                           Avail Use% Mounted on
/dev/sdb5                   4.2G  91% /mnt/boot-sav/sdb5 [COLOR="#0000FF"]- Line 206[/COLOR]

```
Your Kubuntu partition is 91% full with only 4.2GB of free space.

While in a live session, try and create some more free space - aim for 15% free.
The earlier crash may have damaged sdb5 and it may be worthwhile to run fsck on /dev/sdb5

---

### Post by camielcastillo on 2023-11-24
@tea for one: Thanks, I cleared some data, and my Linux partition is now 81% full. Also ran fsck, and it gave no errors. Still same problem. After I choose the grub64e option in my boot menu, I get a black screen and in the top right it says: Reset System. Then it reboots :(

---

### Post by camielcastillo on 2023-11-24
[QUOTE=tea for one;14166603]When your device crashed, were you using Kubuntu?
```
                           Avail Use% Mounted on
/dev/sdb5                   4.2G  91% /mnt/boot-sav/sdb5 [COLOR=#0000FF]- Line 206[/COLOR]

```

I was running Kubuntu when my laptop crashed

---

### Post by jeremy31 on 2023-11-24
> **camielcastillo said:**
> @tea for one: Thanks, I cleared some data, and my Linux partition is now 81% full. Also ran fsck, and it gave no errors. Still same problem. After I choose the grub64e option in my boot menu, I get a black screen and in the top right it says: Reset System. Then it reboots :(

Try the ubuntu option in boot menu

---

### Post by camielcastillo on 2023-11-24
> **jeremy31 said:**
> Try the ubuntu option in boot menu

There is no Ubuntu option in the UEFI boot menu, just Windows, my pendrive kubuntu version and Grubx64e

---

### Post by tea for one on 2023-11-24
I've not heard of Grubx64e before - did you install this?

Two options:-
Try the recommended boot-repair.

Or create a rEFInd Boot manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)

Edit: Make sure Windows is not hibernating before trying anything
Windows updates sometimes enable hibernation

---

### Post by oldfred on 2023-11-24
It looks like you assigned grubx64e as the label to an Ubuntu entry.
But that entry uses grubx64.efi and would not work with UEFI Secure Boot on.
You show UEFI Secure boot is now on.
Secure boot could be reset to defaults with a Windows update or UEFI firmware update from either Windows or Linux. 

You also show another "ubuntu" entry that may work with Secure boot on. But kernel & drivers also have to be signed or versions for secure boot.
May be easier just to turn Secure Boot off in UEFI settings.

---

### Post by camielcastillo on 2023-11-24
> **oldfred said:**
> 
May be easier just to turn Secure Boot off in UEFI settings.

That did the trick, thanks! Seems like after the crash my BIOS got reset. Just the issue that is remaining now is that when I boot my laptop, it automatically starts windows rather than the grub bootloader. Any idea how I van fix that?

thanks!

C

---

### Post by tea for one on 2023-11-24
> **camielcastillo said:**
> That did the trick, thanks! Seems like after the crash my BIOS got reset. Just the issue that is remaining now is that when I boot my laptop, it automatically starts windows rather than the grub bootloader. Any idea how I van fix that?
Access your UEFI settings and change the boot priority.

---

### Post by MAFoElffen on 2023-11-24
If fixed, please visit the "Thread Tools" link in the upper right of the first page of the thread , and mark your thread as "Solved'.

---

### Post by camielcastillo on 2023-11-25
Thanks all, it works like a charm now!

---

