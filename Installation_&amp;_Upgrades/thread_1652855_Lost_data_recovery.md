---
title: "Lost data recovery"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by nathaliesicard on 2010-12-25
Hello everybody! 

Merry Christmas!

I come here for help, I am not a computers person and need some advice.

Recently I went to a lanparty and I deleted some important files without noticing.

My laptop is like this:
1 recovery files partition
2 windows vista partition 
3 ubuntu partition
It also has another small partitions that were automatically created, like the swap one

So I bought an external hard drive with 750gb to save more stuff at the lanparty.

I was having fun with that DC++ program, trying to download things in my windows partition. But I was running out of space, so I figured I'd save some stuff in my new hard drive and continue downloading in my internal harddrive (so that it was faster).

I had a folder with videos, named "Videos" where I had many family videos stored. It was like 3gb so I thought I'd back it up in the external hard drive and delete it. 
I thought I had copied it in the external hard drive and then deleted it off my internal hard drive.
Cleaned the recycle bin. Ran that freeing space tool of windows.
I had DC++ on so more stuff was getting downloaded into my hard drive.
BUT Somehow it wasn't there in the external harddrive and the folder of videos was lost. 
Since then, I've been trying to recover it.
I am not sure if I moved it to the external harddrive and deleted it from there or just never copied it to the harddrive and just deleted it.
I have run a program named GETDATABACK and ZERO ASUMPTION to the windows partition and the external hard drive without success. The folder is not there.

Is anything I could possible still do :(?

Thank you very much! I'd appreciate any help

---

### Post by AbeJarano on 2010-12-25
You really should check the Windows forums for this.  Did everthing in Windows so maybe cut and paste into Annoyances.org??

---

### Post by searchfgold6789 on 2010-12-25
For partition and even in most cases file recovery, I do not hesitate to recommend an all-platform program called testdisk, available from synaptic. It has never failed me for recovering daa from sometimes horribly mangled partitions, usually in pristine condition.
If that doesn't work, then I recommend PhotoRec (also available for any platform from synaptic), which is made by the same guy. It probably works just as well.
Merry Christmas to you too,
 - search

---

### Post by nathaliesicard on 2010-12-26
Thanks guys!

I've downloaded that testdisk program, But it doesn't have a graphical view right? (I can only run it from the terminal)

What option should I choose in the program? Because it just seems to check the disk, not recover data

Thanks :)

---

### Post by MarkAlter on 2010-12-27
Hi nathaliesicard

You must try some other software also sometimes there are situations where a particular software doesn't work but other can recover your data intact. I have personally used one such good software you can also get it free from [http://www.softpedia.com/get/System/Back-Up-and-Recovery/Kernel-FAT-and-NTFS.shtml](http://www.softpedia.com/get/System/Back-Up-and-Recovery/Kernel-FAT-and-NTFS.shtml)
There in no need to worry in the situation as, you might be worrying about the data is the data safe or not the data is safe even if it is formatted the data is there in the hard drive and its not been deleted. you just need to read the software instruction and see data being recovered.

---

### Post by Mark Phelps on 2010-12-27
Sorry to tell you this but GetDataBack is one of the BEST NTFS data recovery products available.  A similar product (but slightly better in my experience) is Recover My Files -- made by the same folks as GetDataBack (Runtime Software).

IF I were you, I would do the following:
1) Download the trial version of Recovery My Files from Runtime Software
2) Install it to the MS Windows partition that did NOT contain the now-missing folder
3) Run that software against the MS Windows partition that IS missing the folder
4) Allow this to run in its most thorough option available -- which means, it may need to run all night to completely scan the partition.
5) When done, look to see if the folder was found -- and look at the files found within it.

If the folder and files were found OK, you will need to purchase the SW to do the actual recovery. Last time I checked it was aroung $70 US.

But hey ... it's your data ... it's your money.

And, don't listen to folks telling you your lost data is perfectly safe ... because it is NOT.  Every time you boot into the OS that contained that folder, you write some files into it.  And every time you do that, you worsen you chance of being able to recovery anything.

---

### Post by presence1960 on 2010-12-27
> **Mark Phelps said:**
> Sorry to tell you this but GetDataBack is one of the BEST NTFS data recovery products available.  A similar product (but slightly better in my experience) is Recover My Files -- made by the same folks as GetDataBack (Runtime Software).

IF I were you, I would do the following:
1) Download the trial version of Recovery My Files from Runtime Software
2) Install it to the MS Windows partition that did NOT contain the now-missing folder
3) Run that software against the MS Windows partition that IS missing the folder
4) Allow this to run in its most thorough option available -- which means, it may need to run all night to completely scan the partition.
5) When done, look to see if the folder was found -- and look at the files found within it.

If the folder and files were found OK, you will need to purchase the SW to do the actual recovery. Last time I checked it was aroung $70 US.

But hey ... it's your data ... it's your money.

And, don't listen to folks telling you your lost data is perfectly safe ... because it is NOT.  Every time you boot into the OS that contained that folder, you write some files into it.  And every time you do that, you worsen you chance of being able to recovery anything.

+1

I would not boot to windows other than to run data recovery software. If you want your data back you must not use the partition that contained the deleted data. Hopefully you haven't done too many write operations already to prevent full recovery of the data.

---

### Post by Sef on 2010-12-27
> I would not boot to windows other than to run data recovery software. If you want your data back you must not use the partition that contained the deleted data. Hopefully you haven't done too many write operations already to prevent full recovery of the data.

Good Advice. Deleting a file does not remove it from the hard drive. It simply removes the link, so that the system can find it. Therefore, your data is on the disk; however, by using that partition, the data that you want saved can be overwritten by new data.

---

