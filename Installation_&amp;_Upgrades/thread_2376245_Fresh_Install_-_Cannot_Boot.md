---
title: "Fresh Install - Cannot Boot"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by prisma128 on 2017-10-31
I picked up an intel nuc (nuc5i5MYHE), and it came with an M.2 SSD already installed, and the ram and everything, and it was running windows just fine. Then I installed ubuntu server to it and everything installed fine, but then the system just wouldn't boot. I was getting the generic "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key" message. I tried re-installing it a few times&#8211;I tried fiddling with BIOS settings&#8211;I tried installing it with manually created partitions and with formatting the drive first, and nothing.

So tonight, I re-installed ubuntu-server(16.04.3-64bit) with all the default options. Everything went fine. Still didn't boot. Then I booted up boot repair and got the boot info ([http://paste.ubuntu.com/25862622](http://paste.ubuntu.com/25862622)), then I ran the recommended repair option (everything went fine, no errors) and got this pastebin ([http://paste.ubuntu.com/25862664](http://paste.ubuntu.com/25862664)).

I'm absolutely stuck and would love any insight anybody has. I read on arstechnica that older versions of the nuc BIOS don't handle ubuntu EFI correctly and you have to go in and manually configure it, but 1. ubuntu-server isn't installing in EFI mode and 2. One of the things I tried was updating the BIOS to the newest version, where that (supposedly) is no longer an issue.

I also ran a s.m.a.r.t check to see if maybe there was something wrong with the ssd and it reported everything was fine, and like i said, it was booting windows fine before i started messing with it.

Again, any insight is greatly appreciated!

Thanks :)
Prisma

Edit: Also, I tried holding shift down while booting and didn't even get the GRUB2 menu, but beyond that I wasn't sure what troubleshooting to do.

---

### Post by jpberes on 2017-11-01
Can you please be more specific ? What do you mean by doesn't boot, you get any messages or ???
And why to install Ubuntu server edition on a stand-alone machine ??

---

### Post by ajgreeny on 2017-11-01
You did not install Ubuntu in UEFI mode you say, but I was very surprised to see Windows was not in UEFI mode; you have also chosen to use LVM about which I am unfortunately clueless.

Which version of Windows do you have, how did you create the partitions when you did it manually, and what was the "fiddling" in BIOS that you did?

The more info we have the more we may be able to help you.

---

### Post by prisma128 on 2017-11-01
> **jpberes said:**
> Can you please be more specific ? What do you mean by doesn't boot, you get any messages or ???
And why to install Ubuntu server edition on a stand-alone machine ??

I'm sorry if it wasn't clear but I'm still getting the  "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key" message.

And I'm installing Ubuntu server edition on a stand-alone machine because I'm setting up a home server? Is this that unheard of?

---

### Post by prisma128 on 2017-11-01
I can't say for certain because I didn't make note of it, but before I messed with anything there were boot entries in the legacy BIOS section of intel's BIOS setup, so windows could have been booting without EFI, but again, I can't say for sure. It was windows 10, but, there's no windows on the machine right now, as I've formatted and re-formatted the ssd several times.

When creating the partitions manually, I tried a couple of things. At first I was confused about the whole EFI vs Legacy BIOS thing so I tried setting up a /boot partition as well as /(root), /home, and /swap partitions. I also did installations with just the /, /home, and /swap partitions. I tried installations with guided options, using the entire disk, and same result every time.

By messing with the BIOS settings I just meant I tried disabling UEFI mode to force Legacy Boot. I also played around with the settings listed in this [guide from intel]("https://www.intel.com/content/www/us/en/support/articles/000022600/boards-and-kits.html") despite having a different nuc model, because I thought that could potentially help. Either way, before the installation attempt last night I reset the BIOS to default settings (which includes EFI boot enabled and secure boot disabled).

I can try re-installing it without LVM. There wasn't any particular reason I chose that, it was just the default selected option of the Ubuntu Server install and I didn't bother changing it this time around.

But also, I'm confused by
> You did not install Ubuntu in UEFI mode you say, but I was very surprised to see Windows was not in UEFI mode;

if you look at the pastebin of boot-repair directly post-installation, it says it installed grub2 on the mbr, without an EFI /boot partition. Unless I have a complete misunderstanding of how this works?

---

### Post by slickymaster on 2017-11-01
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2017-11-03
If you had Windows 10 pre-installed from vendor, then it was in UEFI boot mode using gpt partitioning.
Windows only boots in UEFI mode from gpt partitioned drives.

You erased gpt and installed in the 35 year old BIOS/MBR configuration which is well know as old, but not the newer gpt partitioning which can be used with BIOS boot or UEFI boot if only Ubuntu installed.

Boot-Repair report says UEFI Secure Boot may be on.
You cannot boot in BIOS/CSM/Legacy Mode with UEFI hardware if UEFI secure boot is on.

---

### Post by prisma128 on 2017-11-05
In case it helps anybody in the future, the problem was that that my pc's bios wasn't picking up the correct boot entries so I had to boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it. thanks everybody for the replies though!

---

