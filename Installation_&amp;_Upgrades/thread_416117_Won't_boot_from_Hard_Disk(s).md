---
title: "Won't boot from Hard Disk(s)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by exodar on 2007-04-20
I just installed a Promise SATA300 TX4 card into an older server I had and also installed two brand new Seagate 250GB Hard Drives in hopes of setting up Ubuntu Server 6.10 with a Software RAID1 configuration.

I make it all the way through the Ubuntu Server installation and when I reboot the last thing I see is the Promise SATA300 BIOS show both drives and then it says "IDE BUS MASTER ENABLED" and my computer beeps like it is going to boot and then it just sits there.

I am making the assumption that since my Ubuntu installation saw both drives just fine that the Promise SATA300 card is working properly, but alas it just won't boot.  Is it not possible to boot from drives hooked up to one of these controllers?!?!

Any hints?

---

### Post by exodar on 2007-04-20
I noticed that I am getting this error message just before the Ubuntu 6.10 Server Installation started:

Cannot allocate resource region 4 000:00:07.1
UHCI_HCD: Found HC with no IRQ

Any idea what that means and what I should do about it?

---

### Post by exodar on 2007-04-20
More updates...

I removed the Promise SATA300 TX4 card from the system completely and rebooted.  Then I selected Install Ubuntu From CD and it still gives me those same errors above.  So whatever is not working properly, it is not the Promise card.

Now I am installing Ubuntu to just one of the disks without any kind of Software RAID setup to see if it will boot from that.

Report soon...any help or ideas are GREATLY appreciated!

---

### Post by exodar on 2007-04-20
Okay...eliminating the Software RAID1 from the Installation has gotten me further.  Now at least GRUB tries to load and I get this:

GRUB loading, please wait...
Error 22

Hope someone has seen this.

---

### Post by Techmaster on 2007-04-20
I'm having the EXACT same issue right now.  I'm using an Aopen AX4GE-N motherboard, and a Promise SATA card, I believe the exact same one you are using.  I'm trying to install Feisty server on it, and when it shows the drives, it's showing the two 500GB drives hooked up to the SATA first, then the 20GB drive hooked to the onboard IDE of the motherboard last.  I think the motherboard's BIOS is stupid and is reversing the order of the controllers, and I can't find a way to change that order.

---

### Post by exodar on 2007-04-21
Maybe we can help each other with this.  Are you trying to boot from the SATA drive or the IDE drive?  I would recommend setting up the GRUB bootloader on the IDE drive and use the SATA drives for your installation of Ubuntu...I think thats possible.

---

### Post by Qumefox on 2007-06-28
Ever find a solution to this?  I was having the same issue, and it turns out that the promise sata300 tx4 was reversing the device order listed to the kernel compared to the bios order listed on install. Therefor grub was pointing to wrong boot partition.

To fix this, I used a iso called 'Super Grub Disk'  and it let me both see the order the devices were being reported to the kernel (the order that mattered) and let me reconfigure to point grub to the right location for /boot

---

