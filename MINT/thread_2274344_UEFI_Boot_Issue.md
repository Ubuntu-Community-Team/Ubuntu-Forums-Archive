---
title: "UEFI Boot Issue"
date: 2015-04-19
forum: MINT
---

### Post by andre43 on 2015-04-19
Hi all,

So I just got a new laptop, my first one that uses EFI, and I'm having trouble making it do the Linux. It's an Acer Aspire R14. Please help me.

I've been following the Ubuntu help guide here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Sure enough, I had to disable SecureBoot before it would boot my live USB. I also disabled that Windows fast boot thing from the control panel before I started.

I tried to repartition and install for a dual boot with Windows 8.1 (I'll describe how below). The installation seemed to (mostly) work, but I'm having that problem where I can't boot into my Linux installation, it just boots me straight into Windows.

I ran Boot-Repair as described in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) , but it told me that it had problems and gave me a paste URL: [http://paste2.org/vBt6gtCU](http://paste2.org/vBt6gtCU) . It seems to find a second disk(?) and get upset that it can't make sense of it, but no immediate solution jumped out at me from reading it.

When I installed ubuntu, I picked "do something else". According to Windows disk management, my partitions looked like this before the installation:

600MB Recovery
300MB EFI
(everything else) Windows C:
15.71GB Recovery

After the installation, it looked like this

600MB Recovery
300MB EFI (set as EFI for Ubuntu as well)
169.74GB Windows C:
1.91GB Swap
(everything else) Linux / (ext 4)
15.71GB recovery

Which is what I wanted. But I think it is worth noting that the Ubuntu partition manager seemed to suggest that the drives were in a different order, and a handful of odd extra entries that were 0 or 1MB in size.

Next steps? Is there any other info I can get you to help you help me?

Thanks for your time,
Andre

---

### Post by oldfred on 2015-04-19
I guess Acer requires you to add a password(never lose that) and allow or trust ubuntu as a boot choice.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

For new 4K drives, SSDs and a few other cases, partitions must round size on larger blocks. So the old gparted drives had spaces but rounding did not show them. Not slightly larger and they are over the 1K size so shown. You can ignore them.

Partition order on drive and partition order you have created them in which may not be the same does not matter either. It is just a caution to note that order is different.

Since Mint moved to Other OS.

---

### Post by andre43 on 2015-04-20
Followed the advice in the linked thread and it worked like a charm. I even had the same BIOS revision and everything. Thank you so much!

---

### Post by oldfred on 2015-04-20
Glad it worked. :)

---

