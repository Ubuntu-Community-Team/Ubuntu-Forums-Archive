---
title: "Data lost in home directory after upgrading"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by drahul82 on 2016-02-08
Hi,
I recently upgraded my ubuntu from 10.04 to 14.04. There were two user accounts: ionadmin and ionuser. ionadmin was root account. There were directories under /home/ionadmin, e.g. /home/ionadmin/yyy. After the upgrade, the directories in /home/ionadmin are no longer present. Could anyone please tell me if it is possible to retrieve these data? I had important data in these directories.
Thanks,
Rahul

---

### Post by grahammechanical on 2016-02-08
In Ubuntu the root account is disabled. We are not supposed to activate it. If you have activated the root account then the upgrade would not recognise it. That is my guess. It is also possible that the folders and files are still there. You can try running the file manager with administrator privileges by using this command

```
sudo - H nautilus
```

Now you might be able to see those folders and files in what is actually another user account. You took a big risk upgrading from 10.04 through 12.04 to 14.04 without backing up that important data. I hope you did not upgrade by doing a fresh install of 14.04 over the 10.04 partition? If you did, did you tick to format the partition? If you did tick to format the partition then we are in a completely different universe of data recovery.

Regards.

---

### Post by drahul82 on 2016-02-10
Thanks a lot for your response. I think, the technician formatted the partition. This is his response: "but all of the operating system information to include the home directories is formatted and replaced with the new OS". Do you have any suggestions on any possible ways to recover the data in this case?

Regards,
Rahul

---

### Post by deadflowr on 2016-02-10
Grab a livecd and try something like testdisk.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If at all possible, if you do not have livecd, try downloading one from a different machine.
You want to limit your access or usage to the messed-up system as much as possible.
To avoid ever writing to the disk. 
Every time you write to the disk, it becomes that much harder to recover.

If that makes snese, or helps...

---

### Post by furtom on 2016-02-10
Well, if the partition with root was formatted, then Ubuntu was not *upgraded*, but rather deleted and a newer version was installed.

What I suspect happened is simple: If you created a root account, that home directory would NOT be in /home, but rather in /root. I think your IT guy formatted / but not the separate /home partition. That's why your regular user files were not deleted but your admin account was.

Sadly, it will be difficult if not impossible to recover those files as they have probably been overwritten with the new instillation.

---

### Post by matt_symes on 2016-02-10
Hi

> I think, the technician formatted the partition.

Do yourself a favour in the future.

Don't use that "technician" as, if they didn't make a back up of your data for you before upgrading, they are in no way a technician.

Make sure a backup has been taken of the *entire* system before upgrading otherwise don't let anyone upgrade it.

deadflowr suggested teskdisk. That's my suggestion also and good luck. I hope you can retrieve your important files.

Kind regards

---

### Post by drahul82 on 2016-02-10
Thanks all for your responses. Just to provide you all an idea:
Filesystem           Size  Used Avail Use% Mounted on
/dev/mapper/os-root   46G   20G   24G  46% /
none                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  63G  4.0K   63G   1% /dev
tmpfs                 13G  1.4M   13G   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                  63G     0   63G   0% /run/shm
none                 100M     0  100M   0% /run/user
/dev/sdb1            9.7T  7.2T  2.0T  79% /results
/dev/sdb2             15T   12T  2.8T  81% /rawdata
/dev/sdc1             37T   31T  5.9T  84% /mnt/Despina
/dev/mapper/os-home   19G   45M   18G   1% /home
/dev/mapper/os-tmp    92G   60M   87G   1% /tmp
/dev/mapper/os-var    19G  4.4G   13G  26% /var

there were three directories for three different users under /home. One of them was ionadmin which also has root access. My directories were under /home/ionadmin. It seems to be that /home got formatted during the upgrade.

---

### Post by drahul82 on 2016-02-11
Well, I tried TestDisk last night. It only shows those files or directories that were deleted after the upgrade was performed. This means that it will be impossible to retrieve the data that were deleted due to formatting the partition during the OS install. Thanks everyone for your suggestions!

---

### Post by matt_symes on 2016-02-11
Hi

> **drahul82 said:**
> Well, I tried TestDisk last night. It only shows those files or directories that were deleted after the upgrade was performed. This means that it will be impossible to retrieve the data that were deleted due to formatting the partition during the OS install. Thanks everyone for your suggestions!

Unfortunately i expected that might be the case.

A formatted partition will have lost the files in it unless you use a professional service.

Kind regards

---

