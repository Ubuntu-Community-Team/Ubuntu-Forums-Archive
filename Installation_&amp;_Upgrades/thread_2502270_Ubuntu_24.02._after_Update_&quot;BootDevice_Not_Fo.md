---
title: "Ubuntu 24.02. after Update &quot;BootDevice Not Found&quot;"
date: 2024-11-07
forum: Installation &amp; Upgrades
---

### Post by apophis2 on 2024-11-07
Hi guys!

I hope this is the right forum.

I'm running Ubuntu 24.02 on my HP ProBook 450 G8, with one partition for Windows.

 Yesterday, I installed an update (Ubuntu) and now my computer is not  booting anymore. Instead a "HP PC Hardware Diagnostics UEFI" is loaded.  Exiting this tool gives me:
 BootDevice Not Found
Please install an operating system on your hard disk
Hard Disk -(3F0)
F2 System Diagnostics
For more information, please visit: [www.hp.com/go/techcenter/startup]("http://www.hp.com/go/techcenter/startup")
 I tried to boot from a stick, but it's also not working. The given  link is not helpful at all. I'm very annoyed, because I need access to  my data and it's frustrating that nothing has helped so far.
 Does anyone an idea of what it's happening here?
 I'm thankful for every hint!


 cheers, 
roland

---

### Post by oldfred on 2024-11-07
There is no Ubuntu 24.02? Is it really 24.04.1 or 24.10?

HP requires you to go into HP's system settings to set boot order.
Windows updates often reset Windows to first, so you may just need to reset boot order in System settings, not one time boot menu.
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

HP PROBOOK with preinstalled WINDOWS 11. Locked NVRAM Larger ESP
[https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr](https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr)
Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2) &

HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

---

### Post by apophis2 on 2024-11-08
Hi!

Many thanks for your quick reply!

Actually, an Ubuntu update caused this problem. You'r right, it's probably 22.04.01, Currently, I can't check.

Anyway, after typing F10 come into BIOS but I can't find the entry System Configuration -> UEFI boot.

Nothing has changed so far.

Does someone has a different idea or maybe had the same problem?

Thanks for your hints in advance!

---

### Post by oldfred on 2024-11-08
Create Ubuntu live installer for 24.04.1. 
Often best to always have a live installer or repair/recovery drive for current versions of every installed system.

Did you make good backups before upgrade?
If major issues that can simplify process. 
New install & restore from backup can take as little as an hour.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2024-11-08
F10 > System Configurations > Boot Options > OS Boot Manager > Ubuntu
Save and Exit

Alternatively:-
Power on 
Press F9 (at, say, 1 second intervals)
Boot Option Menu should appear

Any sign of Ubuntu?

---

### Post by wildmanne39 on 2024-11-08
Moved to Installation and Upgrades as a more appropriate sub-forum.

---

### Post by apophis2 on 2024-11-11
Hey guys,

many thanks for your answers.

I decided now for deleting the 'old' ubuntu and installed 24.04.1.

The good message is, that ubuntu is booted *yay*

Unfortunately, a new problem showed up. I have no possibility of booting Windows anymore.

How can I change it?

Thank you again for your valuable hints!

---

### Post by apophis2 on 2024-11-11
ok, obviously I have deleted my Windows partition..... I don't know why but it's gone.

Thank you for your help! I guess I need to re-install Windows again....

---

### Post by yancek on 2024-11-11
The Grub os-prober software to detect other operating systems is disabled by default so you would need to enable it.  The link below is to another thread here at the forums, see post 8 which explains what you need to do.

 [https://ubuntuforums.org/showthread.php?t=2501146&p=14207059](https://ubuntuforums.org/showthread.php?t=2501146&p=14207059)

---

### Post by apophis2 on 2024-11-11
Thank you!

I tried with changing the grub but it's still just booting ubuntu.

I already tried testdisc and photorec as well, I thought I could recover my system, but nothing is changing,

I try to cope with the situation that my windows is gone for some reason......

---

### Post by oldfred on 2024-11-11
Are you sure you deleted Windows partition or just Windows boot loader?
Post link to Summary Report from Boot-Repair.

---

### Post by yancek on 2024-11-11
I don't see anything in your posts indicating which windows version you are using or whether it was EFI or not so posting the output of boot repair as suggested would be your next step.

---

### Post by apophis2 on 2024-11-13
Thank you guys! There is now a lot to read but I'll tell you what happened or if I could solve this issue.

---

