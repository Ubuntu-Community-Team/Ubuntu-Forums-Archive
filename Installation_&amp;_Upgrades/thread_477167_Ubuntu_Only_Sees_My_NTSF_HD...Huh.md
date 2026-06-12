---
title: "Ubuntu Only Sees My NTSF HD?...Huh?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Spleinmuncher on 2007-06-18
Hello!  Just installed Ubuntu, and I have a slight problem:

My partition, listed as "HDA1," is in fact the very same partition as "C:\" in my Windows.  So my question is:
Where  did my FAT32, EXT3, and "Swap" partitions go?

Here is how I split my HD:
-Resized the Primary (Windows) partition to 135 GB (from 149), and left it as what it was originally listed as in the partition tool, namely, "media/hda1" (<-...or something like that...)
-Made a new, 8 GB EXT3 partition (for my Linux).  It was a Primary partition, at the beginning of my HD, and listed as simply "\"
-Next, I made a FAT32 Partition, which was Logical, at the End of my HD, and under the directory "\windows"
-Finally, I made the remaining space on my HD into a Swap Area, which was also Logical

Where did I go wrong, and how do I fix it?

Thank you in advance!

---

### Post by sickpuppet on 2007-06-18
Hi Spleinmuncher - 

That all sounds perfectly good to me! Run the command 'df -h' in the Terminal and paste the output here.

cheers
Ben

---

### Post by Spleinmuncher on 2007-06-18
Regrettably, my internet on Ubuntu seems to be dead as well (I would rather figure this one out first though...) so Copy+Pasting might be somewhat difficult for me.  Let me try though!

---

### Post by Spleinmuncher on 2007-06-18
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              8270100   3632356   4217648  47% /
varrun                  777980       100    777880   1% /var/run
varlock                 777980         0    777980   0% /var/lock
procbususb              777980       116    777864   1% /proc/bus/usb
udev                    777980       116    777864   1% /dev
devshm                  777980         0    777980   0% /dev/shm
lrm                     777980     33788    744192   5% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1            141604904 125171780  16433124  89% /media/hda1
/dev/hda5              5234968         4   5234964   1% /windows
tmpfs                   777980     33788    744192   5% /lib/modules/2.6.20-16-generic/volatile

There are the results...

---

### Post by Spleinmuncher on 2007-06-18
I hate to be pushy, but I need to do some important work on this computer tonight, so any help would be greatly, greatly appreciated.

A link to a website with useful information would also be very helpful.  Thank you.

---

### Post by HotShotDJ on 2007-06-18
You already can "see" your NTFS partition.  No problem.
Your not supposed to "see" your swap partition.  It is used only by the system.  There's nothing to "see."
The EXT3 partition is your root partition, mounted as /.  You can use your file manager to browse up your file system.  Or open a terminal and type "cd /" without the quotes, and then type "ls" without quotes to see the contents.  You will not see it in the same place that you see your NTFS partition.

So, really, the only problem I'm seeing is that you haven't set your system up to look at your FAT32 partition.  Here is what I would do.  In a terminal, type "sudo mkdir /mnt/win_d" (without the quotes... it will ask for your user password).  Now, edit /etc/fstab as root "gtksudo gedit /etc/fstab" (no quotes) and add the following line:
```
/dev/hda5    /mnt/win_d    vfat     defaults   0 0
```and save.  Reboot.  You should see the Fat32 drive.

---

### Post by Spleinmuncher on 2007-06-18
I see

I have one little problem though: When I go into the Terminal and do what you said, it gives me this:
alex@alex-desktop:~$ sudo mkdir /mnt/win_d
mkdir: cannot create directory `/mnt/win_d': File exists
alex@alex-desktop:~$ gtksudo gedit /etc/fstab
bash: gtksudo: command not found
alex@alex-desktop:~$ 
alex@alex-desktop:~$ 

?

---

### Post by merlinus on 2007-06-18
gksudo gedit <filename>

-merlin

---

### Post by Tynach on 2007-06-18
> **HotShotDJ said:**
> You already can "see" your NTFS partition.  No problem.
Your not supposed to "see" your swap partition.  It is used only by the system.  There's nothing to "see."
The EXT3 partition is your root partition, mounted as /.  You can use your file manager to browse up your file system.  Or open a terminal and type "cd /" without the quotes, and then type "ls" without quotes to see the contents.  You will not see it in the same place that you see your NTFS partition.

So, really, the only problem I'm seeing is that you haven't set your system up to look at your FAT32 partition.  Here is what I would do.  In a terminal, type "sudo mkdir /mnt/win_d" (without the quotes... it will ask for your user password).  Now, edit /etc/fstab as root "gtksudo gedit /etc/fstab" (no quotes) and add the following line:
```
/dev/hda5    /mnt/win_d    vfat     defaults   0 0
```and save.  Reboot.  You should see the Fat32 drive.

To save you trouble, I'll go ahead and say that you should edit fstab to say "/dev/hda5 /media/win_d vfat     defaults 0 0" instead, so that you have both the ntfs and your vfat partitions inside your /media folder.

---

### Post by HotShotDJ on 2007-06-18
Since I don't have any windows partitions, I can't say for sure... but what on earth would his NTFS partition (or any other fixed hard drive partition) be doing in /media?  That SHOULD be used for removable media only -- or have they mucked around with the file system hierarchy while I wasn't looking???

---

### Post by merlinus on 2007-06-18
Both of my NTFS partitions have entries in /media, and the contents are easily accessible from there in both Nautilus and Thunar.

-merlin

---

### Post by HotShotDJ on 2007-06-18
*sigh*  I guess Ubuntu developers are taking liberties with the [Filesystem Heirarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html").

---

### Post by Bluecircle on 2007-06-18
> **merlinus said:**
> Both of my NTFS partitions have entries in /media, and the contents are easily accessible from there in both Nautilus and Thunar.

-merlin

That's weird none of mine are like that.

---

### Post by vexorian on 2007-06-18
> **HotShotDJ said:**
> *sigh*  I guess Ubuntu developers are taking liberties with the [Filesystem Heirarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html").
And I love that. It was very useful. (Aka My ntfs partitions are also mounted there)


..
Edit: After reading the specs I am not sure where are ntfs partitions supposed to go, mnt is for temporarily mounted things, and in some ways, the ntfs partitions are "removable media" sigh...

---

### Post by HotShotDJ on 2007-06-18
> **vexorian said:**
> After reading the specs I am not sure where are ntfs partitions supposed to go, mnt is for temporarily mounted things, and in some ways, the ntfs partitions are "removable media" sigh...Well, "temporarily mounted" can mean all kinds of things.  Historically, /mnt was used as the mount point for just about everything that wasn't required to run the system... including cdrom, floppy, etc.  Then removable media was moved to /media (I thought that change was silly, but nobody asked me).  This left /mnt for non-removable media (such as a windows partition).

---

