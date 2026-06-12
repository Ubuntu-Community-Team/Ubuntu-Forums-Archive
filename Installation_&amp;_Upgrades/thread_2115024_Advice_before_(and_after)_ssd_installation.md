---
title: "Advice before (and after) ssd installation"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by zahtar on 2013-02-11
Hello all!

I just bought my first ssd [IMG]http://www.kubuntuforums.net/images/smilies/smiley.gif[/IMG]  It is an intel 330 and I've been searching for ways to get the most out  of it (performance and long levity). I have come to a few things on  which I'd like your opinions and advice.

1) Partition allignment. The most detailed guide I've read is that of  the following link. Is there a better/easier way than the one described?

[http://lifehacker.com/5837769/make-s...ve-performance]("http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance")

2) I've read that it would be good to put the swap partition on a hdd,  which in my case will be my current hdd. Thing is, that I would also  like the hdd to spin down when not in use. Is this possible when having  the swap on the hdd? Some wrote that there is no need for a swap  partition when you are not interested in hibernation, which really is of  no interest to me. 

3) Partitioning: 20GB root, 80GB home (both ext4 filesystem), rest  unsused in case I decide to try dual boot with some other distro or  something. Should I be using the entire device or is it ok as it was  with hdds?

4) Enable trim for each partition

5) Setting the swappiness to 0 to minimize the swap use. 

6) Remove the journalling from the ext4 filesystem to prolong the disk's life.

7) Disabling the nepomuk desktop search thing as in my current system.


Feel free to make any additional suggestions. I am mostly in hurry for 1-3  as they are in the pre-installation stage, others can be tweaked  afterwards as far as I know. I was hoping to install tonight :D

Thanks in advance!

================================================================

**UPDATE**:


Alright, after my research of the ssd info I looked for I came to some  conclusions and made the following settings. All are according to the  numering of the questions I issued in the beggining.

1) Regarding partition allignment, created partitions by:

    ```
sudo parted /dev/sda unit MiB #(change the unit to MiB) 
mklabel msdos #(make new blank msdos table) 
mkpart primary 1 20481 
mkpart primary 20481 102401 
quit
```2) No swap. Still looking into the spin down thing, I think I read  that hdparm in installed by default for 12.04 but no spindown occurs if  the pc is on AC power. So I guess it works out of the box for laptops,  not desktops. Hevent found a gui utility in muon software center, maybe  I'll research more on it at a later time.

3) exactly as described, see (1)

4) Not enabled, will do it manually when I feel like it. Once every week  or so, maybe less. Read somewhere that automatic trim makes deleting  files slower.

5, 6, 7) unchanged

Extras:
1) Set Bios mode to ACHI

2) No Writes for Read Timestamps:   added noatime, nodiratime in etc/fstab
[http://askubuntu.com/questions/1400/...he-os-for-ssds]("http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds")

3) scheduler = noop:               I added added the following command in in /etc/rc.local. Same link as before.
     ```
echo noop > /sys/block/sda/queue/scheduler
```Lots of thanks to everyone for their interest, I'll make further updates if anything interesting comes up. bb!

---

### Post by darkod on 2013-02-11
1. Current versions of ubuntu leave exactly 1MiB at front when creating the first partition with Gparted. That complies with the partition alignment.
Better yet, use parted from live mode to create partitions with exact start/end as you wish:
```
sudo parted /dev/sda
unit MiB #(change the unit to MiB)
mklabel msdos #(make new blank msdos table)
mkpart primary 1 20481
mkpart primary 20481 102401
quit
```

That will create exactly 20GiB and 80GiB partitions, leaving 1MiB in front of the first one. The ssd is aligned.

During the install use the Something Else option and reuse the existing partitions by selecting them, clicking Change at the bottom, and set the correct mount point for each.

2. Yes, you can do without swap, especially if you have loads of RAM. But if you use some huge programs with data and the RAM gets filled, there will be no swap to use.

3. You can leave part of the ssd unused, so you later have space for new partitions. No problem about that.

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by darkod on 2013-02-11
I agree, you should take steps to make things work better on the ssd, but don't get too "paranoid" with it.

