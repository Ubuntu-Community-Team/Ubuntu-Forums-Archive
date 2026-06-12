---
title: "IDE problems when nstalling Gutsy on Advance 10B/10F mobo with VIA chipset"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by bobg-m on 2007-10-21
Hi, I'm having problems installing the final release of gutsy on aPC with VIA IDE chipset. To start with, the live cd will only boot with 'all_generic_ide' added to the boot parameters (F6 from the menu), as without it I get udevd_event[2086]: run_program: '/sbin/modprobe' abnormal exit and thowing me back to the ash shell prompt.

OK, so there is something funny with the IDE chipset. But the install appears to work correctly once the live cd is booted. But booting the installed system fails with being unable to find the IDE hard drive. This happens in the boot process just after the USB stuff, with the error

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/<magic number> does not exist

And I end up back in the initramfs ash shell. The install does not make and of /dev/sda, sda1,sda5 (which is swap) or /dev/disk/by-uuid/<anything>. In fact it doesn't even make /dev/disk directory.

I've tried making the /dev/sda, sda1 and sda5 devices by mounting the root partition from the live cd on mnt, and in /mnt/dev doing mknod sda b 8 0 and sda1 b 8 1 and sda5 b 8 5 and creating the appropriate soft links from (/mnt)/dev/disk/by-uuid back up to the sda devices.

Nothing appears to work, the boot process fails unable to find the disks, even if pointed directly at /dev/sda1 etc.

/proc/modules gives
ide_cd, ide_disk, via_rhine, via82cxxx, ide_core, ata_generic, libata amongst others. No sign of all_generic_ide.

lspci -vv gives 

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        Region 4: I/O ports at a000 [size=16]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

for the IDE controller.

How can I get this system to successfully install and boot?
Would getting all_generic_ide included in the GRUB lines help, if so how would I do that?

Other than that, Gutsy looks great :)

---

### Post by Bo Rosén on 2007-10-21
I am not sure if this will work or if it is a good idea. If you don't know what you're doing you may not want to try.

After installing 7.10, boot again with the live-cd. Open Nautilus and go to the disk where you installed grub, probably hda1. Go into the /boot/grub directory and open menu.lst with the text editor and add all_generic_ide to each kernel line you want it for. Save and exit. Reboot.

---

### Post by bobg-m on 2007-10-21
Sounds great - exactly where on the line, could you give an example?

---

### Post by Bo Rosén on 2007-10-21
This is from my Feisty installation with the option added, I'm too chicken to try my own tips :-)

```

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=897fff8b-5c15-4a96-9113-f84c242df38e ro quiet splash [COLOR=Red]all_generic_ide[/COLOR]
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```Note that you can add options manually to the boot process even if you start from a hard drive (and not from cd) so maybe you should try that first.  I forget how to do it, but a search here should hopefully help.

---

### Post by Bo Rosén on 2007-10-21
Found it. 
When you boot from a hard drive you can hit ESC if you're quick enough, early in the boot process (when grub starts). This will give you a menu of the installed kernels and the option of editing the boot options. The changes are not permanent.

If that works, you can just go to /boot/grub and add the changes that solved the problem to menu.lst. No need for the live-cd then.

---

