---
title: "Urgent: Cannot boot after accidently removing kernel image"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by futureal2032 on 2011-04-19
Hi,

I have Ubuntu 10.10 installed on my laptop.

Its a dual boot with XP, have been using ubuntu/xp for a while now..

**Till now i always used to remove older kernel images after ubuntu update, then update grub and do "sudo apt-get autoclean"**

never had any problem at all..

this time though,
[B]i skipped the second step, i removed the old kernel image and did "Autoclean" on apt-get but forgot to update grub.

Now after i have reboot, when grub loads i can see only 2 "Memtest" lines in grub list and 1 "windows xp" line.

the "Linux kernel generic" line is missing. I can boot in xp (have done just that to post this) but since there is no line in grub list to boot into Ubuntu, cant boot in Ubuntu.

Is there any option, something i can do at "Grub" to boot into Ubuntu?[/B]

---

### Post by oldfred on 2011-04-19
Did you delete the kernel or just the menu entry?

Manual boot from grub menu command line change (hd0,1) & sda1 to your drive/partition:
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

If you deleted kernel, you may be able to chroot into your system from a liveCD and install a new kernel.

---

### Post by futureal2032 on 2011-04-20
> **oldfred said:**
> Did you delete the kernel or just the menu entry?

Manual boot from grub menu command line change (hd0,1) & sda1 to your drive/partition:
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

If you deleted kernel, you may be able to chroot into your system from a liveCD and install a new kernel.

Tyhanks for the reply,
what i did is i updated ubuntu using update manager.

updates installed a new kernel,
so i removed the old kernel image file..

(update installe linux-image-2.6.35-36-generic so i removed linux-image-2.6.35-28-generic)

I will try doing what you suggested

---

### Post by futureal2032 on 2011-04-20
> **oldfred said:**
> Did you delete the kernel or just the menu entry?

Manual boot from grub menu command line change (hd0,1) & sda1 to your drive/partition:
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

If you deleted kernel, you may be able to chroot into your system from a liveCD and install a new kernel.

I did what you said,
but when i type "insmod" command (second line)
it gives me error unknown file system

it gives me same error for "set root" command (third line)

i booted from live usb and gparted shows me my partitions as,

/dev/sda7 boot
/dev/sda8 root
/dev/sda9 home

so i used (hd0,7) (in place of your hd0,1)
and /dev/sda8 (in place of your /dev/sda1)

please suggest what i can do

---

### Post by oldfred on 2011-04-20
If you have a separate /boot you have to mount it also. Most instructions do not include that is a separate /boot is uncommon for standard desktops. Only required for really old systems with 137GB boot limit or servers with RAID or LVM which some do use on desktops.

Post this so I can see exact configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

