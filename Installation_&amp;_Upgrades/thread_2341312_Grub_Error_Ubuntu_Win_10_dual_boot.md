---
title: "Grub Error Ubuntu /Win 10 dual boot"
date: 2016-10-26
forum: Installation &amp; Upgrades
---

### Post by jgb219 on 2016-10-26
Installed Ubuntu 16.04 alongside 64bit Win 10 install but made changes to partition sizes after installation was complete. Laptop will not boot due to grub error, so I downloaded and ran a USB boot disk of boot repair. It didn't successfully boot, and this link was generated: [http://paste.ubuntu.com/23386216](http://paste.ubuntu.com/23386216)

I'd appreciate any help I can get on this,

Thanks

---

### Post by yancek on 2016-10-27
I'm not sure what changes you made to your partitions but, looking at your boot repair, you don't have a grub.cfg file which is what contains the menu you should see on boot.
You have a standard MBR install with Grub code in the MBR but without a grub.cfg file, it won't boot.  There might be an Advanced option with boot repair but if not, you can use  the chroot method at the Ubuntu documentation site below to repair Grub and update it to create a grub.cfg file.

 
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Bucky Ball on 2016-10-27
Let me guess. Did you resize the partitions, *including the Win OS partition*, with Gparted? Either way, upside-down way to do it.

Generally, defrag Win OS partition several times then shrink Win partition using Win tools. Shrink any other partitions you need to shrink (EXT* partitions with Linux tools). Leave blank, unallocated space then install Ubuntu to it. You can create partitions of whatever size you like during the install.

---

### Post by oldfred on 2016-10-27
You have an error in your grub.cfg. Did you edit scripts, use grub customizer, or manually edit grub or 40_custom?

I had this once when I had a typo in my 40_custom.
/boot/grub/grub.cfg.new

That is the error file or version with the error.
Reviewing that file gave me the error line number, but in my case it was a missing }, so error was not exact line.

---

### Post by jgb219 on 2016-10-27
thank you, I am going to try this method. I used a third party app to change the partition sizes. I made a dumb mistake in thinking I needed to manually create partition for Ubuntu. Once I saw that you can actually do that during Ubuntu installation, I figured I could give that 50GB back to the main partition, and once i merged and resized, etc thats where the trouble started

---

### Post by jgb219 on 2016-10-27
I resized and merged the partitions after booting back into windows.. thats when the trouble started.

---

### Post by jgb219 on 2016-10-27
> **oldfred said:**
> You have an error in your grub.cfg. Did you edit scripts, use grub customizer, or manually edit grub or 40_custom?

I had this once when I had a typo in my 40_custom.
/boot/grub/grub.cfg.new

That is the error file or version with the error.
Reviewing that file gave me the error line number, but in my case it was a missing }, so error was not exact line.


No, I actually wasn't  even aware of the term grub until this happened yesterday.

---

### Post by oldfred on 2016-10-28
Then post this in code tags:
cat /boot/grub/grub.cfg.new

---

