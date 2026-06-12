---
title: "Installation in Unallocated Space"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by arfinator on 2006-09-23
I currently have Windows XP installed with very valuable data loaded, and I am trying to install ubuntu on the same disk.  I have used Partion Magic to free up 10 GB into unallocated space.

I am trying to manually choose where to install Ubuntu, but when I choose to install in the unallocated space via the manually edit partitions option, it shows me that I need like 20+ GB of space.  But when I go to the option to find the longest continuous space it gives me two partitions that are going to be formatted.
[LIST]
[*]partition #6 of /dev/hda as swap
[*]partition #3 of /dev/hda as ext3
[/LIST]

How can I force the installer to install in the unallocated space and not erase any of the data that is already on the disk?

Thank you to anyone who might be of help.
I love Ubuntu...

Hess Smith

---

### Post by koshari on 2006-09-23
what you want to do is manually create a swap and linux file system in the unpartitioned space,

---

### Post by koshari on 2006-09-23
oh and of course the "very valuable data" would be backed up of course wouldnt it.

---

### Post by arfinator on 2006-09-23
how would I go about doing what you said?  Should I do that in partition magic?

I tried doing in PM before, but it gave me an error.

Yes... The most important data is backed up to a slave drive.

---

### Post by Sef on 2006-09-23
> tried doing in PM before, but it gave me an error.


PM and Linux do not get along too well.  Best to use the partioner that comes on the install CD.  If you want a commercial partitioner then acronis or system commander are good.

---

