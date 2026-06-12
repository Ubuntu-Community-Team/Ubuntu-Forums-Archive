---
title: "installation on external drive 9.10"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by lmgranger on 2010-04-02
I have windows on my internal drive on a dell D 800. I removed the drive and installed 9.10 on an external drive through the USB port. It works great, until I put the internal drive back in. With the F12 button on startup, and choosing the USB device to boot from, I get a grub recover>. If I remove the internal drive it boots fine with this method. I don't want to have to remove the HD each time. Do you have any idea what to do? Is there a command I can enter at the grub recover prompt?

---

### Post by prodigy_ on 2010-04-02
> **lmgranger said:**
> I have windows on my internal drive on a dell D 800. I removed the drive and installed 9.10 on an external drive through the USB port. It works great, until I put the internal drive back in. With the F12 button on startup, and choosing the USB device to boot from, I get a grub recover>. If I remove the internal drive it boots fine with this method. I don't want to have to remove the HD each time. Do you have any idea what to do? Is there a command I can enter at the grub recover prompt?
It's really simple: at boot time Linux kernel assigns letters and numbers to devices and everything else uses them as identifiers.

When you unplug your internal HDD and install Linux, your external HDD is recognized as **sda**. So in Grub config, the boot partition is referred to as **/dev/sda<some_number>**.

Now you plug your internal HDD back. Linux enumerates it first and it becomes the new **sda** while your external drive becomes **sdb**. But Grub config doesn't know about that. :-)

---

Now, the solutuion... will depend on how familiar you are with Linux command line. If you're not, it might be easier to reinstall Ubuntu from scratch.

---

### Post by lmgranger on 2010-04-03
Thanks, Prodigy. I am not much of a programmer, but will attempt either solution with guidance. I started with an install of Ubuntu to the external drive leaving my internal drive in, but that resulted in the same issue, I assume because Grub was searching for the absent ext HD first. My objective is to have an external HD I can use in travel such that I can choose to boot from it from my laptop assigned from work. That way I won't adulterate anything in the company design on the laptop resident HD and I don't have to carry two laptops. I searched the fora and tried as best I could to follow, but admit - I do get confused.

---

### Post by efflandt on 2010-04-03
You do not have to remove your internal drive to install Ubuntu to an external drive.  But you have to make certain that you know how to put grub on the USB drive (instead of default to mbr of your main hard drive).

After you go through partitioning and everything and get to a **summary** screen just before installation proceeds, pay attention to the **Advanced** button.  Use that to put grub on the mbr of the USB drive.

I have done that and the USB drive is then able to boot fine whether it ends up as sdb on my laptop or sdf on my desktop (where sdb-sde are slots in memory card reader).  If you specify any extra mounts in /etc/fstab, that should be by UUID so partitions can be found even if they end up in a different drive order.

---

### Post by razy60 on 2010-04-03
Hi. You could try something like pendrivelinux or unetbootin.
Personally i would use Unetbootin as it would then be properly portable. I currently have 10.04 on one just to play with.

Raz

---

