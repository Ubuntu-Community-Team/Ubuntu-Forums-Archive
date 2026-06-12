---
title: "installation problems"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by ubienewbie1 on 2012-10-12
Hi, I tried a first-time install of 12.04 64-bit (brand new hardware, no OS, clean formatted drive) with mixed success.  I couldn't make much sense of the various guides for how to set up partitioning, with references to Guided vs. Manual partitioning not matching what the installation options presented, so I eventually just went with the default which I assumed to be the same as guided.

I installed from a USB stick that had been set up in Windows.

Installation completed successfully, at which point I was prompted to reboot.  I think I screwed up there by removing the USB stick, figuring that would be necessary for rebooting without it trying to reinstall.  As soon as I did so, it kicked me out to a command line-like screen (I didn't make note of what it said) with no options to type anything.  All I could do was turn the computer off at that point.  Now I can't boot with or without the USB stick.  (I can get into BIOS/setup, though.)

Any idea how to proceed?  I don't mind reinstalling Ubuntu if I can get back to an initial setup screen.  If I do go that route, any help how to navigate the partitioning screens for a newbie would be appreciated.  I was never presented with anything resembling the Guided options described here:

[https://help.ubuntu.com/12.04/installation-guide/amd64/module-details.html](https://help.ubuntu.com/12.04/installation-guide/amd64/module-details.html)

p.s.  Is there some font I need to install to make these forums more legible?  They show up for me as a very small, cramped, non-anti-aliased font.  I've never seen that anywhere else.

---

### Post by ubienewbie1 on 2012-10-12
I was able to load Ubuntu finally from the boot menu, specifying the USB stick, but I haven't figured out a good way to reinstall yet.  Something like this would be good:

[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

I still can't find anything in my installation that matches those descriptions.  Manually running the installation ISO from the USB stick doesn't work, either.

---

### Post by darkod on 2012-10-12
I think you might have it installed, but the bootloader grub2 ended up on the stick so it didn't boot when you pulled it out.

Now that you have ubuntu booted, open terminal and post the output of these commands:
df -h
sudo parted -l (small L)

---

### Post by ubienewbie1 on 2012-10-12
Thanks for the reply.  (Took me a few minutes to get logged into the forum on the new computer for copying and pasting.  The forum fonts look perfect here, so there's something icky when viewed on my Windows box.)  Here's the output from "df -h":

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       455G  3.2G  429G   1% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           732M  852K  732M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   76K  1.8G   1% /run/shm
/dev/sdb1       3.8G  1.4G  2.4G  37% /media/PENDRIVE
```

I had hoped to set up separate partitions for home, usr, var, swap, etc.  The default install never gave me that option, though, and the manual stage had me rather confounded.

Here's the output from "sudo parted -l":

```
Model: ATA WDC WD5000AAJS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4
 2      496GB   500GB  3979MB  extended
 5      496GB   500GB  3979MB  logical   linux-swap(v1)


Model: Kingston DT Locker (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4008MB  4004MB  primary  fat32        boot, lba

```

---

### Post by darkod on 2012-10-12
OK, so as you can see your hdd is /dev/sda (the stick is /dev/sdb) and you definitely have ubuntu installed and are running from it. As df -h says, /dev/sda1 is mounted as root.

So, with ubuntu running like this, add grub2 to the MBR of /dev/sda with:
sudo grub-install /dev/sda

Reboot without the stick and all should be good.

---

### Post by ubienewbie1 on 2012-10-12
That worked perfectly, thanks!  And thanks for the explanations along with the instructions.  That helps a ton for understanding what I'm doing instead of just blindly copying and pasting.  :)

Any suggestions for getting partitioning set up as originally desired?  I.e. an up to date tutorial to follow.

---

### Post by darkod on 2012-10-13
The only thing I can find with a quick search is this link:
[http://www.dedoimedo.com/computers/ubuntu-install.html](http://www.dedoimedo.com/computers/ubuntu-install.html)

This is very old, for 9.04, but detailed. If you ignore the first part, when you reach the Specify the partition manually, the screens are the same as with 12.04. The option for manual partitioning is called Something Else in 12.04.

The installer screens for the auto methods are changed, but the manual partitioning screen is almost identical.

When you create a new partition, or you want to use an existing one so you first click on it to select it and then click the Change button below, opens a window with three main selections:
Use As - to specify the filesystem to put on the partition
Format tick box - whether you want to format it or not
Mount point - at which mount point to attach this partition

When creating a new partition it will also ask you the size you want and whether you want it as primary or logical (if the disk has gpt table).

Also, below the partition list there will be a drop down box to select the device (disk) for the bootloader installation.

And that's about it. Note that for home users it's usually a good idea to have a separate /home partition, but don't split the disk too much creating many different separate partitions for /var, /usr, etc, because really it's not needed. Also, it is often difficult to assume their sizes and how fast they will eat space, so how would you know how big to make those partitions? If they are inside / it's easier since they simply use the free space in /.

---

### Post by ubienewbie1 on 2012-10-13
Thanks.  I haven't had any luck following that method or any of several others today.  They all seem to be based on fresh installations, not modifying the partitions after the fact, and nothing is quite matching what I'm seeing.

I tried installing Gparted, but that ran into an apparent dead end because I can't unmount the root partition because that has the OS, and without unmounting that it won't let me make any changes.  (I was running it while booted from the USB stick.)

I assume the main drawback to just leaving it to the way it is is the larger than necessary partitions having to be backed up?

---

### Post by darkod on 2012-10-14
Resizing the current install is not impossible, but since this is a new installation I think a fresh install might be much easier. I don't think you had too much time to modify things, or save much data.

Don't forget that the stick has the bootloader from the hdd installation. Since it now works without the stick, boot it from the hdd first, then plug the stick, open Gparted, format it as FAT32 and use Start Up Disk Creator and the ISO file to make the stick again.

After that you will have the original live usb again, not related to the hdd installation.

If you boot with the usb and open Gparted, you can manipulate the root partition and the others. Just note that live mode uses the swap partition on the hdd if it fidns one, so in Gparted you will see it as locked (the keys symbol next to it). Just di a right-click on the partition and select Swapoff. After that you can manipulate all of them.

But be careful what you do with partitions since it can make the hdd installation unbootable.

---

### Post by ubienewbie1 on 2012-10-15
> **darkod said:**
> Resizing the current install is not impossible, but since this is a new installation I think a fresh install might be much easier.

I ended up going with this option, thinking it the easiest...  Far from it, though.  I got all the partitioning stuff situated the way I wanted, following this nice guide plus your own explanation a few posts back:

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Unfortunately, I ran into a series of problems, starting with:

[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

Following those suggested fixes left me with this error:

error: invalid arch independent ELF magic Precise Pangolin 12.04

So, I decided to reinstall one more time, using the previously defined partitions, and now I'm at this error:

[https://answers.launchpad.net/ubuntu/+source/grub2/+question/205360](https://answers.launchpad.net/ubuntu/+source/grub2/+question/205360)

Unless anyone has any words of encouragement, I think it might be time to give Mint a look. :frown:

---

### Post by ubienewbie1 on 2012-10-15
I tried one more reinstall, erasing all partitions and starting from scratch, and making doubly sure that I had the right setting for "device for boot loader installation."  Once again, "error: file not found. grub rescue>" after installation and reboot.

---

### Post by ubienewbie1 on 2012-10-15
Going back to the recommendations at the start of this thread, here's the output of "df -h":

```
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.8G   42M  1.8G   3% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           732M  868K  732M   1% /run
/dev/sdb1       3.8G  1.4G  2.4G  37% /cdrom
/dev/loop0      660M  660M     0 100% /rofs
tmpfs           1.8G  8.0K  1.8G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   76K  1.8G   1% /run/shm
```That's the same thing I got with each of the last couple installation attempts.  Looks royally screwed...  What's with the "/cow" in place of /dev/sda1 mounted to root?  I certainly never added anything by that name, but it keeps showing up.

And here is the output of "sudo parted -l":

```
Model: ATA WDC WD5000AAJS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  20.0GB  20.0GB  primary  ext4
 2      20.0GB  28.0GB  8000MB  primary  linux-swap(v1)
 3      28.0GB  500GB   472GB   primary  ext4


Model: Kingston DT Locker (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4008MB  4004MB  primary  fat32        boot, lba
```

That all looks good from a partitioning standpoint.

It sure would be nice if there were a single, up to date installation guide, instead of having to pick and choose through dated, incomplete bits scattered all over...

---

### Post by darkod on 2012-10-16
1. The link from the launchpad bug you posted is about installing on raid. I don't know what that person used, but it's widely known that for raid you don't use the live cd because the bootloader installation often fails. Yet, people seem to think it's interesting to ignore recommendation.
So, since you are not installing on raid, that doesn't apply for you.

2. There might be cases where grub2 doesn't install correctly when grub2 was already present on the MBR. So if it doesn't overwrite it the old one might be looking for the old partition which is now gone and give the no such partition error.
You can try to fix that by reinstalling grub2 from live mode, only grub2 to the MBR.

3. If you ran that df -h command from live mode (since your hdd installation is not working, right?) then the output is different compared to the standard. This is because it's running in live mode. So, don't mind that /cow thing. Otherwise, I have no idea what it is also.

Use the live cd, go into live mode and try installing grub2 to the MBR with:
```
sudo mount /dev/sda1 /mnt # (since sda1 is your root partition)
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot without the cd and see how that went. If it didn't work, don't reinstall right away, there is another thing to try.

---

### Post by ubienewbie1 on 2012-10-16
Thanks for the continued efforts to help.  :)  Too bad the timezone difference meant I had given up and gone a different direction before your reply...

The links I posted previously were more to show the sequence of errors I was getting than the configuration that got me there.

That would make sense that the "df -h" output was different in Live mode.  I hadn't thought of that.  I went off researching what /cow represents, and that ended up being a big, ugly can of worms!

I did try several times reinstalling grub2 in the way you mentioned (can't remember if I used that exact command, but it was pretty similar), but I kept getting errors.

---

