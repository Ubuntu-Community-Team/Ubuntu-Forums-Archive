---
title: "Installing Ubuntu to a specific HDD partition (Dual boot)"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by Ian_Rucker on 2016-02-26
Hello! I want to install Ubuntu alongside my current OS (Windows 7) and I am having some problems. I wanted to install 100% of Ubuntu on a single logical partition (about 75GB) that I created on my HDD. However, as I was installing Ubuntu I clicked the option of 'Install Alongside Windows 7' thinking it would give me an option on where exactly I wanted the OS installed. However, it did not and Ubuntu was rather installed, as far as I can tell, all over my HDD. I guess my question would, is it even possible to install Ubuntu on a single logical partition of a hard drive and restrict it to that partition? And if so, how?

If it'll help, this is how my disks are configured:

Disk 0 (SSD): Primary partition 1 - C: (Used for OS)

Disk 1 (HDD): Primary partition 1 - E: (General file storage), primary partition 2 - B: (Used for certain backups), logical partition 1 - U: (where I want ubuntu installed)

What I want is to install Ubuntu on partition U: and only U: How would I go about doing this? I'm assuming I would have to use the 'Other' option when installing but it was confusing me a bit. Maybe someone could go through the steps for me.

Thanks!

---

### Post by v3.xx on 2016-02-26
Hi Ian

Easy way to install ubuntu to a certain partition is just make that partition free space (no file system). Then  during the install you will get the option to install ubuntu to the largest free space.

---

### Post by Dennis N on 2016-02-26
It is fairly easy to do. For maximum control, I use the "Something Else" option on the Ubuntu Installer's "Installation Type" screen.

For better analysis of this situation, I suggest you start a live Ubuntu session from USB install media, run the terminal command:
```
sudo parted -l
``` 
and post the output here. This will give an overview of the disk partitions from a Linux point of view instead of the C: E: U: designation which is Windows notation.

---

### Post by yancek on 2016-02-26
You should first familiarize yourself with Linux drive/partition naming conventions.  You won't see any C drive in Linux.  I would suggest you read the tutorial at the link below from the top.  Scroll about half way down the page and you will see a detailed tutorial on dual boot installs.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

