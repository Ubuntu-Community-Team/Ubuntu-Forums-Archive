---
title: "I wish to install Ubuntu without GRUB &amp; select the OS in the BIOS hard drive order"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by John Kemp on 2010-09-03
I wish to reinstate Ubuntu on my complex system, and for reasons I shall explain **I want to select it by changing the order of the hard drives in the BIOS, and have nothing to do with GRUB or LILO.** I have a Windows XP SP3 machine with 3 hard disks: C 250GB D 250GB and E 300GB. **In the past I have been backing up by cloning to the two backup disks alternately.** *I used Acronis Disk Director Suite which has a component called Operating System Selector: a fancy boot loader with plenty of eye candy. It is designed to reside on (any) one place only, and backing up by cloning made such a mess of it that I had to abandon this OSS program, and I strongly suspect that cloning will mess up GRUB or LILO too.* I now select my disk by changing the order of the hard drives in the BIOS: inelegant, but reliable! **I have now repartitioned my 300GB E drive to a 40GB active partition on which I now want to put Ubuntu,** and a 260GB logical partition (which the system labelled G) which I am now using for the proprietory Acronis incremental backups as one cannot clone to a partition. I should add that all my data will be kept on the three Windows partitions. All my 4 drives are formatted NTFS. **I am now ready to put Ubuntu onto Partition E,** *and I want to do so in such a way that I can - indeed have to - boot into it by setting E as the first hard drive that the BIOS looks to to boot.* I could then continue to clone C to D (and D to C if C gets corrupted) and hopefully boot into C, D or E at will. I have the Ubuntu 10.04 DVD which came with "Ubuntu User" Issue 6. How do I do what I want, please? I am moderately computer literate with Windows, an almost complete novice with Ubuntu (a few weeks experisnce of 7.04) but VERY unknowledgeable, inexperienced, and nervous about fiddling about with the BIOS and the MBR.

---

### Post by uRock on 2010-09-03
If you run the installer and tell it to put grub in the / partition, then it will not install to the MBR. I am not sure if the BIOS will see it though.

---

### Post by John Kemp on 2010-09-03
Many thanks, uRock! I presume whatever hard drive is set as first in the BIOS will be seen as the / partition, so to do what I want I have to set to boot into E? I don't want to overwrite my Windows installation, though now I've got my first backup it wouldn't be a total disaster! (I should have added that I did a long overdue clean install last month. I have my Acronis backup on G, but not yet my clone on D as there's still some unique data on it). I'm happy to risk the BIOS not seeing my Ubuntu - at worst I'll just be back to square one with junk on my previously empty E drive! I should also have added that I may yet choose openArtist, an Ubuntu fork on the DVD - I presume I'll have the same installation options.

---

### Post by oldfred on 2010-09-03
Computers/BIOS only boot from the MBR, not the partition boot sector. BIOS will not jump directly to the PBR. You will have to use another boot loader and configure it to boot the install in the partition. With Ubuntu you have to have grub as that is what starts Ubuntu.

If you really want windows tools some have used EasyBCD. I do not recommend it nor have used it as I like grub2.

If you are doing backups that copy everything exactly you still have issues as partitions will have the same UUIDs and on a computer you cannot have two partitions with the same UUID without having issue. But for a good backup you want the same UUID so you do not have to reconfigure grub or fstab.

---

### Post by John Kemp on 2010-09-04
**Many thanks to uRock and OLDFRED.** *Sorry for a long post, but clarity is more important than brevity – readers need to know the whole story.* Just to show my level of knowledge, I had to look up the definition of a UUID, though I had heard of GUIDs and guessed it was similar! But though I’m entirely self taught on computers, I’m a retired research scientist, so hopefully reasonably intelligent.
[B]
I deduce I can and need to separate the two issues here: (1) cloning, and (2) dual booting XP and Ubuntu. [/B]I’m currently booting XP on disk D. I presume my MBR is on D as that is where I reinstalled XP recently. I was going to attempt to set E as my boot disk in order to install Ubuntu on it, without Grub, for intuitive rather than logically sound reasons – a little learning is a dangerous thing! 

**I have in the past had no difficulty in using disks C, D, and E with XP only, cloned alternately at will, by setting the computer to boot from whatever I wished, by changing the order in the BIOS.** I guess I didn’t deserve to be that lucky, because, as I now learn, the cloned disks will all have MBRs on them, and the same UUIDs: a case of fools rush in!  

