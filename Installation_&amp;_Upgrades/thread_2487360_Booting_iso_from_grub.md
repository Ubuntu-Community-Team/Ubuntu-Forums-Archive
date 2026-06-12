---
title: "Booting iso from grub"
date: 2023-06-01
forum: Installation &amp; Upgrades
---

### Post by Impavidus on 2023-06-01
I'm trying to upgrade the Xubuntu system on an old computer, currently running Xubuntu 18.04 32 bit. It can't boot from usb and recent Ubuntu versions don't like booting from dvd, so I try to use this guide &#8594; [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) to boot the Xubuntu 22.04.2 iso from grub. The plan is to install it over the existing Xubuntu system without formatting, to keep existing applications and data. There's no separate /home partition. I checked the sha256 sum of the iso; it's correct. The /etc/grub.d/40_custom file looks like this:```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Xubuntu 22.04.2 ISO" {
    set isofile="/home/egroot/xubuntu-22.04.2-desktop-amd64.iso"
    loopback loop (hd0,3)$isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/casper/initrd
}

```After running update-grub, the entry for Xubuntu 22.04.2 ISO appears in grub. However, when I attempt to boot, it gives me a kernel panic after a few seconds, complaining it can't find init. Any suggestions? Any other issues I'm likely to encounter?

Edit: Some more info on the hardware:```

  *-core
       description: Moederbord
       product: MS-6702E
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080011
          date: 07/28/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.0
          serial: To Be Filled By O.E.M.
          slot: Socket 939
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good cpuid pni lahf_lm 3dnowprefetch vmmcall
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System memory
          physical id: 1
          size: 1013MiB

```Yes, it's ancient, but my dad wants to keep it running as long as possible and it's still fine for reading email or doing spreadsheet stuff.

---

### Post by yancek on 2023-06-01
Your menuentry looks correct to me if you have the correct location of the iso file and the correct drive/partiiton numbers.  I posted a different menuentry for Xubuntu 22.04 which worked for me, might try that.  It would be best to have the iso on a different partition than the one you wish to update/install to.   

>  menuentry "Try or Install Xubuntu" {
    loopback loop (hd0,gpt3)/xubuntu-22.04-desktop-amd64.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/xubuntu-22.04-desktop-amd64.iso quiet splash --
    initrd (loop)/casper/initrd
}

I have a menuentry that booted an iso with the isofile option and it has curly brackets around isofile on the Linux line.  Not sure that will help but easy enough to try.

> iso-scan/filename=${isofile} quiet splash 

---

### Post by MAFoElffen on 2023-06-01
+1 --

RE: [https://askubuntu.com/questions/500295/booting-ubuntu-iso-file-from-grub-menu](https://askubuntu.com/questions/500295/booting-ubuntu-iso-file-from-grub-menu)

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Xubuntu 22.04.2 ISO" {
    set isofile="/home/egroot/xubuntu-22.04.2-desktop-amd64.iso"
    loopback loop (hd0,3)$isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} noprompt noeject
    initrd (loop)/casper/initrd
}

```

---

### Post by Impavidus on 2023-06-01
The other partitions on the hard drive are all ntfs partitions. I think I can clear one of them and format it as ext4. I'll try after lunch.

---

### Post by MAFoElffen on 2023-06-01
??? That seems to be a change in direction with some missing context. LOL

You know that you can boot an ISO file stored on another filesystem other than ext4 if you give it the pointers to the driver for that filesystem right? (So change also be on an NTFS filesystem.) Grub can read other filesystems...

Albiet, I used to create a recovery partition on my old PC, that just just had ISO files in it, that I added to my Grub2 menu.

---

### Post by sudodus on 2023-06-01
It should work well from an ex4 partition according to this link:

