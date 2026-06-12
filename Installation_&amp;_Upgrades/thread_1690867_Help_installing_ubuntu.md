---
title: "Help installing ubuntu"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by kuobob on 2011-02-19
I'm like a noob when it come to installing a new operating system.
When I boot into ubuntu from my usb, everything works fine. Then I click on the install ubuntu icon, but when I get to the allocate drive space, I only have two options:
Erase and use the entire disk
Specify partitions manually 

Why is there not a "install alongside other operating systems" option. :confused:

I use windows 7 and is installing the 32 bit version of Ubuntu 10.10 for desktop.

---

### Post by Sean Moran on 2011-02-19
> **kuobob said:**
> I'm like a noob when it come to installing a new operating system.
When I boot into ubuntu from my usb, everything works fine. Then I click on the install ubuntu icon, but when I get to the allocate drive space, I only have two options:
Erase and use the entire disk
Specify partitions manually 

Why is there not a "install alongside other operating systems" option. :confused:

I use windows 7 and is installing the 32 bit version of Ubuntu 10.10 for desktop.
Golly, Karmic Koala has that, but if you want to make it work without that, then go the manual option, resize some partitions if you haven't already, and just make room for 10Gb total.

You can do the whole install with 4Gb for root (/) but 8Gb is safer, and make a SWAP partition of 2GB, (as a rough estimate for the sake of general installations), and there you have it.  10GB all up, two simple partitions for root (/) and SWAP, and you're away.  You can adjust all of this after the install too.  Bon Voyage mate!

---

### Post by kuobob on 2011-02-19
Thanks
but how do I make partitions

---

### Post by Sean Moran on 2011-02-19
... double-post, can't finjd the delete button

---

### Post by kuobob on 2011-02-19
I followed your instructions, and created some gray unallocated space, but when I try to create a new partition, the program says I can only have 4 partitions.

---

### Post by Sean Moran on 2011-02-19
<another double-post, for some reason ? >

---

### Post by Sean Moran on 2011-02-19
> **kuobob said:**
> I followed your instructions, and created some gray unallocated space, but when I try to create a new partition, the program says I can only have 4 partitions.
Sorry for that post.  Something wrong with my wifi no doubt. 

You can have 4 PRIMARY partitions and quite a lot more LOGICAL partitions inside one EXTENDED partition.

I'm guessing once more, but you'd likely have /dev/sda1, /dev/sda2, /dev/sda3, /defv/sda4, and one of those PRIMARY partitions might or might not be an EXTENDED partition?

If you already have 4 primary partitions, then you must continue with that rigmarole to resize and move, until you can add that free space to the EXTENDED partition, where you can create plenty of LOGICAL partitions within that.  Ubuntu and SWAP will run happily on LOGICAL partitions inside your EXTENDED partition, but it's true, you can only have four PRIMARY partitions in total.

I'll hold off testing my distro on WinXP while we see this through together.

Can you run a terminal command: **df** to give some idea of your hard disk layout?

---

### Post by kuobob on 2011-02-19
sorry for the wait, I had to get dinner.
I ran df in the terminal.
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1530080     78612   1451468   6% /
none                   1524168       304   1523864   1% /dev
/dev/sdb1              7849452    709708   7139744  10% /cdrom
/dev/loop0              676480    676480         0 100% /rofs
none                   1530080       100   1529980   1% /dev/shm
tmpfs                  1530080        16   1530064   1% /tmp
none                   1530080        92   1529988   1% /var/run
none                   1530080         4   1530076   1% /var/lock

---

### Post by Sean Moran on 2011-02-19
> **kuobob said:**
> sorry for the wait, I had to get dinner.
I ran df in the terminal.
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1530080     78612   1451468   6% /
none                   1524168       304   1523864   1% /dev
/dev/sdb1              7849452    709708   7139744  10% /cdrom
/dev/loop0              676480    676480         0 100% /rofs
none                   1530080       100   1529980   1% /dev/shm
tmpfs                  1530080        16   1530064   1% /tmp
none                   1530080        92   1529988   1% /var/run
none                   1530080         4   1530076   1% /var/lock
I had a feeling that "df" wouldn't tell me much as to what these four primary partitions are.

Is there a way that you can determine whether you have /dev/sda1, /dev/sda2, /dev/sda3, and /dev/sda4, and whether any one of them is an EXTENDED partition.  If you imagine your hard disk like a pizza, then the PRIMARY partitions can only slice that pizza into four quadrants.  If one of them is set as an EXTENDED partition, then that partition can be sliced into nice little slivers for at least 20 more LOGICAL partitions, and probably many more, although I don't know the limits of EXT4 logic.

You can also slice the pizza into three small slivers for the PRIMARIES and leave most of the HDD for that one single EXTENDED partition, and that is how we can have many different operating systems and lots of data combined on the one physical hard disk.