**I infer from the above advice that if I leave the first hard drive as D – my current XP boot – and try to install Ubuntu from the DVD, I will get a choice of putting it into partition E? And in doing that, my MBR (presumably on D)will be overwritten by Grub2, giving me a choice at boot of XP (on D) or Ubuntu.** If I then clone D to C, nothing really changes if I leave the BIOS settings alone, and only access C for data. Right? BUT the MBR and UUID will have been cloned on C, and if I then set C as first hard disk for the BIOS to look at, am I right that it will see the cloned Grub on C, and again give me a choice of XP (now on C) or Ubuntu? [B]If I’ve got this right, I’ll have a setup and protocol I’m comfortable in managing.
[/B]
*Perhaps I should explain why my DVD is still in its unopened envelope – why haven’t I just got on with it? Four reasons. *(1) I don’t want to wipe a disk by mistake (2) I’m terrified of ending up with an unbootable system. (3) Recognising that I want to do something non-standard, I don’t want to be confronted with choices or problems beyond my skills, that I have somehow to solve on my own in real time!  (4) If what I want to do can’t be done, or can’t done by someone of my limited and patchy skills, I don’t want to waste time, with all the potential risks of dabbling out of my depth.
[B]
MANY THANKS to all you good people out there. The Ubuntu forum is the most impressive of all the many fora that I participate in![/B]

---

### Post by MartyBuntu on 2010-09-04
I manage a machine with a similar setup to yours...
XP/Lucid dual boot with XP and Lucid on two separate drives, backed up regularly with Acronis to a third separate physical hard drive.

I've never had any problems with Acronis messing up GRUB, but then again, I use the Acronis Recovery CD that is available to be made. It provides all the functions of Acronis without installing, you just boot from the CD.

If I may ask, why are you cloning the disks and not simply doing drive imaging?

---

### Post by John Kemp on 2010-09-04
Many thanks, MartyBuntu, for the information. Obviously, if you are reinstating to the same disk, a cloned GRUB and UUID is unlikely to be a problem. But have you ever reinstalled to a different disk, please? I would still welcome some reassurance that my protocol will work!  

I clone for two reasons: (1) it's the the ONLY way to be 100% sure that the backup is reliable; and (2) with hard disk failure, or serious corruption or malware, I can be up and running again in FIVE MINUTES! But as I said in my early post, my third drive is partioned into E (awaiting Ubuntu) and G, a logical drive that I use for a conventional Acronis imaging backup. Belt and braces approach!

---

### Post by oldfred on 2010-09-04
As far as fear of booting goes. I install a different operating system on every drive and have its boot loader in that drive so each drive could be booted on its own. Then whenever I do a new install I have a couple of liveCDs like rescue disk & gparted in addition to the install CD. I now also created two bootable Flash drives one a full install on a 16GB and now I use CD less and copy all the ISOs to a 4GB flash drive that I use grub2 to boot and use any ISO on the flash drive. I think I have both the belt and suspenders securely in place. 

I have found from my flash drive I can install to a previous partition in under 10 minutes, updates take longer and I do a lot of configuring but still fully set up within an hour. So I do not back up systems just the data. Some data is rsync'd to another partiiton on a different drive, some to my other computer and most to DVDs, but probably not as often as I should.

With the newer larger hard drives some users just put a operating system on the data drive just in case.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by John Kemp on 2010-09-04
**PLEASE &#8211; uRock, oldfred, and MartyBuntu, bear with me: Can one of you (or someone else) reassure me that I&#8217;ve finally got the situation right in Post 5 and in this post, please? ** I do introduce some new ideas here, but if I HAVE now got on top of the problem, with luck this may be last major post on this issue. In this case, I will hold back simply until I&#8217;ve cleared some unique data from C in order to make it available to clone D to C. I shall then (for tidiness&#8217; and tradition&#8217;s sake) make C my prime boot, and then install Ubuntu to E, accepting that it will have necessarily overwritten the MBR on C with GRUB 2. I shall then immediately re-clone C to D in order that my D backup has the GRUB boot loader (and UUID!)too.

**MartyBuntu: Can you or someone else confirm that Acronis backs up the Windows bootloader, please?** I think it must do! And if I did an incremental (or differential) backup of my XP disk to my data partition G after installing Ubuntu, I presume it must see to it that the auxiliary backup deals with the fact that the Windows boot loader has been replaced with GRUB?

