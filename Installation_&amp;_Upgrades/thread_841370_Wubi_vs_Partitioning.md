---
title: "Wubi vs Partitioning"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by phil13 on 2008-06-26
I'm thinking of installing ubuntu. I was just wondering whether it matters whether I use wubi or do  the full installation? If I use wubi will I later be able to switch to full installation without losing all my settings/customizations?

I really don't want to damage windows-I know that it works! Partitioning doesn't look as simple as all the 'Ubuntu is amazing, just get it, ignore all it's faults' sites make out...how much danger is there of damaging windows? I don't have an installation disc so it really would be a problem.

[http://www.techsupportalert.com/review-ubuntu-hardy-heron.htm](http://www.techsupportalert.com/review-ubuntu-hardy-heron.htm)
That's put me off a bit...would it be best to just use wubi?

Thanks in advance
phil

---

### Post by avtolle on 2008-06-26
I currently am running Ubuntu 8.04 AMD-64 under a Wubi installation, and have had no problems with it. There is a way using LVPM to later take the Wubi install and make a true dual boot installation, in its own partition, etc. See the Wubi Forum for discussions on this (some folks have had problems). BTW, if you are interested, there is a new Wubi out (8.04.1) which has tried to fix some of the problems people have had with installing with Wubi; again, I refer you to the Wubi Forum.

Partitioning can be intimidating, especially the first time one does it. I've not had any troubles setting up partitions, but each case is its own, of course, and the past success doesn't mean I won't have a problem the next time. However, there is a lot of help available, and many resources to read before beginning, which is what I did. One can certainly damage Windows during partitioning if one is not careful, no doubt.

---

### Post by Perkins on 2008-06-26
I have found that Wubi is considerably slower than a full install, owing to the fact that it has to go through multiple steps to read and write from the disk.  Also, if your computer suffers a power failure during boot, I have had it render the disk unbootable.  I had to find a bootable CD with Microsoft chkdisk to recover it.  Not the end of the world, but a definite pain.

Partitioning is not as difficult as it used to be.  Modern partition editors like gparted, or the partitioner used by the Ubuntu install CD are usually capable of detecting how full the partition to be resized is, and adjusting accordingly.  Some are even capable of moving the data out of the way if necessary.  That said, there is still some risk.  You can minimize it by defragmenting your drive before you repartition.  Personally I recommend UltraDefrag, available from Sourceforge.  Its algorithm does a considerably better job of organizing the disk than the standard XP defragmenter, but it uses the windows defragment API to actually move the data, so it's just as safe.

If you're still worried about it, then my suggestion would be to get a second hard drive.  You can install Ubuntu on that, and the only thing you'll have to touch on your original drive is the bootloader.  Which the installer should be able to do for you automatically without any problems.  If you're ultra, ultra paranoid, then you can actually install grub on a floppy disk or CD and boot from that without altering your original drive at all.  Personally I do not recommend that last as it is a serious pain to deal with.  Just a second disk is a reasonable amount of paranoia.

If you're not sure that you want to make the change to Ubuntu, then Wubi is a great tool.  It will let you install and test it out with just a few mouse clicks.  If you like it then it's convertable to a full install, and if you don't, then it's removable with just a few mouse clicks.  Just keep in mind that a full install will run as much as twice as fast on some machines, so if slowness is your only issue with it, then try a full install.

The other thing is that Linux is actually capable of installing and running from a USB device.  So if you have a 6+ GB thumbdrive, or an external hard drive you can use that for your test installation.  (I do not recommend a thumbdrive for a permanent install since A: they are slow to access and B: they have a relatively short lifespan.  An external disk drive is acceptable, but you obviously need to be extremely careful not to unplug it while the computer is running. ;) )

---

### Post by Perkins on 2008-06-26
edit:  sorry about the double post.  My internet connection hiccoughed and weird things happened to my browser.

---

### Post by Spaceman9 on 2008-06-27
phil13 if you're really worried about damaging the partition Windows is in the best thing to do is buy a 40GB or bigger hard drive at ebay if you can/want to do that. A 3 or 4 year old 40GB drive should only cost you $20.00 to $25.00 and it solves all the problems of partitioning the drive windows is on.

Also if anything happens to one OS you have a fully installed OS on the other drive and you can keep working. I have Ubuntu 8.04 LTS on my boot drive and PCLOS 2007 on my second drive.

Most computer manufactures will send you a backup cd or dvd if you ask for one. Some make you pay for them and some don't. Some just make you pay for the postage and some will send one for free. 

In regard to the review you posted a link to, don't let it influence you too much. For the last year I kept trying different distros until I found ones that I like and that run well on my hardware. Now I'm free of paying an arm and a leg every 5 years to Gates ego and I like linux so much better than Windows I'd never go back to Windows.

Good luck with your adventures in linux.

---

