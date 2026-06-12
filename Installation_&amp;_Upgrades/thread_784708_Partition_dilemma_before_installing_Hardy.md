---
title: "Partition dilemma before installing Hardy"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by rbarra on 2008-05-06
Hello everyone,

I believe I'm ready to install Hardy Heron. Now I have Gutsy in my notebook, together with Windows. I decided to use GParted to take off some space from the windows partition and give it to Ubuntu.

The result [can be seen here]("http://flickr.com/photos/ricardobarra/2468992211/"). I'd like to know if I am ready for a "clean" installation of Hardy, that means **without upgrading from Gutsy**. I've got Hardy's cd for that purpose.

If you see [the screenshot]("http://flickr.com/photos/ricardobarra/2468992211/"), I have the Windows partition (29 Gb); Swap partition (2 Gb); Ubuntu's files anda data (65 Gb); and one partition for the Ubuntu operating system (14 Gb). With this last one I have a question: is it necessary to have that or could I just leave the windows partition, swap and just one for Ubuntu? What do you recommend?

Thanks in advance and regards from Chile.

---

### Post by Pumalite on 2008-05-06
You can install on top of Gutsy. Go Manual and choose the old partitions. Ignore /swap. Are you able to boot Windows now? According to your screnshot, you have Windows in a logical partition, inside an extended one. Windows needs a primary partition.

---

### Post by rbarra on 2008-05-07
Hello Pumalite,

When you say "choose the old partitions", are you talking about the 65 Gb and the 14 Gb partitions?

Should they stay with the same amount of Gb each one? I mean, there is no change at all, right?

In my screenshot I don't see any extended partition. Windows is in the partition that says "boot" under the "flags" column.

Thank you.

---

### Post by aquavitae on 2008-05-07
Assuming you want to keey everything in your home partition (sda3), choose sda2 to install to, then set the mount point for sda3 to your home directory. If you're asking whether to remove sda2 and just use sda3, I'd say not. Its usefull keeping your docs separate from the os so that you can reinstall without having to do huge backups.

The size of the partitions look fine.

Windows is not in a logial partition, it just looks a bit like it is at first glance because of the green border - a lot of partition editors show extended partitions by changing the border colour.

---

### Post by rbarra on 2008-05-08
Well my friends,

Thank you very much for your answers. Finally tomorrow I will have time to install Hardy Heron.

I'll be back if I run into any problems. Bytes!

---

### Post by Pumalite on 2008-05-08
Saludos al San Cristobal.

---

### Post by rbarra on 2008-05-08
> **Pumalite said:**
> Saludos al San Cristobal.

Jaja, perfecto!

---

### Post by rbarra on 2008-05-14
Hi,

Just to let you know that I finally installed Hardy Heron without any problems. My notebook is running very fast and stable. 

Thanks for your help!!

---

### Post by Pumalite on 2008-05-14
Good luck.

---

