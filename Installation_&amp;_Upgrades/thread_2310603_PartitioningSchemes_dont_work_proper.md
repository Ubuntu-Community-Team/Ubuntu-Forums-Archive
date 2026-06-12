---
title: "PartitioningSchemes dont work proper"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by jan65 on 2016-01-20
Hi,

I am new to ubuntu and wanted to make a dualboot with W7pro.
I have a W7pro DVD and Ubuntu live on a USB-stick.

I booted ubuntu live, and made partitions according to
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) the "partitioning scheme for multiple systems"-part

I made fat32 partition, then Grubpartition, then Linux with /swap, /home and /root.
Closed the system proper
Then I did put/rebooted de W7pro DVD, and nothing happend.
I only can get into my BIOS.

What do you suggest?

---

### Post by yancek on 2016-01-20
I would recommend you use the much more detailed tutorial at the link below.  That is, if you plan on using MBR rather than a UEFI install as there is not explanation of using UEFI.  Windows 7 default is to use MBR.  I can't see the point in a separate boot partition although many people use it.  It just complicates things.  100MB is also too small.  Is the drive you are installing to empty?  You do have your DVD drive set to first boot priority in the BIOS?  I have no other idea why your windows won't boot as I don't use it.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2016-01-20
What system brand & model & what video chip/card?

Windows 7 default boot is BIOS mode only, you have to copy to a flash drive & move some files around to make it UEFI bootable. But Windows only boots from MBR(msdos) partitioned drives with BIOS and only with UEFI from gpt partitioned drives.

With BIOS/MBR Windows only will boot from, install into, or allow repairs to NTFS primary partitions. A second install of Windows can be a logical partition, as long as booting is from a primary partition.

Windows with UEFI requires several partitions if created in advance.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If a new user you just need the default partitions of / (root) & swap. And if dual booting with Windows another NTFS shared data partition. I suggest smaller system partitions and larger data partition(s).

---

### Post by jan65 on 2016-01-20
Hi,

I have a SSD drive for the W7pro and Ubuntu software. (new from shop)
And a 3 T HD also new from shop.

The weird thing is at first Ubuntu started fast from the USB
After i used Gparted for partitions as mentioned above and format.
I did close Ubuntu, and since then I only get a weird kind of menu with Shift F10.
Then I get the BIOS but I cant get into the BIOS too.

Thanks for the link anyway. But now I cant get into the machine anyway

---

### Post by oldfred on 2016-01-20
Your 3TB drive must be gpt(GUID) partitioned if you want all 3TB.
       MBR details including 2TiB limit and GPT link
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record
[/URL]
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

But Windows only installs to gpt partitioned drives with UEFI. Is your system UEFI?
      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

    
If a new UEFI system, you need to make sure fast boot in UEFI is off. And may have to turn on boot of USB drives. Generally better to have UEFI Secure boot off also.


[URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

