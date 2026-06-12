---
title: "Boot Repair problem - request pointers to learn how to fix this :)"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by Gobugs on 2016-10-11
Howdy

I got spanked while cleaning up a partition mess, on a lap top, and fortunately its not a critical issue (have image of before)  - Could you point me the right direction so I can learn.

Lap top, Win81 (cleaning it up to make room for dual boot with Ubuntu 16)
HDD  had 10 partitions, sda1::EFI  sda2&3 unused junk  sda4::win8 sda5->10:: unused junk.

I removed 2 & 3, and 5->10,  and resized sda4 to touch 1 with a 10MB gap,  using Knoppix Gparted.  Reboot to see if all this worked, and it refused to boot up. So I used boot-repair, and still have a no boot laptop.  Using Knoppix again I can see that both sda1 and now sda3 are labelled as boot and esp.

Here is the boot repair summary report.
[http://paste.ubuntu.com/23305432/]("http://paste.ubuntu.com/23308587/")

So, I'm in a learning mode,   what do I need to learn next,  so EFI knows where win8 is,now at sda3?  After that is done, then I will load Ubuntu in the spare space.

Thanks in advance.

---

### Post by yancek on 2016-10-11
You indicate in your post that you had windows 8 installed EFI but there is no EFI partition so that won't work.

> I removed 2 & 3, and 5->10,  and resized sda4 to touch 1 with a 10MB gap

Your boot repair shows that you still have sda2 and sda3 and sda2 and sda4 look like windows system or possibly a recovery partition.  sda3 is just the Extended.
I see you have grldr on sda1, were you using Grub4Dos on this system?
It looks like you have a Linux partition (sda5) but none of the standard files expected show there and it appears to be corrupted.

ntfsfix can repair very minor problems on an ntfs partition but as you can see in the output, this failed on all windows partitions.
You don't have any working Linux or Grub installed so the boot repair is not likely to resolve your problem.  Do you have a windows installation DVD or recovery CD?

---

### Post by oldfred on 2016-10-11
You were driving me crazy. Your link was the same as another I was helping and thought you were using two names. Or description of changes you made did not match link at all.
Then realized you link label does not match where link goes to. Is this then yours?
[http://paste.ubuntu.com/23305432/](http://paste.ubuntu.com/23305432/)

Windows requires certain partitions, and is not happy if you delete those. While it may work for a while at some point it may want that partition.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
Older BIOS/MBR partitions:
[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions
[/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]
[/URL] You must only have one ESP - efi system partition. UEFI spec does say you can have more than one, but no UEFI to date does that.
Remove boot flag from sda3 with gparted or Windows tools.

Make sure Windows boots, chkdsk has been run & fast start up in Windows is off.
More details in link in my signature.

---

### Post by Gobugs on 2016-10-11
Thanks for the replys.

Yes,  oldtom, 23305432 is the one I initiated and working on.  Sorry for the delay to respond, and the confusion.  I did not know the email and forum were tied together,  Sorry for messing it up.

The previous owner of the lap top was dual booted at one time, hence why on part was linux. sda1  what I can tell was efi, and sda4 was win8 as noted in the report.

What I have learned from your assistance;    sda1 should be efi boot, and sda4 dos nobott (win8)
                                                                  ;    boot.repair is normally only for linux ,  ok, dumb me, read the docs.
                                                                  ;    run chkdsk on the win to clean it up
                                                                  ;    go ahead and load ubuntu so grub becomes active.
                                                                  ;    try again   :)

What I don't know is how the efi  addresses the OS part where ever it might be, and can that be edited?

thanks.

---

### Post by oldfred on 2016-10-12
With grub you have /EFI/ubuntu/grub.cfg which refers to the install of Ubuntu and the full grub.cfg file.
I believe Windows uses BCD, but you would have to look on some Windows forums for explanation of /boot/BCD. Not sure if different for BIOS and UEFI boot systems, but BCD is in /EFI/Microsoft/Boot/BCD      in UEFI where in BIOS it is in the Microsoft boot partition.

[https://technet.microsoft.com/en-us/library/cc749510(v=ws.10).aspx](https://technet.microsoft.com/en-us/library/cc749510(v=ws.10).aspx)

---

