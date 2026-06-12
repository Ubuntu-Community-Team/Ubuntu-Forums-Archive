---
title: "Installing Ubuntu on an existing linux partition"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2010-06-20
I already have Ubuntu 10.04 32bit version installed on a partition. Instead of the 32-bit version, I would like to install the 64-bit version on the same partition.

I have a Parted Magic Live DVD and also Ubuntu 64bit OS on a DVD. 

How should I proceed?

Should I just point to the ext4 partition on which Ubuntu is installed and format it?

I am an Ubuntu Newbie and not good with partitions and formatting.

---

### Post by mmanjrekar on 2010-06-20
any specific reason u want to change from 32-bit to 64 bit when everything is working fine ? 

any ways ... when installing the 64-bit should ideally give you the option of retaining everything when u point it to the same partition. do not format.

---

### Post by GeorgeOfTheBush on 2010-06-20
Just want to try it out. I heard its better than the 32bit version.

---

### Post by GeorgeOfTheBush on 2010-06-20
I couldn't find any option to install on the existing partition itself.

---

### Post by cuberts on 2010-06-20
> **GeorgeOfTheBush said:**
> I already have Ubuntu 10.04 32bit version installed on a partition. Instead of the 32-bit version, I would like to install the 64-bit version on the same partition.

I have a Parted Magic Live DVD and also Ubuntu 64bit OS on a DVD. 

How should I proceed?

Should I just point to the ext4 partition on which Ubuntu is installed and format it?

I am an Ubuntu Newbie and not good with partitions and formatting.If you are a newbie, then resizing the partition and all of that will probably get really complicated for you. I think that the best way for you to do this would be actually creating a new partition for the 64 bit. So this will add another option on the GRUB menu. This is the easiest way that I can see to do it. Hope this helps.

---

### Post by GeorgeOfTheBush on 2010-06-20
> **cuberts said:**
> If you are a newbie, then resizing the partition and all of that will probably get really complicated for you. I think that the best way for you to do this would be actually creating a new partition for the 64 bit. So this will add another option on the GRUB menu. This is the easiest way that I can see to do it. Hope this helps.

I had already resized my Windows Vista partition following instructions from a forum post. That gave me some "Unallocated Space" which could be used for installing Ubuntu.

I dont understand why I would need to resize a partition _**now**_. I would like  to install on the same partition where I have already installed the  32bit version of Ubuntu.

Isn't that possible [COLOR=Blue]without[/COLOR] having to resize?

I thought Ubuntu would give me an option to [COLOR=Blue]select a partition[/COLOR] (in this case, the existing ext4 partition), allow me to [COLOR=Blue]format it[/COLOR], if needed, and then [COLOR=Blue]install Ubuntu 64bit[/COLOR].

---

### Post by darkod on 2010-06-20
> **GeorgeOfTheBush said:**
> I had already resized my Windows Vista partition following instructions from a forum post. That gave me some "Unallocated Space" which could be used for installing Ubuntu.

I dont understand why I would need to resize a partition _**now**_. I would like  to install on the same partition where I have already installed the  32bit version of Ubuntu.

Isn't that possible [COLOR=Blue]without[/COLOR] having to resize?

I thought Ubuntu would give me an option to [COLOR=Blue]select a partition[/COLOR] (in this case, the existing ext4 partition), allow me to [COLOR=Blue]format it[/COLOR], if needed, and then [COLOR=Blue]install Ubuntu 64bit[/COLOR].

Yes, it does give you.

In step 4 select Manual Partitioning, you always need to use that if using existing partitions. It will show list of the partitions.

Click on the root partition, then the button Change at bottom. Select use as ext4, or what the filesystem was earlier if you don't want to format. Tick or don't tick the format box, up to you. If you don't have data to keep I say format to wipe clean everything. Set mount point as /.

Click on the swap partition and make sure it's used as swap area.

That's it.

---

