---
title: "Install option takes eternity"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by pigbig842001 on 2007-07-31
Downloaded a copy of Ubuntu 7.04 i386. Burned a CD. Checked by md5sum. everything's OK.

Put the CD in drive. Boot. Chose the first option. Takes about 10 mins or so and shows ubuntu desktop.

Clicked install. Now, wait and wait and wait. Nothing seems to happen. Only the HDD (or system, whatever, the red indicator) led is lit and CD drive led is flickering. I waited for over two hrs but still there was no sign of installation window (installation window didn't appear at all).

Rebooted. Pressed F6. typed "live acpi=off". pressed enter. Ubuntu desktop shows. Now clicked on install. This time the installation window did appear but it wouldn't show the already available partitions on HDD. if I click next then, it shows that the entire HDD (40 GB) would be erased.

I purposely kept 4 GB empty for ubuntu by using acronis.

Help, is there any way to have a dual boot??? :(:confused:

---

### Post by Jussi01 on 2007-07-31
Hmm, there should be a bit just before where it tells you about the available partitions, it asks if you want guided or manual. you want manual, then you can play partition wise.

---

### Post by davidjmayo on 2007-07-31
most people recommend 10Gb for ubuntu + space for swap (2 x RAM or 1GB)

Can you make more space?

Maybe Xubuntu is an option but I never used it so don't know how space it will install in

---

### Post by pigbig842001 on 2007-07-31
> **Jussi01 said:**
> Hmm, there should be a bit just before where it tells you about the available partitions, it asks if you want guided or manual. you want manual, then you can play partition wise.
The problem is, install window only appears if at boot time I type "live acpi=off".

If I go with normal boot then install window doesn't appear at all and the system is damn busy, even the pointer doen't move at times.

---

### Post by pigbig842001 on 2007-08-02
Hey brothers, plz help me.

The problem is that, after clicking the install icon, the CD starts churning and system load led is lit all the way. even after waiting for two hrs there is no sign of the install window. Plz help

---

### Post by Pumalite on 2007-08-02
Post your specs.

---

### Post by mike102282 on 2007-08-02
> **pigbig842001 said:**
> Hey brothers, plz help me.

The problem is that, after clicking the install icon, the CD starts churning and system load led is lit all the way. even after waiting for two hrs there is no sign of the install window. Plz help

You might have a bad burn. Did you burn at the slowest speed?

---

### Post by Gremlinzzz on 2007-08-02
i create two partitions then i delete one of them to make it free space. put windows on the partiton and install ubuntu in free space.ubuntu does all the partitioning when you install this way.after windows is installed put your ubuntu live cd in after it boots up click installer when partition part otf the install comes up choose ///
Guide use largest continuous free space.'' then click next  till it starts installing and your done.that's all you do  there will be nothing to import or anything extra for you too do.

---

### Post by lisati on 2007-08-02
> **pigbig842001 said:**
> Hey brothers, plz help me.

The problem is that, after clicking the install icon, the CD starts churning and system load led is lit all the way. even after waiting for two hrs there is no sign of the install window. Plz help

I had a similar problem when first installing onto a laptop....I eventually gave up and tried the "alternate" CD and didn't have to wait so long. At a guess, with the benefit of browsing the forums over the last month or so, if it's the first time you're putting Ubuntu on your system using the partition manager to set up a swap partition might help....

---

### Post by pigbig842001 on 2007-08-02
> **Gremlinzzz said:**
> i create two partitions then i delete one of them to make it free space. put windows on the partiton and install ubuntu in free space.ubuntu does all the partitioning when you install this way.after windows is installed put your ubuntu live cd in after it boots up click installer when partition part otf the install comes up choose ///
Guide use largest continuous free space.'' then click next  till it starts installing and your done.that's all you do  there will be nothing to import or anything extra for you too do.
Look, this time I went with the 2nd option (safe mode-GUI, whatever) at boot time. The Ubuntu desktop appears with two icons. I clicked on the install icon. Within 20 seconds the install window appears (I was so happy, shortlived happiness).

Clicked on relevent options and buttons. Now, when I arrive at partition page, there are two options. One is **"Guided"** and the other is **"Manual"**.

**Clicked on guided**: it says that no user accounts to import or no operating system loaded (something similar to that which means that the hard-disk is empty).

**But, I would like to say that, my HDD has four partitions and I have kept one partition (4GB) for Ubuntu.**

**Clicked on manual**: it shows 40 GB unallocated space, the device being **/dev/sda**. selected the device and it says that entire drive will be erased, **Cancel or continue**.

To make sure that my drive has indeed 4 partitions, have a look at this:
went to terminal and typed **sudo fdisk -l**
here is the output:

Device         Boot      Start       End             Blocks      Id            System
/dev/sda1        *             1      653         5245191       7       HPFS/NTFS
/dev/sda2                   654    4865       33832890       5          Extended
/dev/sda4                 2235    2759         4217062       7        HPFS/NTFS
/dev/sda5                   654    2234       12699351       7        HPFS/NTFS
/dev/sda6                 2760     4865    16916413+      7        HPFS/NTFS

---

### Post by tadada on 2007-08-02
You should try the alternate CD. I used it didn't even try the Live CD. 
When down loading look for a checkbox that says click for alternate CD.  (only if you want to use the alternate)

---

### Post by pigbig842001 on 2007-08-03
> **Gremlinzzz said:**
> i create two partitions then i delete one of them to make it free space. put windows on the partiton and install ubuntu in free space.ubuntu does all the partitioning when you install this way.after windows is installed put your ubuntu live cd in after it boots up click installer when partition part otf the install comes up choose ///
Guide use largest continuous free space.'' then click next  till it starts installing and your done.that's all you do  there will be nothing to import or anything extra for you too do.
Hey bro,

I think this was the best thing u suggested. popped in the windows Xp CD and rebooted. At the install prompt, I deleted the partition that I intended to use for Ubuntu installation. As soon as that partiton was deleted, I rebooted with ubuntu cd. went for the second option at boot.

at desktop, clicked on install. the install window came up promptly. then, next... next... next. it was a breeze. arrived at partition page, voila, there are now 3 options. I selected manual option. got the deleted partition as unallocated space. partitioned it for swap and ext3.

everything's done and ubuntu is running merrily.

Thanx everybody. thanx ubuntu forum

---

### Post by pigbig842001 on 2007-08-03
Hi,

I would like to disturb u once again.

My problem is that, the only source of internet for me is GPRS. I use my Nokia 5200 to access internet. But I think there is nothing like **"Nokia PC Suite"** for linux. So, there is a problem of updating my copy of Ubuntu.

I have some of the links for updates. Is there any way I can install the updates after downloading it from somewhere and transferring it to my machine???

If so, please guide me and indicate the links if u have any.

I am a total newbie to linux and I am used to point-and-install (damn!!! couldn't be worse) applications (exe files). So,plz give me the detailed codes or anything in this regard so as to upgrade my copy of Ubuntu.

---

### Post by pigbig842001 on 2007-08-04
Plz help me out

---

