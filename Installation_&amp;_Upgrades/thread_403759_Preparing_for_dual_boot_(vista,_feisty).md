---
title: "Preparing for dual boot (vista, feisty)"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by Onesimus on 2007-04-07
I am wanting to have my laptop capable of dual booting either Windows Vista or Ubuntu.  I currently have Windows Vista installed on my laptop.  I have read on the forums and they indicate that I need to shrink my Windows partition down, so the unallocated space can be used by Ubuntu.  

However, Vista only allows me to shrink the partition by a maximum size (based upon the contiguous free space).  I have a lot more free space on my laptop, but because of the unmovable files I cannot shrink it any further.  I am aware that there is a program GParted provided with Ubuntu - is this capable of shrinking the Vista partition beyond what Vista is actually capable of doing itself ?  (I read the GParted home page - but it got a bit techie).

Or is there a way of moving the unmovable files in Vista ?

---

### Post by confused57 on 2007-04-07
> **Onesimus said:**
> I am wanting to have my laptop capable of dual booting either Windows Vista or Ubuntu.  I currently have Windows Vista installed on my laptop.  I have read on the forums and they indicate that I need to shrink my Windows partition down, so the unallocated space can be used by Ubuntu.  

However, Vista only allows me to shrink the partition by a maximum size (based upon the contiguous free space).  I have a lot more free space on my laptop, but because of the unmovable files I cannot shrink it any further.  I am aware that there is a program GParted provided with Ubuntu - is this capable of shrinking the Vista partition beyond what Vista is actually capable of doing itself ?  (I read the GParted home page - but it got a bit techie).

Or is there a way of moving the unmovable files in Vista ?
I can't help you with freeing up more space, but don't use Gparted to resize your Vista partition.

---

### Post by BuddhaNature on 2007-04-08
Dud reply - sorry messing up getting the hang of this 'editing' thing.

---

### Post by BuddhaNature on 2007-04-08
Dud reply - please ignore.

---

### Post by BuddhaNature on 2007-04-08
Hello Onesimus,

I am intending to install Ubuntu to a Win XP system.  I have no experience of using a Vista system so I cannot comment if the following **will work** for you, but it may be worth a try.

Firstly, go here and download 'BootIT-NG':

**[CENTER][http://www.terabyteunlimited.com/bootitng.html]("http://www.terabyteunlimited.com/bootitng.html")[/CENTER]**

Secondly, make up the floppy boot disks ('master' and 'backup') as recommended in the BootIT manual (copy from the website).  Having done that you now have a tool that can, among other things, resize and move partitions around.

Thirdly, **backup all personal data files** on your hard-disks to cd/dvd.  (That way if it all goes wrong you still have your own data.)

Fourthly, defragment all the partitions on your hard-disk.

Fifthly, boot the computer from one of the BootIT floppys.  Once BootIT launches do not choose the 'Install' option, choose 'Maintenance' (mode).  Once in Maintenance, choose 'Partition' (work).  *[Note: the 'Install' option would install BootIT to your hard-disk.  Once that was done you would have access to all functions of BootIT without recourse to the floppys.  At the same time BootIT would also install as a a 'boot manager'.  This is potentially useful as it has boot manager functions that surpass anything else I've read of.  I would like to use it as a boot manager myself across a Win XP and Ubuntu system but I don't know how to do that yet as my understanding is that Ubuntu installs its own manager, probably to the MFT, and that would mess up BootIT.  I will be posting to Ubuntu experts to see if there is a way of getting Ubuntu to install its own manager to /root rather than MFT.]*

Sixthly, before even attempting to resize partitions make an image file of at least your Vista boot partition (you can image other partitions if you want to play doubly safe).  For instructions on doing that goto:

**[CENTER][http://www.heffy.com/image.htm]("http://www.heffy.com/image.htm")[/CENTER]**

and watch the relevant video under the section titled:

**[CENTER]'Using BootIt Next Generation'[/CENTER]**

Lastly, now that you have the image file made, you can start to resize the partitions.  For details of doing that look at the BootIT manual and at the support/help pages at the TeraByte (BootIT) website.  *[Note: BootIT runs at DOS level (it does have a GUI so you don't need to know DOS) and so launches prior to any OS being launched.  Because of this BootIT can be used irrespective of what OS(es) you have installed to you system.]* 

If anything goes badly wrong restore your OS from the image file you made, though if you have altered the boot partition size you might have to re-size it back to what it was before - given that is the issue that Vista might 'complain' about.  *[I know that I could do this kind of thing confidently on an XP system, Vista? - not sure.]*

Why might trying this work?  Because Vista itself - as the operating system - is preventing moving 'unmoveable' files **while you are inside the operating system**.  BootIT gets you out of the OS and hence BootIT should be able to move the 'unmoveables' during its process of reducing the size of the OS partition.  (Problem is, will Vista complain when you try to re-boot into Vista?)

Hope this helps.  Good luck.

P.S.  If you try this and it works out, or doesn't, it would be good to post to the thread with the result.

---

### Post by Onesimus on 2007-04-09
Hi BuddhaNature,

Thanks for your detailed reply.  I shall give it a try, but it may have to wait until the weekend because it seems fairly extensive.

---

### Post by matt_b on 2007-04-09
If you have a large block of unmovable files on your HDD, check to see if hibernation is enabled in Vista. If it is, disable it, reboot and see if they've gone - you should then be able to defrag and free up some contiguous space.

---

