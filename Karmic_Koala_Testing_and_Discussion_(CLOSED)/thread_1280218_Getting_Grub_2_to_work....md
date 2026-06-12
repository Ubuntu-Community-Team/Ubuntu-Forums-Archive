---
title: "Getting Grub 2 to work..."
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-10-01
Newbie here, 

I've been on Alpha 6 and I did update last night (not sure if its updated to Beta or not), but I would like to know how to get grub 2 to be the default loader.

Thanks.

---

### Post by cariboo on 2009-10-01
If you upgraded from an earlier version, you will have to install grub2.

---

### Post by ranch hand on 2009-10-02
> **bridgetothesun said:**
> Newbie here, 

I've been on Alpha 6 and I did update last night (not sure if its updated to Beta or not), but I would like to know how to get grub 2 to be the default loader.

Thanks.
I am assuming that you have grub2, if not go to synaptic, click on search, enter grub2, I think you need 3 packages.

To make it your boot/root;
Boot into the 9.10 OS
Open your terminal.
Run;
```

sudo update-grub

AND

sudo grub-install /dev/<your drive>

```
In my case, for instance, I have 2 drives for testing 64bit.  All the root partitions are on sda and the home partitions on sdb.  I boot from one OS and have a very nice custom menu setup there.  When I install something else, I need to change back to that OS.

I boot into it and run "sudo grub-install /dev/sda" and that is it, I am done.

FUN

---

