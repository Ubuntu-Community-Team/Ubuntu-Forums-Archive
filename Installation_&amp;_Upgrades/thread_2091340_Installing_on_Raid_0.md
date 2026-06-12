---
title: "Installing on Raid 0"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by suny123 on 2012-12-04
Long story short I am installing well trying to install Ubuntu 12.10 onto a SCSI Raid 0 array, it has 2 73GB 15K Seagate drives I believe. I have read and read and read, no actual answers, So here is my problem, right from the get go, when I got to choose the install it shows me to drives with multiple partitions of which I cannot manipulate any part of, I am usually bad at explaining things and very scarce on detail so Ill include a picture, It is attached below I hope, 

Thanks

Nathan 

(don't let the username fool you, it's hard to find a name that no one else has used.)

---

### Post by Forbees on 2012-12-04
hardware raid, software raid, or onboard "fakeraid" ?

---

### Post by suny123 on 2012-12-04
Sorry, I was just rethinking it in my head and realized that I left allot out, It is a Hardware Raid I am pretty sure, It is using an onboard controller the SCSI U320 it is a Dell Precision 670, and a big thing that I forgot to mention was that I am trying to dual boot it with Windows 7 Ultimate, I think it just became a bigger challenge.

Nathan

---

### Post by Forbees on 2012-12-04
an actual hardware raid is out of my scope. have you tried the [windows installer]("http://www.ubuntu.com/download/help/install-ubuntu-with-windows") method? 

if windows boots perfect with your raid setup, installing ubuntu inside windows should work.

---

### Post by suny123 on 2012-12-05
I tried the idea of the windows installer but it still gave me the same results as before, 

Same picture, 

Nathan

---

### Post by darkod on 2012-12-05
It is a bit strange, since proper hardware raid shouldn't show this. A proper hardware raid is done by the hdrware controller and presents a single disk to the OS, so the OS sees only a single disk.

Usually the /dev/mapper/... device is seen on fakeraids which means sort of a software raid.

But put that aside, you can see in the picture that your windows partition is taking the whole array. So where do you plan to install ubuntu when there is no unpartitioned space so it can create its partitions?

First boot windows, open Disk Management, and shrink the win7 partition for the size you plan to allocate to ubuntu. Reboot win7 few times to do it's disk checks.

Only after that start the installer, and when you get to the same step, at the top under /dev/mapper/...RAID0 you should see the two partitions ending with p1 and p2, and also the unpartitioned space. You need to create your ubuntu partitions from this space.

For bootloader installation you need to select the raid MBR which is the /dev/mapper/...RAID0 but the live cd often can't install grub2 on fakeraid properly. If this happens, you will need to boot the ubuntu cd in live mode and add grub2. We can talk about that if it happens.

---

### Post by suny123 on 2012-12-05
Thanks for the reply after reading that I realize what I should have done, I knew it I just did not know where and when to use that knowledge, anyway thanks and I will post with further results,

Nathan

**EDIT**

I get an error to do with unmovable files, Ill try a defrag as it suggests that

---

### Post by suny123 on 2012-12-05
Doing the DeFrag did not change a thing, I still receive and error stating that there are unmovable filesand I cannot shrink that drive/partition. Should I try a different partition editor, Easus Partition Manager is the name I believe.   

Nathan

---

### Post by darkod on 2012-12-06
Windows can be a real pain if other tools are touching its system partition. It's not impossible, but it can complain.

The unmovable files problem sometimes can be solved by temporarily disabling hibernation and the page file. Google for resizing win7 with unmovable files message.

If nothing works, you are welcome to try a third party software. Just remember, this is a windows thing and don't blame ubuntu if it goes wrong. :)

---

