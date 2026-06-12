---
title: "Ubuntu installation fails (amd ide sata)"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by jourik on 2006-11-10
I used to run Linux for a while back in the days. Now that I'm getting tired of Windows, Ubuntu seems like a decent option.

The installation process runs fine, however on the first boot, the system hangs on the first screen after OS selection, with the orange progress bar only progressed a few pixels..

My specs:
AMD64x2 dual core 3800+ with 2GB DDR2 RAM
hda
- hda1: active, /boot
- hda2: /
hdb: ntfs
hdc: ntfs
hdd: cdrom
sda (SATA)
- sda1: active, windows, ntfs
- sda2: ntfs

-Kubuntu- installation oddly hangs at the disk partitioner (qparted) which seems to have problems with the sata disk..

Fedora 6 installs fine as well but hangs at the grub loader..

I tried several setups (just one partition, seperate boot and root partitions, another HD as primary master)

Does anyone recognize a pattern here, or know about issues?

---

### Post by jourik on 2006-11-11
I ran the recovery mode as well, it says it is "waiting for the root filesystem... ..." (nothing happens at that point)

---

### Post by Kurkoko on 2006-11-11
I got same problem, when installation reaches the partitioning step system hangs up or i can cancel but no way that gnome partitioning tool doesnt recognise my sata drives, sound card and ethernet. Seems like a problem with chipset?

I tried ubuntu 6.06.1 and 6.10, the 6.06.1 give me problems detecting graphics card and I have to edit xorg.conf "ati"->"vesa", but 6.10 crashes anyway.

Here with 2 sata HD, 1 pata DVD+-RW
Motherboard Asus K8N4-E Deluxe socket 754 amd64
PCI-E Ati x800xl

Thanks.

---

### Post by jourik on 2006-11-12
Ok I now installed it on the SDA drive.. managed to load the kernel and start linux manually via the grub prompt.. though halfway booting (after 135.877176) it hangs with the message:  ALERT! does not exist. Dropping to a shell..

Then it shows Busybox with the error message: can't access tty; job control turned off

---

### Post by shimrah on 2006-11-14
Similar problems here...

I've convinced my wife to switch to Ubuntu (Frozen Bubble and my screensavers won her over :S ) ... but her ASUS K8N4-E Deluxe just won't do it! ](*,) 

I can get into the 64- and 32-bit LiveCD, as well as the 64-bit Alternate text install CD ... but in all cases it hangs before allowing me to partition.

32-Edgy LiveCD is the same.

She has one SATA drive. BIOS is updated. Has anyone with this MB gotten this to work?

Thanks!
Shim

---

### Post by nova- on 2006-11-15
Hi!

check these:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33269](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33269)

(from: [http://www.google.com/search?hl=en&lr=&q=K8N4+linux+sata&btnG=Search](http://www.google.com/search?hl=en&lr=&q=K8N4+linux+sata&btnG=Search) )

> 
[http://forums.fedoraforum.org/showthread.php?t=74313](http://forums.fedoraforum.org/showthread.php?t=74313)

linux irqpoll noapic acpi=off
------
or try this:

Had same problem with same hardware (K8N4-E)

This is what helped me along: at the startup of the installation cd, boot the linux kernel with the option

"pci=nommconf"


just for comparison:
I've seen some posts where the ASUS A8N-E (different mobo, i know) works using SATA drives just fine, like:
[http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/](http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/)

---

### Post by nova- on 2006-11-15
double post

---

### Post by shimrah on 2006-11-17
Ah! Happy day!

To recap, my ASUS K8N4-E wouldn't get past the partition step in the Dapper install... and the mouse (USB) didn't work...

This posting saved me: [https://launchpad.net/distros/ubuntu....15/+bug/34651](https://launchpad.net/distros/ubuntu....15/+bug/34651)

Just toss a pci=nommconf to the install parameters, and the problems melt away. :-D :-D :-D 

This may restore my wife's faith in Ubuntu (and me!) ... 

... so, to ask a real newbie question... where do I add this parameter to the installation to avoid this problem in the future?

Thanks!



> **shimrah said:**
> Similar problems here...

I've convinced my wife to switch to Ubuntu (Frozen Bubble and my screensavers won her over :S ) ... but her ASUS K8N4-E Deluxe just won't do it! ](*,) 

I can get into the 64- and 32-bit LiveCD, as well as the 64-bit Alternate text install CD ... but in all cases it hangs before allowing me to partition.

32-Edgy LiveCD is the same.

She has one SATA drive. BIOS is updated. Has anyone with this MB gotten this to work?

Thanks!
Shim

---

### Post by nova- on 2006-11-17
edit this: /boot/grub/menu.lst

search until you find something like this:
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

add pci=nommconf to the kernel line eg:
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash pci=nommconf

reboot

you can also (if prefered, or needed) temporarily modify the kernel boot options while inside grub (command line at bootup), take this for reference:

after reboot press key 'e' (edit) in grub-menu on highlighted Menu-entry you want to boot, 
then select "kernel" line and press key 'e' again. 
add your options, enter to save, escape to cancel
b to boot.  these changes are temporary and wont be saved for the next boot.

note: if you press escape and go back to the root menu, then your changes will be removed, so remember this.

---