**The help I&#8217;ve received so far convinces me that I can do what I want to do, but that I asked the wrong question &#8211; because the answer does not need to, and cannot, by-pass GRUB!** Am I right in my understanding of the situation as follows (which I have acquired from this and other threads): There can *normally *only be one MBR on a multi disk system, and this will be normally on the disk on which the default OS resides. To boot into any other OS requires either that the MBR be modified to provide this option (the standard setup), **OR **that the other disk(s) have their own MBR(s)which can only be selected by changing the hard disk order in the BIOS. If my default OS is XP on disk D, installing Ubuntu on E will replace the Windows MBR on D with GRUB 2, thus providing the choice of OS at bootup. If I then clone D to C, then C will have an exact copy of the MBR AND a duplicated UUID. I can boot into D or C by choosing which hard disk is set as first in the BIOS, and at that point I&#8217;ll also be given the option to choose the one and only Ubuntu installation if I so choose?

**If I ever had to reinstall Windows,** which hopefully will be a rare event, with my belt and braces approach to backups, it would overwrite GRUB 2 with the Windows MBR, and I  would lose access to Ubuntu, because GRUB 2 won&#8217;t be on that disk. Right? But in that case, it might be SIMPLEST (for newbies like me) to solve the problem by reinstalling Ubuntu as the easiest way to get the Windows MBR replaced by GRUB 2. 

**If I were to set the first hard disk in the BIOS as E** (currently empty and thus no OS to load!), **and then installed Ubuntu from the DVD into E, would it write GRUB 2 onto E, giving access to Ubuntu, but presumably no access to Windows because it wouldn&#8217;t know it was there?!!! I would then arrive at what I suggested in my very first post &#8211; and have access to any of my three disks with OS on, by changing the order of the hard disks in the BIOS? But I would not be attempting the impossible &#8211; to boot Ubuntu without GRUB 2.**I don't now plan to do things this way, but a (hopefully postive) answer to this question would boost my confidence in my understanding of the issues I have raised!

*I know I&#8217;m making heavy weather of this, but though this thread is very personal to my quirky needs, that answers that are coming out will I think be of value to others, by exposing alternative approaches to dual booting, and to backups. *

On a final point: am I right in thinking that my idiosyncratic suggestions would be just as applicable to dual boots of Ubuntu with VISTA or Windows 7 too &#8211; provided, as always &#8211; one puts Windows on first?  
[B]
Again, many thanks to you all![/B]

---

### Post by MartyBuntu on 2010-09-04
> **John Kemp said:**
> 

**MartyBuntu: Can you or someone else confirm that Acronis backs up the Windows bootloader, please?**

Acronis will backup the boot sector if you choose it to. 
You can backup up any partition, or exclude any partition you want.

---

### Post by MartyBuntu on 2010-09-04
FWIW, you are making this extremely complicated for yourself.

Acronis has the ability to simplify your backup strategy. Let it do all the heavy lifting for you.

P.S. *Acronis can also verify the drive image after it's made for reliability. There is no tangible benefit to a clone over an image for your purposes.*

---

### Post by oldfred on 2010-09-04
Install Ubuntu to what you call E: Windows mixes partitions and drives and calls them all drives. In linux drives are sda, sdb, sdc etc and partitons are sda1, sda2, sdb1 etc.

If you install Ubuntu to E: (and it is a drive not partition) then you can install grub2 to the MBR of E:. But grub normally defaults to sda as that is the common boot drive. There is an advanced button on the last partition screen that lets you choose which drive to install grub onto. Do not choose partition(s).
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)

Any multi drive configuration will follow this example:
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by John Kemp on 2010-09-07
**Thankyou, oldfred!  I shall be taking your advice **and see to it that GRUB goes on the boot sector of E, the disk on which I shall be putting Ubuntu. *For various personal reasons it will probably be 3 weeks before I do this *(shouldn’t be longer, MIGHT be sooner), but I SHALL be doing it. I think I’ve got my head round it all. (About time too!!!) What I will do, however is to wait till I’ve had a chance to clear my C drive, and clone my D drive – my current XP boot – to it. 

I have two reasons for this: (1) it’s one more backup – can’t have too many! (2) I shall then be in a very commonplace situation where my Windows is on C and I’m putting Ubuntu on another hard disk. I am confident that the wizard will let me do this because if there were any problems with this we’d know about them by now, and they would all be sorted out! But with XP on D, I’m less confident as it is such a non standard setup. By the way, I’ve had a think about WUBI but decided against. 

