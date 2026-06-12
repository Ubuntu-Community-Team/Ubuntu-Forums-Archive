---
title: "software to make backup CDs for Windows &amp; Ubuntu"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by boobahzone on 2008-10-05
Hi,

I just bought a new HP laptop that came with Windows Vista pre-installed on it.  I'd like make some changes to have my computer dual boot to Vista and Ubuntu, but want to backup my system before I do that.  I'd also like to periodically backup my system anyway in case of HD failures or if I screw things up on accident.

My HP came with software to create a set of backup CDs, but it says that it will only create ONE set of backup CDs, ever (and because they pre-loaded this software, they did not give me any installation CDs for Windows).  Is there a set of open-source software I can use to create sets of backup CDs for Vista and Ubuntu?  I'd prefer free & open-source if it's available.  If the same program can create backups of Vista and Ubuntu, that'd be especially great, but if I need two different packages that would be fine too.

Thanks for any help!

---

### Post by Rebelli0us on 2008-10-05
HP back up only burns installation CD to restore your system but it's not good at backing up your data.

In Windows, most CD burning software (like ImgBurn or Infra Recorder) will let you burn the contents of one or more directories to DVD. Windows doesn't recognize Linux file system, so you'd have to do that separately from within Ubuntu. Linux CAN read NTFS partitions, so that may work better for you if you want to do it all in one shot.

---

### Post by boobahzone on 2008-10-05
Thanks Rebelli0us,

I'm actually not too worried about my data, as I plan to periodically back that up which I've done before.  More, I'm looking for programs that will back up my system data, such as my OS (esp. Vista since Ubuntu as the live CD), programs, etc.  Any software that will do this?

---

### Post by cariboo on 2008-10-05
There are several ways to do what you want running linux. You don't even need to have it installed. dd will make an exact duplicate of your hard drive including the empty space to use it in a Applications-->Accessories-->Termianl type:

```
dd if=/dev/sda of=backup.iso
```

or you can install partimage in to ram, and run it. Partimage will make and exact duplicate of a partition but it doesn't include empty disk space. Optimally you would do your backups to and external drive and then burn your dvd's form the rsutling images.

Jim

---

### Post by boobahzone on 2008-10-05
I see... so I would likely need an external hard drive to do that?  

Also, is there a way to backup my Windows (not Ubuntu) system onto CDs?

---

### Post by cariboo on 2008-10-05
Yes you can use partimage on any type of partition, it doesn't care what is on it. It just duplicates the data byte for byte.

Jim

---

### Post by hwnddawg on 2008-10-06
If the HD in your HP is a Seagate or Maxtor, you can use the free version of (industrial strength) Acronis True Image.  Just Google "acronis seagate maxtor" for links such as this one: 
[http://mel.wordpress.com/2007/06/05/free-acronis-true-image-oem-for-seagatemaxtor-hdds/](http://mel.wordpress.com/2007/06/05/free-acronis-true-image-oem-for-seagatemaxtor-hdds/)

This free version needs to "see" a Seagate/Maxtor HD.  If that's not installed on your HP, you can connect a Seagate/Maxtor HD via USB so Acronis sees it, then backup to that USB HD.

Also, since Linux partitions are usually far smaller than humonguous Windows ones, i usually keep a backup copy of my entire ext3 partition stored somewhere on my Windows partitions and/or copy them to DVDs/external HDs.  I can also backup entire Windows partitions, but don't bother to do so, i just use MS's Documents and Settings Transfer wizard to save those settings.

HTH,

Wyn

---

### Post by FredKornyev on 2008-10-06
Hi,

Well at this point in time I am not aware of any free solutions to this, because I got my Acronis True Image ( [http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)) for free and that is what I use. 

If you really need a free app for this keep looking, but if you just want something compact and reliable try it out. You can save the partitions separately or all in one file, make backups of data, files, email and even the MBR. The backup usually takes around 10 mins (depending on how much data you have of course), and the restore process is about the same.

And yes, Generally you'd want to do this to an external HDD and then burn it to a DVD or two to free up the space on the drive, especially if the file gets big (with Vista it will get big).

Not sure if this is what you're looking for, but if you have questions regarding Acronis, let me know.

---

