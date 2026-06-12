---
title: "Win7+Ubuntu in separated hard disks problem"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by kourasmenos on 2011-04-15
[SIZE=3]I used to have win7+ubuntu 10.04 installed at my pc in a single 320gb hard disk. (100gb for win7, 20gb for ubuntu 10.04 and 200gb free space that was accessible to both OS).

A few days before i decide to get another 500gb hard disk in order to install Ubuntu 10.10 to the new drive.
So i format them all and made the new partitions like this.
[/SIZE]
[LIST]
[*][SIZE=3]I separated the 320gb HD and gave 120gb to win 7 and 200gb free storage space plus the new 500gb HD which was empty.[/SIZE]
[*][SIZE=3]So i installed Ubuntu 10.10 to the 500gb disk which i manually partitioned like this. 96.5gb to Ubuntu 10.10 OS, 3,5gb SWAP and 400gb  free storage space.[/SIZE]
[/LIST]
[SIZE=3]After completing the installation correctly restarted of course, but dual boot menu didn't show up. So i red someone's post here and got into BIOS and change HD's boot priority and gave first boot priority to the hard disk which Ubuntu 10.10 was installed.

Hopefully the menu appeared so i logged in Ubuntu but: I checked my hard disk and saw that they weren't separated as i was planning to.
It supposed to be 120gb(windows 7) and 100gb (ubuntu) plus 200gb and 400gb free space which should be accessible from both OS.
[/SIZE]
[LIST]
[*][SIZE=3] **Instead of that, check what i got at the image bellow**[/SIZE]
[/LIST]
[SIZE=3] [[IMG]http://img854.imageshack.us/img854/4338/screenvf.jpg[/IMG]]("http://img854.imageshack.us/i/screenvf.jpg/")

[[IMG]http://img546.imageshack.us/img546/2757/screenshothe.png[/IMG]]("http://img546.imageshack.us/i/screenshothe.png/")

Apart from that, when i got into windows 7 I realized that the new HD was not available, not even the 400gb free space. 

Tnx 4 your help in advance
[/SIZE]

---

### Post by Dutch70 on 2011-04-15
[SIZE="3"]Ohh, where to start...oh yeah, 

Hi and welcome to UF :)

1st, please post pics of your partitions from Gparted, not Nautilus.
2nd, if you post the output of fdisk -l, please copy/paste the output between [CODE][ /CODE] tags by using the "#" in the toolbar. 

When you say free space, does that mean unallocated? 
It won't show up in windows unless it's formatted to ntfs.

Your post is well written, yet still a little confusing as to what you want.[/SIZE]

---

### Post by kourasmenos on 2011-04-16
[SIZE=3]The output is this[/SIZE]:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c01a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11733    94238281+  83  Linux
/dev/sda2           11733       12158     3417088   82  Linux swap / Solaris
/dev/sda3           12158       60802   390728704   83  Linux

Disk /dev/sdb: 320.1 GB, 320069031424 bytes
18 heads, 4 sectors/track, 8682428 cylinders
Units = cylinders of 72 * 512 = 36864 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18dd18dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          29        2873      102400    7  HPFS/NTFS
/dev/sdb2            2873     2912740   104755200    7  HPFS/NTFS
/dev/sdb3         2912740     8682383   207707136    7  HPFS/NTFS

```[SIZE=3]I think that i made a mistake when created the partitions of the 500gb HD.
I set 96.5gb Primary, ext4, mount point /
3.5gb swap
400gb primary (i cant recall the fortmat i chose), mount point /home[/SIZE]

---

### Post by Dutch70 on 2011-04-16
[SIZE="3"]Yeah, 96.5GB for / is about 70-80GB of wasted disk space if you have a /home. 

It looks like you've got nothing but windows on the 320GB hdd & nothing but Linux on the 500GB hdd.

I can't tell you about windows, but if you want to use the entire 500GB disk for Ubuntu, I would partition it like this...

[COLOR="Red"]/[/COLOR] = 15-20GB (can't see any reason for it to be bigger than 30GB.
[COLOR="Red"]swap[/COLOR] = equal to the size of your physical RAM + about 10% if you want. [[COLOR="Blue"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")
[COLOR="Red"]/home[/COLOR] = the remainder of your 500GB hdd.[/SIZE]

[SIZE="2"]**You can make /home smaller & create an ntfs partition and share files with windows, or you could create the ntfs partition on the windows hdd. Which is probably what I would do. Just too many options to list here when it comes to partitioning schemes.[/SIZE]

---

### Post by kourasmenos on 2011-04-16
[SIZE=3]So im gonna make it like this...30gb ext4 mount point / for ub 10.10
                                                3gb swap
and what should i choose for the rest 467gb in order to be available in both windows and ubuntu?

I guess ntfs format and what about mount point?
[/SIZE]

---

### Post by Dutch70 on 2011-04-16
[SIZE="3"]Hmm, good question, I've never created an ntfs partition during install. I believe the mount point would be /media though. 

If you do it that way, everything you save will be saved to / because your /home will be inside the same partition. You can create folders in the ntfs prtn and symlink them to your home folder by middle clicking & dragging them to your home folder.[/SIZE]

---

### Post by theDaveTheRave on 2011-04-16
I would go along with dutch70's advice.

If you want to permanently have all the data on the ubuntu disk also avialable to Windows when you log into it then you will have to format as NTFS.

However it depends what you are using the 'shared' section for?

If you need access to specific documents (and it will only ever be documents) you could conceivable set a section of disk to automount at /home/[yourUserName]/Documents.

Then of course you could do the same for your photo's, and videos.

You could of course go really mad....

Create a partition on your user's home
/home/yourUserName  - set this to a Linux specific format as allow ubuntu to put all of the required user specific config files into it (have a look at your home drive and there are a bunch of directories tarting '.' that are 'hidden' and hold all the user config data, being a linux specific format will prevent your windows partition from accidentally doing stuff with it, as these are often text files.

then create partitions to clearly separate your concerns, as suggested above... One for documents, one for photos, another for music, another for video.... and on and on and on... The idea here being that stuff that you don't change very often (like your music and video files) can inhabit their own space, and then when you open them from windows there is less chance for 'fragmentation' etc.

I believe that you can even read ext2 / ext3 etc formats from windows, but you need a special bit of software to allow it [see here]("http://www.howtoforge.com/access-linux-partitions-from-windows") for advice...

Hope all that helps....

---

### Post by Dutch70 on 2011-04-16
[SIZE="3"]+1 for fs-driver, I use it to access a /home prtn that's nearly 3 years old & formatted to ext2, and it works great.[/SIZE]

---

### Post by kourasmenos on 2011-04-16
So im gonna give it another try and ill inform you...lets hope i wont  ](*,) when done!!!

---

### Post by Dutch70 on 2011-04-16
[SIZE="3"]Sometimes it's best to use the live cd/usb to create your partitions in advance.[/SIZE]

---

### Post by kourasmenos on 2011-04-17
[SIZE=3]I formated the ubuntu, merged the hard drive and do it all from the beggining.

So i used the live cd and created a 30gb partition for 10.10, 3gb swap but the rest of the free space was left unallocated.
Then i logged into win7 and created a new partition with the free unallocated space. Simple as that.

[I]At least now i can use this space from win7 but still can see it in 10.10
It would be nice to be able to use that space from both OS :confused:[/I]
[/SIZE]

---

### Post by Dutch70 on 2011-04-17
[SIZE="3"]Not sure why you can't see it from Ubuntu, but you should have used Ubuntu to create the ntfs partition as well. Why did you login to windows to do it? Once you shrink your hdd, you're done with windows tools. The only reason for shrinking it from windows, is because it is a windows partition that you're messing with & windows doesn't play well with others.[/SIZE]

---