**What I expect to achieve is: C drive (sda) with a Windows bootloader on the boot sector, and my D drive(sdb), a clone of the C drive – identical in all respects including UUID. My third hard disk E (sdc)  is already partitioned in readiness, into E (sdc1) 40GB and G (sdc5) 260 GB – a data disk with Acronis backup (image, not clone) on it. Ubuntu will be on E (sdc1), as will GRUB2. I’m assuming GRUB 2 will point to C (sda) as the default for the XP choice at bootup. I shall be disappointed if it cannot easily be tweaked to point to D (sdb) for XP if my C drive fails, but I’ll cross that bridge when I come to it. I’m assuming that I shall have a second way of booting into C or D if disk E fails, by changing the boot order in the BIOS.**

So, I shall probably be absent from this forum for 3 weeks, but be back on to tell you all is ok – solved! – (Hopefully!) Again, many thanks to all you contributors!

---

### Post by oldfred on 2010-09-07
Grub uses UUIDs to boot but can use drive, partition like sda1. If you have cloned sda to sdb grub may randomly boot either if the UUIDs are the same. 

You can modify the settings to use sda1 instead of UUID for both grub and fstab to prevent that.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Search on UUIDs
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by John Kemp on 2010-10-05
**As promised **(or threatened, depending on your opinion of me!) – **I’m reporting back! **

