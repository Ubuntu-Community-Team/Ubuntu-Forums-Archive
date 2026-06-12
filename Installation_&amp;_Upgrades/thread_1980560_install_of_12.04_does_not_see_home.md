---
title: "install of 12.04 does not see /home"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2012-05-15
I had 10.04 74 vers installed with no problems. I tested 12.04 running from CD and every thing looked OK. I decided to do a clean install 64 GB versions I have done in the past and it fails to see my old /home files.
my disk set-up is as follows: 
/dev/sda1 Linux bootable mount / ext3 15 GB
/dev/sda22 Swap 3.9 GB
/dev/sda3 Linux 731GB Ext3 mount /home 

I did a clean install  formatting only sda1 and making 1 mount / and 3 mount /home

Linux came up but did not recognise my /home files.

I did this twice with the same results.

I reinstalled 10.04 (64 version) and after a lot of downloading of files my system is restored.

any ideas would be appreciated.

Tom Atkins

---

### Post by darkod on 2012-05-15
If you told /dev/sda3 to be used as /home it has to work. Make sure to select to be used as the same filesystem, if it was ext3 select ext3 again. That is very important. Otherwise, it will try to format it.

What could be an issue, is that you have to be aware that all users don't exist by default.

When doing the 12.04 clean install you are entering the first, main user, as usual. This user should be the same first user you created when installing 10.04. In that case, when you login as this user you should have the Home folder available, but only for this one.

After that, you create other users and specify where is their Home (otherwise a blank Home will be made) in terminal with:
```
sudo adduser --home /home/username username
```

In case it refuses to allow the new user permissions to the files, make it owner with:
```
sudo chown -R username:username /home/username
```

That should work.

---

### Post by Tom Atkins on 2012-05-15
I did specify Ext3 for both files. I just looked at my files and there was 0 in each folder. I also reinstalled all the users in the same order as under 10.04 and no one had any files.
When I went back to 10.04 each user had there old files back.

---

### Post by SeijiSensei on 2012-05-15
What is the contents of /etc/fstab on the 12.04 version?  When that version is running, what do you see when you type "mount"?

Are the filesystems in /etc/fstab mounted by UUID or by device name?  If the former, try replacing "UUID=string" with /dev/sda3.  Maybe a new UUID was generated that doesn't match the existing one.

---

### Post by Tom Atkins on 2012-05-15
I do not have the 12.04 version available. when I went back to 10.04 it was wiped out. I will try to reinstall it later, I live in FL and there are thunder storms in the area so I do not want to start a big job now.

Thanks for your help.

---

