---
title: "Installation almost done"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by tmon on 2011-01-03
Hi there, I'm sure this has been done numerous times although I have gone through the steps in the installation for the latest Ubuntu Desktop and once I get to the final screen (entering name and password etc) I can't go any further. The "forward" button is hidden and down the bottom it states "ready when you are" and that leads to script (which unfortunately I had no idea about).

Any ideas?

Thanks.

---

### Post by howefield on 2011-01-03
By "hidden", do you mean ghosted as in you can't press it ?

If so, check the username you have chosen, no capitals.

Or do you mean simply can't see it.

---

### Post by matt_symes on 2011-01-03
Hi

The user name can't contain spaces, cannot start with a number and must contain all lowercase characters. 

Try that.

Kind regards

---

### Post by tmon on 2011-01-03
Ah great, you're a champion! That was exactly what was wrong with it and such a quick reply. Knew this community was cool!

---

### Post by stargazergal62 on 2011-01-03
I am also having the same problem - install freezes during "Who are  you."  And, yes, I have been doing the same thing with the upper case  letter, so I will be sure to make it lower case.  Here's my question:  What is the best way to install Ubuntu  since it was interrupted in the middle of the install?  I am installing  it alongside of Windows 7.  When I get to allocating disk space, it  appears that Ubuntu is already installed, but I know that it did not  finish installing.  Any ideas?  Thanks so much for any help you can give  me.

---

### Post by matt_symes on 2011-01-04
Hi

If the installer has already repartitioned the hard drive but it did not install correctly then i would use the advanced install option on the partition page when installing from the LiveCD/USB.

This will allow you to select the partition, set it as the root point and format it.

Here is a basic guide but instead of selecting *add* to add a new partition, select *edit* to edit the existing Ubuntu partition (created by the last Ubuntu install) and set it's mount point as /. Also format it. The guide will give you a general idea of what the screen shots look like though

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Kind regards

---

### Post by xyepblra on 2011-01-04
I realize this thread might not be the best suitable place for my post, but to me it seems to be the best I could find.
For a year and a half I've been using my laptop in dual boot (Vist + Ubuntu). Few days ago I ran out of free disk space and thus decided to erase Vista. I installed Ubuntu 10.10 on the repartitioned hard drive and found out that I don't know how to use some 150 GB left after creating swap, / and /home. Can anybody instruct me on how to use this space for storing multimedia data and other stuff you usually put on volume D in Windows?
Here is the way my hard drive is partitioned:
/dev/sda1
         /dev/sda5         ext4         /
         /dev/sda6         ext4         /home
         /dev/sda7         linux-swap
         /dev/sda8         xfs          not mounted yet

---

### Post by matt_symes on 2011-01-04
Hi

> /dev/sda8 xfs not mounted yet

The best way to do this is to mount it at startup by adding an entry to fstab.

In the first instance open a terminal and type

```
sudo blkid
```

Enter your password. You will not see it echoed to the screen. This is normal. Post the output back here.

Kind regards

---

### Post by xyepblra on 2011-01-04
> **matt_symes said:**
> Hi
```
sudo blkid
```
Enter your password. You will not see it echoed to the screen. This is normal. Post the output back here.
Kind regards
Hello, Matt!
```
sudo blkid
/dev/sda5: UUID="48138949-5557-4660-ba46-3d729220914c" TYPE="ext4" 
/dev/sda6: UUID="cd589498-dfa9-463a-b5fb-f14a07e23541" TYPE="ext4" 
/dev/sda7: UUID="e6e6d040-0217-4a69-ae4e-72a322623ae1" TYPE="swap" 
/dev/sda8: LABEL="data" UUID="3e62277e-3eba-49aa-b095-f94fba60cf1f" TYPE="ext4"
```

---

### Post by matt_symes on 2011-01-04
Hi

Open a terminal and type

```
sudo mkdir /media/data
```

to create a new directory under media. Edit your fstab by pressing alt  F2 together and entering 

```
gksudo /etc/fstab
```

to edit your fstab file. At the end enter this line.

```
UUID=3e62277e-3eba-49aa-b095-f94fba60cf1f /media/data ext4 defaults 0 0
```

and save the file. Check the above by typing

```
sudo mount -a
```

to mount all the partitions in your fstab.

Kind regards

---

### Post by xyepblra on 2011-01-04
Thank you very much, Matt!
The only thing I dare add to what you said is that quotation marks are not required in UUID you write to /etc/fstab, and old label of partition we've been mounting with all operations described here has to be either commented out or erased completely.

---

### Post by matt_symes on 2011-01-05
Hi

Yes. The quotes were a copy and paste typo from your post (I copied the UUID of the result from the blkid command and forgot to remove the quotes). Sorry about that. I will edit my post.
But you get the general idea of how to edit your fstab.

Kind regards

---

### Post by stargazergal62 on 2011-01-05
Thanks so much for the help installing Ubuntu - it worked and I'm loving it!  However, when I boot up the computer, it gives me options as to what program I would like to open.  When I click on Windows 7, it takes me to Recovery and wants to reinstall factory specs.  I'm brand new to Linux and Ubuntu, so I'm lost as to what I need to do.  Any advice?

---

