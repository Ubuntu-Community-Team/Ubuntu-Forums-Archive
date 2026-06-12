---
title: "Cannot Install from DVD drive"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by lordofscripts on 2019-10-28
A few days ago I downloaded Ubuntu Desktop 19.x and burnt the ISO image on DVD. In the resulting DVD I see a series of folders but I do not see an autorun.inf on the root. The DVD was verified and is correct.

I have an old ASUS with Windows 10. I plan to use a clean 1TB external drive for my Ubuntu installation, it is connected to my USB port. I changed the BIOS settings to boot first from DVD, then external drive and then internal drive.

However, when I restart the machine (twice already) hoping that the DVD would kick in and show me an Ubuntu install screen, I see that it first tries to access the DVD, then moves on to the external drive and then finally it boots from internal drive and I never get to see the Ubuntu install.

What am I missing here? BTW I do NOT want to alter my internal HDD boot record, I want EVERYTHING to be installed on the external drive. The last time I installed Linux on a machine (other than VMWARE) it screwed up my boot record on the main drive (I hate GRUB, never had a problem with LILO).

---

### Post by CatKiller on 2019-10-28
> **lordofscripts said:**
> In the resulting DVD I see a series of folders but I do not see an autorun.inf on the root.

Why would you?

> I have an old ASUS with Windows 10.

I believe it's Asus that makes their machines only able to boot Windows unless you jump through hoops with Secure Boot to make it trust something else. I've never used any of their machines.

> BTW I do NOT want to alter my internal HDD boot record, I want EVERYTHING to be installed on the external drive.

That's not going to be easy, and will require more hoop-jumping. The old BIOS method would have the bootloader included in the Master Boot Record of an MBR-partitioned drive, meaning that it was relatively straightforward to have everything separate; each drive has an MBR, so each drive can have its own bootloader. The newer UEFI method has multiple bootloaders in the EFI System Partition of a GPT-partitioned drive. The default install will put a bootloader in the ESP of your internal drive even if the install is to the external drive.

If you're tentative about actually installing and using Ubuntu, perhaps simply using it in a VM would better suit you?

---

### Post by lordofscripts on 2019-10-28
My laptop is not powerful enough to run VMWare, it has Windows 10 Home so I do not think it has the Microsoft vvirtual machine either.

BTW I managed to get it to boot from my DVD drive where I have the Ubuntu image. What I had to do was go into the BIOS and change the Boot from UEFI to LEGACY which in turn automatically disables Secure Boot whatever that is. Now I can boot Ubuntu from DVD although I am having other issues as mentioned in another post, namely that is shows my internal drive as /dev/sdb instead of /dev/sda.

---

### Post by CatKiller on 2019-10-28
> **lordofscripts said:**
> What I had to do was go into the BIOS and change the Boot from UEFI to LEGACY which in turn automatically disables Secure Boot whatever that is.

That's a bad plan. It's fine for trying things out, but your Windows 10 install is using UEFI. Booting the install media in Legacy mode will cause the installer to install as BIOS rather than UEFI. Mix-and-matching BIOS and UEFI like that won't work.

In general you can turn off Secure Boot without putting it into BIOS mode, but Asus have a reputation for doing peculiar things there.

> Now I can boot Ubuntu from DVD although I am having other issues as mentioned in another post, namely that is shows my internal drive as /dev/sdb instead of /dev/sda.

Those identifiers are largely meaningless. They're just allocated based on which device happens to respond first. They aren't guaranteed to be the same between boots. Labels or UUIDs are the sensible ways to distinguish drives from one another.

---

