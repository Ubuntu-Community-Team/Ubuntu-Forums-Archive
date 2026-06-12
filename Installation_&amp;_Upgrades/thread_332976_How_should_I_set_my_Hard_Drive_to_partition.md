---
title: "How should I set my Hard Drive to partition?"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Luigi239 on 2007-01-06
[IMG]http://img523.imageshack.us/img523/3493/screenshotqh1.png[/IMG]

I am going to install on an external usb hard drive. This is my first Linux installation, so I am abit nervous.

I set the 20gb of free space for Ubuntu. My question is, what option should I select at the install screen for partitoning? I don't mind manually editing the partitans if I need to, and not deleting the other partitans would be nice, but I can if needed.

Thanks. :)

---

### Post by xiaoxin on 2007-01-06
Just tell it to use the unpartitioned space

---

### Post by finer recliner on 2007-01-06
create a partition of linux-swap space approx double the size of your physical memory (RAM). map to it when asked

format the rest of you unallocated space to ext3 and map root (/) to it when asked

---

### Post by Luigi239 on 2007-01-06
> **finer recliner said:**
> create a partition of linux-swap space approx double the size of your physical memory (RAM). map to it when asked

format the rest of you unallocated space to ext3 and map root (/) to it when asked

Er...you lost me.

That would mean taking everthing off the drive though wouldn't it?

---

### Post by imonlyhuman on 2007-01-06
> **Luigi239 said:**
> Er...you lost me.

That would mean taking everthing off the drive though wouldn't it?

No, it would actually just format the blank, unformatted space on your disk.
You format your linux partition, after you resize your windows, partition.

Word of advice, you should backup your files, sometimes, rarely, but sometimes, it can cause data loss.  Also, defragmenting, you disk makes partition faster.

---

### Post by Luigi239 on 2007-01-06
> **imonlyhuman said:**
> No, it would actually just format the blank, unformatted space on your disk.
You format your linux partition, after you resize your windows, partition.

Word of advice, you should backup your files, sometimes, rarely, but sometimes, it can cause data loss.  Also, defragmenting, you disk makes partition faster.

Oh, Ok, thanks.

Will I still need to back the Data on the internal HD as well, even though Im installing from the external? (this drive is my backup drive)

---