Some progress, so far more in understanding rather than action (I've done a LOT of studying and googling on this), **thanks** in particular to **oldfred** and **MartyBuntu**! In brief, I’ve cleared my C drive of all except a little unwanted junk, and got everything I want onto my current first-boot drive, my D drive, which, I’m embarrassed to remind you, runs XP. I have imaged D (with Acronis True Image) to partition G on my third hard disk which Windows labelled E (and G also contains a few GB of extra not very important data that wouldn’t fit onto my D installation).
[B]
I understand the nature (if not the minutiae) of the advice on UUIDs and when I have solved this subsidiary problem it’ll be “all systems go!” [/B]It seems that whether I clone D to C, or reinstate a second copy of D onto C from my ATI image, I will end up with the same problem: two disks identical even to sharing UUIDs. From a very limited quick search, it seems that neither cloning software nor imaging software is designed for awkward people like me that want to have two cloned disks available at the same time, and a boot loader like GRUB that works with UUIDs rather than alphabetic disk labels, as does a MBR generated by Windows. 

**I greatly appreciate oldfred’s advice on using Linux programs to modify the boot to avoid the problems, and have just realised I can do this from a live disk.**  I had a brief go at Ubuntu 7.04; left off for some reason, and am now making a committed attempt to return to Ubuntu, but I’ am still a BEGINNER! So what then did was to research how to either edit a UUID with a Windows-based program, or at least something I can access from my Windows bootup (e.g. a DOS program), or do something (I have no idea what) I can do easily to one of the disks that will force a re-creation of a new UUID! But googling suggested that it was mainly users with Ubuntu already installed that encountered, and thus had to deal with, this problem of duplicate UUIDs. Windows users don’t seem to be as creative with their backup strategies!

*So, though my first reaction was to baulk at oldfred’s suggestion, as I wanted to sort it out with Windows or DOS procedures before installing and getting familiar with Ubuntu, further research suggested that I was being hasty. But I still really really want to change the UUID before I install Ubuntu, rather than fiddle with GRUB to make it select disks by letter rather than UUID. *

**The advantage of changing the duplicate UUID before I install Ubuntu is that the GRUB bootloader generated by the installation will not need any further modification, and I have the definite impression that changing the UUID is easier, quicker, and safer option.**

I’m currently studying the following threads:   [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=4135885]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=4135885")
[http://ubuntuforums.org/showthread.php?t=678629]("http://ubuntuforums.org/showthread.php?t=678629")
[http://hubpages.com/hub/Finding-UUIDs-numbers]("http://hubpages.com/hub/Finding-UUIDs-numbers")

**But my un-busy period is coming to an end, and I may choose to wait till I can find a very clear week, which could be mid-November.** [I]I don’t want to get Ubuntu installed and then have to leave it without the time to learn how to use it. 
[/I]
**But I’m very tempted to close this thread as [B]SOLVED ***now*, but hesitate because I have still not yet had time to confirm this by finishing and succeeding with my project. But maybe MartyBuntu or oldfred would feel able to reassure me that (1) yes, I seem to know now what I need to do, and should be able to succeed without further help, and (2) there’s enough on this post to help others who ask the same question! [/B]

---

### Post by oldfred on 2010-10-05
Even though I like to have good backups, I am one to jump in an do something and then when it does not work figure it out. (Maybe thats why I like helping out here in the forum:)).

If you change UUIDs then you do not have cloned drives that will work. Also a clone of a drive will only work when you replug it in where the original was as the drive order may be different otherwise. I think I suggested use sda1 notation, but actually labeling partitions and using the labels is the best way. If you follow your labels they never change where UUIDs can change only with major partition edits and drive, partition numbers sda1 etc can possibly change with any partition edit.

Since you are using a separate drive, just install to that drive, make sure grub installs to that drive's MBR and then learn about how good Ubuntu & grub2 is. Then you can update to use labels if you want for grub & fstab once you start to understand how they work.

---

### Post by John Kemp on 2010-10-05
Thankyou, oldfred. I nearly explained why I may seem a bit tardy over this, but my last post was already long.  I am cautious, with two good reasons! (1) My computer is a tool that I use for so many disparate tasks as an amateur astronomer, member of many committees of voluntary organisations, and as a language lab, darkroom etc. etc. that I cannot afford to be without it. (2) In doing my cloning, I ended up with an unbootable system, even changing the hard disk order in the BIOS to each disk in turn. Neither the System Mechanic repair CD nor the XP disk worked to repair the MBR. I have no idea what went wrong. The process should not have touched my first-boot OS - or the MBRs except on the new clone.  I've often cloned and am comfortable with it. But I’ve lost my nerve a bit! 

I was down to my last option: my Acronis image on my third hard drive, booting from the Acronis recovery CD. It reinstated over 200GB in less than half an hour, so quickly I thought something else had gone wrong! It's truly AMAZING software! It's softened my attitude to proprietary backups (you’ll be pleased to hear this, MartyBuntu!): I think what I'll do now is to make sure I've got enough backups, and I always 'validate' them, and then I’ll install Ubuntu to E and leave the cloning issue till later, as you, oldfred, advise, when I’m comfortable with editing GRUB with Linux software. (Btw, I assume this backup ‘validation’ works with checksums somehow? Surely it can’t be matching bit for bit – especially as it can all be done with the OS in use?) 

One thing worries me: “ntalamai”, post No. 6 in this thread [http://ubuntuforums.org/showthread.php?t=678629]("http://ubuntuforums.org/showthread.php?t=678629") says that with disks with duplicated UUIDs, GRUB boots into the “old” drive, and NOT at random: I presume he means that it was set up recognise a UUID linked to a drive in a particular physical location, and that if this is later cloned to another drive, it may be identical in all respects concerning the data in every section, but that since it HAS to be in a different physical location, which GRUB will not and cannot associate with the UUID, it will be unavailable to GRUB, and unbootable? I presume, oldfred, that this is the kind of issue you have in mind when you caution against trying to do what I want to do by mucking about with UUIDs? Looks as if I’d have to manually edit GRUB anyway to retrieve the situation, which removes the whole appeal – indeed, feasibility - of trying to avoid this by changing the duplicate UUID.

[B]I think what I’ll do is to ‘restore’ my system to Disk C (remember: for reasons of history my prime boot is XP on D at present) from the Acronis backup, and reset the BIOS to boot from C (if only because that it what my live Ubuntu install disk will be expecting!) and then follow the wizards to put Ubuntu  WITH - using the advanced options as necessary - GRUB onto E. If I’ve understood everything so far, I will have in effect two clones – C and D – because C will have been populated by a restoring a backup of D onto it. GRUB will have picked up C as the classic C drive, and either be unaware of D or will report it as unbootable. I PRESUME I AM RIGHT IN THINKING THERE’S NO WAY THAT IT’S PRESENCE, WITH A DUPLICATE UUID – CAN INTERFERE AND CAUSE PROBLEMS – THIS SUBTLE QUESTION IS OBVIOUSLY VERY, VERY IMPORTANT?!

If I then lose – by corruption or malware – my XP OS on C, I can set the BIOS to boot from D, but in doing so I’ll lose easy access to Ubuntu. OR – I can restore my C drive from a backup. 

If I lose C because of hard disk failure, I could, if I learn it up well enough, edit GRUB to point to D as my XP option till I get C replaced.

Am I finally talking sense, please?[/B]

---

### Post by John Kemp on 2010-10-05
> **oldfred said:**
> If you change UUIDs then you do not have cloned drives that will work. Also a clone of a drive will only work when you replug it in where the original was as the drive order may be different otherwise. 

Oldfred, Just one more point - I have used cloned drives as backups with XP with no problem. I'd never heard of UUIDs and could boot at will by changing the HD order in the BIOS. I therefore presume (am I right?) that the Windows boot ignores UUIDs? If it did use UUIDs, the problem that you raise would crop up here too. But surely, IF I change the UUID on a clone BEFORE I install Ubuntu, it'll accept the disk as it finds it? And if I change it AFTER Ubuntu and GRUB is installed, would it not be seen as equivalent to changing a hard disk? I can see that it might not immediately be bootable or even recognised and might have to be 'told' that there's a new disk - however one does that?

---

### Post by oldfred on 2010-10-05
I know with XP it boots from the MBR which just looks at the partition table for the active (boot flag) partition and jumps to the partition boot sector. The code in the PBR uses the boot.ini. Boot.ini has entries by drive and partition so it does not use UUIDs but is more like using sda1, sda2 etc for drive & partition info. I assume Vista & & do the same inside the BCD but have not reviewed enough BCD's to know.

We have seen several users with cloned drives that had issues with them booting the wrong (clone copy) drive. It may have to do which which drive the system sees first.

If you have two installs of windows mounted, I would expect grub's osprober to find both and it has two lines for finding drives, the first uses hdX,Y but the search uses UUID and the search line is after the set root = (hdX,Y). You can comment out the  search in grub and it will still work if the hdX,Y has the correct drive & partition. But the search exists because all drives do not mount as the same position in all systems. Some USB drives become sda, moving internal drives to sdb etc. My USB install get mounted as many different drive numbers depending on system and other drives installed, so search is the only way those work.

---

### Post by John Kemp on 2010-10-05
Many thanks, oldfred. I think we've reached the stage where I now have to "jump in an do something and then when it does not work figure it out" as you put it! I have enough crucial safeguards in place now to give me the confidence to go ahead. (1) I have enough backups and the one I've just used worked fine from a disk with no OS, using the Acronis recovery CD (2) I understand that provided I put GRUB on the Ubuntu disk E (I shall fiddle about till I manage to do this) I can't end up without a working or easily repairable computer, if only with XP. (3)I have plenty of experience of resetting the BIOS to choose which disk I boot into, and I understand that if I set the BIOS to boot into C or D I am independent of GRUB, and whatever mess I make of disk E the worst that can happen is that I'll have to put off my Ubuntu till I have time to sort it out. I do think I WILL be getting to this before mid November after all now, and I do NOT expect to fail! I'll report how I get on.

---

### Post by John Kemp on 2010-10-08
Well, I&#8217;ve jumped in. I ought to explain that the problem I had with my boot was that I was getting an error message &#8220;NTLDR is missing Press Ctrl+Alt+Del to restart&#8221; &#8211; I did this: endless loop. It corrected itself I know not how, and I ignored the problem. As I explained, I wanted the XP OS back on my C drive, so that I could present the Ubuntu install disk with a system that was commonplace, except for a second XP installation on my D drive, which I hoped it wouldn&#8217;t see. I restored my XP disk from my Acronis backup to C, and again ended up with an unbootable system. I got the same error message as before, but it did not go away. What puzzles me is that I could not boot into either C or D (by changing HD order n the BIOS), yet I had not touched the D drive! 

I took my box into the small local firm who assembled it for me, and the chap that did it (their Linux expert) recommended a reinstallation of XP. As I&#8217;d done this a month or so ago and had a nice clean system, I did NOT want to do this yet again so soon. I put my dedicated observatory laptop online and did some more googling. I found that this problem has cropped up over and over again, albeit at low frequency, with Acronis backups. The fix is given in [http://pctechnotes.com/how-to-fix-ntldr-is-missing-error/](http://pctechnotes.com/how-to-fix-ntldr-is-missing-error/)  - Use the XP installation disk, take the R option, and at the terminal 

copy e:\i386\ntldr c:\
copy e:\i386\ntdetect.com c:\

(If e ISN&#8217;T the Cdrom drive, and c ISN&#8217;T the OS and boot drive, amend drive letters accordingly!)

This worked! I also found out from other posts that you CAN muck up the bootup into a disk whose MBR you haven&#8217;t touched &#8211; I don&#8217;t understand this, but it&#8217;s a known happening, but thoroughly unnerving!

But on resetting the BIOS to C, the XP installation was slightly and subtly crippled: Scanner wouldn&#8217;t work, nor printer, and the Printer folder in the control panel was empty. I could not reinstall the printer, because it was picking up (presumably from the registry) my OS disk as D as that was what it was cloned from, and I had no option to change this! And Windows update wasn&#8217;t working properly either. Still booted into C, I copied NTLDR and ntdetect.com files from the C drive back to D, reset the BIOS to boot from D and I&#8217;m virtually back where I started a month ago!

That was yesterday. I learned today that my local Linux expert was leaving the firm and wouldn&#8217;t be available for any more help I needed. He also advised against trying to do what I wanted to do with the XP other than on the C drive. 

I then started looking into WUBI as an alternative, only to find out that it&#8217;s not quite as unproblematic or &#8211; even more important &#8211; as safe as I had thought.

I have always said that my computer is a tool not a toy. But I made a strategic mistake: as soon as I had a few days fairly free time in my busy (if retired) life, I turned immediately to my Ubuntu project. I discussed this with my wife and the bottom line is that I&#8217;m giving Ubuntu a miss for now. I spend FAR to much time on my computer, and if it ain&#8217;t broke, don&#8217;t fix it! My wife is right. But I feel very embarrassed about this, after all the time, effort and generous help that oldfred and MartyBuntu have put into this on my behalf. I&#8217;m sure oldfred has given me and others a workable recipe, but I can&#8217;t use it just now. I believe this thread should be closed as SOLVED, because there&#8217;s enough info there for anyone with more, courage, time, and stamina than I have to succeed in doing what I am suggesting, or something very similar. (But it&#8217;s also clear to me that having clones around is a can of worms). I guess it&#8217;s up to me to close this thread. Oldfred, do I have your approval to do this, please?

---

### Post by oldfred on 2010-10-08
My wife tells me I am on the computer too much, but I love it so she puts up with it, plus then I am out of her hair.:)

Hope you come back, I really like Ubuntu vs. my XP. Have not tried Vista nor 7. Both my kids have converted to Macs, and I am even having trouble getting them to install Ubuntu on their old PC to try it.

That said I still boot XP several times a week for one application I still have not converted as the linux equivalent is not quite as good, but getting closer.

Good luck and when you are ready, someone here will be glad to help you.

---

### Post by John Kemp on 2010-10-09
Thankyou, oldfred, for your gracious understanding and acceptance of my position. I guess you can read between the lines!  I WILL be back – “don’t know where, don’t know when” – to quote the song! I’ll look properly at the Live CD option to have a test drive: I might make a bootable USB disk I can use on my desktop or my observatory laptop; I might buy a cheap Dell or HP laptop with Ubuntu pre-installed. 

Currently I use my observatory laptop in emergency about twice a year if I’ve hit a problem with my desktop. It’s a hassle: updating the antivirus and Windows and putting it back online. I think I’ll regard my desktop C drive as a data backup (remember: my prime boot is XP on D!), knowing that I could boot into it if I had to, but I’ll not waste any more time repairing or updating the OS on C. I shall keep “My Documents” on C synchronised with the folder on my D drive, using Argentum Backup (a delightfully simple and unpretentious program that I used to use: it gives one the option of backing up as simple file copies – such that they are accessible to Linux, unlike Acronis backups!)

I’ll probably get another 16 or 32GB USB stick and set it up with Ubuntu, Firefox (with my bookmarks), Open Office, and the GIMP (or Photoshop Elements under WINE), my address list and old emails, and my most important key documents. I can use this to test drive Ubuntu “at my leisure”, giving me emergency access to my full data repository on C if my D drive fails, and it’ll give me some access to my laptop if that plays up too. **I’ll close this as SOLVED in a few days time unless you, oldfred, or anyone makes a further post that suggests it would be appropriate in the interests of the wider community to keep it open for a little longer to clarify any points raised. **

My thanks to everyone who has participated in this thread.

---

### Post by oldfred on 2010-10-09
USB install is a way to test drive Ubuntu, just realize it will be a little slower as flash drive writes are very slow.

Karmic install with encryption, but current versions are similar and you do not have to encrypt.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Some settings Herman mentions in above link to reduce writes.
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

See C.S.Cameron Posts ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
[http://ubuntuforums.org/showthread.php?t=1539342](http://ubuntuforums.org/showthread.php?t=1539342)
[http://ubuntuforums.org/showthread.php?t=1556519](http://ubuntuforums.org/showthread.php?t=1556519)

---

### Post by John Kemp on 2010-10-12
Thanks again, oldfred! I left this thread deliberately for a few days to see if there were any more posts. I've been revising all the posts in order to make a final summary post and then close the thread as SOLVED, but I've had another idea that I'd welcome your comment on, oldfred (or anyone else!)

I understand that mucking about with UUIDs can make clones ( or presumably any disk) unbootable. But what if one changes the UUID by "legitimate" operations? What I have in mind is a sneaky way to solve this problem: to repartition a disk by adding a new partition of say 1GB in some unused space. This will generate two new UUIDs for the now two partitions. If I then recombine the partitions, I'll get a new "legimate" UUID which, because of the random element in its generation, will NO LONGER BE A DUPLICATE of the one on the original partition! Problem solved?

---

### Post by oldfred on 2010-10-12
You can change a UUID.

Change UUID uuidgen tune2fs
[http://ubuntuforums.org/showthread.php?t=561080](http://ubuntuforums.org/showthread.php?t=561080)
tune2fs command with the -U option to change the UUID number in one of copy, (man tune2fs)

Anytime you muck with UUIDs you may have to reinstall grub2 or edit fstab. Just be prepared to do that if it does not boot.

---

### Post by John Kemp on 2010-10-12
What I have in mind is to change the UUID BEFORE I instal Ubuntu. Since Windows seems not to bother with UUIDs, I should be OK, am I right? I'm just wondering whether I'm right about an easy way to do this, as I've not found a Windows program to do this. I'm assuming that if I split a partition, the original (now diminished) partition is given  new UUID, and that when I recombine them, again we get another new UUID. I only need one of these premises to be true for me to succeed!

---

### Post by John Kemp on 2010-10-14
**SUMMARY AND CONCLUDING POST.** As I said, I’m having to close this post as for two related reasons: **(1)** I have always said that my computer is a tool not a toy, but if I continue with my project just now it will be turning into a toy, as my wife with some reason has been saying for some time!

**(2)** I’ve had so many unexpected problems (partly due to my attempts to use cloned disks as interchangeable bootups, as distinct from purely reserve backups) including ending up with unbootable systems, unnerving and difficult for me to solve, that I dare not **(a)** risk putting my computer out of action as it’s too important a tool, and **(b)** I cannot afford the time and effort to continue with this project at this time. 

However, I do believe that oldfred, MartyBuntu, and others have indeed given me the tools and the techniques to do so when I decide to return to Ubuntu, hopefully with a better thought out configuration. I won’t try to be too clever next time. There is such a wealth of knowledgeable info on this thread to help anyone with similar queries, that it is appropriate to close this thread as SOLVED, rather than let it hang and go to waste just because I’ve baulked (for honourable reasons – force majeure) at completing my project for now. 

**In summary**: I wanted to install Ubuntu, by-passing GRUB, because I wanted to choose my bootup from between Ubuntu and XP, and a series of clones – my perverse choice of backup procedure - of my XP disk.

I was quickly informed that Ubuntu requires GRUB. I learned also that I had a chance of succeeding IF I put GRUB onto the disk which was to contain my Ubuntu, but would have to edit it in order to have the access I wanted to my XP clones.

I tried to tidy up my system to put my main boot back onto C (for historical reasons it had been on the D drive) but ended up with an unbootable system due apparently to a quirk in my Acronis True Image software – or the way I used it - that I was using for cloning. My clone was missing the ntldr and ntdetect.com files that were essential for the XP boot.

I solved this but then found that my XP OS on C was subtly crippled – enough to make it unusable except in dire emergency. The problem appears to be that because it was a clone of an installation done on the D drive, all sorts of registry entries that would normally be to C were to D, requiring a horrendous amount of meticulous editing of the registry to sort out. I again baulked at this. One example: I couldn’t reinstall my printer (one of the things that was crippled) because the installation disk picked up that the OS was supposedly on D and tried to install the driver to D, with no option to choose C! 

I then again ran up against the problem that cloned disks have identical UUIDs, and that GRUB identifies disks by UUIDs rather than disk labels. I learned that it is possible to edit GRUB to use labels, but this process was way beyond my comfort zone, partly because most of the procedures put my way involved using a Linux bootup – with a live USB stick - but I was and am FAR too inexperienced with Ubuntu to tackle this yet.  

Again, my thanks to everyone who has contributed to this thread.

---

