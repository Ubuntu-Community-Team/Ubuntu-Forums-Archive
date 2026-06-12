---
title: "Toshiba UEFI boot issues Windows 8 &amp; Ubuntu"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by tchaffee on 2013-01-28
I'm trying to get Ubuntu 12.10 64 bit working alongside Windows 8 on a Toshiba P845t.  I can boot from Ubuntu on a USB stick when I change the bios to not use the UEFI mode, and Ubuntu installs fine, but then it boots Ubuntu only and will not show the grub menu. After using boot repair it boots only Windows and shows no menu at boot.  Here's the URL I get from boot repair.

[http://paste.ubuntu.com/1578237/](http://paste.ubuntu.com/1578237/)

---

### Post by oldfred on 2013-01-28
Moved to your own thread.

You always need to install Ubuntu in UEFI mode, if Windows is UEFI. You cannot dual boot a BIOS install and a UEFI install unless you go into UEFI/BIOS and change modes each time or a real hassle.

Boot-Repair converted your BIOS install to a UEFI install. You should just need to go into UEFI/BIOS from boot key not Windows and set ubuntu as default boot choice.

You also installed grub2's boot loader to the PBR of the efi boot  partition. You were in BIOS mode. In BIOS you always install grub2's  boot loader to the MBR. In UEFI it auto installs to the efi partition  but not the PBR. That may cause issues, but I do know if FAT has a  backup like NTFS does or not. If Windows boots then your grub to PBR has  not totally corrupted it like it does with a Windows NTFS partition.

---

### Post by tchaffee on 2013-02-04
I started over again and still no love. I installed Ubuntu 64bit to my USB stick and I get the UEFI grub boot menu, but when I choose Ubuntu it just hangs.  Any suggestions?

---

### Post by oldfred on 2013-02-04
It seems some Toshiba have major issues. They left signing key out in UEFI.
       Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
    
But I would think if secure boot is off, and fast boot is off. Then you should be able to boot with UEFI anyway?

Some also have video issues. What video chip do you have. Do you have Optimus?How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
 [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


       
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by tchaffee on 2013-02-04
Thanks for the quick response. I can confirm it will not boot even with secure boot and fast boot turned off.

Concerning the video chip, how can I tell which video chip I have?

---

### Post by oldfred on 2013-02-04
If you can boot liveCD/DVD/Flash we could run some commands. Otherwise it is look at vendors specs for your system. 
Not sure with Windows 8 how to see hardware details, but I am sure there is a way.

---

### Post by UltimateCat on 2013-02-04
Have you tried disabling the Secure Boot?
That helped a friend of mine that had Win's 8 and a Samsung laptop-
He told me that the EFI bootmanager which runs in the BIOS can be frobbed at runtime using EFI bootloader.

For Linux to access UEFI Runtime Services the UEFI Firmware processor architecture and the Linux Kernel must match. It is independent of the bootloader used.

Just trying to help-

I read these articles to learn more about UEFI.
[http://fedoraproject.org/wiki/Features/EFI](http://fedoraproject.org/wiki/Features/EFI)
[http://www.linuxfoundation.org/search/node/uefi](http://www.linuxfoundation.org/search/node/uefi)

---

### Post by tchaffee on 2013-02-04
I have tried disabling secure boot. Still hangs once I select any of the options from EFI grub boot menu.

---

### Post by tchaffee on 2013-02-04
oldfred: I can get a livecd to boot from usb if I switch back to CSM boot. What commands should I run?

---

### Post by oldfred on 2013-02-04
In your first post you had BootInfo. Rerun that to see if anything has changes.

But if you can get to grub menu and then it does not boot that is a video issue or other boot parameter that may be required.

To see Video:
       lspci -nnk | grep -iA3 vga 
            sudo lshw -c display
sudo lshw | grep -A 11 display
       
 #Resolution:
xwininfo -root

---

### Post by tchaffee on 2013-02-04
lspci -nnk | grep -iA3 vga:

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fb71]
    Kernel driver in use: i915
    Kernel modules: i915

sudo lshw -c display:

  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:7fc00000-7fffffff memory:90000000-9fffffff ioport:3000(size=64)

sudo lshw | grep -A 11 display:

        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:7fc00000-7fffffff memory:90000000-9fffffff ioport:3000(size=64)

xwininfo -root:

xwininfo: Window id: 0xd8 (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1366
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1366x768+0+0

---

### Post by oldfred on 2013-02-04
You have Intel in 1366x768 ?

Intel only have the open driver and it should work.

Some have to add this at grub menu, if it works we can add it permanently:

       if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot

---

### Post by tchaffee on 2013-02-04
Unfortunately neither of those did anything. Still just hangs with a blank screen.

---

### Post by oldfred on 2013-02-05
Then it may be other boot parameters or several including the above.

Without splash quiet you see the boot process, it goes by quickly but does it say something is not working. Last entry iis not usually the issue.

        Some Asus need this boot parameter, but it seems it is more UEFI vendor (only 4 or hardware like Intel related)

pci=nomsi
            vt.handoff=7 rootdelay=90 reboot=a,w

---

### Post by tchaffee on 2013-02-05
The strange thing is that even without "splash" and without "quiet" I see absolutely nothing. It immediately hangs.

I've tried the extra params you suggested above, both alone and in combo with both variations of i915.modeset and still no luck.

---

### Post by oldfred on 2013-02-05
So you get no command lines posted at all?

We have had issues with BIOS installs and large / (root) partitions. I do not think I have seen it with any of the UEFI installs, but they may not have had large / partitions. You might try a smaller root. As a test, just use gparted to shrink your sda8 to less than 100GB. You can use the rest for /home or data if it works.

---

