---
title: "Dual boot toshiba laptop, win 8 Ubuntu 13.10"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2013-11-13
I completed a dual boot with my new toshiba laptop with Win * pre-installed.  I shrunk the main partition and added two new partitions.   / and linux swap.

I then installed Ubuntu 13.10 on teh / partition.  

When I start up I get Grub 2....  I choose ubuntu and all is well.

When I choose window eufi loader I get an error....

```
/EndEntire
file path: /ACPI(a0341d0,0)/PCI92,1f)/unknownMessaging(12)/HD(2,200800,8200,1fc7116fd9e211,a5,c4)/file(\EFI\Microsoft\boot)/File(bootmgfw.efi)/endEntire
error: cannot load image.
Press any key to continue....

```

I did reboot several times after making the partitions, Windows did not perform a chk disk....  

When I installed ubuntu...  I was not given an option to install along side,,, it stated there was not an operating system installed.  I did turn off fast start up for the shut down.

Thanks,

D

---

### Post by oldfred on 2013-11-13
Best to see details. If an Ultrabook you may have had Intel SRT that uses RAID and then Ubuntu desktop installer has issues seeing drive correctly.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Also see info in links in my signature.

---

### Post by ubfan1 on 2013-11-13
This is bug 1091464. Please add yourself to the "Does this affect me" link on the bug page.  A workaround may be to turn off Secure Boot, but I've never tried that (affects me too), I just use the efi boot menu (F12) to select the non-default OS (Windows) when I need it.

---

### Post by claven123 on 2013-11-14
Please write on a paper the following URL:
[http://paste.ubuntu.com/6419169/](http://paste.ubuntu.com/6419169/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

No change has been performed on your computer.


Thanks,

D

---

### Post by claven123 on 2013-11-14
Secure boot in enabled

D

---

### Post by oldfred on 2013-11-14
Have you tried without secure boot.

And with secure boot on and with it off can you do this? Both Ubuntu and Windows?
Can you directly boot from UEFI/BIOS or using one time boot key. f12 on my system, but may vary.

---

### Post by claven123 on 2013-11-15
Ok, so I thought that with Ubuntu 13.10 it would have some how gotten past the secure boot issue....  but simply disabling it worked.  I just went into the efi loader,,,,, pressed f2 at start up and changed it to disabled.  Then on reboot it worked just fine.

Thanks,

d

---

