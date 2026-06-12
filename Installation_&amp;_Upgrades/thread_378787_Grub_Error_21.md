---
title: "Grub Error 21"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by ronald_stall on 2007-03-07
Help, I just installed Edgy on my WinXP system on a separate HD but now when it boots I get and Grub Error 21. Please help! I cannot seem to find this error code.

---

### Post by mikewhatever on 2007-03-07
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

I have read of this error being described after the number2 hard disk with the Linux installation on it has been removed from the machine. Grub had been installed in the MBR in the number1 hard disk, and when the number2 hard disk was removed, the machine could not boot anymore, and showed 'grub error 21'.

This is because bootloaders have two or three parts. The first part, called 'stage1', normally is very small, and lives in a special part of the MBR. The second part, called 'stage2', is much larger and lives in the operating system itself. Other bootloaders work the same way too.

Basically the only work the small part (stage1) has to do is to find the other, larger part, 'Stage2'.
It is 'stage2' that does all the hard work, it can because it is bigger.
In the case of Grub, there is also another part called 'stage1_5' which helps 'stage1' to find the other part.

When the hard disk that contained the operating system has been removed, Grub cannot work because the larger part of it is gone.
The first part of Grub, which is very small and whose only job is to find the larger part, gets help from stage1_5, but if the hard disk with stage2 on it is gone, they cannot find stage2 of course, so they complain by printing out this error massage.

Please put the hard disk with stage2 in it back into the machine, and/or make sure it is properly plugged in and detected and set up in the BIOS.
If you happen to be using a hard disk larger than 137 GB, see also error 18.


taken from [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

in case you want more help, post some information about your specs and installation.

---

### Post by ronald_stall on 2007-03-07
Thanks for the reply. Brings up a new question though. I have 3 hard drives installed. Two are in a raid0 config running WinXP. The 3rd is the drive installed ubuntu on and now seemingly is not seen. is there a work around for this. I found the FAKERAIDEDGY, does this apply even though I am not installing Ubuntu on the raid drives?

---

