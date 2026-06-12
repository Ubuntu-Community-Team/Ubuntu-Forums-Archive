---
title: "Cannot boot Windows 8.1 from Grub with Secure Boot enabled"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by abovett2 on 2013-10-20
Hi

I've got a Dell Inspiron 15R which I dual-boot with Ubuntu 13.10 and Windows 8.1. I used "Boot Repair" to sort out the dual booting, and it works fine without Secure Boot enabled - I can boot Windows or Ubuntu from the Grub2 menu. 

However, I would like to take advantage of Secure Boot, but when I enable it in the UEFI setup (after selecting the "SecureBoot" option in Boot Repair), I cannot boot Windows from the Grub2 menu. Ubuntu still boots OK.

I _can_ boot Windows from the UEFI boot menu (accessed via the F12 key as the PC boots) with Secure Boot enabled, but I'd like to be able to boot either OS from the Grub2 menu.

The message I get from Grub2 when I try to boot Windows with Secure Boot enabled is something like this:
```

/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(1,800,fa000,78cd082761b71840,9b,bd)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image

```

I have run Boot Repar several times with different options to try to fix this, but without success. The URLs provided by Boot Repair are:

[http://paste.ubuntu.com/6271276/](http://paste.ubuntu.com/6271276/)

[http://paste.ubuntu.com/6271482/](http://paste.ubuntu.com/6271482/)

I've read a few posts and discussions elsewhere but none seem to cover this case. I'm still struggling to get my head around UEFI and am wary about fiddling too much with the UEFI settings in the PC setup in case I render it completely unbootable, so any advice from someone who understands this better than me would be welcome. 

Regards

Andy

---

### Post by ubfan1 on 2013-10-20
This is bug 1091464.  Please add yourself to the bug, and provide some details on your machine.

---

### Post by abovett2 on 2013-10-20
Thanks, ubfan1. Glad to know it's not just me being stupid. I've done as you suggested and added my details to the bug in question.

---

### Post by oldfred on 2013-10-20
Post #11 in bug report also discusses use rEFInd. 
Somewhere in grub2's chainload a file that is not secure boot must exist. 

But secure boot is not all it is played up to be by Microsoft. 
       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by brooklynzoo81 on 2014-09-08
Hello i am having the same exact problem as well on a Dell XPS 13 with version 14.04 and windows 8.1.  For now i have disabled secure boot and i am able to boot into both.  Not sure if having bitlocker and home folder encrypted in ubuntu plays any factor to this, which i have.  How can i submit my info towards a bug report?  thanks.

---

### Post by oldfred on 2014-09-08
@brooklynzoo81
Clickable link to bug report. But your encryption may be something different also, but they should include that if possible. 
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

