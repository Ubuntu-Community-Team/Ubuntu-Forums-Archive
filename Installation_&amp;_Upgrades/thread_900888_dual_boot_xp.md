---
title: "dual boot xp?"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by thebozenator on 2008-08-25
I have a computer with two hard drives. What i want to do is use one of them as the boot drive for both Ubuntu and XP and I want to split the other drive in half and use it as the drive i save my documents to for both OS's. Anyone know how i can go about doing this?

PS: i am kind of new to Linux :grin:but i am good with computers so please try to make answers as simple as possible. thanks.

---

### Post by calibre97 on 2008-08-25
I suggest you boot to a Live Linux CD or Rescue CD (that has GParted, a partitioning program, on it) and use that to set up all your partitions. You'll need a Primary one for Windows and then either another primary for Linux (/, root partition) or one gigantic Extended partition because Linux doesn't really care in that regard. Don't worry about sizes yet as you can set all that during the Linux install. Just set up the XP Primary partition first. Install XP and then install Linux. It'll install GRUB, a text-based boot loaded that will then let you boot to Linux or Windows. During the Linux install, create partitions in that Extended partition. You can go with everything but swap in a single partition, but it's highly recommended you create a separate partition for /home where all your config info (and more) lives.

As for the second drive, sure, you'll be fine creating partitions for both XP and Linux (for XP it'll be NTFS, for Linux it'll be ext2 or ext3 or any of the multiple file systems available). Keep in mind that with the latest nifty NTFS driver, usually installed by default in most distributions (was in Kubuntu for me) all partitions will be available to you when you boot into Linux.

Depending on what you need XP for, you might consider going Linux only and using XP in a virtual machine (VMWare's VMWare Server is free). This is what I did on my laptop. But if you're going to game and do other intensive things, go with the dual boot.

I know this was sketchy and jumped around a little but hopefully it'll help you get started. Keep searching in these forums and elsewhere because many other people have already done what you're asking. My particular setup is a single disk (laptop) but I don't think having the second disk will be too much trouble.

---

### Post by manishtech on 2008-08-26
Just boot through Ubuntu LiveCD and goto System>Administration> Gnome Partition Manager
This is the place where you can edit your partitions. Windows needs a primary partition and Linux can even work on logical ones.

Now select your first hard disk (sda) and then try to partition it by giving ubuntu a fair share. You would need a swap partition. I suggest creating linux on logical as you can have only 4 primary+extended partition. You can have therotically unlimited partitions inside extended.

Now select sdb and split it into two partitions.

Nothing much is to be done, its quite simple. First try out GNOME partition editor.

---

