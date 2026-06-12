---
title: "About backup the complete SSD hard-drive"
date: 2022-07-21
forum: Installation &amp; Upgrades
---

### Post by satimis on 2022-07-21
Hi all,

About backup the complete SSD hard-drive

SSD 500G
Ubuntu 20.04 desktop
KVM/QEMU

Free space 104G

$df -h ```

/dev/sdc2       457G  330G  104G  77% /
tmpfs            15G  364M   15G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            15G     0   15G   0% /sys/fs/cgroup
.....
...

```

I'm prepared to follow below tutorial to backup the whole disk;

Ubuntu 20.04 System Backup and Restore
[https://linuxconfig.org/ubuntu-20-04-system-backup-and-restore](https://linuxconfig.org/ubuntu-20-04-system-backup-and-restore)
Create and restore backup by using the Timeshift’s command line

timeshift is on repo
$ apt policy timeshift```

timeshift:
  Installed: (none)
  Candidate: 20.03+ds-2
  Version table:
     20.03+ds-2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

Will the backup include KVM/QEMU and all their guests ?

Please advise.  Thanks.

Remark: After its backup I'll upgrade it to Ubuntu 22.04 desktop.  I'll start another posting about the steps

Regards

---

### Post by TheFu on 2022-07-21
If you want to backup virtual machines from outside the VM, then you'll need to 100% quiesce those VMs. They cannot be running, unless you take steps using an enterprise volume manager, say LVM, to create a snapshot of the VM storage.  Actually, if you want to backup any system completely, the storage needs to be 100% quiesced.  Leaving the VMs running won't be good.

I treat each of my VMs like they are physical servers and backup each in that manner.  I used to backup file-based VMs from the VM host, but soon those huge files were taking hours to backup each, which was unacceptable.  I had to find a better solution.  That better solution can backup all the VMs in about 2 hrs total, not 14 hours like before.

But you should do what works for you. I have doubts about timeshift, since they recommend using another backup too.  I've always been confused as to why anyone would want to spend the time learning more than 1 backup method, but people do.  OTOH, I've attempted many times to help people here use my backup method and only intermediate level to experts seem to be capable of implementing it successfully.

Don't trust it until you've performed the backup AND performed all the different sorts of restores you may need.  Never trust any backup methodology until you've tested the restore yourself.

BTW, an SSD storage device is completely unimportant to backup+restore methods. That doesn't matter.

---

### Post by ActionParsnip on 2022-07-21
I'd shutdown the VM to sort the disks out, then make an image of the server and archive that as you like

---

### Post by satimis on 2022-07-22
Hi all,

Thanks for your advice.

I'm preparing upgrade Ubuntu 20.04 desktop to Ubuntu 22.04 2 weeks later when the official upgrade will be available.

This PC:
1. SSD hard-drive 1TB, solely running Ubuntu 20.04 desktop as OS, 90.2 GB free space available
2. The hard-drive for data storage is a WD 4TB drive, 2.9TB free space available.

All VM images are on "VirtualBox VM" folder on the OS hard-drive.

Please advise what will be the Ubuntu way to backup the OS?  I won't start VirtualBox.

Thanks

Regards

---

### Post by TheFu on 2022-07-22
If you are using virtualbox, yuck, then I'd use the built-in "Export VM" feature. I think that creates 2 files for each VM. Copy those off.

If you want daily, versioned, backups, without downtime then you'll need a better method.

---

### Post by satimis on 2022-07-22
> **TheFu said:**
> If you are using virtualbox, yuck, then I'd use the built-in "Export VM" feature. I think that creates 2 files for each VM. Copy those off.
Thanks for your advice.

What I did in the past, I just copied the entire "VirtualBox VM" folder to the storage hard-drive.  In case of problem I just reinstalled the problematic VM from its image on that folder.  It never failed.  

I only use "Export VM" feature exporting a VM to another PC running VirtualBox.  Also I can copy its image folder from "VirtualBox VM" folder to another PC and install the VM there.  It works the same.

> 
If you want daily, versioned, backups, without downtime then you'll need a better method.
Yes, I'm considering to run periodical backup of the entire hard-drive.  I wonder whether "timeshift" will help?

Regards

---

