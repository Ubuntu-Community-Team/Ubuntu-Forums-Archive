---
title: "grub-install fatal /dev/sda hardware software 11.04"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by danh-a on 2011-05-26
I bought a Hitachi disk drive and put it in my dell inspiron 530 and attempted to install ubuntu 11.04 on the new drive.

My procedure was to boot into the live cd, then click on the install ubuntu icon.

For partitioning, i attempted to make 4 partitions, because i intend to install some other oses on these.

During the install, an alert came up that said:
   Executing 'grub-install /dev/sda' failed.
   This is a fatal error.

Does this indicate some problem with the drive (e.g., the first few blocks cannot be written on)?

Or is there a software-only explanation?

I can get an xterm on the desktop to look around at logs, but don't really know where to look or what to look for.

Thanks in advance for any info or suggestions!

dan

---

### Post by Hedgehog1 on 2011-05-27
You would likely be best served if you made you partitions manually using Gparted from the LiveCD/LiveUSB.

Depending on the other OS's you plan to load, you partition plan will vary.

If you are not expecting to load Windows in the future on this drive, then things are easier.

Might I suggest you establish a basic plan and set that up on the drive manually?

You may also need to create a partition table on the drive.

You can do that using gparted by doing this:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-27
These are a simple example of a 3 partition Ubuntu only install. Your own install will likely be more complex, but it gives you a feel for the steps involved when using gparted:

B]Then begin creating 3 partitions for '/' (root) '/home' & Swap:[/B]

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

***The Hedge***

---

### Post by danh-a on 2011-05-27
Thank you The Hedge.

sudo /usr/sbin/gparted
works very smoothly and is more self-explanatory than the partitioner built into the installer.

I still have the problem with grub-install, however.

After running gparted, i tried to manually run grub-install, by
sudo grub-install /dev/sda

It failed with status 1 and the message:
/usr/sbin/grub-probe: error: cannot stat `aufs'.

So i'm not sure if this is a matter of something wrong with the front of the disk, or maybe i just don't know where to put grub.

My ultimate goal is to be able to boot several different oses using grub.

(None will be windows, but just other free systems.)

So --- is /dev/sda (the only drive in the system, at least for now) the right place to put grub, or should grub go within a partition?  (But no matter what, it has to write the master boot record somehow doesn't it?)

Thanks in advance for any info.

dan

---

### Post by Hedgehog1 on 2011-05-27
As I do not know which partition is your '/' (root) partition, I am going to guess that it is partition /dev/sda1.  This is the partition that contains the '/boot' directory where you grub setups go.

Grub has two parts, the small part that is written on to the MBR, and the larger part that is store in the '/boot' directory.

If you are manually installing/reinstalling grub from your LiveCD, the commands would look like this (this assumes your root drive is /dev/sda**1**)

```
sudo mount /dev/sda**1** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```


***The Hedge***

:KS

---

