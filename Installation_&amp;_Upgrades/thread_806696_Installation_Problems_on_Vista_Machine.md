---
title: "Installation Problems on Vista Machine"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by WillockBoy on 2008-05-25
I am trying to install Ubuntu 7.10 on a Dell Dimension 9200 machine running Vista SP1 and Raid hard drives.

Having read some advice, it would seem that it would be sensible to use EasyBCD boot loader. I have also read that it is perhaps advisable to create Unallocated free space on the C: drive (two WD 160GB drives acting as one 320GB raid drive)and then install Ubuntu into the largest continuous free space.

I created 40GB of unallocated free space and then tried install Ubuntu. However, I received an error message telling me that  Ubuntu "Failed to partition the selected disk or free space is too small to be automatically partitioned". Any thoughts as to why this error message is occurring?

I have also read the advice given on the NeoSmart Technologies web site to let Ubuntu find the free space and partition the drive. Is this method a safe one which would not corrupt Vista?

Thank you for any help.

---

### Post by fmartinez on 2008-05-25
Use the windows partitioner to free up some space for Ubuntu. I have 2 drives both 350GB in HP machine. 
1 has Vista
1 has Ubuntu 
and this works great.

---

### Post by WillockBoy on 2008-05-25
Thank you FMartinez for your reply. I think that the problem lies with the Raid 0 drive set-up on my machine. It would seem that Ubuntu does not read the "fake" Raid used by many computers. If this is the case, then I suppose that the only option is to remove the Raid and reinstall Vista, then Ubuntu.

---

