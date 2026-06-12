---
title: "Installing to one partition"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Skyline969 on 2010-03-29
Ok, on my Dell Inspiron 1525, I have the current hard drive setup:
Small, reserved partition (Dell diagnostics or something... I have no access to it whatsoever)
Dell MediaDirect partition (Dell loves to hog the partitions, if I delete that and accidentally press the MediaDirect button when my laptop is off, the MBR will get mangled as it tries to boot to the nonexistent MediaDirect partition)
Windows 7 Professional
Empty Partition

Ok, all of the three used are primary partitions. However, I know that a hard drive can only have 4 primary partitions on it at maximum. I know nothing of Linux's filesystem... will I be able to install Ubuntu (OS partition, swap, etc that the default dual-boot installation creates) as a dual-boot with Windows 7 with only one primary partition free? Additionally, I remember that Ubuntu does not like wireless drivers, so will my wireless NIC work in Ubuntu? I'll be installing 9.04 and then upgrading to 9.10, as the latest CD I have is 9.04 (I could get a 9.10 ISO, but meh).

Thanks in advance for your help.
Skyline969

---

### Post by akand074 on 2010-03-29
Yeah you can just install Ubuntu as an Extended partition, you can have lots of those. But for a standard install you could just install ubuntu on a primary partition and swap would be extended I don't see why not. Either way, it can be done. I'll be splitting my Ubuntu into 6 partitions when Lucid is released.

---

### Post by Skyline969 on 2010-03-29
> **akand074 said:**
> Yeah you can just install Ubuntu as an Extended partition, you can have lots of those. But for a standard install you could just install ubuntu on a primary partition and swap would be extended I don't see why not. Either way, it can be done. I'll be splitting my Ubuntu into 6 partitions when Lucid is released.

Ah, alright, yeah I know I can have a lot of extended partitions... I'm not sure what the limit is, but I know you can have more than Windows would recognize, as Windows only recognizes as many as there are letters. Anyways, so if I just pop in my Ubuntu CD (after shrinking my Windows partition by 50 GB to make enough for Ubuntu) and hit Install, it should work 100% with the default settings (just mindlessly clicking next)?

---

### Post by oldfred on 2010-03-29
Your last primary becomes an extended partition that can hold many logical partitions. It is just a container for the logical partitions. Of course you have to have it large enough to create several logical partitions depending on what you want to do.

Wireless has been a problem. Most have been solved or have workarounds. You need to search on your exact model to know for sure. My 3 year old toshiba worked without any issues at all.

---

### Post by Skyline969 on 2010-03-29
> **oldfred said:**
> Your last primary becomes an extended partition that can hold many logical partitions. It is just a container for the logical partitions. Of course you have to have it large enough to create several logical partitions depending on what you want to do.

Wireless has been a problem. Most have been solved or have workarounds. You need to search on your exact model to know for sure. My 3 year old toshiba worked without any issues at all.

Well let's hope my Inspiron works fine. I'll be installing Ubuntu after class, in a dual-boot. I'll be using ~50GB for all extended partitions. My classmate told me in order to make sure his worked, he plugged in an Ethernet cable into his laptop so he could download drivers. From there, once Ubuntu was installed he just went into some sort of hardware or driver or something management in Administration and re-scanned the hardware on the machine. It found his wireless NIC and installed the generic drivers for it. I hope it's as easy as that for me!

Thanks for the help, everyone, I appreciate it. I'll mark this as solved when I successfully install Ubuntu on my laptop and am able to mark this topic as solved from there.

---

