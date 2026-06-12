---
title: "dual booting on Lenovo Ideapad Y510P"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by chronodekar on 2013-09-21
I recently bought a new laptop - the [Lenovo Ideapad Y510P]("http://shop.lenovo.com/us/en/laptops/ideapad/y-series/y510p/") that comes with Win8 pre-installed. Something unique about lenovo systems is their "recovery button". Basically it is a small button on the side of the laptop that I can push to bring the system back to factory settings. My *guess* is that lenovo does this with hidden partitions. From windows, I can see 2 partitions, but from the Administrative tools (under win8), I can see 6 partitions! (see [this thread]("http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/ideapad-y510p-why-so-many-partitions/td-p/1241675") on the lenovo forums and [these two]("http://forums.lenovo.com/t5/image/serverpage/image-id/27339i37E9A02521943E2E/image-size/original?v=mpbl-1&px=-1") [pics]("http://forums.lenovo.com/t5/image/serverpage/image-id/27341i02D92E8964D7334F/image-size/original?v=mpbl-1&px=-1"))

I want to dual-boot this system. Reading around, I found that I needed to disable the "secure boot" option from my BIOS. That was simple enough. From another system, I torrented Ubuntu 12.04.3 LTS 64-bit and made a bootable USB drive. Before using that on my laptop, from the win8 tools, I made an empty partition of about 230GB or so (to install ubuntu in). Then I booted off my USB drive and went though the usual procedure - though instead of selecting the "install alongside windows" option, I decided to manually select the partitions myself. Basically, I carved out about 10GB worth of swap space and allocated the remaining 220GB as root "/" directory. Ubuntu installed just fine and I was able to see GRUB come up during boot.

The problem was selecting windows from GRUB. It didn't work. An error message came up and then the system restarted. Sorry, but I do not remember what the error message was. I'm not exactly sure how, but by using Lenovo's "recovery button", I was able to boot back into windows. Some internet searching (from windows) told me to "repair my grub". Basically, the instructions told me to boot off the live-USB, install "boot repair" and select the default repair options there. I did that and at the end, it gave me the following URL,

[http://paste.ubuntu.com/6136211/](http://paste.ubuntu.com/6136211/)

The good news is that I can now boot into windows from grub. The bad news is that I have about 4 or 6 "windows" options to boot from in the grub menu and only the 3rd (or 4th?) one is relevant to me. The rest don't seem to do anything other than print some error message. Ubuntu works just fine. I'm worried about the following,

* Is my setup stable? As in; will it break again after an update ?
* How can I set windows as my default boot OS (instead of ubuntu) ?
* Finally - Is it possible to remove the redundant windows grub entries ?

Even though I *seem* to have things working, I'm really worried about stability. I've already got quarter of a mind to just go back to factory settings and forget about using ubuntu on this laptop.

Worried,
chronodekar

---

### Post by oldfred on 2013-09-21
You can turn off os-prober that creates incorrect BIOS type Windows chain load entries. And if you do not want all the efi entries that Boot-Repair added to 25_custom, you can manually edit out any that you do not want.
You should be able to go into UEFI menu and change boot order, similar to changing BIOS to boot DVD or Hard drive first. 
You also can use efibootmgr as a command line tool to edit UEFI entries.

Info on cleaning up menus is in link in my signature. Also posted essentially same info in this thread.
       Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

UEFI is new, both for vendors so an Update to UEFI/BIOS may change some things, but one advantage of UEFI is that it has its own memory so most settings should not change.
I would back up efi partition which most users do not do. 

As with any updates a grub update may cause issues, but if you know how to use Boot-Repair it can easily be fixed.

---

### Post by chronodekar on 2013-09-22
While I like to consider myself as a "technically competent" ubuntu user, keeping track of grub ... hiccups is NOT something I want to be doing. :(

It looks like there are 2 kinds of "boot" modes. One is the traditional GRUB thing before win8 and today, we have this "secure boot" thing. From the thread you pointed out, it looks like I should have been able to install ubuntu even with secure boot ON. I was looking at older material before and switched it off. The other boot method is the "EFI" thing, which I seem to be bypassing.

Right now, I'm thinking of resetting my laptop back to factory settings. That will remove ubuntu, but at least I won't see a messed up grub. After that, I'm thinking of keeping "secure boot" ON and installing ubuntu (64bit, 12.04.3) from there. If I understood things correctly, it will NOT install grub over my MBR, but should just add another entry to the "secure list".

Will I get a clean boot-loader that way?

When I say "clean" boot-loader, I'm talking about a system where I won't have to worry about the boot-loader going corrupt/bad after an update from canonical.

On a different note; how do you backup the EFI partition? Will using Clonezilla to copy my entire HDD to a USB storage ([as shown here]("http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/")) be enough?

-chronodekar

---

### Post by oldfred on 2013-09-22
If you want to back up efi partition, you can just copy the files in it. Clonzilla would be a way to backup entire system.

You have three boot modes. UEFI with secure boot, UEFI without secure boot, and BIOS/CSM/Legacy.
Only the CSM mode uses the MBR and each system overwrites each other when you install.

With UEFI each system installs boot loaders into the efi partition. So if one system is damaged you should be able to go into UEFI and choose to boot another. You can install many systems in one efi partition and choose from UEFI. UEFI is a boot managed where grub is both a boot manager and boot loader for Ubuntu. Windows in efi is only a boot loader for Windows.

If you turn secure boot on, then only systems that are secure boot will show in UEFI menu as bootable. You can use Boot-Repair booted with secure boot on, to install the signed kernels and convert Ubuntu to secure boot.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security


 As of 12.04.2 or later, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

