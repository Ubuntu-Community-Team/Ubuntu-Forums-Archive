---
title: "Help with Partition using Parted software on Ubuntu live CD"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by krishna_akella on 2008-08-09
Hi,
I am having a HP laptop with Vista Home premium loaded. Planning to partition my hard disk and install Ubuntu. Got excellent documentation from the forums. However having a problem when tried to do the partition using the software available in the live CD. Attached the screen shot of the problem.

I am not able to partition the disk. Please help.

---

### Post by mikewhatever on 2008-08-09
You need to shrink the Vista partition. Defragment it first.
The screenshot doesn't show there is a problem. There seems to be a single partition sda1 taking up all the space. Is that correct?

---

### Post by Pumalite on 2008-08-09
If you are using Vista; allocate space for Ubuntu with the Vista partitioner first. Later you can use Gparted

---

### Post by krishna_akella on 2008-08-16
> **mikewhatever said:**
> You need to shrink the Vista partition. Defragment it first.
The screenshot doesn't show there is a problem. There seems to be a single partition sda1 taking up all the space. Is that correct?
Hi,
Thnaks for the response. I tried defragmenting and shrinking. THe message saya that 
Total size before shrink - 76316 mb
Size of available shrink space - 551 mb

However when I check C drive properties, it shows 40 GB free space. 
Please help.

---

### Post by Pumalite on 2008-08-16
Did you use the Vista Partitioner?

---

### Post by Pumalite on 2008-08-16
If you have to; set Page File to =0 and later returned to what it was.

---

### Post by krishna_akella on 2008-08-16
Is it same as shrink? I tried Disk management -> Rightclick on c drive -> shrink volume. That is hwn I get the message about the space. PLease let me know if vista partitioner is diffrent!

---

### Post by krishna_akella on 2008-08-16
> **Pumalite said:**
> If you have to; set Page File to =0 and later returned to what it was.
I tried setting pagefile to zero. Still no improvement

---

### Post by Pumalite on 2008-08-16
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by krishna_akella on 2008-08-16
> **Pumalite said:**
> [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
Looks like lot of others have the sam problem. But no solution proposed.

---

### Post by Pumalite on 2008-08-16
Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management.


Right-click on the main Vista partition and select Shrink Volume - the Shrink tool will assess how much space can be freed up.

As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB) it should accommodate both operating systems.

Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space.

Once that's done, shut down the Vista machine.

---

### Post by krishna_akella on 2008-08-16
> **Pumalite said:**
> Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management.


Right-click on the main Vista partition and select Shrink Volume - the Shrink tool will assess how much space can be freed up.

As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB) it should accommodate both operating systems.

Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space.

Once that's done, shut down the Vista machine.
Hello,
Thanks for your patience. I tried exactly the same and that is when it shows 550 mb as available space.

---

### Post by Pumalite on 2008-08-16
You can use Gparted, but I cannot assure good results. Microsoft is your owner.

---