### Post by housam on 2008-06-27
In your case Wubi is the best solution and it will not harm your windows . but you'll not be able to change to a complete fresh install from Wubi.

---

### Post by VMC on 2008-06-27
Phil, Full install would be better. If you follow instructions you won't damage Windows. It creates its own partitions. It's almost like your on another hard drive. There's boundaries to protect you.

The best advice I would offer you is to backup your Windows partition. I would do that no matter what you try. Good protection in case the worst comes to pass.

---

### Post by chubbtech on 2008-06-27
I am sorry to say that I somehow managed to corrupt my windows partition...don't know exactly how it happened but FYI it didn't happen when I installed Ubuntu... I think it's more along the way of upgrades or maybe even getting back some files from my Vista partition.

---

### Post by larry19l on 2008-06-29
> **Perkins said:**
> I have found that Wubi is considerably slower than a full install, owing to the fact that it has to go through multiple steps to read and write from the disk.


The issue is speed. All I needed to know. Got a new box: decent muscle and moved drives from the old one. So now, drool folks: AMD 9600 quad core HP Media PC, 5gig ram, 640gig C: (winVista h.premium), 1,000gig E: (WD Mybook 4 datafiles), 400gig Seagate Baracuda (D: for HH). Enough elbow room I think...

And a couple of USB WD pasports (80g & 120g). But you gave me an interesting idea: Using either one of the passports or an 8gig sandisk U3 cruzer, I would like to set things up such that when the cruizer or the passport drive is plugged in the system would automatically boot into HH and when not plugged in, boot into Vista. Is this possible and if so, has anyone done it or know how it could be done ? I don't mind some experimentation here but not much. Least, not until I get the old system (an HP/Compaq notebook) back to experiment with: Virtualbox,winXPpro32 & HH.

---

### Post by phil13 on 2008-07-09
Thanks for all your advice guys, and sorry it's taken me so long to get back! I have a 160gb external hard drive but I've allready had to claim on the warranty once - which worked but I think the reason it broke was because I partitioned it...

The Laptop I will be installing ubuntu on will be fully backed up, apart from windows! It's a Dell Latitude D520 - I'll probably see if it's got a recovery partition and reinstall windows anyway just so it's nice and clean.

Defragmenting isn't a problem - I've got various freeware programs that I use regularly.

I think I read somewhere that you can make a windows install disc from a fresh installation of windows - I guess I could do that just in case...

I'm now very excited about finally getting my hands on a proper installation of ubuntu! (I've tried installing it to a 4gb usb flash drive and it broke a bit too fast for my liking!)

---

### Post by Midwest-Linux on 2008-07-09
My experience with WUBI, is it didn't work correctly on the Vista laptop. While the actual install of Wubi and the 8.04 went well. On boot up I ended up with errors.

 Vista has a good, fast and easy partition shrink program built in to Vista. I shrunk the Vista partition by 12 GB. That part is called "free space". I installed Hardy on the freed space and the installation worked fine.

 Some say WUBI and Vista don't get along well, others might disagree. But my computer wasn't able run Hardy through Wubi, but ran perfectly on a direct install to the hard drive.

---

### Post by phil13 on 2008-07-09
Is it best to partition the hard drive before going through the installation process then?

---

### Post by avtolle on 2008-07-09
It's best to shrink the Vista partition (after defragging the drive at least twice) using the Vista resize utility, then install on the free space, allowing the installer to do the partitioning during the installation.

---

### Post by phil13 on 2008-07-09
I'm running xp...

---

### Post by avtolle on 2008-07-09
Sorry for the misread; if there is a native tool in xp to shrink the partition, I'd encourage you to use that but (showing my ignorance) if there isn't, then boot from the install CD, and allow the partitioner to shrink the xp partition and then install on the free space, as mentioned above. The defragging step is still needed, so do that first before starting the installation.

---

### Post by phil13 on 2008-07-09
Thanks for all your help, I'm sure I'll be getting back to you once it comes to the installation - there's no such thing as an error free process!

---

### Post by Sar on 2008-07-09
I was running a wubi installation, and dual booting prior to that between XP & Vista.

Wubi installed fine on 10Gb of free C:\ space, and after a week of tweaking I converted it, using LVPM, to a full installation on a 30Gb partition created using gParted, which I find to be a great tool.

I have now bought a new 500Gb sata drive which I've partitioned up with 200Gb of ext3 space for my new Ubuntu installation, with the remaining space (265Gb due to losing 35Gb through formatting, which is normal) dedicated to a fat32 partition, which I intend to share between the 3 OS's.

I tend now to use Ubuntu day to day, and only really go into either Windows variant in order to play PC games, as Wine I find isn't terribly good at running anything pretty recent (IE 2003 on).

It plays City of Heroes and Diablo 2 fine, but Beyond Good and Evil and The Witcher do not to run at all.

---

