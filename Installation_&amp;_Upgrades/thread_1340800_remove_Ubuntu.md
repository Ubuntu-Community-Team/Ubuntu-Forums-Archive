---
title: "remove Ubuntu"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by IamGibby on 2009-11-29
Can anyone link me to a tutorial on how to completely remove ubuntu on a dual boot setup so that the partitions on the HDD assigned to ubuntu can be regrouped into my normal HDD? I upgraded to Win7 on my tablet and it removed the grub boot GUI and I figured I'd just completely remove ubuntu on this machine and keep it win7 since my workstations all dual boot with Ubuntu/Linux atm. I've tried to search the forums for a while now with no luck on a removal guide for vista/windows7. I really appreciate anyone's help.

Thanks

Chris.

---

### Post by BenAshton24 on 2009-11-29
Boot from your ubuntu live cd and run
> sudo gparted
Using gparted, delete all Ubuntu related partitions and then right click on your windows 7 partition and choose resize/move, adjust the size so that it fills the entire HD then click apply.

note: windows 7 will probably require you to re-active after having done this.

---

### Post by Nburnes on 2009-11-29
> **BenAshton24 said:**
> Boot from your ubuntu live cd and run

Using gparted, delete all Ubuntu related partitions and then right click on your windows 7 partition and choose resize/move, adjust the size so that it fills the entire HD then click apply.

note: windows 7 will probably require you to re-active after having done this.

Or the user can just go boot into Windows 7 and then Start menu > Right-click Computer > Manage > Disk management and then delete the partition Ubuntu is on, then right click on your Windows 7 partition and choose extend.

---

### Post by BenAshton24 on 2009-11-29
> **Nburnes said:**
> Or the user can just go boot into Windows 7 and then Start menu > Right-click Computer > Manage > Disk management and then delete the partition Ubuntu is on, then right click on your Windows 7 partition and choose extend.

[sarcasm]
yes because expanding the same partition that windows is using won't be problematic at all...

---

### Post by IamGibby on 2009-11-29
> **Nburnes said:**
> Or the user can just go boot into Windows 7 and then Start menu > Right-click Computer > Manage > Disk management and then delete the partition Ubuntu is on, then right click on your Windows 7 partition and choose extend.

I really should of listened to BenAshton24... But since I couldn't find a live disk real fast, I decided to do the above. The deletion went in a instance and now  I can't expand my Windows Partition at all and the deleted partitions went into a 'Free Space' state and not an unallocated state. I can't even create a basic Volume with the 'free space' so I could format it.... Does anyone have any suggestions x_x...

EDIT***

If I clicked delete partition on the 'free space' sector, and it prompts that if you delete it it'd be inaccessible, I said yes and that put it into the sate of unallocated space. then i expanded my Windows Partition. Just so anyone who looks into this and see's his post and has the same problem, that was my solution.

Thanks

Chris.

---

### Post by darkod on 2009-11-29
That happened because probably you had logical partition inside extended partition. If you delte the logical ones the space is stil occupied with the extended partition. Until you delete it too. Only then it's unallocated, unpartitioned space.

---

### Post by rajeeja on 2009-12-05
I tried the windows way and deleted the ubuntu9.1 partition, the extend button was disabled for some reason and when i tried to do 

@IamGibby Post#5 when I tried - "

EDIT***

If I clicked delete partition on the 'free space' sector, and it prompts that if you delete it it'd be inaccessible, I said yes"

It gave an error you dont have sufficient disk space. So, I decided to reboot. After rebooting I get - 

GRUB loading.
error: no such disk
grub rescue> 

I am able to boot from USB into ubuntu 9.1 and open gparted. Please let me know what should be done here to get the computer to boot windows7 (factory installed). Gparted now shows:

unallocated 1MB

/dev/sda1 system 1.46GB
/dev/sda2 T1xx   250GB --- this has flag set to boot

/dev/sda3 extended 37.54GB
 under this
      unallocated 35.95GB
      /dev/sda5 linux swap 1.59GB
unallocated 9.05GB

Is there a way to get to boot windows7 without using the win7CD?

---

### Post by rajeeja on 2009-12-05
One more thing /dev/sda3 and /dev/sda5 are locked or having a key symbol next to the File System.

---

