---
title: "changing permissions on my new Raid1 aray"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by stuckeyneila1982 on 2013-02-17
I have almost got my ubuntu server setup the way i want.  But i noticed that i cannot change permissions of my mdadm Raid1 by right clicking and properties.  Is this a known issue in 12.10 ?  Could someone post how to change the permisions of my disk at /media/neil/Raid1 .  Please and thank you.

---

### Post by MrKaliman on 2013-02-17
Can you change it using CLI?

sudo chmod ... /path/of/array

---

### Post by stuckeyneila1982 on 2013-02-17
keeps saying missing operand i tried sudo chmod -r +rwo /media/neil/Raid1

---

### Post by SaturnusDJ on 2013-02-18
You want to apply the command recursive? Then use -R, not -r.

And you want read/write access for the owner of the files?
That's: u+rw.

```
sudo chmod -R u+rw /media/neil/Raid1
```
If you're not the owner you might want to become it using chown or apply read/write to everyone.

Most of the time I use the numeric/octal way of chmod.
It's easier for basic operations. Check out: [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by stuckeyneila1982 on 2013-02-18
so would the chown command be sudo chown neil:users /media/neil/Raid1 ?

---

### Post by stuckeyneila1982 on 2013-02-18
also why is my raid in media/neil/Raid1 ?  shouldn't it be in the basic filesystem area like my ubuntu install hdd sdc1 ?

---

### Post by darkod on 2013-02-18
> **stuckeyneila1982 said:**
> also why is my raid in media/neil/Raid1 ?  shouldn't it be in the basic filesystem area like my ubuntu install hdd sdc1 ?

How are you opening it? All partitions are recognized but only the ones in /etc/fstab are mounted on boot.

By clicking a partition that is not mounted, it mounts in /media.

You can create any mount point you want, and create a corresponding entry in /etc/fstab so that the raid device mounts there on boot.

Can you post the output of:
```
cat /etc/fstab
```

---

### Post by stuckeyneila1982 on 2013-02-19
results of cat /etc/fstab


neil@server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0103df44-2e31-4dbc-a1ce-b531d2e85209 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6598f0b3-04a3-4f9a-bb01-7eb1de475c4f none            swap    sw              0       0
neil@server:~$

---

### Post by darkod on 2013-02-20
You are not mounting it automatically, that's why it mounts in /media.

Choose a mount point suitable for you, for example /data. Is that good, is this a data array?

Also, post the output of:
sudo blkid

so we can provide exact entry format to put in fstab.

---

### Post by stuckeyneila1982 on 2013-02-20
neil@server:~$ sudo blkid
[sudo] password for neil: 
/dev/sdb1: UUID="989aeeb3-879e-1ee8-9adc-1f7bf460d296" UUID_SUB="79e59c1f-6342-0b76-f3f1-e39ade08c0da" LABEL="server:0" TYPE="linux_raid_member" 
/dev/sda1: UUID="989aeeb3-879e-1ee8-9adc-1f7bf460d296" UUID_SUB="496b077d-bc43-22c2-3b28-452b5b706a71" LABEL="server:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="0103df44-2e31-4dbc-a1ce-b531d2e85209" TYPE="ext4" 
/dev/sdc5: UUID="6598f0b3-04a3-4f9a-bb01-7eb1de475c4f" TYPE="swap" 
/dev/md127: LABEL="Raid1" UUID="eb7db817-cb3b-4343-8e45-a9d27af8f9de" TYPE="ext4"

---

### Post by darkod on 2013-02-21
If you want to mount it at /data for example, you need to create it first.
sudo mkdir /data

Then in /etc/fstab create a line like:
```
UUID=<string without the quotes>   /data   ext4   defaults   0   2
```

You have the raid UUID in the blkid output. Use the string only without the quotes. That should mount it on every boot at /data.

---

### Post by stuckeyneila1982 on 2013-02-23
Nice to see you again darkod.  I have the raid working i created a share i can see it in Win7 i can enter the directory but cannot add files or create directories. I have tried some chown and chmod commands but cant get it to work.  keeps saying destination folder access denied. By the way i re installed ubuntu with server edition as i did not like how my ram was almost gone on the desktop version.  all is good execpt the permissions errors in windows.  if i share a folder in non-raid it works fine no probs.  so obviosly i need some permission changes just not sure what to do.

---

### Post by darkod on 2013-02-23
In linux you have to think about the actual folder permissions too. Also, is the samba security option set to share or user in the global section?

If security = user you will need the user/password to be created on the ubuntu server both as linux user and samba user.

If you want access to all, it's best to set security = share.

But even in that case the actual linux permissions on the folder might be denying access. To set read/write access to all on specific folder, you can use:
```
sudo chmod a+rw /path/folder
```

That will sort it out from linux filesystem point of view. I think after that you can still control it with the samba options if you use security = user, you will have to specify which users are allowed to access each share, and those users/passwords will have to exist.

---

