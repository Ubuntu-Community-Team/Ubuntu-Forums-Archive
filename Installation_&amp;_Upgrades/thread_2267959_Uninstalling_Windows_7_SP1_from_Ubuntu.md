---
title: "Uninstalling Windows 7 SP1 from Ubuntu"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by mandarpowale on 2015-03-05
Hey guys,

I want to uninstall my Windows 7 SP1 from my Ubuntu. I had installed Windows first and Ubuntu Later. So How do I go about doing so?

I do have the Windows 7 installation CD.

Ty in advance.
Mandar

---

### Post by Bucky Ball on 2015-03-05
Install Gparted, if it's not already installed. Launch it, right click the Windows partition (it will be NTFS) and unmount it. Right click it again and delete it.

You may need to run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to reinstall the grub if you then can't get into Ubuntu. Did you install Win7 and Ubuntu in UEFI? If so, I imagine that might be a little more complex, but Boot Repair might take care of that too. Not sure. Give it a go. I can't really help with UEFI as don't use it and minimal knowledge of it. ;)

---

### Post by mandarpowale on 2015-03-05
> **Bucky Ball said:**
> Install Gparted, if it's not already installed. Launch it, right click the Windows partition (it will be NTFS) and unmount it. Right click it again and delete it.

You may need to run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to reinstall the grub if you then can't get into Ubuntu. Did you install Win7 and Ubuntu in UEFI? If so, I imagine that might be a little more complex, but Boot Repair might take care of that too. Not sure. Give it a go. I can't really help with UEFI as don't use it and minimal knowledge of it. ;)


I have Gparted Installed. I'm downloading Boot Repair which I will burn to a CD and use to uninstall Win 7. Lets hope it works. I'm going to use recommended settings.

My Bios does support boot from USB which I have to do using F8. There is no Rufus on my Ubuntu unless they make it for Linux too. I don't think that booting from USB is reliable.

I think I have Simple BIOS (UEFI is not supported)

Thanks for helping out.

---

### Post by Bucky Ball on 2015-03-05
You can't uninstall Win with Boot Repair. Use Gparted, then run Boot Repair if you *_can't_* boot to Ubuntu. You might not even need it.

Once you've deleted the Win partition and you can boot fine to Ubuntu, open a terminal and:

```
sudo update-grub
```

Then reboot. That will remove the Win grub entry.

---

### Post by mandarpowale on 2015-03-05
>                               [INDENT]                     You can't uninstall Win with Boot Repair. Use Gparted, then run Boot Repair if you *_can't_* boot to Ubuntu.
[/INDENT]




I downloading Boot Repair in case I have to face that scenario. It is better to be prepared for the worst.

Thanks for your help.

ADD: It worked , many thanks.

---

