---
title: "software has detected that the disk has at least 1 bad sector"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by PlayWithFire on 2011-08-20
This is a brand new Zotac MAG computer, on which I am trying to install OPENELEC. I tried using Ubuntu to re partition the drive, but getting an error "software has detected that the disk has at least 1 bad sector". I ran chkdsk, rebooted twice but that didn't help. I get the same error when I run the GParted Live CD. Should I return the computer and get it replaced or is there something else I can do?

---

### Post by tom4everitt on 2011-08-20
I would return it, it's no good with a broken hard drive. 

If you really don't want to do that, I guess you could try to only make a small partition somewhere - then maybe you would avoid the bad sectors if you're "lucky". 

But returning it is really only the sane option in my mind.

---

### Post by recluce on 2011-08-21
> **tom4everitt said:**
> I would return it, it's no good with a broken hard drive. 

If you really don't want to do that, I guess you could try to only make a small partition somewhere - then maybe you would avoid the bad sectors if you're "lucky". 

But returning it is really only the sane option in my mind.

+1

If you want to know more about the health of the drive, install smartmontools and do the following:

```

sudo smartctl --test=short /dev/sda

```

The program will return the time the test takes, usually about 2 minutes. After that time has elapsed:

```

sudo smartctl -a /dev/sda

```

Other test options are "long" (can take several hours) and "conveyance" (not supported by all drives).

I would bet than your drive gets failing results. On modern drives, you only see bad sectors after the drive's spare sectors are used up - which is an extremely bad sign!

---

### Post by PlayWithFire on 2011-08-21
Well, I managed to fix it by running [partition tool]("http://www.partition-tool.com/") under windows. That allowed me to resize the NTFS partition and create the partitions I needed. 

But, I guess I will RMA it.

---

### Post by PlayWithFire on 2011-08-21
I have a follow up question. 

Would it be a good idea for me to close the hard-drive and restore it on the new machine? I spent 2 days configuring everything, and I would really like to avoid doing it again. 

Is there any risk cloning a bad hard-drive like this?

---

### Post by recluce on 2011-08-22
> **PlayWithFire said:**
> I have a follow up question. 

Would it be a good idea for me to close the hard-drive and restore it on the new machine? I spent 2 days configuring everything, and I would really like to avoid doing it again. 

Is there any risk cloning a bad hard-drive like this?

There should be no problem. If you use Clonezilla, there is an option to clone even if there are errors. The worst that could happen is that, once you restore to the new system, the image won't work - at that point you would be no worse off than not having cloned the broken drive. If it works (most likely) you save 2 days. So what do you have to loose?

---

