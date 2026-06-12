---
title: "Mint Boot Repair isn't helping&#8207;"
date: 2016-03-02
forum: MINT
---

### Post by elson3 on 2016-03-02
[http://paste2.org/zgv5c7vb](http://paste2.org/zgv5c7vb)

Hello, I have two Linux Mint installations in this drive. Let me tell you what happened:

First,  I had only one Linux Mint installation, with its home folder encrypted  in a separate partition. Some days ago, I decided to try VMware in this  installation, and after rebooting the system, Mint refused to load. 

Since  then, I'm trying to troubleshoot this issue using Boot Repair in Linux  distributions running with live usbs. On my first try, after solving  some confusion about the need of a dedicated unformatted boot partition,  Boot Repair hanged while purging and reinstalling kernel for hours and I  had to manually stop it. Second try, similar things happened.

After  many tries, I decided to install Linux Mint again in a separate  partition and try to recover what I could from the first installation.  After achieving this, I decided to try Boot Repair again, report if it  didn't work and try to see if any expert could help me. After some  tries, my problem continues. My first Linux Mint installation remains  unacessible. 

So, reporting and asking for help is what I'm doing now.

Thanks  for your attention. Any help is very appreciated. I would really love  to restore my access to my first Linux Mint installation, as I already  customized it heavily to my preferences.

---

### Post by oldfred on 2016-03-02
Moved to Mint sub-forum.
Mint also has its own forum.

Do not know Mint.
Your sda4 is shown as bios_grub, but also shows ext4?
The bios_grub partition should be 1 or 2MB unformatted. So remove format using gparted and reinstall grub. (I think unformatted is at bottom of list in gparted).
Boot-Repair should not be running fsck on sda4, but saw ext4 so ran it.

---

### Post by elson3 on 2016-03-02
Hi I tried it again. I did what you told regarding the bios_grub partition, I removed that one and created one of 2MB unformatted at the start of the disk and put in it the bios_grub label as well as legacy_boot.

Running Boot Repair again and well.... it is stuck at kernels purging: 

[IMG]http://i.imgur.com/Bnz6pgI.png[/IMG]

---

### Post by oldfred on 2016-03-02
Is Internet working, as it has to download latest grub/kernel.
Best to use hard wired Ethernet for install & major updates.

---

### Post by elson3 on 2016-03-02
Yes, it's working. I can download and install things in terminal and elsewhere (boot repair was downloaded in terminal). This is a live usb running Lubuntu.

---

### Post by oldfred on 2016-03-02
I though Boot-Repair chrooted into your install to update from inside it.
But if using Lubuntu to update Mint and not chrooted not sure what happens, it may be trying to update Ubuntu kernel when you need Mint's version.

---