[help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

You can scroll down to 'Menuentry Example'.

Please notice that you need a modified 'linux' line for the Ubuntu 23.04 iso file, but if I understand correctly the old version should work well for the 23.04 flavours.

When you use the boot option 'toram', you can unmount all partitions on the source drive when it is also target drive, so you can overwrite what is there, but please remember that once overwritten you can no longer use this method to boot and install unless you move the drive to another computer and make it bootable again.

---

### Post by Impavidus on 2023-06-01
> **MAFoElffen said:**
> 
You know that you can boot an ISO file stored on another filesystem other than ext4 if you give it the pointers to the driver for that filesystem right?
Thanks for reminding me. Still no success though. It does load the kernel of the live system stored the ntfs partition, but still complains that it cannot find init. I'll do some experiments on my laptop.

---

### Post by C.S.Cameron on 2023-06-04
Sudodus showed me that an ISO stored on NTFS is hard to shut down once booted using GRUB.

---

### Post by ajohnl on 2023-06-04
Just a question as I have a laptop with built in dvd and some dvd's. I assume Ubuntu wont boot and install from the bios's dvd boot entry?

---

### Post by Impavidus on 2023-06-08
My laptop boots fine using the above 40_custom with the same Xubuntu iso. I also tried burning it to dvd. The sha256 sum shows errors on the dvd, so I won't try to install it, but at least my laptop boots fine from the dvd (a bit slow). The old desktop still gives the same error: can't find init. I suspect the old hardware just doesn't like the iso. Maybe I should try Debian?

---

### Post by Impavidus on 2023-06-08
> **ajohnl said:**
> Just a question as I have a laptop with built in dvd and some dvd's. I assume Ubuntu wont boot and install from the bios's dvd boot entry?

It should boot, slowly. Expect to watch a black screen for several minutes.

---

### Post by oldfred on 2023-06-08
Ubuntu now is too large for DVD. And is intended for newer systems which now rarely have DVDs.

Flavors are usually smaller.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by sudodus on 2023-06-08
> **Impavidus said:**
> My laptop boots fine using the above 40_custom with the same Xubuntu iso. I also tried burning it to dvd. The sha256 sum shows errors on the dvd, so I won't try to install it, but at least my laptop boots fine from the dvd (a bit slow). The old desktop still gives the same error: can't find init. I suspect the old hardware just doesn't like the iso. Maybe I should try Debian?

> **oldfred said:**
> Ubuntu now is too large for DVD. And is intended for newer systems which now rarely have DVDs.

Flavors are usually smaller.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

@Impavidus,

0. What computer is it (brand name and model of the computer or motherboard)?

1. Did you try booting from a [Plop](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB#PLoP_Boot_Manager) CD or DVD disk? That way it should be possible to boot from the optical device and then continue booting from a USB drive because Plop provides drivers that help the computer 'see' the USB drive and chainload from it.

2. Did you try to boot from the internal drive into an iso file with some other system (for example older Xubuntu version or Debian or Puppy Linux)

---

### Post by MAFoElffen on 2023-06-09
> **sudodus said:**
> 1. Did you try booting from a [Plop]("https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB#PLoP_Boot_Manager") CD or DVD disk? That way it should be possible to boot from the optical device and then continue booting from a USB drive because Plop provides drivers that help the computer 'see' the USB drive and chainload from it.
Oh man! Did that bring back memories!!!

I had an early AMD64 with a CD drive, and did it this way to boot from USB. I can confirm. It does work, boots that way. LOL. Thinking back that I thought those times were normal business as usual.

---

### Post by Impavidus on 2023-06-11
The motherboard is an MSI MS-6702E. CPU is AMD Athlon 64 3000+. It's about 18 years old. RAM isn't maxed out yet. Could this result from lack of memory? Question is, is this machine still worth getting some old, second hand memory to max it out at 4GiB? It's not for me to decide that, but it would be nice to know whether that's likely to give a working system.

The CPU is 64 bit, fortunately, but I remember how a few years ago Firefox suddenly stopped working on some old CPUs that didn't support sse2. Something similar could happen any day on this CPU. I want either a supported Linux desktop on this box, or prove that it cannot be done.

I'll try the other suggestions later. I've several old xubuntu isos on my HD.

---

### Post by sudodus on 2023-06-11
It is possible that 1 GiB RAM is small for 22.04 LTS, at least for the installer to work, but you might succeed better if you extract and clone Ubuntu Server directly to the internal drive according to [this link](https://ubuntuforums.org/showthread.php?t=2474692) (read the whole thread before tampering with it).

Then you will see if and how it works to update & upgrade the system and in the next step you can install a desktop environment (for example xubuntu-desktop or lubuntu-desktop) or maybe a simpler window manager and a few GUI programs for example according to [this link](https://askubuntu.com/questions/886313/what-is-the-simplest-way-to-have-remote-gui-access-to-ubuntu-16-04-server-from/886398#886398).

[hr][/hr]
If the suggestions above are too much for the old beast, I would suggest that you try Puppy Linux, maybe Bionic Pup would be a good alternative. It works well for me in an old IBM Thinkpad T42 as well as in an eeePC 900. I have not tried any newer version of Puppy, maybe there is a Focal Pup and/or a Jammy Pup now.

Edit: I found **FossaPup64 9.5** at [https://puppylinux-woof-ce.github.io/](https://puppylinux-woof-ce.github.io/)

---

### Post by MAFoElffen on 2023-06-13
Or maybe Lubuntu LTS 22.04.2?
```

lubuntu@lubuntu:~$ cat /proc/cpuinfo | grep 'model name' | head -n 1
model name      : AMD Opteron 240 (Gen 1 Class Opteron)
lubuntu@lubuntu:~$ free
               total        used        free      shared  buff/cache   available
Mem:          991936      280412       67232       12528      644292      558408
Swap:         495964      221440      274524
lubuntu@lubuntu:~$ lsb_release -a | grep 'Desc'
No LSB modules are available.
Description:    Ubuntu 22.04.2 LTS
lubuntu@lubuntu:~$ uname -r
5.19.0-32-generic

```
I just spun up a KVM VM with an emulated AMD Opteron Gen1 vCPU with 1GB RAM. Booted Lubuntu great. Was responsive and snappy. Just saying, maybe a good option.

---

### Post by Impavidus on 2023-06-15
I can boot the Xubuntu 20.04 live iso from grub. It's end-of-life, but at least the parts in common with Ubuntu are still supported, which includes most web-facing parts, so that's at least better than what's now on the machine (although, is the Firefox deb on 20.04 still supported? Ubuntu had switched to a snap in 20.04). I'll give Lubuntu 22.04 a try.

---

### Post by Impavidus on 2023-06-27
> **C.S.Cameron said:**
> Sudodus showed me that an ISO stored on NTFS is hard to shut down once booted using GRUB.

I can confirm that: after reaching target "Shutdown" or "Reboot" it just enters a loop printing some messages. Not too much of a problem. All filesystems were cleanly unmounted already and this box has a nice reset button.

Anyway, I have now installed Lubuntu 22.04.2 LTS. It appears to run fine; I just have to restore some backups. I decided to do a clean install after all.

Marking this thread as solved.

---

