---
title: "Breezy 5.10 on USB hard drive boot problem"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by RyanGT on 2005-10-09
I recently tried out the Breezy Badger Live CD and was very impressed.  I have now tried to install it to a USB hard drive attached to my laptop and am having so troubles.

I have a somewhat interesting setup.  My laptop is currently dual boot with Windows XP and Fedora Core 3.  I am trying to install ubuntu breezy on a USB hard drive to try it out and with the intention of taking Linux off my internal hard drive to recover some space (possibly also moving fedora to the USB or ditching it).

I tried following the steps in this thread:
[http://www.ubuntuforums.org/showthread.php?t=5151](http://www.ubuntuforums.org/showthread.php?t=5151) which is for 5.04, but when I got to steps like 'nano /target/etc/mkinitrd/modules' the modules files was not there.  I don't know what I did wrong.  I was reading a fedora post on usb installation and the author kept saying that in FC4 this would all be automatic, so wondering if 5.10 made usb installation automatic, I tried it.  So, without using the expert install method, I installed ubuntu 5.10 on on partition of my external hard drive.  I also install GRUB on the MBR of the USB hard drive, but I had to go into my BIOS and change the boot order for it to boot from the USB hard drive.  That means that the boot order is now different from when I installed ubuntu and the (hd1) entries in GRUB would need to be (hd0).  To make that more complicated, it appears that unplugging and replugging the USB drive makes my BIOS switch back to booting from the internal hard drive first.

But, GRUB is already on my MDR of the internal hard drive, only it only includes Windows and fedora.  Can I simply add ubuntu to the existing GRUB and if so, how to I do it?  Do I use a rescue CD or boot into fedora?  How do I get the names of the kernel files and all of that that I will need?

Lastly, do I have a problem becuase I did not use the expert method and did not add modules like usb-storage to the kernel initialization process?  Can I go back and add the needed modules without reinstalling everything?

Thanks for any help,

Ryan

---

### Post by RyanGT on 2005-10-09
Just a quick update.  I was able to use the grub prompt to edit the boot parameters from root (hd1,2) to root (hd0,2) and start the boot from the MBR of my USB hard drive.  This seemed like it was starting to work and then it stopped shortly in saying /dev/sda4 did not exist - this is supposed to be the root partition.  I am assuming it doesn't exist because usb-storage and friends aren't in the initrd img. How do I fix that with the least ammount of pain?

I was able to get the information on the kernel and initrd from the grub on the usb hard drive and then booted into fedora on my internal hard drive and added ubuntu to that grub.  I can now get just as far into the install from either grub, so that problem is solved.  I think I just need my sda devices to work in the initrd and I might be in business.

Please help.

Thanks,

Ryan

---

### Post by RyanGT on 2005-10-09
One last update before heading to bed.  I tried following the recommendation of this thread to create a new initrd.img with the modules need for usb hard drive:
[http://ubuntuforums.org/showthread.php?t=20522&highlight=initrd](http://ubuntuforums.org/showthread.php?t=20522&highlight=initrd)

Following those steps, I had a problem with mkinitrd and mkinitrd.conf.  It seems that the rescue CD for 5.10 includes mkinitramfs instead of mkinitrd (I could not find a mkinitrd.conf and mkinitrd is not in /usr/sbin)  I tried editing the mkinitramfs config and modules files and then tried creating an image using mkinitramfs -o /boot/initrd.img-kernel # but when I try to boot from this I get a message 
"can't access tty: job control turned off"

What should I do now?

Ryan

---

### Post by balabek on 2005-10-15
Hi,

I also had this problem.

I am installing it using Install CD on an external USB disk. Installation goes and then asks me to reboot.
Then I am booting using 5.10 LiveCD. The problem is Breezy 5.10 does not include mkinitrd tool in LiveCD. mkinitramfs comes instead.

I tried to to read documentation on mkinitramfs and initramfs.conf.

I added following lines in file "/etc/mkinitramfs/modules":
[INDENT]sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage
[/INDENT]

Really not sure if the above step is required, since initramfs.conf has a parameter for automatic loading of modules for USB among others.

I ran command "mkinitramfs -o /boot/usbinitramfs.img", then modified GRUB parameters. Rebooted the computer and got an error.

The booting process seems to proceed without modules getting loaded. The guide for 5.04 had mentioned introducing a delay during booting.

So I tried inserting the following line at beginning of file "/etc/mkinitramfs/initramfs.conf" 
[INDENT]**WAIT=10**[/INDENT]
They should have documented this in initramfs.conf manual. 

Again, I ran command "mkinitramfs -o /boot/usbinitramfs.img", and rebooted. It works :smile: .
While booting it paused for 10 seconds without displaying any messages, and then proceeded normally.

---

### Post by RyanGT on 2005-10-16
When it boots do you see a message that it is waiting 10 seconds?  I get a message like that in Hoary.  I didn't add that wait and didn't know where.   I guess I don't need it though.  I don't know where to look for mkinitramfs documentation (especially before you have linux installed).

---

### Post by balabek on 2005-10-16
It does not display message that it is waiting. I too would receive that message in 5.04. Now it says that modules are loading and simply waits for some time. But it works.

The manuals I am referring to are accessible using the man command from shell.
[INDENT]man mkinitramfs
man initramfs.conf[/INDENT]
WAIT option seems to be supported, since mkinitramfs produced the ram image without errors. But this option is not mentioned in provided manuals.

---

### Post by RyanGT on 2005-10-16
Cool.  I am glad that it works.

---

