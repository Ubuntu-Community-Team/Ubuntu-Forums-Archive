---
title: "Installing Windows 7 on Ubuntu (Help me)"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by evelynx0x0 on 2012-09-02
Unfortunately Ubuntu isn't right for me as it is too complicated and overwhelming for me to use. 
I am trying to reinstall Windows on my Ubuntu PC, however I am unable to do so because of the following error: 

''Windows was unable to create a required installion folder. Error code: 0x8007007A''

I am running Wine to run setup.exe. I am using a USB to install Windows while Ubuntu is online (Not booting from a USB) 

Please help. Thank you for reading, 
Evelyn ):P

---

### Post by opensshd on 2012-09-02
You'll need to boot from windows installation media to install windows.

---

### Post by oldfred on 2012-09-02
In addition, Windows will not see Linux partitions. It need free unallocated space and an available primary partition or a primary partition formatted NTFS with the boot flag.

---

### Post by Mark Phelps on 2012-09-03
You can't install Windows using Wine; as already mentioned, you'll need to boot directly from the USB.

But first, you'll need to remove the Linux filesystem because the Windows installer can't make sense of that.

To do that, you'll need a Linux utility. You can build a bootable USB of either Ubuntu, or GParted -- instructions are at both websites.

---

### Post by Mark Phelps on 2012-09-04
evelyn:  boot from the media you used to install Ubuntu but select the option  to Try Ubuntu.  That will put you into LiveCD/LiveUSB mode.

Then, click on the dash icon on the upper left and enter gparted in the search box. Select Gnome Partition Editor -- and use it to remove the Linux partitions from the PC.

When done, reboot using your Win7 USB stick -- and install from that.

---

### Post by darkod on 2012-09-04
I don't think removing the linux partition is really necessary, especially if it's confusing for the user. The win7 installer will offer to delete existing partitions and create new ntfs partition(s). Only in rear cases it might complain if the disk is with linux partitions.

---

### Post by Mark Phelps on 2012-09-04
> **darkod said:**
> I don't think removing the linux partition is really necessary, especially if it's confusing for the user.

I agree that it should not be necessary, but we get lots of posts here with folks booting into a Win7 USB/DVD and it won't offer the option to reformat the drive.  Maybe it just gets confused when it sees Linux filesystems.

---

### Post by darkod on 2012-09-04
I might have used the word 'offer' in a misleading way. When the step to select the partition to install onto shows up, below the partitions list there will be some options/buttons (they are not really in a form of a button, just words). One of them is Advanced.

If you open that, it displays more options among which Format, Create, Delete, etc.

If you try Format directly, it will not do it onto linux type partition.
But the Delete options works in any case, so you can delete all partitions and then use Create which will format it in the process.

Few weeks ago I was moving my system to my new SSD, but I was creating the partitions in advance with parted and wanted to format the win7 partition with the installer. I forgot that parted will leave it as 82 and not 07, so the win7 installer couldn't format it. But the Delete option was enabled, I could have deleted the partition if I wanted to.
After I used cfdisk to change the type from 82 to 07, the win7 installer had no problems formatting it.

Again, there might be isolated cases where it gives you problems, but the Advanced options in the partitioning step should be enough for you in most cases. I hope I remember it correctly since I don't do win7 installs that often. :)

---

### Post by Slim Odds on 2012-09-04
Sorry Darko, it just doesn't work that way. The Windows installer is just plain stupid. I've run into this before myself.

The installer just doesn't know what to do with Linux partitions (I, personally, think that this is by design). So you have to delete these partitions before attempting a Windows install. I usually just wipe out the partition table, but that's because I'm a geek.

---

### Post by darkod on 2012-09-05
> **Slim Odds said:**
> Sorry Darko, it just doesn't work that way. The Windows installer is just plain stupid. I've run into this before myself.

The installer just doesn't know what to do with Linux partitions (I, personally, think that this is by design). So you have to delete these partitions before attempting a Windows install. I usually just wipe out the partition table, but that's because I'm a geek.

Now you made me boot up a VBox VM of Debian I have. :)
I booted it with the win7 ISO simulating a CD as if installing. Evidence attached.

The first time the partitioning step shows up, there is the Drive options (advanced) option. Once you click that, it opens more options as seen in image2. Notice how the Delete option is active, while Format and New are not active.

It can't format a linux partition because it can't understand it, but it can delete it despite this fact. After that you simply create a new partition with the option New which will become enabled as soon as there is unallocated space on the disk.

---

