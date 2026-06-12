---
title: "Removing Grub from one drive / virtualization"
date: 2016-03-14
forum: Installation &amp; Upgrades
---

### Post by bozo_the_grey on 2016-03-14
Hello,

I have 3 drives in my machine:
sda is dedicated to Ubuntu (and the priority boot drive)
sdb is a shared drive with mainly media and docs
sdc is a Win10 dedicated drive

I am trying to run a Win10 virtual machine from Ubuntu, the machine will be booting from the sdc drive
I want to have the option to boot into Win10 from grub too (that is working as of now)

I think I have done everything fine on the virtualbox side. However, when I start the machine, I got a grub error: "no such device: 6db9766c-d7af-4f82-8350-3a93c9cfb8f5" (ie the linux drive)

That looked strange to me, as I didn't expect Grub to be installed on the sdc disk.
Boot-repair log seems to confirm that Grub is installed a bit everywhere, in sdc too. [boot repair log]("http://paste.ubuntu.com/15384315/")

```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6db9766c-d7af-4f82-8350-3a93c9cfb8f5 root hd0,gpt3 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------

```

(my Linux installation was a bit troublesome, with multiple boot-repair fixes - the multiple instances of Grub might be a consequence of that ?)



I was thinking of removing Grub from dev/sdc.
Is that safe ? Safer to keep a copy ? Is there a recommended page with instructions (I can see many threads on the forums ) ?
I assume I should replace it with Windows MBR. Correct me if I am wrong but, as long as the sdc drive is not the first to boot, this shouldn't constitute a problem (i.e. spoil my normal grub startup process).

Or maybe I could consider editing grub in dev/sdc and make it point to the Windows partition only, removing references to Ubuntu.


Thanks,

Bozo

---

### Post by bozo_the_grey on 2016-03-15
I ran boosect on my windows drive from a Windows Repair key ( /dev/sdc )
Now Windows 7/8/2012 is installed in the MBR of /dev/sdc.
If, from motherboard BIOS, I give boot priority to this disk, Windows doesn't start, no OS is found ! :confused:
However if I boot from the Linux disk, GRUB2 is loaded and I can start either linux or windows.

If I run Virtualmachine from Linux I get the same error message as when I boot from Window disk: 
```
An operating system wasn't found. Try disconnecting any drives that don't contain an operating system.
```


[http://paste.ubuntu.com/15391503/](http://paste.ubuntu.com/15391503/)
```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6db9766c-d7af-4f82-8350-3a93c9cfb8f5 root hd0,gpt3 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.
```

---

### Post by 1clue on 2016-03-15
Does your motherboard and cpu support vt-d and is it turned on? If so you should be able to donate sdc to the vm.

---

### Post by bozo_the_grey on 2016-03-15
motherboard is GA-Z170MX-Gaming 5 (I don't see vt-d in the specs)
[http://www.gigabyte.com/products/product-page.aspx?pid=5530#sp](http://www.gigabyte.com/products/product-page.aspx?pid=5530#sp)
Cpu is Intel Core i5 Skylake

How does the donation work ?

---

### Post by 1clue on 2016-03-15
Assuming that both processor and motherboard support vt-x (virtualization support) and vt-d (virtualization of peripherals) then you would tell your VM hosting software (VirtualBox, qemu, etc) to donate the device directly.

What this means is that your host software does not even need a driver. The host is configured to ignore the entire drive, and the PCI device is passed through as raw hardware.  The guest needs to have the correct driver to manage the device, there is no help from nor interference from the host.

This also works with network cards or any other pci device.

I don't see any mention of virtualization in your motherboard's spec sheet, but your CPU probably has it.

---

### Post by bozo_the_grey on 2016-03-15
What I was originally trying to do was getting to a configuration where I can:
a. boot into windows and linux from GRUB2
b. boot into linux, lanuch VM on the rawdrive where Win10 is running

Basically one Win10 drive that can be accessed "normally" and virtually.
(on the rawdrive [https://www.virtualbox.org/manual/ch09.html](https://www.virtualbox.org/manual/ch09.html))

My problem with b. is that my windows MBR and Boot Configuration Data BCD seems to be corrupted and I cannot manage to repair it with a Repair disk.
I assume that is because of this (seems reasonable afterall), my virtual machine will not boot into windows (as I cannot boot into windows without GRUB)

(how difficult it was to create a Repair Disk ... a struggle
 I attempted something along these lines: [http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows](http://www.thewindowsclub.com/repair-master-boot-record-mbr-windows) ... it didn't work
I will try [http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm](http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm) too )

However the good news is that the OS partition is not corrupted and GRUB2 can start Windows.

I could give up on b and live with my current configuration a.

What you are suggesting seems to be:
- wipe your windows installation from drive sdc
- dedicate sdc to virtualization through vt-d/vt-c

Do I understand correctly ?

---

### Post by bozo_the_grey on 2016-03-15
In the meantime, Windows startup repair has removed GRUB
[http://paste.ubuntu.com/15392653/](http://paste.ubuntu.com/15392653/)

Through Live USB and Boot Repair, I got here
[url]http://paste.ubuntu.com/15392785/[url]

I feel I am playing with fire ...

---

### Post by bozo_the_grey on 2016-03-15
and now Boot Repair, advanced options, fixed everything, even windows MBR. Magic.
Now my virtual machine can start from the raw windows drive.

Current setup:
Ubuntu 14.04 on 120GB SSD [sda]
Windows 10 on 250GB [sdc]
A hard drive shared between the two [sdb]
Forget sdd, is the USB key

I don't know what is this SysLinux MBR, but it is installed on the sdc disk and seems to be crucial.
If I understand correctly, GRUB is installed on the Linux drive only.



[http://paste.ubuntu.com/15392785/]("http://paste.ubuntu.com/15392785/")


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6db9766c-d7af-4f82-8350-3a93c9cfb8f5 root hd0,gpt3 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

---

### Post by 1clue on 2016-03-15
Good to see you got it going.

I'm not much help with dual booting. I haven't done it since about 1999 or so. Even if I remembered how it worked, it wouldn't work the same way now.

---

