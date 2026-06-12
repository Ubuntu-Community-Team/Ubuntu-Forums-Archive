---
title: "cannot boot into windows 8."
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by awesomemanX17 on 2013-03-18
Hello people. linux newbie I'm having problems booting into windows 8 after trying to remove Ubuntu 12.04 from my computer to try out Kubuntu.

I knew that deleting all my Linux partition would also delete my windows boot files, so I created a recovery usb drive to restore. I popped it in and did fixmbr and fixboot. it didn't work.
I must be one Unlucky guy because on my second boot of the usb, I got a \efi\microsoft\boot\bcd 0xc000000f error code.
it was telling me my computer need to be fixed and to insert the recovery media....My reaction was,"but this is the recovery media". it was then that I was starting to get a tad bit angry.

  Thank goodness I still had my Ubuntu installation usb so I popped it in and re installed Ubuntu. Grub2 didn't have a windows 8 entry of any sort so then I used boot-repair in hopes of fixing this mess.
It had put windows 8 on there but when I entered it, I got an error code 0xc0000225. I Don't know what to do now and I was hoping you guys could help me.

I'm running a dell inspiron 660

here's my most recent pastebin from boot-repair [http://paste.ubuntu.com/5625908/](http://paste.ubuntu.com/5625908/) 
I have more of then if needed.


any help would be appreciated.

---

### Post by oldfred on 2013-03-18
@akitta
You have your own thread, boot issues are almost always unique.
[http://ubuntuforums.org/showthread.php?t=2126833](http://ubuntuforums.org/showthread.php?t=2126833)

@awsomemanX17
I do not think any repair will work as you have multiple efi partitions. You can only have one as UEFI goes to the efi partition to find boot files. It cannot got to multiple ones. Use gparted an remove boot flag from all the others.
By putting Ubuntu into sda1 you may have messed up original efi partition or other Windows partitions. The Microsoft reserved partition must be the one before the main partition and have no format. You now have two reserved partitions one with format NTFS which is invalid.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by awesomemanX17 on 2013-03-18
> **oldfred said:**
> @akitta
You have your own thread, boot issues are almost always unique.
[http://ubuntuforums.org/showthread.php?t=2126833](http://ubuntuforums.org/showthread.php?t=2126833)

@awsomemanX17
I do not think any repair will work as you have multiple efi partitions. You can only have one as UEFI goes to the efi partition to find boot files. It cannot got to multiple ones. Use gparted an remove boot flag from all the others.
By putting Ubuntu into sda1 you may have messed up original efi partition or other Windows partitions. The Microsoft reserved partition must be the one before the main partition and have no format. You now have two reserved partitions one with format NTFS which is invalid.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

okay, I think I understand. I removed all of the boot flags that I was suppose to. now is there anyway I can move partitions?

---

### Post by oldfred on 2013-03-18
I do not know how you managed to move the Windows partitions around. But the Microsoft reserved has to be just before the main Windows install. The efi partition has to be first per UEFI, but Windows seems to want its repair/recovery first and that also works.

I would set up partitions just as Windows defines them, then add Ubuntu after those partitions on the drive. With all the changes you have done I am not sure you can move them all around but with some effort it should be possible. I just do not use Windows 8 and do not know all the details, other than what Microsoft suggests.

For better info on Windows 
 [http://www.eightforums.com/](http://www.eightforums.com/)

Then we can help on Ubuntu or dual booting.

---

### Post by awesomemanX17 on 2013-03-19
I don't know how either. I made sure not to touch my windows partition. Maybe my computer was shipped ln that order Idk.

Do you think it's possible to change my partition number using the copy feature on Gparted?


Heres and older pastebin. just incase it might help [http://paste.ubuntu.com/5562935/](http://paste.ubuntu.com/5562935/)

---

### Post by oldfred on 2013-03-19
You still are showing two efi partitions. You have a boot flag on sda5 which looks like your main install. Only in MBR(msdos) partitioning did you put boot flag on the Windows partition with the boot files. Even then boot flag in Windows 7 was on a 100MB boot partition not the main install.
You also have two recovery environments. Is sda4 really a recovery, if it is empty you may be able to delete it and move sda3 so it is next to sda5. I do not know if it is location on hard drive or partition number for Windows to have its reserved just before main install. Or you may be able to change sda4 to be the reserved & delete sda3. The reserved partition has to be unformulated and have the correct gpt partition type code or id. It only needs to be the size of your current sda3.

---

