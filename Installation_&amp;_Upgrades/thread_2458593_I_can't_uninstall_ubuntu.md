---
title: "I can't uninstall ubuntu"
date: 2021-02-28
forum: Installation &amp; Upgrades
---

### Post by mar221 on 2021-02-28
Hello, I don't know if this is the correct thread but I need help uninstalling ubuntu. I apologise for my english in advance.

I was going to follow the instructions that many tutorials out there give you (deleting the disk partition where ubuntu is installed and changing the grub), but something weird happened.

First I removed the grub with the bootrec /fixmbr command.

Then I created the windows installation USB, and after that I headed to Disk Management to remove the previously said partition, but it didn't gave me the option (gray letters). I looked up the cause and I read that it could be because i probably had installed something there so I restarted my PC to go to Ubuntu, but obviously the dual boot had disappeared, Windows initialized directly.
[ATTACH=CONFIG]288029[/ATTACH]

I tryed removing the partition with diskpart, but it was no use.

In conclusion, I'm stucked in Windows and I can't free 180 GB of space from the ubuntu partition. Is there anyway to fix this?

---

### Post by ajgreeny on 2021-02-28
The 180G partition, the third in your shown listing, that was your Ubuntu is now marked as a second EFI partition for some reason, and I do not know Windows well enough to know which partitions other than that are essential to Windows.

However, I may be able to help more if you can boot to a live Ubuntu system (the USB you used to install it, if you still have it) and from that live system run **gparted** and show us a screenshot of the **gparted** window which I can usually understand better than the Windows Disk Management, which always confuses me, telling only half the story when it comes to any Linux partitions.

Running gparted you may be able to simply delete or reformat the old Ubuntu partition and then use it in Windows again but I'm reluctant to tell you to do so in case it has for some reason taken over as your EFI partition, meaning you can no longer boot to Windows.

---

### Post by mar221 on 2021-02-28
Hi, thank you for your answer.
I did what you said and I was able to get into ubuntu. Here is a screenshot of the gparted. There's an unknown partition, maybe that's what is causing the problem?[IMG]https://postimg.cc/hJ1dbJJP[/IMG]
[ATTACH=CONFIG]288030[/ATTACH]

---

### Post by CelticWarrior on 2021-02-28
No, it isn't.

The partition with 180.23GB is the one you want to remove. For some reason it has flags "boot, esp" which explains why Windows was considering it as another ESP (EFI partition). This is highly unusual and I suspect user mistake.

---

### Post by Frogs Hair on 2021-02-28
You will also likely to have to repair Windows from a Windows DVD or USB  after removing Ubuntu. I have in the past simply deleted the Ubuntu  volume from Windows disk management in the process reinstalling newer versions of Ubuntu , but if Ubuntu is deleted and the system rebooted Windows will require repair. Note : I have never used the install along side option so can't comment on what's done by the installer during that process.

---

### Post by howefield on 2021-02-28
Not a tutorial thread, so moved to the "*Installation & Upgrade*" forum for a better fit.

---

### Post by CelticWarrior on 2021-02-28
> **Frogs Hair said:**
> You will also likely to have to repair Windows from a Windows DVD or USB  after removing Ubuntu. I have in the past simply deleted the Ubuntu  volume from Windows disk management in the process reinstalling newer versions of Ubuntu , but if Ubuntu is deleted and the system rebooted Windows will require repair. Note : I have never used the install along side option so can't comment on what's done by the installer during that process.

Apparently Windows boots directly (it's a UEFI system) so no repair should be needed. And that in spite of > [COLOR=#000000]First I removed the grub with the bootrec /fixmbr command[/COLOR] which isn't applicable but so far seems to have done no harm.

---

### Post by mar221 on 2021-02-28
Do I have to remove those flags to solve the problem? Or do I have to do something more?

---

### Post by CelticWarrior on 2021-02-28
> **mar221 said:**
> Do I have to remove those flags to solve the problem? Or do I have to do something more?
No need.
You can remove the partition with Gparted in the live session. Then boot Windows and expand the partition immediately left to the now unallocated space.

---

### Post by Frogs Hair on 2021-02-28
> Apparently Windows boots directly (it's a UEFI system) so no repair should be needed. And that in spite of 

> [COLOR=#000000]First I removed the grub with the bootrec /fixmbr command[/COLOR]

Thanks , Much easier than legacy if that's the case regardless of the boot flag selection.

---

### Post by mar221 on 2021-02-28
Thank you all for your help. I finally was able to uninstall it!:KS

---

