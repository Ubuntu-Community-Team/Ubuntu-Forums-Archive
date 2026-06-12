---
title: "Linux + AM2 motherboard.. just keeps getting worse for me."
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by SimonTheMime on 2007-02-04
I really shouldn't have upgraded up still from AM2 and gone for something with Intel C2D.. :\..

So I've been having problems with Linux and AM2 mobos before. I've had to install by adding noapic to the line before booting from DesktopCD (otherwise it'll tell me to disable apic and won't go through further). Each time then installer would go through with some trouble.. but eventually went through. Then about two weeks after my installation would go haywire. 

I've replaced my motherboard about three times now, each time assuming a different problem. I've replaced my hard drive and my PSU since then (not just for this but because I needed new ones anyway). BY the way I'm using an x86 installer.

Now I've bought AMD Athlon X2 64 5200+, and M2N4-SLI mobo. 

First time it booted from disc, it went through and told me to disable apic before I started. Restarted.

Second time booting from disc, added noapic to line, status bar went all the way through, but x server didn't show up because monitor showed "Out of range". Restarted.

Third time booting from disc, added noapic to line, and this time it was stuck at Loading Linux Kernel (around half-way), wouldn't go further. Restarted.

Fourth time booting from disc, added noapic to line, this time it was stuck at Loading Linux Kernel at 8%, wouldn't go further.

Everytime it just gets worse and worse. Please help, I'm so sick of this T_T.

Edit: I tried again, and it got into the desktop and everything, but the Install program would **not** run. Then a second time, and it froze at 32% loading Linux kernel.. /sigh

---

