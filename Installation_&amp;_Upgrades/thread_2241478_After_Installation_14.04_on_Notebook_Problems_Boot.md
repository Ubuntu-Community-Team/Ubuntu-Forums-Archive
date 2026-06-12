---
title: "After Installation 14.04 on Notebook Problems Booting"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2014-08-26
I installed Trusty (14.04) on a Toshiba P755 notebook a few days ago.
At first it worked perfectly, till today.

Then this morning ran into these errors.
```

mount: mounting /dev/disk/by-uuid/54422875-4fc1-b0cf-e8ff8c4133ed on/root failed Invalid argument
mount: mounting /dev/on root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on root/proc failed: No such file or directory
Target filesystem doesn't have requested sbin/init.
No init found. Try passing init=bootarg.
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

```

Well, I did something that ended up working. I soft booted [ctrl]+[alt]+[del]
and the system came up perfectly.

Then there was just an update which was installed. It required a reboot, and all that was happening was GRUB would come up, I would select "Ubuntu" from the menu, and the system would reboot bring me back to the GRUB menu. (Kind of like the movie Groundhog Day :)  )

Any idea what is causing the error message, and the constant reboot when I try to enter Ubuntu.
And how to fix this?

I attached a GParted screen shot:
[ATTACH=CONFIG]255846[/ATTACH]

---

### Post by LaughingHorse on 2014-08-26
Ubuntu is in sda1
it is an ext 4

home is in sda4
it is also an ext 4

I was trying to make sda 3 a bios_grub, but have not done that yet. Is that important to have?

---

### Post by yancek on 2014-08-26
Did you notice that sda3 also shows as a mount point of /.  19GB partition with nothing on it.  That's a little weird.  Check your /etc/fstab to see where / is mounted.  Also run blkid command from a terminal and compare its output to the uuid number from your post above to see what it is.  Are you still getting the error message in your initial post or is just the login loop problem?

---

### Post by LaughingHorse on 2014-08-27
Thank you yancek!

Re sda3:
When setting up the partitioning, I wanted to set up a grub_bios partition, and unfortunately (for me) I mis read the size. I wanted to to be about 2 gb.
Do I need a grub bios partition if my hd is only running Ubuntu, and no other OS is on my computer?
I have no problem using GParted to either delete or shrink that partition.

Re error:
I used the install disc, and ran
```

sudo fsck -y /dev/sda1

```

And that seemed to fix the error problem.
Now I have a loop problem.

What comes up is a menu with
Ubuntu
mem test

Ubuntu (on sda1)

If I use the top Ubuntu, I just loop.
If I use Ubuntu on sda1 I am able to log in.

I'd like to fix that one.

---

### Post by yancek on 2014-08-27
I'm not sure what you mean by a grub bios partition.  You can have a separate boot partition or a separate grub partition but there is no need for either, meaning not required.
If it is booting to sda1 and that is your Ubuntu install, you should not need to make any changes.  I would not delete the partition as it will probably change sda4 to sda3 and create problems accessing your separate /home partition.  Just format sda3 ext4 (or whatever filesystem you use) and create a mount point for it in the /mnt directory and then use it for data storage.  Example:  sudo mkdir /mnt/data (name whatever you want) then put an entry in /etc/fstab for it using the current entry for /home as an example modified to fit that partition.

Boot Ubuntu and open a terminal to verify which partition you are on by running:  df -h  That should show output similar to below, in this example / (root filesystem) is on sda13, your should show sda1. 

> bash-4.2$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda13       20G  9.8G  8.9G  53% / 

If there are no boot files on sda3, running:  sudo update-grub should remove that first entry from grub.cfg.

---

