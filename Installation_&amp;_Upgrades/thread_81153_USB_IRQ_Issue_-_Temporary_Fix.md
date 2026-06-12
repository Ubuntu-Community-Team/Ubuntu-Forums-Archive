---
title: "USB IRQ Issue - Temporary Fix"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by Darkhack on 2005-10-23
For those of you who have had numerous problems with USB or IRQ issues such as Linux (all distros) not being able to see certain USB devices or not accepting IRQ addresses, then here is a temporary fix.  Boot Ubuntu with the following kernel parameters...

Boot: linux noapic pci=irqroute pci=noacpi acpi=off **irqpoll**

irqpoll is the key.  If at all possible ignore all the other parameters and try using just "irqpoll".  Odds are it will work but I included the other parameters for a "worst case senerio" type situation.

During installation of Ubuntu 5.10 (Breezy Badger) I was successfully able to boot.  This fix has ONLY been tested with certain versions of Pheonix BIOS.  If you have another BIOS this fix is still worth a try but you may need to attempt editing IRQ settings in your BIOS.  If the IRQ issues persist after these boot parameters and/or BIOS tweaking; I am sorry to say that you may be out of luck.  I have been researching this issue for a while and have finally found a fix after many months of on and off research.  

I add this topic hoping that maybe this might one day help someone who searches the forum for such a problem.  The error that appears during boot may vary but is along the lines of...

USB: device not accepting address 2.  Error -110
USB: device not accepting address 3.  Error -110
USB: device not accepting address 4.  Error -110
USB: device not accepting address 5.  Error -110
Unlink after no-IRQ? Controller is probably using the wrong IRQ

I am unaware if this will work with other distrobutions.  I know this error occurs on many (PCLinuxOS and SimplyMEPIS included) distrobutions and I believe this fix will work on most (but I am still uncertain).  

Thanks again for your time.  I hope I have assisted atleast some of you in your quest for Linux!  :D

---

### Post by wickwire on 2006-02-14
You've got my thanks right here!

kernel booting without parameters --> good wifi, problematic usb (not mounting usb storages, sluggish usb mouse)

kernel booting with noapic --> good usb ports, no wifi (error registering irq)

kernel booting with **irqpoll** --> wifi and usb!

Thank you very much!

---

### Post by theQmaster on 2006-02-14
Can one of you please explain how do I chage the boot parameters ?
What file I'd have to edit ?

Thanks,
Q

---

### Post by wickwire on 2006-02-15
sudo nano /boot/grub/menu.lst

In the active kernel you're using, find the line:

title           Ubuntu, kernel 2.6.12-10-i686
root            (hd0,0)
**kernel          /vmlinuz-2.6.12-10-i686 root=/dev/hda3 ro quiet splash vga=0x31B**
initrd          /initrd.img-2.6.12-10-i686
savedefault
boot

and then just add irqpoll at the end of it, save it and reboot.

---

### Post by theQmaster on 2006-02-15
So like this ?

title Ubuntu, kernel 2.6.12-10-i686
root (hd0,0)
kernel /vmlinuz-2.6.12-10-i686 root=/dev/hda3 ro quiet splash vga=0x31B
initrd /initrd.img-2.6.12-10-i686
savedefault
boot
acpi=off
irqpoll

---

### Post by dcstar on 2006-02-16
[QUOTE=theQmaster]So like this ?

title Ubuntu, kernel 2.6.12-10-i686
root (hd0,0)
kernel /vmlinuz-2.6.12-10-i686 root=/dev/hda3 ro quiet splash vga=0x31B
initrd /initrd.img-2.6.12-10-i686
savedefault
boot
acpi=off
irqpoll[/QUOTE]
No:

kernel /vmlinuz-2.6.12-10-i686 root=/dev/hda3 ro quiet splash vga=0x31B acpi=off irqpoll

---

### Post by theQmaster on 2006-02-16
Thanks dcstart! Now I realize why you bolded that line...

All make sense now.

---

### Post by t0mc4t on 2006-11-07
Can anybody explain why we have to put that parameter to make the USB works normally?
Thanks...

---

### Post by monocongo on 2007-02-16
I also have the same trouble with USB support as mentioned in the start of this thread.

I tried the workaround suggested and bad voodoo ensued. To wit I added "irqpoll" to the end of the kernel line in /boot/grub/menu.lst, and after rebooting I ended up getting a black screen which looked something like this:
```
BusyBox Built in shell (ash)
 /bin/sh: can't access tty; job control turned off 
(initramfs)
```

After rebooting into a previous kernel version and backing out the changes to menu.lst I am now back to where I was before.

Does the above error tell us anything, i.e. should the irqpoll option not have this effect? Does the bad result of adding the irqpoll option to the kernel line in /boot/grub/menu.lst indicate a possible source of the USB error (or maybe something worse like a system misconfiguration)?

Should I try again using the extended list of options mentioned in the original post (i.e. noapic pci=irqroute pci=noacpi acpi=off irqpoll)?


--James

---

### Post by mssever on 2007-02-16
> **monocongo said:**
> I also have the same trouble with USB support as mentioned in the start of this thread.
 
  I tried the workaround suggested and bad voodoo ensued. To wit I added "irqpoll" to the end of the kernel line in /boot/grub/menu.lst, and after rebooting I ended up getting a black screen which looked something like this:
  ```
BusyBox Built in shell (ash)
 **/bin/sh: can't access tty; job control turned off 
 *(initramfs)
```After rebooting into a previous kernel version and backing out the changes to menu.lst I am now back to where I was before.
 
  Does the above error tell us anything, i.e. should the irqpoll option not have this effect? Does the bad result of adding the irqpoll option to the kernel line in /boot/grub/menu.lst indicate a possible source of the USB error (or maybe something worse like a system misconfiguration)?
 
  Should I try again using the extended list of options mentioned in the original post (i.e. noapic pci=irqroute pci=noacpi acpi=off irqpoll)?
 
 
  --James
 It's worth a try. However, I wouldn't change your menu.lst until you've found something that works.
 
 Select the kernel you want to boot from the GRUB menu. Press *e* to edit the boot options. Then, select the line that contains the kernel boot parameters and hit *e* again. Edit the line to your satisfaction, then hit enter. When you're done, hit *b* to boot. These changes will only take effect for the current boot, so if you mess something up, a reboot will revert your changes.
 
 If/when you find something that works, edit /boot/grub/menu.list and make the changes there. In menu.list, *don't* edit the kernels directly. If you do, you'll lose your changes the next time you update the kernel. Instead, edit the commented lines between ```
### BEGIN AUTOMAGIC KERNELS LIST
```and```
## ## End Default Options ##
``` When you're finished, run ```
sudo update-grub
```

---

### Post by monocongo on 2007-02-18
Thanks *so* much for the help.  I used the approach which you explained and it turned out that I only needed the single additional kernel option irqpoll after all.  I appended this to the defoptions in menu.lst, ran update-grub, and now my USB problems are solved.  Beautiful.

--James

---

### Post by tgyorgyi on 2008-06-13
Thank you soooooo much! I was growing desparate, searching the forum up and down, and finally, this made my external HDD sing!

---

