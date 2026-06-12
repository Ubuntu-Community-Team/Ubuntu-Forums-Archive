---
title: "Resize Ubuntu partition"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by MetalDrummer on 2012-06-23
Hi!
I have a Dual Boot computer with Windows 7 and Ubuntu 12.04. I have more space in the Windows partition than Ubuntu's.

I want to reduce Windows partition size and increase the Ubuntu partition size, but every time i try to do it, when i restart it doesn't load Grub bootloader. Instead, a prompt saying "grub rescue>" shows up.

Maybe I'm doing it wrong! Can someone tell me how to do it?

---

### Post by wilee-nilee on 2012-06-23
> **MetalDrummer said:**
> Hi!
I have a Dual Boot computer with Windows 7 and Ubuntu 12.04. I have more space in the Windows partition than Ubuntu's.

I want to reduce Windows partition size and increase the Ubuntu partition size, but every time i try to do it, when i restart it doesn't load Grub bootloader. Instead, a prompt saying "grub rescue>" shows up.

Maybe I'm doing it wrong! Can someone tell me how to do it?

So what does try it actually mean what are you doing.

W7 should be resized with its partitioner, and Ubuntu using a live Ubuntu cd.

If you need to reload the mbr try the boot repair app, using the recommended repair. If you have problems post the HTTP address of the bootinfo summary which is run automatically when you use the boot repair tool.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When you see a grub rescue> it possibly means there has been a change which may be under this circumstance a change of the UUID identifying the partition Ubuntu is in.

---

### Post by nipunshakya on 2012-06-23
> **MetalDrummer said:**
> Hi!
I have a Dual Boot computer with Windows 7 and Ubuntu 12.04. I have more space in the Windows partition than Ubuntu's.

I want to reduce Windows partition size and increase the Ubuntu partition size, but every time i try to do it, when i restart it doesn't load Grub bootloader. Instead, a prompt saying "grub rescue>" shows up.

Maybe I'm doing it wrong! Can someone tell me how to do it?

Have u already tried to resize your partitions??
did the error about grub occur after u tried to resize? 
see the following link to resize it:gparted is being used there;
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
 if you have startup problem, follow wilee-nilee's link on boot-repair tool

---

### Post by MetalDrummer on 2012-06-25
> **wilee-nilee said:**
> So what does try it actually mean what are you doing.

W7 should be resized with its partitioner, and Ubuntu using a live Ubuntu cd.

If you need to reload the mbr try the boot repair app, using the recommended repair. If you have problems post the HTTP address of the bootinfo summary which is run automatically when you use the boot repair tool.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When you see a grub rescue> it possibly means there has been a change which may be under this circumstance a change of the UUID identifying the partition Ubuntu is in.

I used the boot-repair-tool, but after rebooting it doesn't shows GRUB bootloader. It loads from Windows directly

---

### Post by MetalDrummer on 2012-06-25
> **WinuxUser said:**
> Have u already tried to resize your partitions??
did the error about grub occur after u tried to resize? 
see the following link to resize it:gparted is being used there;
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
 if you have startup problem, follow wilee-nilee's link on boot-repair tool

WinuxUser, the error occurs after resizing and rebooting

---

### Post by nipunshakya on 2012-06-25
the boot-repair should have done the trick for you... so basically, now you can boot only to windows right? 
So run the boot info script and post its output here:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by YannBuntu on 2012-06-26
Hello. I guess either:
 - Ubuntu partition is broken so not detected by os-prober, then Boot-Repair restored a generic MBR to boot directly Windows
 - or Boot-Repair reinstalled GRUB but update-grub didn't detect the kernels

**@MetalDrummer:** what was the URL which appeared after you used Boot-Repair? if you don't remember, please run Boot-Repair, click "Advanced options", click the "Backup partition tables.." button, save the ZIP file somewhere, then send me this ZIP file by email (yannubuntu ATT gmail DOTT com) or attach it to your reply in this thread.

---

### Post by MetalDrummer on 2012-06-26
> **YannBuntu said:**
> Hello. I guess either:
 - Ubuntu partition is broken so not detected by os-prober, then Boot-Repair restored a generic MBR to boot directly Windows
 - or Boot-Repair reinstalled GRUB but update-grub didn't detect the kernels

**@MetalDrummer:** what was the URL which appeared after you used Boot-Repair? if you don't remember, please run Boot-Repair, click "Advanced options", click the "Backup partition tables.." button, save the ZIP file somewhere, then send me this ZIP file by email (yannubuntu ATT gmail DOTT com) or attach it to your reply in this thread.

@YannBuntu here is the URL: [http://paste.ubuntu.com/1061288/](http://paste.ubuntu.com/1061288/)

@WinuxUser I think the URL is what you asked

---

### Post by nipunshakya on 2012-06-26
MetalDrummer, i don't see any GRUB installed in your system... i think YannBuntu is right here... your ubuntu partition is broken... and as he said, the generic mbr is restored to sda. 

The sda5 should have grub installed in it, but its not there.. further more, ubuntu isn't detected. Maybe a reinstallation of ubuntu would be fine ..

---

### Post by oldfred on 2012-06-26
Script says it is a 10GB drive. 

How are you booting both Windows 7 which needs more than 10GB, 30 usually recommended and Ubuntu which needs 4.5GB but 10 to 20GB unusually suggested.

---

### Post by YannBuntu on 2012-06-27
> **WinuxUser said:**
> The sda5 should have grub installed in it, but its not there.. further more, ubuntu isn't detected. Maybe a reinstallation of ubuntu would be fine ..

+1

> **oldfred said:**
> How are you booting both Windows 7 which needs more than 10GB, 30 usually recommended and Ubuntu which needs 4.5GB but 10 to 20GB unusually suggested.

+1

Also, the BootInfo indicates it is Win98, not Win7.

---

### Post by MetalDrummer on 2012-06-28
> **oldfred said:**
> Script says it is a 10GB drive. 

How are you booting both Windows 7 which needs more than 10GB, 30 usually recommended and Ubuntu which needs 4.5GB but 10 to 20GB unusually suggested.

Actually, I am testing it at Virtualbox before doing it on my physical machine. At my Virtualbox machine I have Windows 98 and Ubuntu 12.04 installed in two different partitions.

---

### Post by nipunshakya on 2012-06-28
MetalDrummer, you said you have windows 7 and ubuntu 12.04 installed as dual boot isn't it??? as u said?
 but the sda1 has windows 98 detected in it... Im having a bit of confusion of what you are doing.... or maybe you are confused of what u did...
Just to remind you... virtual box is just a software that installs other os as guest os.. removing virtual box will remove all your guest os too...without affecting your machine.....

---

