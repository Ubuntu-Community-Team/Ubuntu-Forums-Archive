---
title: "Problems booting"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by JengaBlocks on 2007-03-23
Ok I just installed Ubuntu 6.10 desktop and am getting the following errors:

ACPI: Unable to locate RSDP
ALERT! /dev/hda1 does not exist. Dropping to a shell!

No idea whats going on ... newb here. Help!

---

### Post by 1/0 on 2007-03-23
Have you tried the alternative install CD instead of the standard desktop install CD? Otherwise this could probably be avoided by turning off ACPI. This is done at boot of the install cd by issuing the noacpi command. Try that.

---

### Post by JengaBlocks on 2007-03-23
thanks for response... I am new to ubuntu and linux. 

Where do I download the Alternative CD?
How would i go about turning off acpi?

---

### Post by confused57 on 2007-03-23
> **JengaBlocks said:**
> thanks for response... I am new to ubuntu and linux. 

Where do I download the Alternative CD?
How would i go about turning off acpi?
Here's an excellent explanation of boot parameters:
[http://www.ubuntuforums.org/showpost.php?p=2279812&postcount=56](http://www.ubuntuforums.org/showpost.php?p=2279812&postcount=56)

Editing the kernel line, as mentioned by Herman, involves highlighting your Ubuntu entry at the grub menu,  pressing "e", then  just adding the parameters to the kernel line, then press "b" to boot...these changes are temporary, but you'll be able to determine if the boot parameters will work.

You might want to try:
noapic
acpi=off

If you want to download the alternate cd, there should be a fast download mirror near you, just try different ones:
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)

---

### Post by JengaBlocks on 2007-03-23
Thanks for the info. Downloading from the mirrors as I write this and will read the link you gave. Appreciate it!

---

### Post by JengaBlocks on 2007-03-23
Can I try this on the Desktop version by hitting the ESC key and "e" to put me into grub? That is, forego using the Alternative CD?

I did this and up came the following:

root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash
innitrd /boot/initrd.img-2.6.17-10-server
quiet
savedefault
boot

Where do I put in the noapci and apci=off?

I am assuming that these changes are only temporary during the boot process and that after diagnosing and getting things to work, I can go to a file to edit the changes and save it. Correct? (i.e. thats what you meant by temporary)

---

### Post by confused57 on 2007-03-23
> **JengaBlocks said:**
> Can I try this on the Desktop version by hitting the ESC key and "e" to put me into grub? That is, forego using the Alternative CD?

I did this and up came the following:

root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash 
innitrd /boot/initrd.img-2.6.17-10-server
quiet
savedefault
boot

Where do I put in the noapci and apci=off?

I am assuming that these changes are only temporary during the boot process and that after diagnosing and getting things to work, I can go to a file to edit the changes and save it. Correct? (i.e. thats what you meant by temporary)
Here's where you'd add the entries:

root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash noapic acpi=off
innitrd /boot/initrd.img-2.6.17-10-server
quiet
savedefault
boot

If it works, you can make it permanent:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```

ctrl+x,y,enter,   to save

menu.lst is short for menu.list

---

### Post by JengaBlocks on 2007-03-24
Thanks...

I tried all three combinations and it didn't work

kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash noapic     came up with ACPI: unable to locate rsdp and hung
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash acpi=off   hung with screen saying starting up...
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash noapic acpi=off  hung with screen saying starting up...


I finished burning the Alternate CD and booted it up. Right off the bat the ACPI: unable to locate rdsp message appeared and then I got kicked into the installer

---

### Post by confused57 on 2007-03-24
> **JengaBlocks said:**
> Thanks...

I tried all three combinations and it didn't work

kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash noapic     came up with ACPI: unable to locate rsdp and hung
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash acpi=off   hung with screen saying starting up...
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hda1 ro quiet splash noapic acpi=off  hung with screen saying starting up...


I finished burning the Alternate CD and booted it up. Right off the bat the ACPI: unable to locate rdsp message appeared and then I got kicked into the installer

I'm not familiar with the rdsp message, but you might try:
acpi=force

I'm not sure what difference it would make, but:
noacpi

A Google search didn't really turn up any useful info for rdsp, other than a possible hardware problem.

---

### Post by JengaBlocks on 2007-03-24
Right now the Alternative CD is installling and I can't get to the machine yet. 

What's the difference between the Alternative CD and the standard Ubuntu Desktop? What's the Alternative CD's purpose?

I just realized that the message "ACPI: unable to locate rsdp" is different than what I have been reading in the Googling efforts:
   noapic acpi=off

Notice the spelling. They are two different things.
[LIST]
[*]APIC = Advanced Programmable Interruptable Controller
[*]  ACPI = Advanced Configuration and Power Interface
[/LIST]

Will try your suggestion and fiddle with the kernel options when the system is installed. This system used to run Red Hat 7.x but hasn't been in use for over 3+ years. I don't recall any problems with APIC/RSDP issues.

Various threads here suggest its a hardware problem:
[Ubuntu thread 1]("http://ubuntuforums.org/showthread.php?t=267568")
[Ubuntu thread 2]("http://ubuntuforums.org/showthread.php?t=229207&highlight=ACPI%3A+Cannot+locate+RSDP")
[Ubuntu thread 3]("http://www.ubuntuforums.org/showthread.php?t=189190")

The error message itself seems that ACPI cannot find a RSDP (Root System Description Pointer) 
[Buggy RDSP in APCI Code]("http://www.ussg.iu.edu/hypermail/linux/kernel/0406.2/0325.html")

[Intel ACPI Specification]("http://www.ussg.iu.edu/hypermail/linux/kernel/0406.2/0325.html")
Discusses RSDP as an internal data structure in the architecture and throws exceptions. In particular AcpiFindRootPointer().
"Scans first 1 megabyte of physical memory looking for the RSDP signature"

---

### Post by JengaBlocks on 2007-03-24
Ubuntu Desktop 6.10 installation done (allternate CD)
[COLOR="Red"]The system is up and running![/COLOR] :) 

- ACPI error message still shows when booting.
- System runs slow when loading programs (probably need another 256MB stick)
- Graphic redraws appear slow
- System Monitor:
   52% memory usage
   98% free disk space

Given I know squat about Linux, this is quite cool

Now of to get the following running:
[LIST]
[*]Linksys WMP54G wireless card
[*]   Apache 1.3x installed
[*]   MySql 5.x installed
[*]   Php 4.3x installed
[/LIST]

---

