---
title: "Booting installed Ubuntu instance across multiple hardware?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by ziesemer on 2008-11-30
It seems I'm trying to do something not-so-common, as Google search results aren't helping much.  (The search terms for what I'm trying to do get easily confused with traditional dual-booting, etc.).

I have a new laptop, and I'd like to use Ubuntu Intrepid Ibex (8.10) as my primary OS.  However, there are still a few applications that will only run under Windows - particularly some audio/video applications with particular hardware that just won't work under Wine, etc.

I'm already setting up dual booting.  However, I'd also like to be able to run my Ubunutu instance while Windows is running.  This can be accomplished using VMware / VirtualBox / etc.

What I'm wondering is, can I use the same installed instance for both the dual-boot and the virtual machine?  I'm guessing it does, but where can I find information on supporting multiple "hardware profiles"?  (What would it be called?)  Will Linux take kindly to switching back and forth between "hardware", optionally loading different drivers for each?  Any additional tips that anyone would like to share?

Both hardware "profiles" will be x64.  Native, then emulated.

I'd just like to avoid having 2x of everything - 2x the hard disk, and 2x the maintenance, including installing the same software across both instances.

Thanks!

---

### Post by zvacet on 2008-11-30
I´m sure that you can find more or better ,but [this]("https://lists.ubuntu.com/archives/ubuntu-us-nm/2008-February/000521.html") is what I find.I hope that will help.

---

### Post by ziesemer on 2008-11-30
Guess I'm getting hung up on the issues I didn't expect...

VirtualBox apparently doesn't support using physical partitions, at least not under Windows hosts.  Microsoft VirtualPC doesn't support 64-bit guests.  Looks like VMware Workstation would be the best bet, but this isn't worth paying a license for.  The server edition may work, though it's not officially supported under 64-bit Vista - and the latest versions aren't exactly "desktop" friendly...

---

### Post by ziesemer on 2008-12-01
I just found that VirtualBox does support using physical disks / partitions.  It's apparently just not available for configuration in the GUI.  See section 9.9 of the VirtualBox user manual.

---

### Post by Mark Phelps on 2008-12-01
If I understand your question, you want to be able to use Virtual box to point to your already-installed version of Windows so you can run it without having to install a second instance.

I would be very interested in hearing back about how well it works for you -- because if it does, I would like to do the same thing.

Please report back after you've done the setup.

Thanks

---

