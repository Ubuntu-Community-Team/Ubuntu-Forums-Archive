---
title: "Ubuntu 14.04 updating trouble and possible loss of data"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2015-04-16
Hi,

unfortunately this morning I deleted my /etc and /var folder and a lot of troubles began. So I decided to install a new ubuntu 14.04 from scratch, since I have the home folder in separate partition.
I installed the system and all worked well up to the moment I tried to add the old home folder to the new system. As described here [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) I typed

```

cd / && sudo mv /home /old_home && sudo mkdir /home

```
and then
```

mount -a

```
then
```

sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
gksu gedit /etc/fstab

```

but I cannot edit fstab since seems that my sudo password is wrong. Then I rebooted the system and now I'm not able to access my system. Moreover with a liveCD I cannot read some very important files in my home folder since they are recognized as Binary with content unreadable.

What can I do? I have lost a lot of very important data? Can you help me?

Edit:
If I try to access to those files from terminal I receive cannot access folder Permission denied
The strange thing is that some files and folders in this home are readable but are these less important

---

### Post by erotavlas on 2015-04-17
I'm very lucky, I was able to recover my data :)
I reinstalled the system again from scratch. Now, how can I add my old home folder to the system without making a new mistake?

Thank you

---

### Post by grahammechanical on 2015-04-17
If you have /home on a separate partition then when you install after selecting the partition for / and clicking Change and set up Use As and ticking format and setting a mount point of /, then do something similar with the partition you are using as home.

But this time do not tick to format and give it a mount point of /home.

Regards.

---

### Post by erotavlas on 2015-04-18
I solved by following extacly the standard guide of Ubuntu [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).

---

