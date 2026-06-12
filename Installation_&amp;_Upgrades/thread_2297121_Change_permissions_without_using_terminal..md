---
title: "Change permissions without using terminal."
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by hey2 on 2015-10-01
Hi.

I just made a clean install with the following partitions:

Swap
Ext4 /
Ext4 no mount point

i plugged in my Ntfs Back up hard drive and tried to copy data to the ext4 (no mount point) partition, but it doesn't let me.

Is there a way, without using the terminal, to make this work?

Before this clean install i had a windows xp and a partition for files and folders. I just deleted the windows xp and created the swap, / and everything worked. I could write and read the ntfs partition.

Since i wanted a completely clean hard drive i created a new partition table.

Please help.

I&#8217;m kinda getting frustrated :D

 Thanks

---

### Post by The Cog on 2015-10-01
> but it doesn't let me
In what way does it let you? Does it give an error message when you try?

---

### Post by hey2 on 2015-10-01
> **The Cog said:**
> In what way does it let you? Does it give an error message when you try?

Hi.

Thank for your reply.

i tries do copy something and the menu paste command was greyed out.

Then i tried to create a file or folder. The same. All greyed out.

I clicked on permission and it says I&#8217;m not the owner. The same happens on computer partition.

I though that when you crate a partition without a mount point it would be like connecting a external drive.

Once again thank you.

---

### Post by grahammechanical on 2015-10-01
First of all, there needs to be a folder on that partition. You may need to run File Manager (nautilus) with administrator prileledges to create that folder and that is what makes root the owner. But that is not really an issue. You need Create & Delete files permission and not just Access.

Again we can do this using the File Manager running with administrator priviledges.

1) Open the File Manager and browse to the partitition.
2) Select a folder and right click the folder.
3) Select Properties.
4) Open the Permissions tab and you will see

Owner = Root. Access = Create and Delete files
Group = root. Access = Create and Delete files
Others   Access

You need to change Access to Create and Delete files.

To run the File manager with administrator privileges run

```
sudo - H nautilus{/code]

You can also try

[code]gksudo nautilus{/code]

Ignore the error messages. But gksudo may not be installed so

[code]sudo apt-get install gksudo
```

Regards.

---

### Post by hey2 on 2015-10-01
> **grahammechanical said:**
> First of all, there needs to be a folder on that partition. You may need to run File Manager (nautilus) with administrator prileledges to create that folder and that is what makes root the owner. But that is not really an issue. You need Create & Delete files permission and not just Access.

Again we can do this using the File Manager running with administrator priviledges.

1) Open the File Manager and browse to the partitition.
2) Select a folder and right click the folder.
3) Select Properties.
4) Open the Permissions tab and you will see

Owner = Root. Access = Create and Delete files
Group = root. Access = Create and Delete files
Others   Access

You need to change Access to Create and Delete files.

To run the File manager with administrator privileges run

```
sudo - H nautilus{/code]

You can also try

[code]gksudo nautilus{/code]

Ignore the error messages. But gksudo may not be installed so

[code]sudo apt-get install gksudo
```

Regards.

Thank you very much for your detailed answer.

The partition doesn't have any folders in it (new partition). If i choose permissions on the entire drive instead of the folder will the result be the same?

Sudo -h nautilus is the same as sudo nautilus?

Why was this not needed when i had the ntfs partition?

Once again thank you very much for your time.

Hi.

I just tried the sudo -H nautilus command and it gave me an error. If i run with a pace beeetwin - and h i tells me that the command is not found.

It was somethig like it couldn't create a file.

I tried on my laptop before.

I just tried and now it display a message that the location could not be displayed.

I tried to change the permissions on the entire drive.

Hi.

I tried, but i couldn't do it. Bah.

I just tried a clean installation with:

- Swap
-Ext4 /
-Free space

After the installation ended, i used the gparted on the live usb to create a NTFS partition and it worked. I can write and read on the extra NTFS partition.

So i went and tried the same, but this time creating a Ext4 partition. It didn't work.

I opened the terminal and wrote " sudo nautilus"

After that, i clicked on the drive permissions, and on group, i clicked on my user name - create and delete files and others access - none.

This time it worked. i can write and read files.

Is this the right way? Is this safe? Would it be better to just create a NTFS partition?

---

### Post by yancek on 2015-10-01
If you want to access the partitions from a windows system, you will need a windows filesystem type such as ntfs or vfat since windows does not recognize and therefore cannot read or write to a Linux partition.  I'm not sure what you are doing but, if you are just using a Linux/Ubuntu operating system, ext4 should work.

---

### Post by hey2 on 2015-10-01
> **yancek said:**
> If you want to access the partitions from a windows system, you will need a windows filesystem type such as ntfs or vfat since windows does not recognize and therefore cannot read or write to a Linux partition.  I'm not sure what you are doing but, if you are just using a Linux/Ubuntu operating system, ext4 should work.

Hi.

I'm gonna use just Linux but i'm having so much trouble wit this permissions thing.

Do you know how to set it so that everyone who have a password can access it?

I just tried to put adm on group and if two are logged in, one gets a error message.

---

### Post by yancek on 2015-10-01
> I just tried to put adm on group and if two are logged in, one gets a error message. 		

You forgot to post the error message.

> Do you know how to set it so that everyone who have a password can access it?

Before you can access a partition, you need a mount point.  Ubuntu on newer releases has partitions accessible under /media/username.  If you log in as user A, you go to /media/A/ and should be able to access files.  If you had logged in as user B, you would be able to access them under /media/B and if when logged in as user B you tried to access /media/A you would be denied, you don't have permissions.

You could create another mount point under the /mnt directory.  If it is for your third partition, for the sake of simplicity just call it sda3 although you can name it whatever you wish.

sudo mkdir /mnt/sda3
sudo mount -t ext4 /dev/sda3 /mnt/sda3

The first command above creates the mount point, the second command mounts it  You would need to have an entry in the /etc/fstab directory for it to be available on mount and you could put all users in one group and give the group write permissions if that's what you want.

---

### Post by hey2 on 2015-10-02
> **yancek said:**
> You forgot to post the error message.



Before you can access a partition, you need a mount point.  Ubuntu on newer releases has partitions accessible under /media/username.  If you log in as user A, you go to /media/A/ and should be able to access files.  If you had logged in as user B, you would be able to access them under /media/B and if when logged in as user B you tried to access /media/A you would be denied, you don't have permissions.

You could create another mount point under the /mnt directory.  If it is for your third partition, for the sake of simplicity just call it sda3 although you can name it whatever you wish.

sudo mkdir /mnt/sda3
sudo mount -t ext4 /dev/sda3 /mnt/sda3

The first command above creates the mount point, the second command mounts it  You would need to have an entry in the /etc/fstab directory for it to be available on mount and you could put all users in one group and give the group write permissions if that's what you want.

Thank you very much for you time and for helping me.

Unfortunately i had to give up and i made a NTFS partition for my data.

The error was that i didn't have permission to access even though i put adm on the group. It must be because of what you explained above.

I was trying to avoid the terminal and I got scared that I would not be able to access or edit my data created on that partition.

After i created the NTFS I saw the permissions and it was like this:

Owner Me - Create and Delete Files

Group My user name None

Other Access None.

If I created a EXT4 Partition and edited the permission (sudo nautilus) to look like the NTFS, would it be the same as a external drive? Is it safe?

I don't remember to see the "me" option on the owner option. Is it the same as the user name?

Would it be possible to make a clean install and access everything the way a external drive does?

Thank you very much once again.

---