### Post by p!=f on 2007-02-04
As I can see it has nForce4 chipset. Section flaws ([http://en.wikipedia.org/wiki/Nforce4)](http://en.wikipedia.org/wiki/Nforce4)). It's known to have problems.
2 months ago I bought MSI K9A Platinum (AMD ATI RD580+ chipset, also known as ATI Xpress 3200) with AM2 3500+. Absolutely no problems so far.
If you have BIOS version < 0601 I would recommend to take a look at the manufacture's website for BIOS update. (latest is 0802 -> [http://dlsvr01.asus.com/pub/ASUS/mb/socketAM2/M2N4-SLI/M2N40802.zip](http://dlsvr01.asus.com/pub/ASUS/mb/socketAM2/M2N4-SLI/M2N40802.zip))
```

M2N4-SLI BIOS version 0802
1. Support new CPUs. Please refer to our website at: http://support.asus.com/cpusupport/cpusupport.aspx.
**2. Enhance compatibility with certain CPUs**
3. Add "Press TAB to display BIOS POST Message" string on POST logo screen.

```
Also, try to install from alternate install CD.

---

### Post by SimonTheMime on 2007-02-04
Upgraded, new disc.. same problems.

Last three boots wouldn't even get to the loading status bar. Just gets stuck at Loading Linux Kernel :\..

---

### Post by p!=f on 2007-02-04
Do you have RAID set up? Is RAID selected in BIOS? Try to boot with acpi=off kernel option.

---

### Post by teaker1s on 2007-02-04
what bios make? mine has been a git and I'm edgy base with feisty kernel=100% better

---

### Post by SimonTheMime on 2007-02-04
A git? And it's the latest bios update.

> **p!=f said:**
> Do you have RAID set up? Is RAID selected in BIOS? Try to boot with acpi=off kernel option.
Raid's disabled. Should it be enabled?

And I just did acpi=off.. and just as sometimes before that when it b]would[/b] eventually get past Loading Linux Kernel, it goes to a black screen and a blinking underscore.

Edit: Second boot using that, it got stuck at Loading Linux Kernel again. So I guess it didn't help.

---

### Post by teaker1s on 2007-02-04
git is English slang for a problem/pain!       also for example 

it's being a sod

-another example

---

### Post by SimonTheMime on 2007-02-04
Oh, well I guess I'll try Feisty herd 3 then, see if it works any better o,o.

Burning disc as we speak

---

### Post by SimonTheMime on 2007-02-04
Nope didn't do a thing T_T

---

### Post by mr.v. on 2007-02-05
SimonTheMime--
I think you may have to compile your own kernel since you're having trouble with the precomped ones.
head over to [http://www.linuxfromscratch.org/livecd/](http://www.linuxfromscratch.org/livecd/) and burn the iso. It provides a nice livecd with a great clean build environment and a stable kernel + kernel source (but feel free to download the latest kernel from [http://www.kernel.org/pub/ ](http://www.kernel.org/pub/ ) ... I think it's 2.6.19.2 at the moment)

boot into the live-cd and see if it can boot to the terminal prompt. If it can, you're in good shape. Mount your hard-drive to some directory and untar the kernel source package to your harddrive (preferrably in your /mnt/yourdrive/usr/src/ directory).

then go into the newly untarred directory, configure and compile your kernel by typing
**make menuconfig**
/*go through the menu for enabling choices. Things are fairly well documented but it is a pain going through everything but remember this is just a temporary kernel to get yourself up and running again
if you ask nicely someone may even post a .config file so you don't even have to bother with all the choices. I'll look into your motherboard and see. Just be sure you don't select modules. Just choose everything with 'y' so things are statically compiled into the kernel.*/

after going through menuconfig, type
**make bzImage**

then copy the bzImage from ./arch/i386/boot/bzImage to your /mnt/yourdrive/boot/vmlinuz-2.6.16.27 (or whatever version of the kernel you built). Also copy the ./System.map to /mnt/yourdrive/boot/System.map-2.6.16.27 (or again, whatever version of the kernel you built).

since you didn't bother with modules, you'll save yourself the hassle of compiling them and installing them.
Also forgo things like framebuffers and bluetooth for now. You can play with that sort of stuff once you figure out how to boot =)

Now you've got your newly hacked kernel onto your harddrive...go ahead and edit the /mnt/yourdrive/boot/grub/menu.lst to add an entry for your new kernel. Boot with your minimal kernel to see if you can get things going.

hope this helps

---

### Post by SimonTheMime on 2007-02-05
Hm a few questions:

How can I mount my HD to a directory?

Also, by doing LFS.. what's it based off of.. like I wouldn't be able to use apt and such, right? :\...

---

### Post by SimonTheMime on 2007-02-05
Update: Just tried running dapper with noapic, loaded the kernel, then this came up:

[17179573.160000] Call Trace:
[17179573.160000] [<c020741d>] acpi_rs_create_pci_routing_table+0x1e/0x17a
[17179573.160000] [<c0200003>] acpi_ex_opcode_1A_0T_1R+0x2ba/0x427
[17179573.160000] [<c02084ad>] acpi_rs_get_prt_method_data+0x2b/0x3e
... [a few more lines of this kinda stuff]
[17179573.160000] [<c038887d>] do_initcalls+0x4d/0xc0
[17179573.160000] [<c01002c0>] init+0x0/0x150
[17179573.160000] [<c01002f1>] init+0x31/0x150
[17179573.160000] [<c01-1385>] kernel_thread_helper+0x5/0x10
[17179573.160000] Code: 83 c4 0 5b 5e 5f 5d c3 55 57 56 53 51 8b 44 24 18 8b 50 0c 89 14 24 8b 68 1c 31 f6 31 ff eb 5f 8b 44 bd 00 8b 50 1c 31 db 8b 01 <8a> 41 0 3c 02 74 12 3c 14 75 07 66 83 79 0a 2d 74 07 83 c2 04
[17179573.160000] <0> Kernel Panic - not syncing: Attempted to kill init!

Any ideas what this means?

---

### Post by mr.v. on 2007-02-05
> How can I mount my HD to a directory?
at the shell prompt type:
```
mkdir /mnt/hd
mount -t ext3 /dev/hda1 /mnt/hd
```

this assumes the following things...the directory /mnt has been made (which it almost invariably has) and that your ubuntu partition is /dev/hda1

if you installed ubuntu on, say, the 1st partition of the 1st IDE channel's Slave drive it would be /dev/hdb1
The Ide channel 1 is /dev/hda and /dev/hdb where hda is the master and hdb is the slave
The IDE channel 2 is /dev/hdc and /dev/hdd where hdc is the master and hdd is the slave
If you have a sata drive they're generally in
/dev/sda1 (/dev/sda2...3...4...etc)

> Also, by doing LFS.. what's it based off of.. like I wouldn't be able to use apt and such, right? :\..
well...you'd only be using the LFS live CD to compile a kernel with support for your hardware. Then you'll place that kernel on your Ubuntu partition and update grub to load your compiled linux kernel on the Ubuntu part. Then you should be able to boot into Ubuntu using your custom kernel since the prepackaged ubuntu kernel isn't working. Once in Ubuntu things like package management like synaptic/apt-get etc should all work the same.

For several other distributions it's very common to compile your own kernel in place of the distribution supplied one.

**For now, I'd try a different live-CD like knoppix, LFS, or DamnSmallLinux and see if you can function in those for a while (browse the internet etc).**

There may be some kernel setting that is a problem. You may also try to disable ACPI in the BIOS rather than the kernel. If it's disabled in the BIOS then the kernel won't load support for it anyway.

---

### Post by SimonTheMime on 2007-02-06
Do you think if I bought a different AM2 mobo, by a different brand maybe, I wouldn't have this problem?

---

### Post by mr.v. on 2007-02-06
have you tried a different distro's live-cd yet? I'd try DamnSmallLinux (<50MB download and a surprisingly large amount of functionality) and Knoppix to see if you can get it working and play around with it.

I'm worried it may just be Ubuntu's kernel config on your hardware. I wouldn't keep going through motherboards if another distro's kernel boots just fine and works for a while...

Another thing to try is to do the memtest86+ from the livecd in case you've got bad memory, but again, I'd first see if DamnSmallLinux or Knoppix boot okay before running memtest86+ all night...

---

