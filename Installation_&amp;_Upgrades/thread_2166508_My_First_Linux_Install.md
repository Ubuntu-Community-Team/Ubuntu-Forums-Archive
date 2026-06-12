---
title: "My First Linux Install"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by TravScrog on 2013-08-09
Well, I'm new to this whole shin-dig. I have a MacBook Pro 7,1 and I am going to attempt to install Ubuntu 12.0.4.2 on it.

My question is, since there are newer versions available, will Linux allow me to update straight to those after I do the initial install? Or do I need to download the newer version?

My only other question is about [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) - it only shows 12.10 as being supported (not 12.04). So, will I be able to update to this if I install 12.04? Will 12.04 even install? If not, where can I download 12.10?

Thanks,

Travis

---

### Post by Netstatus on 2013-08-09
First of all: welcome to this shin-dig!

> My question is, since there are newer versions available, will Linux  allow me to update straight to those after I do the initial install? Or  do I need to download the newer version?
This should answer it: [http://www.techrepublic.com/blog/linux-and-open-source/upgrading-ubuntu-1204-to-1210/](http://www.techrepublic.com/blog/linux-and-open-source/upgrading-ubuntu-1204-to-1210/)

> My only other question is about [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)  - it only shows 12.10 as being supported (not 12.04). So, will I be  able to update to this if I install 12.04? Will 12.04 even install? If  not, where can I download 12.10?
I doubt that if 12.10 is supported, 12.04 will work much worse. I'm quite certain you'd at the very least be able to install 12.04.

---

### Post by Netstatus on 2013-08-09
Keep in mind that Ubuntu 12.04 is a long-term support release (it will be supported until April 2017), while 12.10 will be supported for a shorter duration (18 months, I believe)

---

### Post by BlinkinCat on 2013-08-09
This - [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

shows that 12.04.2 is a LTS release with support to April, 2017

Cheers - :)

---

### Post by TravScrog on 2013-08-09
Thanks for the replies! I did install it successfully, however I am confused about the partitioning. Now, I'm not really technical with computers, but I'm certainly not computer illiterate (just to give you an idea of whom you're working with).

Before I started the install, I went ahead and partitioned my HD using Disk Utility and I set it up as 100 GB, and named it LINUX HD formatted in FAT-32. (I read that Linux likes FAT32 better than anything else (?). Hope that's right.) During the install, I came to the partitioning part. I did the first option( run Linux alongside OS X), but it only recognized the LINUX HD partition and then wanted to partition that further. I thought this was wrong, so I clicked on the advanced part to view the 6 hidden partitions. I saw my OS X partition, my 'LINUX HD' partition, and some other small partitions (I assume are from OS X and deal with the actual OS and whatnot). I tried to get it to go through there, but it was trying to get me to reformat the partition from there. I decided to go back to my first choice and just split the partition 50 GB and 50 GB, hoping that they would both somehow end up available for Linux use. This was not the case. I only was showing ~45 GB of free space. I went back to OS X to look through Disk Utility and it shows:
150 GB - Travis' HD (Mac OS Extended) --- good, this is my OS X partition and all is well
50 GB - LINUX HD (MS-DOS (FAT32)) --- a solid 50 GB off
1 MB - disk0s5 *(**not mounted) * - what...
46 GB - disk0s6 *(not mounted) *(MS-DOS (FAT32)) - why...
4 GB - disk0s7 *(not mounted) *(Linux Swap) - ugh...

I see the problem and all, I just need some guidance on how to correct it. Do I need to repartition the entire HD and then reinstall Linux and let it partition it?

---

### Post by Bucky Ball on 2013-08-09
*Thread moved to **Installation & Upgrades**.*

Welcome.

Don't bother partitioning with anything prior to installing Ubuntu. Just make sure you have enough free space and the partitions will be created when you install onto it. Linux uses EXT* partitions and you can't create them with Win (or Mac I don't think) anyway. Ubuntu WILL NOT install onto any other filesystem.

Some points:

1/ Ubuntu will read/write to NTFS and FAT partitions (and Mac) fine. Win has no idea what an EXT* partition is so if you want to share, create an NTFS partition;
2/ I always sit down with a pencil, piece of paper and beverage of choice, relax and make a solid plan of how the drive is partitioned and how I want the drive to be partitioned before I commence the install;
3/ I repeat, create free space and install to that by using 'Something Else' when you get to the partitioning section;
4/ I know you have, but back-up anything you don't want to lose before attempting any install;
5/ Generally, a drive can have no more than four primary partitions, unless you're using EFI, which is when things can get complicated. You can have as many virtual drives (logical partitions) inside an extended partition, though, and Ubuntu will live happily on one (unlike Win).

Linux does *not* like FAT better than anything else. FAT is dated and has limitations. It likes EXT.

Suggestions: Use this as a dry run and learning experience. Kill that ugly FAT partition and post a screenshot of Gparted so we can see exactly what is on that drive and how it is currently partitioned. Also, and this might work in Mac, could you post the output in the terminal of this command:

```
sudo blkid
```

If not, run from a Ubuntu LiveCD desktop (the screenshot from Gparted would be best from here also if you don't have a working Ubuntu install). 

As of 13.10, the cycle will be nine months for regular releases (I believe). LTS releases appear every two years and are supported for five (14.04 LTS the next one - 14=2013, 04=April). With a regular release, you can ONLY upgrade from within the system to the next release, 13.04 to 13.10 say. This may change. With LTS releases, you can skip everything in between and upgrade from 10.04 to 12.04. 

Not uncommon to use an LTS as your main squeeze, the stable monolith(!), and have a few playthings on other partitions which you can experiment with and happily break without loss.

LTS the best place to start, intended to be the most stable and for production machines/servers and anything else that is required to be rock solid.

* Just a note, there are many variations to how you might go about setting up your partitions/install. Basically, Ubuntu has a / partition and inside that will create, by default, a /home directory for settings and your personal data; Vids, Music, Documents, etc. Which is where the fun starts. You can create a separate /home *partition* rather than having the default directory, separating your data from the OS (installed on /, the root partition). This has benefits. Ubuntu can then be installed on a 15Gb partition with room to spare. Your /home partition can be as large as you like.

Another option, and my preference due to its flexibility, especially between installs, is to install / with the /home directory inside there, delete the user directories (NOT hidden settings directories) and replace them with symlinks to existing directories on another partition. This partition can be any format Ubuntu can read/write to, not necessarily EXT*.


Just thought I'd throw that in. ;)

---

### Post by TravScrog on 2013-08-09
Bucky Ball,

Thanks a lot for the help, but some of that went straight over my head, lol. I have attached the screenshot and this is what Terminal in Ubuntu returned. (It did not work in OS X.)
/dev/sda1: LABEL="EFI" UUID="2860-11F4" TYPE="vfat" 
/dev/sda2: UUID="6bdf5385-699d-3124-afc8-2b9d9509b3f2" LABEL="Travis' HD" TYPE="hfsplus" 
/dev/sda3: UUID="6606363e-480d-3bc5-9b54-4f0e05317c5d" LABEL="Recovery HD" TYPE="hfsplus" 
/dev/sda4: LABEL="LINUX HD" UUID="7FB4-190B" TYPE="vfat" 
/dev/sda6: UUID="a5b05ae8-7b0b-44e3-92f9-ffedefe9e202" TYPE="ext4" 
/dev/sda7: UUID="2b15fe0d-ed85-4192-af89-030e4659cd36" TYPE="swap"

I have Linux up and running, I was just wanting to get the partitions straightened out. Also, what exactly are the benefits of separating the /home folder? And how exactly do I go about doing it?

Thanks

---

### Post by Bucky Ball on 2013-08-09
Well, if the system breaks or you just want to do a clean install, everything is stored elsewhere on another partition. Kill / and reinstall. Your personal data will remain where it is, on the /home ***partition***. If it was inside the /home ***directory*** in /, on the other hand, gone.

For resizing partitions, don't resize Win install partitions (or Mac I imagine) with Gparted. Do it with Win apps else risk a complete mess and possible non-functioning,  broken system. For resizing Ubuntu partitions, they need to be unmounted. Consequently, best to do all resizing of EXT with Gparted while running from the LiveCD (you can't resize / if you are running the OS installed on it).

/dev/sda4 is called Linux HD but is, in fact, available to all OS's (as it's FAT) and would act more like a shared partition for data you want to be able to access from everywhere. Getting back to my last post, your alternative to the separate /home partition would be to create symlinks in the /home directory *inside* the install (/) to personal data directories on /dev/sda4 (or /dev/sda*, actually). 

This way, all OSs have access to whatever is in your /home partition, not just Ubuntu (impossible if the /home *directory* is inside / on an EXT partition). 

Hope that helps and is a bit clearer. ;)


* Note: Just looking at your Gparted screenshot, and as an example, say you want to use 'Travis HD' as your existing data partition, forgetting about the 'Linux HD'. Open up your /home directory in the Ubuntu install. Copy the directories (NOT hidden ones or Desktop) to the HFS+ partition. Delete the directories inside /home. Create symlinks to the directories on HFS+. A symlink can be achieve with this syntax:

```
ls -n /path/to/source/directory /path/to/symlink
```

For instance, say you want to create a link to your Documents directory on your desktop:

```
ls -n /home/username/Documents /home/username/Desktop/Documents
```

Voila! You will now have a link on the desktop which, when clicked, will actually open the Documents folder at /home/username/Documents. This is great but can get confusing, as you can imagine, if you start getting carried away with symlinks! ;)

Finally, I have no idea whether Ubuntu reads/writes HFS natively, but here are some tips if not:

[http://www.beingmanan.com/wp/2008/07/accessing-ext3-ntfs-hfs-via-windows-ubuntu-os-x/](http://www.beingmanan.com/wp/2008/07/accessing-ext3-ntfs-hfs-via-windows-ubuntu-os-x/)

Right near the bottom read 'HFS+ in Ubuntu'. Cheers.

---

### Post by TravScrog on 2013-08-10
That helps a lot! I really get the whole moving the /home partition by itself and I understand creating symlinks to access it easily from my desktop and such, but how do I make sure the OS knows where to look? Just store them in all the folders? If so, that seems like a lot of work. Is there a program or anything that can automate some of it?

---

### Post by carl4926 on 2013-08-10
FYI: FAT32 is restrictive,wouldn't NTFS be better?
Why do you want to clutter up the desktop, all the partitions are accessible via Nautilus

Having /home on a separate partitions keeps all your personal files and settings safe during upgrade

---

### Post by Bucky Ball on 2013-08-10
Ubuntu will know what to use. In the partitioning section, you will find that along with / as a default mount point, there is also /home, /boot and some others. If you choose the /home as a mount point for a partition, that's what the system will use for /home.

Also, if you had an existing mount point named /home at install, you simply mark that partition to use BUT NOT TICKED TO FORMAT and the new install will automatically use the existing /home (same with /swap). 

As for the symlinks, if you do a regular install (/home directory inside /), when you enter your /home directory, you will see your personal folders. Copy them to the partition you want to use for your personal data (doesn't have to be a /home partition), delete the originals in the /home directory (once you have double checked the data is present and correct where you copied it to) and create a symlink there to the copied directory on the data partition.

(On a fresh install, there will be nothing in the Documents, Vids, Music, etc. directories, so you can just create data directories wherever you like, kill the empty originals in the /home directory and create symlinks to the folders you have created.)

The symlinks can link to anywhere. A directory on the same partition, another partition or disk, /Music symlinked to a /Music partition and /Video to a /Video partition. Whatever you fancy. However you go about it, you will have Ubuntu installed on a modest sized partition and your data stored securely elsewhere. ;)

So, you can have /home on a separate partition, set during install (this is the regular way of going about it but, although trickier, you can move /home later) or have a /home directory inside / which is, in effect, empty but for the symlinks to other directories elsewhere (giving the impression you have done a regular install with /home inside / with your personal data in there, but it's not!).

> **carl4926 said:**
> FYI: FAT32 is restrictive,wouldn't NTFS be better?

Having /home on a separate partitions keeps all your personal files and settings safe during upgrade

Both correct. NTFS definitely preferable.

---

### Post by Bucky Ball on 2013-08-10
This explanation and attached screenshot might make it clearer.

- sda1, 2 and 4 are Win (primary) partitions (sda2 Windows7, sda4 Win recovery);
- sda3 is an extended partition which takes up the rest of the drive (and reaches the four partition limitation for partitions on a single drive);
- sda5-12 are all logical partitions *inside* the extended partition (as they are inside the extended partition, only the extended partition is counted, they are virtual drives within that and 'don't count' as primary partitions).

* The logicals are self-explanatory pretty much, but I have Xubuntu 10.10, Xubuntu 12.04 regular install and a 12.04 minimal install, along with a EXT4 partition with nothing in it and another, LFS, which is ready for experimenting with Linux From Scratch, when I get around to it. /mnt/Misc is my 'shared' NTFS partition (not FAT) shared between Ubuntu and Windows. People generally call this something like '/Shared' but the choice is yours.

* The three installs all use the /storage partition as /home. I'm in my main, stable squeeze right now, the mini install, which see it as /storage. Other installs see it as /home, names change, but the /dev/sda*s remain the same, naturally, while the mount point names vary (as does what is mounted at boot and what is linked to in /home directory).

Things have changed as it's grown but for now, 10.10 sees /storage as /home, has no symlinks in / and everything is 'normal': Ubuntu with a separate /home partition. 12.04 and mini both use symlinks to get to /storage and, effectively, have no data inside the /home directory in /. ;)

---

### Post by TravScrog on 2013-08-10
[COLOR=#000000][FONT=Helvetica]Alright, so I deleted all of the Ubuntu partitions and attempted to reinstall. When it came to the partitioning part, it did not have the easiest option - only the options to replace OS X or advanced. I clicked on the advanced part (sorry, I really can't remember the proper names) and it would not let me resize the partition. So, I went back to OS X to resize (tried to, found out I had accidentally deleted my recovery partition, then proceeded to use my recovery USB) and left 100 GB of free space, assuming Ubuntu would know to use the free space. Went back to install and the easy option was back. I clicked it thinking i I would have to opportunity to do some simple partitioning, but it just started instead. Not really a big deal. It did use the free space, and I have everything updated and running properly. I have a screenshot from Disk Utility (I didn't want to install anything while it was installing the 300+ system updates) for you to look at. Did it separate stuff by itself? (I only think this because there is the 4 GB partition.)[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Anyways, you're better at this than me so you can instruct me on what to do next! I do want to separate /home by itself.[/FONT][/COLOR]

---

### Post by TravScrog on 2013-08-10
I would also like to add that Mac OS X's Disk Utility lists the 96 GB partition as FAT32. Either the install did that or rEFIt did that.

---

### Post by Bucky Ball on 2013-08-10
I repeat, EXT partitions are unpredictable as to what they'll show up as in anything but Ubuntu/Linux. The Mac and Win reports are redundant here. Win would show those partitions as 'unknown' but 'healthy' so disregard the Mac readout. What it shows up in in Gparted is all that matters here.

Did you choose 'Something Else' at the partitioning section? The option to manually partition is there, must have been overlooked. (Advanced probably has the 'Something Else' option somewhere.)

---

### Post by carl4926 on 2013-08-11
> **Bucky Ball said:**
> 
Did you choose 'Something Else' at the partitioning section? The option to manually partition is there, must have been overlooked. (Advanced probably has the 'Something Else' option somewhere.)

As in
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png)

---

### Post by TravScrog on 2013-08-11
No, I chose to install alongside OS X hoping it would do everything right and not allow me to goof it up, lol.

---

### Post by Bucky Ball on 2013-08-11
And so it did, creating a /home directory inside /.

You can now put symlinks inside that /home linking for directories in 'TravisHD', for instance ...

Remembering the OS itself is taking up less than 10Gb of /, the system is configued to keep a lot of information in the /home directory of /. 

You could make changes from here, now or later, quite easily (for instance shrinking / to 15Gb and making the free space created into /home), so if you're happy for now, you're at a good place to start exploring the OS. ;)

Good luck, enjoy the learning curve, the forums, and have fun.

---