For TRIM to work I have only added discard option in fstab, and noatime which I think reduces writes.

If purchased new, they come with years of warranty and by the time it runs out, you will probably want a new one anyway. :)

---

### Post by zahtar on 2013-02-11
Guys, thanks a lot for your input.

Darkod, I'll install the ssd and do the things you mentioned (in ther code) through Partrition editor in my current setup. But before that, 2 questions:

1) Why not make an extended partition and put them inside? On the other hand the remaining space (~11GB) is not enough for many partitions...

I have 4GB ram and I almost never do multitasking. Hardest thing I can remember was torrent + watching movie, or torrent + burning iso or something. Not many tabs in firefox or many office files run at the same time. So I guess my ram is already too much to get filled.

2) How about the spin down option, will it work if I set the swap at the hdd?

Thanks again in advance :)

---

### Post by oldfred on 2013-02-11
I used gpt on my SSD as suggested by the arch site.

       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
    
but Windows only works with gpt partitioned drives if booting with the new UEFI. Ubuntu works with BIOS if you add a tiny bios_grub partition or with UEFI with the required efi partition. (I added both since I now have BIOS but may move drive to a new system with UEFI).

With gpt I think the main advantage is that it has a backup partition table and there are no logical partitions. 

Gparted automatically aligns partitions, so that is not an issue if you use a recent version of gparted.

       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

    
Altough I just saw a new comment that noop may not be the best scheduler. The alternative for SSD may be deadline. I think cfg is the default which is good for rotating drives.

---

### Post by zahtar on 2013-02-11
**oldfred**, thanks for your reply but I can't understand the biggest part of your post.:confused:

I did understand that gparted aligns partitions but I just did what darkod suggested earlier through terminal. I now have th e two partitions (not formated) plus the unallocated space.

Should these commands you mentioned be used after installation?

```
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
```by changing in bios the mode to achi, could my current setup stop working? (only kubuntu12.04, now in "native-ide" as the bios indicates. no other OS intalled)

Thanks again

---

### Post by darkod on 2013-02-12
> **zahtar said:**
> 

1) Why not make an extended partition and put them inside? On the other hand the remaining space (~11GB) is not enough for many partitions...



While having only logical partitions (in extended container) can work for linux, I personally don't like creating them as logical when we are talking only about two partitions.

I see the extended partition as something you would use after you already have 3 primary, so instead of creating 4th primary which is the limit, you create logical partitions (extended container).

For two of them, I don't see a point to be logical, but it will work. Up to you.

---

### Post by Thee on 2013-02-12
> **zahtar said:**
> Thing is, that I would also  like the hdd to spin down when not in use.

As far as I know, SSD's have no moving parts, so there is nothing to spin down.

---

### Post by oldfred on 2013-02-12
I have changed from IDE to AHCI and back. Ubuntu booted either way, but my old XP on another drive,  only booted with IDE not AHCI. There are AHCI drivers for XP but just about have to be loaded during install. Since I have been promising to shut my XP down for almost 5 years, my new SSD forced the issue. :)

---

### Post by darkod on 2013-02-12
> **Thee said:**
> As far as I know, SSD's have no moving parts, so there is nothing to spin down.

The OP was referring to putting the swap partition on the hdd to save the ssd. And is wondering if in that case the hdd can spin down or having swap on it is considered as using the disk and it will never spin down.

Personally, I don't know if it spins down when swap is on it. When swap is not used, I would guess it spins down.

---

### Post by Thee on 2013-02-12
Ah ok, I got that wrong then, sorry :)

---

### Post by markbl on 2013-02-12
> **darkod said:**
> 
For TRIM to work I have only added discard option in fstab, and noatime which I think reduces writes.

I use the *noatime* option on my ssd but not *discard* as you are better off doing the trim by adding a "fstrim -v /" to your /etc/rc.local. Ref [https://patrick-nagel.net/blog/archives/337](https://patrick-nagel.net/blog/archives/337) (in particular, see first reply there from OP Patrick).

---

### Post by zahtar on 2013-02-17
Hello all! 

I'd like to thank everyone for their help. I updated my initial post with the settings I made, and marked the thread as solved.

Further comments and suggestions are always welcome ):P

---

