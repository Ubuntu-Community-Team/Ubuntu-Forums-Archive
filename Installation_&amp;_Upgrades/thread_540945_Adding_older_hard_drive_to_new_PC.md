---
title: "Adding older hard drive to new PC"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-09-02
I've just inherited a white box PC with Celeron 2.6 ghz and 512 RAM. Has a 40 gb hd with Ubuntu 7.04 installed on it. I want to take my 40 gb hd with PCLOS2007 on it from another PC and add it to this newer one.

How do I add the GRUB to show both at boot up?

How do I get MBR to be in the correct place?

Problem Solved. How you do add that to the first title post?

---

### Post by Pumalite on 2007-09-02
Did you connect it?. Can you still boot Ubuntu?.

---

### Post by geovino on 2007-09-02
Yes... I can click Places > Computer and it reads the files from the PCLOS hdd.

Here's the menu.lst from the GRUB in PCLOS:

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,0)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdb1  acpi=on resume=/dev/hdb5 splash=silent vga=788
initrd (hd1,0)/boot/initrd.img

title linux-nonfb
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hdb1  acpi=on resume=/dev/hdb5
initrd (hd1,0)/boot/initrd.img

title failsafe
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdb1  failsafe acpi=on resume=/dev/hdb5
initrd (hd1,0)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title linux-ubuntu
kernel (hd0,1)/dev/hda2 BOOT_IMAGE=linux-ubuntu root=/dev/hda2 
initrd (hd0,1)/boot/initrd.img

title      Ubuntu, kernel 2.6.20-15-generic
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.20-15-generic root=UUID=78fa238b-c3ae-4485-87ce-e97adf596f35 ro quiet splash
initrd      /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Should I copy part of it and paste in the Ubuntu menu.lst?

---

### Post by confused57 on 2007-09-02
What I would try is to add a configfile entry to your Ubuntu menu.lst:
```
title  PCLinux
configfile (hd1,1)/boot/grub/menu.lst
```

Then you might want to check the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Feisty may recognize your hard drive as /dev/sdb, instead of /dev/hdb...if this is the case you would need to change the kernel line to reflect this...When you select PCLinuxOS from grub when you boot your pc, the next screen "should" be your PCLinux grub menu, highlight your latest entry, press "e", then highlight your kernel line, press "e" again, change hdb1 & hdb5 to sdb1 & sdb5, press "enter", then "b" to boot.   If your PCLinuxOS is recognized as /dev/hdb in Feisty, then you shouldn't need to make any other modifications...most of your problems would be hardware differences between the 2 pc's.

---

### Post by geovino on 2007-09-02
What's the command to save changes in the menu.lst?

Here's what comes up when I do $ sudo fdisk -l :

davek@davek-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4684    37624198+  83  Linux
/dev/sda2            4685        4865     1453882+   5  Extended
/dev/sda5            4685        4865     1453851   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4795    38515806   83  Linux
/dev/sdb2            4796        5005     1686825    5  Extended
/dev/sdb5            4796        5005     1686793+  82  Linux swap / Solaris
davek@davek-desktop:~$ 
davek@davek-desktop:~$ 


So the PCLOS hdd is sdb1

---

### Post by Pumalite on 2007-09-02
First backup:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
Then:
gksudo gedit /boot/grub/menu.lst
Change what you have to change, save and exit. Reboot.

---

### Post by geovino on 2007-09-02
Thanks, but that didn't do it.

Here's the menu.lst now:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title  PCLinux
configfile (hd1,1)/boot/grub/menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

Do I have to save it as sd1,1 instead of hd1,1 ? or maybe the whole entry is wrong.

---

### Post by confused57 on 2007-09-02
The entry "should" work, based on the info from this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You might want to go into your bios setup and make sure your hard drive controller is "enabled" or set to "auto" for your 2nd drive.

Correction:  Based on the output of "fdisk -l", your entry should probably be:

```
title PCLinuxOS
configfile (hd1,0)/boot/grub/menu.lst
```

Added:  You also shouldn't need to change your kernel entries in your PCLinusOS from hdb to sdb, since the entries here are how PCLinuxOS recognizes your hard drives...sorry, my mistake, leave them as /dev/hdb1 & /dev/hdb5.

---

