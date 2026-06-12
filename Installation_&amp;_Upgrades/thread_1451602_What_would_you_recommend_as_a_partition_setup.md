---
title: "What would you recommend as a partition setup?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by pra5508 on 2010-04-10
Hi,
   Am very sorry if this has already been asked here, however I am a newbee and am not too sure, but anyway, here it goes. What would you recommend as a partition setup for a laptop  with 1gb ram and 160gb hdd? Please note, the setup needs to be able to keep all documents, settings and programs on updates and whatnot.
I really hope someone can help me here.
Newty.

---

### Post by emanuel.b on 2010-04-10
Are you asking what kind of file system you should use?

---

### Post by wojox on 2010-04-10
Will you be dual booting at all?

---

### Post by oldfred on 2010-04-10
A lot depends on what you are doing.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by pra5508 on 2010-04-10
> **wojox said:**
> Will you be dual booting at all?

Hi.
   No, shall not be dual booting, and if I do, shall only be between different versions of linux.
Update for others, am wishing to replace my current version of 9.10 with the same version, as I cannot boot the current version, am not sure why, however this is the least of my worries. The issue is that next month when the update comes out, I shall near enough have to go through this same monotonous process, which takes several hours each time, then takes another day to get all near enough back to what it was, as all the apps have to be reinstalled and so on, and I'd just love a way of partitioning my hdd so as it would retain all my data and apps, and just update the version of the os.
Also, thanks to oldfred for the links, these seem very useful to me.
Hope this update helps, and I hope someone can help.
Newty.

---

### Post by emanuel.b on 2010-04-10
Then you should just use the default Ubuntu installation settings...

---

### Post by wojox on 2010-04-10
If you want /swap / and /home follow this guide: [http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

---

### Post by pra5508 on 2010-04-10
> **wojox said:**
> If you want /swap / and /home follow this guide: [http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)
Hi,
   Thanks for that. Would I need to just have a /home, or would I need to add more partitions to ensure that I kept all my documents and programs and whatnot?
Paul.

---

### Post by wojox on 2010-04-10
That guide is for using the Manual partition option. So you would need to have a /swap / and /home. If you just want the easy route then go with what Emanuel .B suggested. I use default all the time now and keep good backups.

---

### Post by pra5508 on 2010-04-10
> **wojox said:**
> That guide is for using the Manual partition option. So you would need to have a /swap / and /home. If you just want the easy route then go with what Emanuel .B suggested. I use default all the time now and keep good backups.
Thanks. Would I also need partitions such as /usr, or /tmp stored as another separate partition so as I can keep all programs upon update? Sorry, it's just that I sadly don't understand the use of all the different partitions, and what each section within / actually does.

---

### Post by SnickerSnack on 2010-04-10
Hi,

The main reason I see to keep different system directories in separate partitions is control their hard disk usage better.  For example, on a webserver, you should have /var on its own partition since that is where logs are kept, and you don't want log files to fill the root partition.  I suppose that someone could intentionally cause problems for your server if have everything in one partition.  I don't know if there are other big reasons.

The main reason I am posting is to say that when I partitioned the drive on my laptop, I knew that I might want to try a few different linux distros, so I have three 15 GB partitions.  One holds ubuntu 32 bit, and the other two are empty for now.  So, since you mentioned "dual booting" with other types of linux, I'd recommend having a few other empty partitions.  You can, of course, use the same /home partition for each.  And on that point, I made a separate partition for /home so that it would be easy to have more than one distro and to wipe one or another if I decide I don't like it.

As someone said earlier, you should have at minimum, /, /swap, and /home.  If this is just for a personal use computer, then that is all you need.

---

### Post by oldfred on 2010-04-10
If /home is separate it saves all your settings.

You can export all your installed apps and reimport them, I periodically export my current list and include the text file in my backups :

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by Herman on 2010-04-10
:) In my opinion, simplicity is bliss.

I like my operating system to be all in one partition,  I even use a swap file instead of a separate swap area. 

The entire thing can be backed up with a single dd command and restored again with with another dd command.

It's advisable to store your backups on some other disk, in case your hard disk fails. Hard disks can fail suddenly, they don't always give any warning, and you can't always recover your data either. You need at least two backups of your data on at least one other media. 

I always keep my data backed up separately from the operating system image files so I can access it easier and the dd command works faster when it doesn't have users files to copy backwards and forwards. :)

---

### Post by pra5508 on 2010-06-22
Thanks everyone... Just the help I needed. have now got my laptop running a 20gb / for main distro, and 2 spare 5gb partitions for other tests, along with 2gb /swap and the rest set for /home use. Also seems to run a heck of a lot faster as well...:lolflag:

---

