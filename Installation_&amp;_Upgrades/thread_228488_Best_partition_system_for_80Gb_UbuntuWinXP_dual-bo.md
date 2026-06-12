---
title: "Best partition system for 80Gb Ubuntu/WinXP dual-boot"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by allanlewis on 2006-08-03
Hi,

I've got a laptop with an 80Gb HD, currently with 3 partitions, as shown in the attached PNG. (Ignore the first ~1GB partition, that's just a "recovery" system installed by Acer at the factory and can be safely wiped as I have the same on my recovery disc.)

Can anyone give me any advice on how best to use this space if I were to reformat the whole drive? i.e. I would prefer to have a separate partition for /home, so how big should that be? etc etc.

(I assume I would have to install Windows first, and I know about partitioning using GParted before running the Ubuntu installer.)

Also, is the default swap partition size created by Ubuntu sensible? When I run system monitor it always seems that hardly any of it is being used. (I have 512MB of RAM.)

Also, given the current situation in my attached PNG, is there a simple way I can remount /home on a separate partition without re-installing anything?

Thanks in advance!

---

### Post by kaffelars on 2006-08-03
If you want to reformat the drive, you should definitely install Windows first. During the install, create a Windows partition of the wanted size (hard for me to guess how much you need for this).

The Linux swap partition should be 1,5-2 times the size of your RAM (if you have 1GB RAM, 1,5GB or 2GB of swap space should be fine.

On my laptop I have a 15GB root-partition (this is way more than enough), if you're not going to install **everything** I think 5GB should be enough.
The home partition should be much larger, at least if you want to store something else than documents. If you make this about 50GB, you have a lot of space, and still have some room for Windows with applications (about 25GB, probably a little less). I think the Windows partition can be resized when you install Ubuntu, if you have changed your mind since the Windows installation.

But, this is **just a suggestion**! It suits me, but probably not everyone else ;)

---

### Post by VK2XCI on 2006-08-03
A Hint ;) 

I put a 1Gig FAT32 partition straight after the Win NTFS partition. I use it for documents such as OOo, PDF and HTML that I want to write to from both OS's. Trying to figure out how to share things such as Thunderbird Emails and Firefox Bookmarks too.

---

### Post by allanlewis on 2006-08-03
> **VK2XCI said:**
> Trying to figure out how to share things such as Thunderbird Emails and Firefox Bookmarks too.

Try Google Browser Sync, it's great. Adds a few seconds to Firefox's startup time but works really well. [http://www.google.com/tools/firefox/browsersync/index.html](http://www.google.com/tools/firefox/browsersync/index.html)

Also, I use FAT32 for my WIndows partition because then I can run Windows apps via Wine without the problems associated with NTFS on Linux.

Also, thanks for your suggestions - any more, anyone?

---

### Post by kaffelars on 2006-08-03
Another possibility is to mount EXT2 and EXT3 in Windows. There's one driver called Ext2ifs (this only supports EXT2) but I believe there's also one that supports EXT3.

---

### Post by allanlewis on 2006-08-03
I have such a driver already installed, and I would rather use ext3 as a format for my "shared" storage partition, but I was looking for advice on how big each partition (namely: WinXP, Linux /, Linux /home, and shared data) should be to use my 80Gb most efficiently. Obviously I could resize later with PM in Windows or GParted in Ubuntu (or whatever partition app Knoppix comes with) but I'd like to get it about right first time.

---

### Post by kaffelars on 2006-08-04
Of course, it's always best to get it right the first time :)
But it's difficult to say what's the optimal solution for others. For example, if you need Windows for 10 different games you need a lot more space than if you use Windows for just one application.

I think the person who's in the best position to decide is you, because you know all the details of your needs :)

---

### Post by Megamanic on 2006-08-04
I'm in a very similar position to you.  Laptop, 80Gb HDD Dual boot still necessary :sad: 

First off take how much space you need for XP - depends on how many apps you need to install.  I gave it 20Gb which turned out to be plenty.  If I had my time again I'd go for 15Gb still...

Allowing 15Gb for "/" as partition 3 and 1Gb (RAM x 2) swap as partition 4 I get 49Gb left for an EXT3 partition 2 for shared data.

Sounds good to me.

You could go for the experimental NTFS driver but we don't want to go there do we? ;)

Why oh why can't windoze do mount points?  I would LOVE to be able to map "Program Files" and "Documents and Settings" to separate partitions so when I reinstall I don't lose all of the apps though with that disaster that is the windows registry you're usually out of luck anyway...

---

### Post by allanlewis on 2006-08-04
> **Megamanic said:**
> I'm in a very similar position to you.  Laptop, 80Gb HDD Dual boot still necessary :sad: 

<snip>

Allowing 15Gb for "/" as partition 3 and 1Gb (RAM x 2) swap as partition 4 I get 49Gb left for an EXT3 partition 2 for shared data.

<snip>

Why oh why can't windoze do mount points?  I would LOVE to be able to map "Program Files" and "Documents and Settings" to separate partitions so when I reinstall I don't lose all of the apps though with that disaster that is the windows registry you're usually out of luck anyway...

Do you (or does anyone else) know if Windows would have a problem installing programs on an Ext3 partition, given that the IFS driver makes such partitions appear to Windows like any other? Obviously, if I reinstalled Windows, I'd have to reinstall that software to restore the registry entries, but this would mean that I could make my Windows partition minimal size, perhaps even 5Gb or so (does anyone know the official minimum for a full XP Home install?) and then install any big apps (e.g. games) on the FAT32 "storage" partition.

Hmmm... lots to think about for when I next reformat!

---

### Post by richbarna on 2006-08-04
I have installed windows on a 3 Gb hardrive, the operating system needs about 3Gb once it gets running.

My recommendation for an 80 Gb harddrive is the same as I have got.

The first 20 GB is Windows
The next three in the extended (light blue) partition are Linux distros.
The last in the extended partition is Ext 3 storage partition(I recommend you use Fat 32) for access from Windows. I don't need it so I used ext 3.
Then finally 1Gb Swap. It's a good system if you want to use different linux distros later, you don't have to mess around with partitions.


[IMG]http://ubuntuos.wordpress.com/files/2006/07/new-partitions.png[/IMG]

---