### Post by geovino on 2007-09-02
I checked the BIOS. I think it's OK. the entry still doesn't work. Maybe it has to be something else. 
Any other options?

---

### Post by confused57 on 2007-09-02
> **geovino said:**
> I checked the BIOS. I think it's OK. the entry still doesn't work. Maybe it has to be something else. 
Any other options?
Did you try the configfile entry with (hd1,0)?  Are you getting any errors when you try to boot with the configfile entry...I edited my last reply for the corrections you'll need to make.

---

### Post by geovino on 2007-09-02
Yes I did...  and no error messages, it just boots into Ubuntu with no boot menu at all. 

I just ran the PCLOS live CD and went into their Control Center > Boot section and it read both drives and said there is no bootloader. That means that when I installed Ubuntu on the 40gb hdd before adding the second hdd, Ubuntu didn't create a bootloader because it wasn't needed at the time. Now I will try to find out what entries are needed for both Ubuntu and PCLOS and add them to the boot loader in PCLOS. 

Or, I could install the Ubuntu live CD and go to install and add the bootloader from there. Is that possible?

Any ideas for what the boot loader entries should be?

Thanks

---

### Post by confused57 on 2007-09-02
> **geovino said:**
> Yes I did...  and no error messages, it just boots into Ubuntu with no boot menu at all. 

I just ran the PCLOS live CD and went into their Control Center > Boot section and it read both drives and said there is no bootloader. That means that when I installed Ubuntu on the 40gb hdd before adding the second hdd, Ubuntu didn't create a bootloader because it wasn't needed at the time. Now I will try to find out what entries are needed for both Ubuntu and PCLOS and add them to the boot loader in PCLOS. 

Or, I could reinstall both Ubuntu and PCLOS on the two drives and start all over, but I'd rather not do that.

Any ideas for what the boot loader entries should be?

Thanks
I'm not sure what's going on...I know you've already posted your Ubuntu menu.lst, but if you would, please boot into Ubuntu & post your current boot entries, open a terminal(Applications---Accessories---Terminal), post the output of:
```
gedit /boot/grub/menu.lst
```

Added:  Might be quicker just to reinstall PCLinuxOS...you shouldn't need to reinstall Ubuntu.  If you need to get some files off of your current PCLinux install, just mount the root partition, then copy & paste to Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by geovino on 2007-09-02
Here it is...


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4613ab1a-738d-4025-8aa2-c615bdfa0824 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title  PCLinuxOS
configfile (hd1,0)/boot/grub/menu.lst

---

### Post by confused57 on 2007-09-03
If I understand correctly, when you boot your pc it boots to your Ubuntu grub boot menu...when you choose to boot Ubuntu on (hd0,0), you have no problem booting into Ubuntu.  When you select to boot PCLinuxOS on (hd1,0) with the configfile entry, it also boots directly into Ubuntu on (hd0,0)?

I really don't see why this is happening, and I would definitely suggest reinstalling PCLinux on your 2nd hard drive.

Here's an excellent guide on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by geovino on 2007-09-03
Because I installed Ubuntu one one hdd, it never created a bootloader. So when I installed the PCLOS hdd two days later, Ubuntu could see the drive and the files but there's no boot loader. I could reinstall PCLOS, or could I install the Ubuntu live cd and go into install and create a bootloader that way?

---

### Post by confused57 on 2007-09-03
> **geovino said:**
> Because I installed Ubuntu one one hdd, it never created a bootloader. So when I installed the PCLOS hdd two days later, Ubuntu could see the drive and the files but there's no boot loader. I could reinstall PCLOS, or could I install the Ubuntu live cd and go into install and create a bootloader that way?

Let's try this...boot into Ubuntu, open a terminal & open your /boot/grub/menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Find the line with:
```
hiddenmenu
```
place a # in front:
```
#hiddenmenu
```

Change your line with:
```
timeout  3
```
change it to:
```
timeout 10
```

quit & save

Then reboot your computer, select PCLinuxOS & see if it will boot.

---

### Post by geovino on 2007-09-04
Thanks for the info, but I ended up reinstalling PCLOS and after the install, I copied the fist entry off the Ubuntu menu.lst then added it to the PCLOS menu.lst. That added the Ubuntu entry to the PCLOS boot loader. :)  [Solved]

---

