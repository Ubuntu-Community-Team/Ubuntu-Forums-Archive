---
title: "Need to remove it low on disk space"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by NoSuchDevice on 2010-12-26
OK so I have installed a lot of PC software (3Ds Max / Mudbox / Visual studio. Just programs which require high powered computers) 

Now I need to get rid of linux from this pc cause I am running out of space. So How do I do this? 

Thanks in advance.

---

### Post by dabl on 2010-12-26
You need be cautious -- you didn't say what the other OS is. If it is Windows 7, you might want to try using the Windows partitioning tool to delete the Linux partition(s), then expand the Windows partition.

GParted, running from a booted Live CD, can certainly delete the Linux partition(s), but the question is, how will the other OS deal with the changed partition table? It could get ugly. A safer approach might be to simply shrink the Linux partitions down to tiny size, and leave them, so the number of partitions remains the same afterward.

Take seriously the warning to back up your user data first, before twiddling the partitions.  ;)

---

### Post by NoSuchDevice on 2010-12-26
I am on Windows Vista Home Premium. (32bit) Now I did have that idea of removing the Linux partition from windows, but what will happen to the boot menu it will go right? My data is OK it backs up to a external HDD.

---

### Post by dabl on 2010-12-26
Right -- Grub will be left pointing to empty space.  Probably you'll need to run the "fixmbr" routine from the Windows installation CD.

---

### Post by NoSuchDevice on 2010-12-27
Is there a tutorial somewhere on how to uninstall Linux I have already killed my computer once don't wanna' do it again. 

Thanks

---

### Post by dino99 on 2010-12-27
not that hard: format the ubuntu partition, that it.

---

### Post by ottosykora on 2010-12-27
@dino99

>not that hard: format the ubuntu partition, that it.<

and then? what will he do with the grub pointing to nowhere, looking for its files? They are in that partition, if simply formated, no boot possible anymore. Only 512byte of grub are in the MBR, the rest is in the linux partition. If formated, it is lost.
Restore disk of vista might be then the only help.

---

