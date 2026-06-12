---
title: "New UEFI Laptop... 32Bit Ubuntu a must"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by LinuxFanBoi on 2013-02-20
I just brought home a new ASUS R500A (UEFI) Laptop and after much finageling to figure out how to bot from a thumbdrive and numorous failed attempts to install 12.04.2 32bit I finally got 12.04.2 64bit to successfully install.

Only one problem, I can no longer boot into my windows partition nor can I invoke the system recovery via F9 at startup.

I attempted several boot-repairs and Now I'm out of ideas..  I do have a pastebin of the last boot-repair output, I hope someone can help.  I have an RMA from ASUS in case I have to send the machine back for a full system reset, but I would like to make sure I've exhausted all options first.

Please have a look at the output from boot-repair, I hope it helps.

[http://paste.ubuntu.com/1695034/]("http://paste.ubuntu.com/1695034/")

PS there are three partitions owned by windows,  The OS partition, the recovery partition and a system image partition.  I can mount all three in linux and I can see that they are all intact as far as I can tell. I don't know if that helps at all.

---

### Post by LinuxFanBoi on 2013-02-21
Downloaded Windows 8 evaluation .iso and burned,  Turned back on secure boot and turned off all legacy support.  Booted from Windows 8 DVD, ran restore utility and reverted my system back to factory.

Kinda irritating that it's now impossible to dual boot because grub doesn't know how to handle EFI boot options for windows.  I need 12.04 32 bit for my assembly language class,  so 64bit is a no-go.  C'mon devs.  get us up and running again.

---

### Post by oldfred on 2013-02-21
I do not understand why you have to have 32 bit. Both Windows on Ubuntu are only 64 bit with UEFI.

Boot-Repair adds the correct boot stanza for efi booting. 

Know grub2 bug as it only creates BIOS chain load entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

I have never used a VM, but many suggest that if you want multiple installs. Not even sure if VM will work with UEFI?

---

### Post by LinuxFanBoi on 2013-02-22
I have to have 32bit becuse the assembly language instructions I'm using for class are 32bit OS specific.  If I install the 64 bit,  and attempt to compile and run my programs written for the 32 bit OS the univers will fold itself inside out.  Sorta like what happens when you attempt to divide by 0.

---

### Post by LinuxFanBoi on 2013-02-22
I have a brand new ASUS laptop with UEFI.  I'm taking a class in assembly language systems programming, and I absolutely MUST use a 32 bit Ubuntu.  I've encountered nothing but failure attempting to dual boot, and even installing Ubuntu as a standalone OS fails miserably.

Did I just throw away $650 on a new laptop?

---

### Post by oldos2er on 2013-02-22
As far as I know, 32-bit is not compatible with UEFI. You could always run 32-bit Ubuntu inside a virtual machine.

---

### Post by Scott Goodgame on 2013-02-22
Why not install 64 bit, then 32 bit ubuntu in a virtualbox?

---

### Post by LinuxFanBoi on 2013-02-22
> **oldos2er said:**
> As far as I know, 32-bit is not compatible with UEFI. You could always run 32-bit Ubuntu inside a virtual machine.


I tried running 12.04. 32 bit inside a VM... it installs, then gives me a warning that it's running in low graphics mode and crashes.  I'm going to try to install the 32 bit ubuntu and windows 8 both from scratch in legacy mode. if that fails I will attempt to install the 64 bit ubuntu as my dual boot and run a Vbox in ubuntu and see if I get better results.

The developers should not abandon us lowly old 32 bit users.  there are still plenty of legitimate needs for 32 bit opperating systems.

/frustrated

---

### Post by papibe on 2013-02-22
Thread merged.

---

### Post by seanreynoldscs on 2013-05-26
I have a legitimate issue with this as well.
I just bought a Dell Latitude 10 with the intended purpose of trying out ubuntu's more touch friendly features on my new atom 32bit processor.
As all dells now come with EFI instead of BIOS i'm suck until the 32bit Grub is adapted to support EFI. 

I can get the 64bit ISO on a thumbdrive to be recognized by the Dell Latitude 10 inch tablet.
But when I select it to boot, it just goes to windows. 

I cannot get the 32bit ISO to be recognized. 

I believe this is an issue with Ubuntu's lack of EFI support on their 32bit ISO.

Is there a beta version we can begin testing?

Does anyone know if you can turn off EFI on the Dell Latitude 10?

---

### Post by fantab on 2013-05-27
U[EFI] should be disabled in the BIOS, you can enter Bios-setup and search for it. 32bit don't support UEFI, at least not Ubuntu. I AFAIK even Widnows 32bit won't load with UEFI.

I don't think that 32bits will get support to boot with UEFI because 'most' of the new hardware is 64bit capable. We still have 32bit around for the older machines which most of the times do not have UEFI. 
One must be careful when one buys newer machines because some OEMs are notorious for selling equipment with weird hardware configurations.

---

