---
title: "Grub 1.5 to Grub2 problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by lvalen18 on 2009-11-14
MY PC for whatever reason does not boot a DVD of anykind.. So while using Ubuntu over the Years i managed to get a DVD option in grub witch starts up the Bootable DVD since the Bios doesnt see it. But with 9.10 Out Grub is different and I can't Manage to get The DVD Option to work

In the old Grub this is what I Put along with the Files in their correct location

[B]title 		DVD Boot

root		(hd0,0)

kernel 		/boot/grub/memdisk.bin

initrd 		/boot/grub/sbootmgr.dsk[/B]

With this I can Use a Bootable DVD but since the Change to the new Grub Version I cant seem to make it work.. I'm just not that familiar with Ubuntu 9.10 to make it work and thats mostly what sets me back from an Upgrade..

So Im Asking if theirs somebody who might take the Time to Explain how to basically convert the Entry Setup from the Grub used on 9.04 to the new one on 9.10. Please and Thankyou

---

### Post by drs305 on 2009-11-14
Do you already have Grub 2 and Karmic installed?

In Grub 2, I can mount the Karmic iso. Others using the same menuentry have not always had the same success.

In this example, the iso is stored on sda7. The "noprompt" helped when logging off the iso.

> 
menuentry "Karmic 64 ISO (sda7)" {
loopback loop (hd0,7)/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-desktop-amd64.iso noprompt
initrd (loop)/casper/initrd.lz
}


I put this in /etc/grub.d/40_custom. Make sure it is executable, then run "sudo apt-get update" to update the grub.cfg file.

---

### Post by lvalen18 on 2009-11-17
I Have Karmic with Grub 2 Installed..
SO I see that a Custom Folder needs 2 be created in the /Grub.d directory.. along with the Menu entry in a executable file

---

### Post by lvalen18 on 2009-11-25
I found out i can just uninstall Grub 2 and install the previous version ... Doesn't Fix the Probem but it patches it up for now.... Thank You to all who viewed and replied :D

---

### Post by von Stalhein on 2009-11-27
> **lvalen18 said:**
> I found out i can just uninstall Grub 2 and install the previous version ... Doesn't Fix the Probem but it patches it up for now.... Thank You to all who viewed and replied :D

GRUB 2 has been naughty to me and won't boot XP (I've filed a bug)

What I want to do is remove it and go back to 1.5 - can you tell me how you did that please??

TIA

Belay that request!!
[http://ubuntuforums.org/showpost.php?p=8341799&postcount=4](http://ubuntuforums.org/showpost.php?p=8341799&postcount=4)

---

