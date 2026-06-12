---
title: "Virtualbox not accessing drives"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by ddvanrooy on 2010-08-30
Hi All. I am running Virtualbox with Win XP on Ubuntu 10.04, Everything is mostly ok, but I find two problems. I cannot seem to find a way to access my second (physical) harddrive as well as DVD writer. I have tried to add it to shared folders in Virtual box, but no go. 
I can , however, access my USB drives ok, after I found out about the Vbox user permissions. But what I do notice is that it seems Ubuntu unmounts the USB drive as soon as Vbox "mounts" it. Is there no way to have these drives mounted simultaneously on both platforms ?
Thx
D

---

### Post by Bachstelze on 2010-08-30
> **ddvanrooy said:**
> Is there no way to have these drives mounted simultaneously on both platforms ?


[SIZE="6"]**[COLOR="Red"]NO![/COLOR]**[/SIZE]

**Never** mount the same drive twice. Even if by some clever trick you are able to have the system let you do it, you have a 100% guarantee for data loss.

---

### Post by ddvanrooy on 2010-08-30
Ok thanks. However , I still need to solve the problem of the second hard drive. It is on a separate controller, (SATA) and I have managed to enable it in the "settings" - "storage" options. however the virtual XP machine still doesnt see it.

---

### Post by lechien73 on 2010-08-30
To access an entire physical hard disk in VirtualBox, you need to create a raw disk. AFAIK this can only be done via the command line.

The VirtualBox manual gives details on how to give access to an entire physical disk from a guest, at this link: [http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

In summary, though, if the disk is available in Ubuntu as /dev/sdb, then you would issue the following command:

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/HardDisks/rawdisk.vmdk -rawdisk /dev/sdb -register
```

Then in the GUI, attach this disk to your XP guest.

---

### Post by ddvanrooy on 2010-09-03
I found a solution by setting the drive up as a network drive. Now the virtual XP machine can access it fine. It was quite a process to figure out. The Vbox network adapter must be set as "host-only". Then in preferences, the Vbox DHCP must be disabled, and a static IP giving top the vboxnet0 adapter. of course this IP must be in the same range as the host PC. Finally, in XP the IP  must be set also as static, within the same range. As long as these folders are shared in Ubuntu, the XP machine access it like a normal network drive. The IP addresses can be: Host machine: 192.168.0.5 , the vboxnet0: 192.168.0.15 and finally XP: 192.168.0.16
Hopes this can help someone in future

---

