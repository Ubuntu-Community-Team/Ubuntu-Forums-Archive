---
title: "Grub Error 17"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by Tom1942 on 2007-10-05
I successfully set up a dual boot of windows xp sp2 and ubuntu 6.06 on a desktop.  The xp was installed first on a new hard drive that was partitioned for xp and ubuntu.  It was an upgrade xp.  Then, ubuntu was installed into a large partition and 2 smaller partitions, one for swap and one an extended partition.  Menu.lst was set to pause so I could choose xp or ubuntu.

I also installed ubuntu 6.06 on a laptop.  I found that I mostly did my linux on the laptop and xp on the desktop.  I was having problems defraggng the c drive on the xp desktop which was down to only 7% free space.  I decided I would remove ubuntu from the desktop and only use the laptop for linux.  _That's when I made a knucklehead decision._  I chose the smallest partition on the desktop and tried to delete it (in order to reallocate that space to the C drive).  Using the management console in xp I tried to delete the partiton but xp said it couldn't do it.  I figured ok, no harm, forget about it and figure something else out.

Next boot up of the desktop resulted in "Grub loading stage1.5" and "Error 17".  I have not been able to boot up since.

I tried the recovery console in xp.  It wants an administrator password.  None of the passwords I usually use for logins works, pressing enter without typing anything (null) does not work.  When I installed xp I created a new administrator account and then deleted the default administrator account.  My research indicates that should not be a problem as the recovery console admin password is not the same as the log in admin password, but so far nothing works.

I decided to attack the problem from an ubuntu instead of xp point of view.

I eventually found System Rescue CD at [www.sysresccd.org/](www.sysresccd.org/) which let me get into ubuntu and find the menu.lst file highlighted in red.  I tried to edit it but was told it was read only.

I'm hoping I can create a new menu.lst and save it in the right place but I don't remember what was in it, or how it was generated, I'm pretty sure I didn't write it out.

The relevant portion of the menu.lst on the laptop is:

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

The dual boot menu.lst has an entry for windows xp.

Where can I find the correct entry for xp for a dual boot xp/ubuntu 6.06 menu.lst?
Is it reasonable to expect that if I have a correct menu.lst the grub loading problem will be fixed?
Is there a better way to go about fixing a corrupted menu.lst?

Thanks,
Tom

---

### Post by Pumalite on 2007-10-05
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Tom1942 on 2007-10-06
My solution to this problem came from using the "Offline NT Password & Registry Editor".

I made a floppy disk according to instructions and when prompted inserted another floppy with drivers to complete the boot process.  I was given a choice to skip the requirement for a recovery console administrator passwrord.  Once that was done, I rebooted with my windows xp operating system cd and chose recovery console and successfully accessed it.  From there I ran fixmbr.

Using fixmbr this way cost me access to the linux/ubuntu partitions I had, but I had already decided to abandon ubuntu on this desktop and just use it on a laptop that i dedicated to ubuntu.

So far, I think I have solved my problem.

---

### Post by Pumalite on 2007-10-06
The original question was this:

Where can I find the correct entry for xp for a dual boot xp/ubuntu 6.06 menu.lst?
Is it reasonable to expect that if I have a correct menu.lst the grub loading problem will be fixed?
Is there a better way to go about fixing a corrupted menu.lst?

And it was answered.

---