Speaking of pizza, the second-most talkative part of my brain is telling me to go for a walk and get some food, and there's not much pizza hopping around in the jungle, but I have plenty of jungle on all sides to find suitable grasshoppers and frogs to fry up on my pitta bread with cheese, so I'll be back in an hour or so.

---

### Post by kuobob on 2011-02-19
I think I just screwed up on something. Now I can't boot into windows anymore.
I'm going to use the whole disk for ubuntu instead. Sorry for troubling you.:(
Thanks for the help, and sorry that I screwed up.

---

### Post by Sean Moran on 2011-02-19
> **kuobob said:**
> I think I just screwed up on something. Now I can't boot into windows anymore.
I'm going to use the whole disk for ubuntu instead. Sorry for troubling you.:(
Thanks for the help, and sorry that I screwed up.
My screwup mate.  I've been trying to explain the fuindamentals of disk partitions on an unknown hard disk, and if I'd been able to see what's on yourt hard disk, or even how many GB it is, we could have done better.

One thing to remember, is always install Windows first, and then Ubuntu will fit around that, and Windows will still be happy after GRUB is installed, but if you install Ubuntu and then install Windows, Windows will take over the Master Boot Record (MBR) and then you'll need to fix GRUB all over.   Do Windows first, because Windows is very unsociable.  Linux is sociable, so it won't mess up Windows, but Windows gets jealous every time it sees someone else on its MBR.

---o0o---

If you're still around somewhere and haven't gone ahead with the install yet, I know a fairly versatile way to setup your hard disk for dual boot with 1xWindows and 2 or more x Linux, such as Ubuntu.  You'll need to understand gParted, which is on the Live-CD and you can apt-get install gparted to Ubuntu if you need to.

Start with a clean hard disk, hopefully at least 80Gb but the more the merrier.

Boot from a Live-CD and start gParted - your tool for graphical GNOME partitioning.

Create a new partition, /dev/sda1 - right click on the unalllocated space or find the New in the toolbar.  Make it 8192 MB, format it as FAT32.

Create a second partition, /dev/sda2: This one format as ext4 and still just 8192 MB.

Create a FOURTH partition at the very end of your hard disk, /dev/sda4.  Make it 2GB and format it as Linux SWAP.

Now go back and create a third partitonm /dev/sda3.  Make this one EXTENDED and use all the remaining space between your PRIMARIES /dev/sda2 and /dev/sda4.

Once you have your EXTENDED PARTITION, and two primaries for Windows and Linux, plus a little bit of SWAP at the end, you can start to allocate the space for the logical partitions within that /dev/sda3 EXTENDED partition.

You can use these logical partitions for Ubuntu and boot to them, or for data, but Windows might not like to be stuck on a logical partition.  Still most of your space on your computer is going to be data, unless you're a computer lab or Internet cafè.

Let's assume your HDD is 160Gb and you've just used 16GB at the start and 2GB at the end, so you have around 140GB on the EXTENDED partition in the middle.

It's time-consuming, but you only have to do this once every now and then, like once a year, to help your HDD avoid ugly footprints.  

Set /dev/sda5 (your first LOGICAL partition) to 8192MB and make it EXT4.  This is to use for testing new Linux distros.

Do the same for /dev/sda6 and save that 8GB for things you might want to do in the future. 

That's 16/140 used.  You still have 124GB left.  Make /dev/sda7 32768MB and call it /home.  /dev/sda8 can be 32768MB too, and save that for all your photos and images and mp3 files and big things that take up lots of roomn and might be better stored on their own partition.

Now you have only 60GB left.  Out of this remaining unallocated space, create one big partition, but set it carefully, and reduce it down to everything minus 8GB.
Then create one last 8GB partition at the very end for a scratch partition, where you can test out new distros, or hide all your porn, or store legitimate downloads or anything you need to do over a month.  There's still a big 52+GB partition one step to the left that you can use for massive data storage before you can sport through all the wheat from the chaff, so this last little 8GB one is more for experimentation, and naturally I was only kidding about the porn.  You'll always find a time when you will find a good use for another spare partition to experiment with, so that is what this last one is for, so that your main data-scratch partition doesn't have to be messed with if you need an extra 8GB partition to format and play with. 

Many others will suggest separate partitions for /boot or /usrt or /var, but to start out, that's a fairly comprehensive set of partitions for a dual boot system, and will probably take 20 minuites to configure in gParted and the rest of the weekend to copy all the data onto and do the rest of the installations.

---o0o---

Now, I really must get back to testing my minimal system with its six 7z parts on Windows XP to see if I can produce a CD ROM that will start from Windows and install my little Ubuntu on that last spare partition that's only there for experimentation, so goodnight and hope to catch up in the morning.

---

