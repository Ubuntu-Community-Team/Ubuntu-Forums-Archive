---
title: "Installing Ubuntu with Windows on Dual Boot - Grub Missing and Boot-Repair Failing!!"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by Phugoid on 2013-03-19
Hi all,

I've been having an absolute HELL of a time with my new laptop. I bought it about 2 weeks ago and to this day I still haven't done anything useful with it because I can't manage to get Windows and Ubuntu to behave and co-exist!

It's an EFI system, which I despise, and that's the root of my issues.

Anyway, it came with Windows 8 which I think is alright and I need it for work, so I need to dual boot. I partitioned my hard drive to leave unallocated space for Ubuntu, and installed it using a live USB. 

Before I did this I set my bios (or whatever we need to call it these days) to "support legacy mode", which disables secure boot, etc.

After install, it went straight to Windows. So I booted using the live USB again and installed and ran boot-repair as according to these instructions: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, my boot-repair gets to a point where it says "Reinstall GRUB. This may require several minutes", and it just hangs there. The status bar darts from side to side as if it is working, but after leaving it almost an hour, it isn't doing anything.

So I aborted it, shut down, and tried to boot up in Windows... which now tells me that my boot-up system is damaged and needs to be recovered.

I seriously want to throw this laptop out of the window and go live in a cave - the information age isn't worth this much stress, can anyone help and make this easy for me?!

---

### Post by Phugoid on 2013-03-20
Thanks for the replies. Ubuntu community is soooo useful.

---

### Post by oldfred on 2013-03-20
Sorry, I have been traveling and I am just about the only one that answers the UEFI secure boot issue questions. Oldfred is open to as many as would like to also jump in, to do that.

Best to post details from Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

