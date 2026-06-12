---
title: "Updating problems..."
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by jiryan2316 on 2016-07-07
SO...

I loaded Ubuntu onto my son's old laptop and it's great, but every time i have it try to update, it tells me

**FAILED TO DOWNLOAD REPOSITORY INFORMATION**
             check your internet connection

but, if I didn't have an internet connection, I couldn't post on forums, and the icon in the upper right corner has 4 full waves.

Help.

James Ryan

---

### Post by jiryan2316 on 2016-07-07
I also get it telling me I don't have enough disk space, in /boot, but I have like 241 GB free...

---

### Post by grahammechanical on 2016-07-07
What version of Ubuntu? We need to make sure that you installed a version that is still getting support. Versions that have reached end of life have their repositories closed and any attempt to update or install software will give out that message.

You should run this command and post the output in this thread in between quote tags


```
sudo apt-get update
```


Also if you install Ubuntu and choose to have LVM or an encrypted driver then the installer would have created a boot partition to put the Linux kernels in. We do not know how long this installation has been in place. After a time kernel upgrades will fill up the boot partition and then we get into a situation of a kernel upgrade failing to complete. And that causes problems with updating.

If this is the situation then open a terminal and run

```
sudo apt-get autoremove
```

Regards.

---

### Post by kansasnoob on 2016-07-08
> **jiryan2316 said:**
> I also get it telling me I don't have enough disk space, in /boot, but I have like 241 GB free...

We should also probably see the output of:

```
df -H
```

---

