---
title: "Install 12.04 64-bit and keep /home partition (11.10 32-bit)"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by K3v|n on 2012-07-29
Hello,

I have 2 drives: The main one is used for the ubuntu 11.10 32-bit, the second one is used for /home. I was wondering if ubuntu 12.04 64-bit gives me an option during installation to keep /home partition so that all users can keep the same logins along with their data.

Thanks,

---

### Post by darkod on 2012-07-29
For that you need to use the manual install option (Something Else).

When the list of partitions shows up, select the root partition and click the Change button below. Then change the Use As from Not Used into the filesystem you want to use (for example ext4). Tick the format box, it allows allolder system files to be deleted. Select the mount point as /.
Then select the /home partition, in the Use As select the same filesystem as it has currently, DO NOT tick the format box, select mount point /home.

That's all you need to do. Make sure in the partitions list there is no tick mark meaning it will format the /home partition. Double check that before you continue.

During the install create the main, first user the same as the first user of the previous install.

After the installation is finished, you add the other users and specify their existing Home folders in terminal with:
sudo adduser --home /home/username username

That will detect the existing Home folders and use them.

---

### Post by K3v|n on 2012-07-29
Thanks darkod!
I have RAID 1 for the /home drive, hopefully manual installation will recognize the /home partition.

So for every user I have to do:
sudo adduser --home /home/username username

Can I just do?
sudo adduser --home /home/*

---

### Post by darkod on 2012-07-30
Whether it will recognize existing raid array doesn't depend on whether the install is manual or automatic. It depends on the raid type and the installer cd used.

If you are using fakeraid (board bios raid), the standard desktop live cd should be able to detect it. If it doesn't don't continue with the installation, exit immediately. The Alternate CD should detect fakeraid in almost all cases.

If you are using mdadm software raid, the live cd doesn't have the mdadm package so it will not see it. You would have to boot into live desktop first and add the package. The Alternate CD can recognize mdadm arrays by default.

The Alternate CD is recommended for raid so I suggest you use that regardless of the raid type.

As for adding the home folders/users, that's the only way I know, one by one. Even if you try to make some sort of automated command, you will still need to supply all usernames, right? I don't think it's worth the risk if things go wrong.

---

