---
title: "Which OS is on which partition?"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by Warrior4Christ on 2014-07-05
All right, so, this may be a stupid question, but I'm a bit of a Linux newb, so bear with me. :)
So, I have Ubuntu 12.04 installed on my computer. I once tried to upgrade to 12.10, but things went south and, long story short, I have 12.10 installed, but it's unusable. Also, I have ElementaryOS installed, and it recently started giving me problems, and I've done as much as I can to solve the issues to no avail. So, I decided to delete 12.10 and eOS and free up some space....however, I realized something: Which partitions do I delete to get rid of the OS's and free up space? I definitely don't want to delete the wrong partition, so how can I tell which OS is on which partition? 

Again, this may be a very dumb question, but I honestly don't know. I've never done this before.

---

### Post by gjohnz on 2014-07-05
What actually boots? What OS are you able to use? You say Ubuntu is unusable. Can you boot Elementary? Are there other OS's installed as well?

---

### Post by sudodus on 2014-07-05
Boot into the linux distro/version that works, and that you want to keep. Open a terminal window. Run the df command. It will show what partitions it uses.

```
df
```

After that, run a parted command to list all partitions and a blkid command to get the labels (if any)

```
sudo parted -l
```

... space minus ell

```
sudo blkid
```

Please post the output of these commands within code tags.

Copy and paste the text into a reply, 'go advanced' (red button below the editing window), mark the text and click on the # icon above the editing window.

---

### Post by Warrior4Christ on 2014-07-05
I can boot into Elementary, but nothing appears except for the desktop background.  I can only boot into tty when trying to boot into 12.10

---

### Post by Warrior4Christ on 2014-07-05
Here's the output of the commands, sudodus:

```
Filesystem     1K-blocks     UsedAvailable Use% Mounted on
/dev/sda6       21469408 16397568  3981232  81% /
udev              761108        4   761104   1% /dev
tmpfs             154504      936   153568   1% /run
none                5120        0     5120   0% /run/lock
none              772504      160   772344   1% /run/shm
/dev/sdb1        7801432  2878968  4922464  37% /media/FD2


Model: ATA FUJITSU MHV2060A (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical):512B/512B
Partition Table: msdos
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  24.7GB  24.7GB  primary  ext4            boot
 2      24.7GB  60.0GB  35.3GB extended
 7      24.7GB  36.1GB  11.3GB  logical  ext4
 6      36.1GB  58.4GB  22.3GB  logical  ext4
 5      58.4GB  60.0GB  1607MB  logical  linux-swap(v1)


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical):512B/512B
Partition Table: msdos
Number  Start   End     Size    Type    File system  Flags
 1      16.4kB  8004MB  8004MB  primary fat32        b

```

---

### Post by sudodus on 2014-07-05
*You* must decide what you want to keep. Maybe the best alternative is to save all important files to another drive, in other words, backup everything you want to keep :-)

Then, with peace in mind, you can remove the linux partitions and make a fresh install. You told us about 12.04, and it is still going strong (except Lubuntu 12.04 that has passed end of life). I suggest that you install the flavour of ***12.04.4 LTS*** that suits best for you and your computer. *Try* without installing before you decide what to install.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

You can run those commands in post #3 while trying (from a live session). You can also backup your files from a live session.

---

### Post by sudodus on 2014-07-05
> **Warrior4Christ said:**
> Here's the output of the commands, sudodus:

```
Filesystem     1K-blocks     UsedAvailable Use% Mounted on
[COLOR=#ff0000]/dev/sda6       21469408 16397568  3981232  81% /[/COLOR]
udev              761108        4   761104   1% /dev
tmpfs             154504      936   153568   1% /run
none                5120        0     5120   0% /run/lock
none              772504      160   772344   1% /run/shm
/dev/sdb1        7801432  2878968  4922464  37% /media/FD2


Model: ATA FUJITSU MHV2060A (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical):512B/512B
Partition Table: msdos
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  24.7GB  24.7GB  primary  ext4            boot
 2      24.7GB  60.0GB  35.3GB extended
 7      24.7GB  36.1GB  11.3GB  logical  ext4
[COLOR=#ff0000] 6      36.1GB  58.4GB  22.3GB  logical  ext4[/COLOR]
 5      58.4GB  60.0GB  1607MB  logical  linux-swap(v1)


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical):512B/512B
Partition Table: msdos
Number  Start   End     Size    Type    File system  Flags
 1      16.4kB  8004MB  8004MB  primary fat32        b

```

I saw your post after posting (post #6)

You have 3 linux partitions, sda1, sda6 and sda7. When you ran df, you were booting from sda6 (the root partition '/'). This should help you identify the partitions. Do you need to identify the other two partitions too?

---

### Post by Warrior4Christ on 2014-07-05
I keep everything backed up to Google Drive and Dropbox, and I've tried other flavors, also. I think I'm going to keep Ubuntu, with Unity DE and re-install ElementaryOS Luna. :)

---

### Post by Warrior4Christ on 2014-07-05
I know that ElementaryOS is on sda7, so I would assume that Ubuntu 12.10 is on sda1. Thanks for the help!

---

### Post by sudodus on 2014-07-05
That's good. I wish you good luck with your partitions and operating systems :-)

If you have more problems related to this thread (and its title), please post back. Otherwise I suggest that you click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

-o-

If you get other problems, please create a new thread with a good descriptive title to attract people, who can help with those problems.

---

### Post by Warrior4Christ on 2014-07-05
Uhm, I just realized that /boot is on sda1, which I want to delete. Wouldn't that delete the GRUB?

---

### Post by sudodus on 2014-07-05
You can always re-install and or repair grub. See this link

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

---

### Post by Warrior4Christ on 2014-07-05
Never mind, I stumbled upon a tool called "OS-Uninstaller", and I uninstalled both eOS and 12.10 without messing up the bootloader. Thank you, though!

---

