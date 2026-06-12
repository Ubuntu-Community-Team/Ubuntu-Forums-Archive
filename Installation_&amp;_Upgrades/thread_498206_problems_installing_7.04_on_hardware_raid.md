---
title: "problems installing 7.04 on hardware raid"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by nieradka on 2007-07-11
First off, im a complete newbie, this is my first attempted linux install, so please excuse my ignorance.

The problem i am having is i cant create a partition to install to on any of my raid arrays. When the installer gets to the "prepare disk space" screen i choose guided use entire disk /dev/i20/hda it goes through a few screens then generates "the creation of swap space in partition #5 of /dev/i2o/hda failed. Doing it manually in the menu doesnt work. using the text based installer generates the same error in a different wording. Using gparted when i try to set the disk label it gives an error: "error while setting disklabel" using parted from the command line:

> ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# parted
Warning: Unable to open /dev/hda read-write (Read-only file system).  /dev/hda
has been opened read-only.
GNU Parted 1.7.1
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel                                                          
New disk label type? msdos                                                
Error: Can't write to /dev/hda, because it is opened read-only.           
Ignore/Cancel? ignore                                                     
*** stack smashing detected ***: <unknown> terminated
Aborted (core dumped)


All the utilities see the correct sizes of the 3 arrays. 

The controller is a promise supertrak 100 bios 1.00 build 13 (intel i960 chip). In its bios i set it to mode:Linux and deleted the previous arrays (and nuked windows) and defined new ones on two of the arrays, so they are unpartioned. (the other array is an ntfs partion which my data  is backed up on. 

Ive tried:
Disabling acpi in the system bios.
Turning off pnp os installed in the bios, and disabling a serial and a parallel port and the on board usb, removing the sound card. Shuffled the pci cards to diffrent slots. (this got the installer to see my network card and detect that there were arrays on the card at least)
Disabled apic live=no-apic noapic nolapic at the boot menu of the cd.

i tried searching google and the install guide while i found plenty about installing on fake raid, i didnt see much about hardware raid from the last 5 years, prolly i dont know what to search for.

Doesnt look like a irq problem 
> root@ubuntu:~# more /proc/interrupts
           CPU0       CPU1       
  0:     544148          0    XT-PIC-XT        timer
  1:       6293          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  6:         15          0    XT-PIC-XT        floppy
  8:          4          0    XT-PIC-XT        rtc
 10:     190610          0    XT-PIC-XT        uhci_hcd:usb1, ohci1394, radeon@p
ci:0000:00:10.0
 11:        857          0    XT-PIC-XT        uhci_hcd:usb2, ehci_hcd:usb3, iop
0
 14:       9417          0    XT-PIC-XT        ide0
 15:       4010          0    XT-PIC-XT        eth0
NMI:          0          0 
LOC:     543871     543878 
ERR:          0
MIS:          0
root@ubuntu:~# 


Installing on a non raided drive off on the onboard ide works, but thats kind of not the point. 

Any suggestions would be appriciated.

---

### Post by NeoMatrixJR on 2007-08-02
Looks like you're having the same issues I am with the SuperTrak66.  Although from your output it looks like you're confusing /dev/i2o/hda with /dev/hda.  These are two different things.  I'm sorry I won't be much more help.  I can't get mine working either.  I don't think Ubuntu is properly set up to handle these cards :( .

---

### Post by dave_abrahams on 2008-05-11
I have the same problem when trying to use an ipod nano as an external disk, FWIW.

(parted) mklabel msdos                                                    
*** stack smashing detected ***: <unknown> terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e83138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7e830f0]
/lib/libparted-1.7.so.1[0xb7f9e614]
/lib/libparted-1.7.so.1[0xb7f8dc18]
[0x0]
======= Memory map: ========
08048000-08056000 r-xp 00000000 fe:02 34665      /sbin/parted
08056000-08057000 rw-p 0000e000 fe:02 34665      /sbin/parted
08057000-08078000 rw-p 08057000 00:00 0          [heap]
b7c54000-b7c5e000 r-xp 00000000 fe:02 114793     /lib/libgcc_s.so.1
b7c5e000-b7c5f000 rw-p 0000a000 fe:02 114793     /lib/libgcc_s.so.1
b7c6e000-b7c6f000 rw-p b7c6e000 00:00 0 
b7c6f000-b7cae000 r--p 00000000 fe:02 254017     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7cae000-b7caf000 r--p 00000000 fe:02 254018     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7caf000-b7cb0000 r--p 00000000 fe:02 254019     /usr/lib/locale/en_US.utf8/LC_TIME
b7cb0000-b7d91000 r--p 00000000 fe:02 254020     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7d91000-b7d92000 rw-p b7d91000 00:00 0 
b7d92000-b7d95000 r-xp 00000000 fe:02 114756     /lib/libuuid.so.1.2
b7d95000-b7d96000 rw-p 00002000 fe:02 114756     /lib/libuuid.so.1.2
b7d96000-b7edf000 r-xp 00000000 fe:02 180282     /lib/tls/i686/cmov/libc-2.7.so
b7edf000-b7ee0000 r--p 00149000 fe:02 180282     /lib/tls/i686/cmov/libc-2.7.so
b7ee0000-b7ee2000 rw-p 0014a000 fe:02 180282     /lib/tls/i686/cmov/libc-2.7.so
b7ee2000-b7ee5000 rw-p b7ee2000 00:00 0 
b7ee5000-b7f12000 r-xp 00000000 fe:02 127020     /lib/libncurses.so.5.6
b7f12000-b7f15000 rw-p 0002c000 fe:02 127020     /lib/libncurses.so.5.6
b7f15000-b7f17000 r-xp 00000000 fe:02 180285     /lib/tls/i686/cmov/libdl-2.7.so
b7f17000-b7f19000 rw-p 00001000 fe:02 180285     /lib/tls/i686/cmov/libdl-2.7.so
b7f19000-b7f1a000 rw-p b7f19000 00:00 0 
b7f1a000-b7f46000 r-xp 00000000 fe:02 204821     /lib/libreadline.so.5.2
b7f46000-b7f4a000 rw-p 0002c000 fe:02 204821     /lib/libreadline.so.5.2
b7f4a000-b7f4b000 rw-p b7f4a000 00:00 0 
b7f4b000-b7fa9000 r-xp 00000000 fe:02 34455      /lib/libparted-1.7.so.1.0.0
b7fa9000-b7fab000 rw-p 0005d000 fe:02 34455      /lib/libparted-1.7.so.1.0.0
b7fab000-b7fac000 rw-p b7fab000 00:00 0 
b7fac000-b7fad000 r--p 00000000 fe:02 254021     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fad000-b7fae000 r--p 00000000 fe:02 253957     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fae000-b7faf000 r--p 00000000 fe:02 254022     /usr/lib/locale/en_US.utf8/LC_PAPER
b7faf000-b7fb0000 r--p 00000000 fe:02 254023     /usr/lib/locale/en_US.utf8/LC_NAME
b7fb0000-b7fb1000 r--p 00000000 fe:02 254024     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fb1000-b7fb2000 r--p 00000000 fe:02 254025     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fb2000-b7fb3000 r--p 00000000 fe:02 254026     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fb3000-b7fba000 r--s 00000000 fe:02 24623      /usr/lib/gconv/gconv-modules.cache
b7fba000-b7fbb000 r--p 00000000 fe:02 254027     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION

---

