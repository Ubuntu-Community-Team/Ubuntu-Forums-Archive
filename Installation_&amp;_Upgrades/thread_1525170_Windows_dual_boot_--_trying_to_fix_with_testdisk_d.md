---
title: "Windows dual boot -- trying to fix with testdisk deleted everything?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by Fillanzea on 2010-07-06
I had my computer dual booting Windows 7 and Ubuntu 9.10. Last night I upgraded to 10.04. Everything seemed to go fine on the Ubuntu side, but when I booted to Windows I just got a blinking cursor on a black screen.

After searching the forums, I downloaded and ran testdisk. I tried "rebuild BS" on both the Windows "recovery" partition and the Windows "OS" partition. This time I still got the blinking cursor when I tried to boot into Windows, and not only that, but where the Windows partition had previously been mountable in Ubuntu, I'm now getting the message 

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 4096  usa_ofs: 48  usa_count: 2: Invalid argument
Actual VCN (0x3003800010001) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Needless to say I can't get into Windows to run chkdsk.

If I go into "Undelete" on Testdisk, it brings up seemingly every Windows system file, so ... did I accidentally delete everything? Next question: is there a way to select *everything* in there to be undeleted? I've been going file by file but it's very tedious and I don't even know if there's a way to select multiple items at once.

Where do I go from here to recover my Windows dual boot? I don't have any necessary data on that partition, so that part isn't an issue, but I don't have a system recovery CD, so any way around that would be really helpful. How do I recover my deleted files? And once I've recovered them, how do I turn that into something I can boot from? Would it be simpler just to request a recovery disk from Dell?

---

### Post by WinRiddance on 2010-07-06
Oh man, sorry to hear about these problems. I've always had the best results with this free utility, parted magic, which enables you to restore your master boot record, previous partitions, and so on. Here's the link to parted magic, hope this helps:

[http://partedmagic.com/](http://partedmagic.com/)

Good luck !!! ;)

---

### Post by Fillanzea on 2010-07-06
Thank you... I tried to download Parted Magic and the iso won't even boot, and even if it would, Parted Magic has a ton of utilities on it and to be honest I don't know how to do anything with any of them, so I'm going to need more detail on what to do here.

---

### Post by WinRiddance on 2010-07-06
> **Fillanzea said:**
> Thank you... I tried to download Parted Magic and the iso won't even boot, and even if it would, Parted Magic has a ton of utilities on it and to be honest I don't know how to do anything with any of them, so I'm going to need more detail on what to do here.

The downloaded ISO file has to be copied to a cd _with a special program_ which is meant to burn ISO images onto a CD. There are plenty of free programs available, just google "ISO maker" and you'll find plenty of them. After you burn the ISO image onto a CD (try not to use a DVD disk) it will be bootable ... as long as your _computer bios_ is set up to recognize bootable ISO cds. Just try it and see what happens. Parted Magic is actually **very user friendly** which is why I recommended it.

If the ISO CD won't boot automatically when you restart your computer, you'll have to enter the bios of your machine. This is different from one computer to another but most commonly either the F2 or DEL or ESC key will get you there once you restart the machine. When the bios has been accessed (blue screen with white text) there will be several options that you can move to and change with your ARROW KEYS. Often some brief single line instructions appear on the bottom of the screen too. **Don't change anything other than the boot sequence.** You want your CD drive to appear as the _first or top line in the boot order_ which will then enable your computer to boot from the bootable ISO CD that you created.

You can even leave your bios settings that way when you're all done because unless your computer is super old (10 years ???) the machine will only use the cd boot option if there's actually a bootable cd in the cd drive. Otherwise it'll boot automatically to the main operating system on the hard disk. Good luck !!!

---

### Post by Fillanzea on 2010-07-06
I will fully admit my ignorance, but I *do *know how to burn an .iso to a CD, and I *do* know how to go in to the BIOS on a computer.

When I try to boot from the CD, I get the message:

No default or UI configuration directive found!
boot:

---

### Post by Fillanzea on 2010-07-06
There's no way I can cope with this right now, I've just requested a recovery CD from Dell.

---

