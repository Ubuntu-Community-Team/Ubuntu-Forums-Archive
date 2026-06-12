---
title: "Ubuntu with Winxp installation"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by dhawald3 on 2006-10-05
I am having intel 845gebv2 MOBO with p4 1.8 Ghz
and a ATI Radeon 7000 series graphics card.

Right now I am having
Winxp and Win2K on my pc.

I want to replace Win2k with Ubuntu.

what is the shureshot method of installing it,
without any glitches occuring.

I cannot afford to reinstall Win XP](*,)  if some problem occurs.

I would prefer stability of Winxp and Ubuntu over fancy bootup.

please help.

---

### Post by Pjotr123 on 2006-10-05
How much RAM does your PC have?

Greeting, Pjotr.

---

### Post by imaginos on 2006-10-05
**_(!) Assuming that your XP is on hda1 (C:\)**_:

The most simple method, in your situation, is to install Ubuntu on formatted partition where w2000 was (formated as ext3 filesystem). Ubuntu will install GRUB, and rewrite MBR so GRUB will be invoked at startup. Then, GRUB will let you choose if you want to start XP or Ubuntu.

This is ok, and it works, but it would be a good idea (in your case) to let MBR load ntldr (windows loader) and make ntldr ask you if you want to continue to XP, or chainload GRUB->Ubuntu. This way you will not disturb XP boot in any way, and you can remove Ubuntu if nessecary, and XP will not know about it. It is not so simple procedure (it is more boring that complicated), so if you want that info, I will write it.

---

### Post by Irony on 2006-10-05
Personally I would boot into XP use it to delete 2K (leaving it unallocated).

Before shutting XP down I would then put the Ubuntu CD in the drive and then shutdown.

Now boot up and install Ubuntu to the unallocated free space - put GRUB to the MBR.

---

### Post by Senshi on 2006-10-05
In any case, you should have a backup of all your data.  The way I see it, you should never be in a position where you can say, "If this gets fubar'ed, then I'm screwed."

Yes it might be a pain to backup your data, depending on how you do it, and a pain to reinstall everything.  But in the end it will be better than not having any data.

---

### Post by dhawald3 on 2006-10-05
> **imaginos said:**
> **_(!) Assuming that your XP is on hda1 (C:\)**_:

The most simple method, in your situation, is to install Ubuntu on formatted partition where w2000 was (formated as ext3 filesystem). Ubuntu will install GRUB, and rewrite MBR so GRUB will be invoked at startup. Then, GRUB will let you choose if you want to start XP or Ubuntu.

This is ok, and it works, but it would be a good idea (in your case) to let MBR load ntldr (windows loader) and make ntldr ask you if you want to continue to XP, or chainload GRUB->Ubuntu. This way you will not disturb XP boot in any way, and you can remove Ubuntu if nessecary, and XP will not know about it. It is not so simple procedure (it is more boring that complicated), so if you want that info, I will write it.



I have my (c:\)(containing boot.ini) as fat 32 drive and
windows Xp is in (e:\) which is NTFS

also shud I leave the win2k drive unallocated or partition it as
ext3 file system using partition magic 8 from windows.

---

### Post by imaginos on 2006-10-05
> **dhawald3 said:**
> I have my (c:\)(containing boot.ini) as fat 32 drive and
windows Xp is in (e:\) which is NTFS
is win2k on C: ?
It would be a good idea to make ghost image of C disk before you start any installation. Also, you should have Win installation CD so you can do fixmbr if something goes wrong. Having Win install CD and ghost image of C: should provide you the ability to restore system very quickly if something goes wrong.

> also shud I leave the win2k drive unallocated or partition it as
ext3 file system using partition magic 8 from windows.
I would leave win2k unallocated, and use Ubuntu tools to set things up: define 2 partitions: ubuntu root and swap (=RAM*2) and format them as apropriate filesystems (ext3 and swap).

---

### Post by dhawald3 on 2006-10-07
> **imaginos said:**
> is win2k on C: ?
It would be a good idea to make ghost image of C disk before you start any installation. Also, you should have Win installation CD so you can do fixmbr if something goes wrong. Having Win install CD and ghost image of C: should provide you the ability to restore system very quickly if something goes wrong.


I would leave win2k unallocated, and use Ubuntu tools to set things up: define 2 partitions: ubuntu root and swap (=RAM*2) and format them as apropriate filesystems (ext3 and swap).


No the c:/ drive is empty(containing only boot.ini)
Win 2k is on a third drive G:/

---

### Post by Irony on 2006-10-07
If 2K is on a separate drive then the installation is very simple.

Leave the separate drive as unallocated freespace.

When it comes to installing simply direct the installer to auto install to this freespace - it will divide the freespace into swap and root automatically.

Personally I would then install GRUB to the MBR - it will detect XP and Ubuntu, so you choose what to boot into on boot up.

And as noted backup everything first.

---

### Post by imaginos on 2006-10-08
Now you have this situation:

MBR->ntldr->
1)XP
2)win2k


you want
MBR->GRUB->
1)ntldr->XP
2)ubuntu boot

or you want:
MBR->ntldr->
1)XP
2)GRUB->Ubuntu


First solution is easier in terms of installation. You just need to free the w2k paetition and let ubuntu manage its installation and it will also manage boot chainloading (as irony had said).
Second solution is maybe "better" in terms of your needs, because it forces XP boot sequence and xp boot/init will be independent of grub. In other words, nothing will change from the XPs point of view (I understand that XP is you primary tool). Whatever you do to Ubuntu or grub, will not affect XP booting. This may, or may net be important if you plant to learn/tweak Ubuntu settings and init files.

Anyway, I believe that both solutions will work just fine.

---

### Post by randell6564 on 2006-10-08
> **Irony said:**
> Personally I would boot into XP use it to delete 2K (leaving it unallocated).

Before shutting XP down I would then put the Ubuntu CD in the drive and then shutdown.

Now boot up and install Ubuntu to the unallocated free space - put GRUB to the MBR.

This is EXACTLY how you SHOULD do it! You are already familiar with your Windows disk manager, I assume, so go in and delete your Win2k partition and reformat it as Fat32, (This way the Vfat will be easier for you to recognize when you are in the Ubuntu partition phase of your new installation!)  
Tell Ubuntu to install to that partition.  Ubuntu will automatically reformat the Vfat to Ext3 and add the needed partitions for Swap etc...,and install the GRUB-Bootloader to you MBR, giving you your dual-boot option.

---

### Post by lugduweb on 2006-10-08
> **randell6564 said:**
> ...go in and delete your Win2k partition and reformat it as Fat32, (This way the Vfat will be easier for you to recognize when you are in the Ubuntu partition phase of your new installation!) ...

What for ? Sorry, but I find this step useless...
Ubuntu install works very well with ntfs. You can also resize a ntfs partition into a ntfs and an ext3 partition...

---

### Post by randell6564 on 2006-10-08
> **lugduweb said:**
> What for ? Sorry, but I find this step useless...
Ubuntu install works very well with ntfs. You can also resize a ntfs partition into a ntfs and an ext3 partition...
Well, ONLY because for those who are not yet familiar with Linux, I think would find it less intimidating if they could actually SEE a partition that they recognize while at the partitioning phase of the installation rather than just being asked if they want to use the "available free space".  

In my opinion when a new user is presented with that question, they are still unsure of thier answer!  They dont want to harm thier existing OS, They are unsure of what "use available free space" means, AND Linux Identify's partitions as hda, hdb, sda..etc, rather than what a regular Windows user is use to seeing, C, D, E, etc...

So, by formatting the partition as Vfat, Ubuntu will CALL it Fat32 therby making it easier for the new linux user to locate and identify the partition that he/she wants to install to without the stress of wondering if they made the right decision!

I dont know.,maybe this same idea works formatting as NTFS as well.  The whole point is to just make the partition that you want to install to recognizable during the partitioning phase of Ubuntu, eliminating the stress of wondering if you are about to screw-up your exsisting OS!

---

### Post by brickbat on 2006-10-10
I just got a new HD and I am considering this very question.  I have installed Ubuntu at least 5 times and I think that chaining it from ntldr is safest.  You keep you mbr in pristine windows XP condition and if you decide to remove Ubuntu, you don't have to stuff around with recovery disks.

It is fiddly but not particularly difficult or unsafe since you don't touch your xp other than ADDing a line to boot.ini

I would take up imaginos on his offer for some free specific instructions for this.

---

### Post by imaginos on 2006-10-10
> I would take up imaginos on his offer for some free specific instructions for this.
I am very glad to help.

**WARNING**: English is not my native language, so if you don't _completely_ understand what I wrote, please ask. Read all steps before you start.
Also, feel free to edit this manual and make it better and easier to understand and follow.


-- -- -- --

Idea is to chainload GRUB after ntldr. 
Boot sequence will look like this:

MBR->ntldr->
1) Win XP
2) GRUB->Ubuntu

First, I will provide a short description of steps need to be taken (coarse grain story) before setting up the actual boot sequence, and after I will give a detailed instructions (fine grain "manual") for making the actual "boot system".

In order to install Ubuntu, we need to make some free space on a hard disk. That can be accomplished in several ways, but I will give one that seams most logical to me. I used Partition Magic to delete old (for example, Win2k) partition and format that unallocated space as two partitions. One is ext3, and the other is swap (twice as large as your RAM). The same can be done by using other tools (fdisk, Ubuntu CD, etc). 

Atfer this step, we need to install Ubuntu from live CD. Installation is simple, Ubuntu will recognize freshly formated partitions, ask you if you want it to install itself there, and that is it. 
**Important thing**: We should be aware that after Ubuntu installation, our boot sequence looks like this:

MBR->GRUB->
1) ntldr->Win XP
2) Ubuntu

-----

After the installation of Ubuntu, you need to take these steps in order to set the boot sequence described above.

Assumptions taken in this example:
- Ubuntu is installed on hda6. Change commands according to your actual state of partitions.

**1]** Restart Ubuntu

**2]** Go to terminal (Applications->Accessories->Terminal) and execute this command:
```
dd if=/dev/hda6 bs=512 count=1 of=lin_boot.bin
```
**Substitute hda6 with your Ubuntu partition!**
After this command you should have file **lin_boot.bin** in your home directory. The file is small, only 512 bytes, but it contains the boot sector of your Ubuntu partition. It will be crucial to have this file in the step 8] of this manual.

**3]** Copy that file to a floppy disk.
**I strongly advise you to make several copies of this little file!** 

**4]** This step is probably not mandatory, so I advise you to do it _only if you are 100% certain and understand what to do_. If not, jump to step 5].
Start terminal and type:
```
sudo grub
grub> setup=(hd0,5)
```
"grub>" is the prompt of GRUB program, don't type it.
Be aware of:
hd0 - primary/master hard disk (if your Ubuntu is installed on a slave hdd, change to hd1)
5 - partition number of **_hda6**_. GRUB counts from zero, not from 1!!!
This will install GRUB od partition hda6. GRUB is most likely installed there by Ubuntu installation, but I believe it is smart thing to do this anyway.

**5]** Put Win XP installation CD and restart computer.
Boot from that CD.
Wait several minutes until CD loads files and offers you to install, repair or exit.
Choose "R" - repair
Choose "1", or wherever is your XP located.
When asked, type administrator password.
When you see prompt C:\>, type
fixmbr
Next, type:
exit

**6]** Boot to Windows XP (not from CD!).

**7]** Remember that little file **lin_boot.bin** you had put on a floppy?
Copy it to C:\

**8]** Open file C:\boot.ini in notepad, and add the following line:
c:\lin_boot.bin="Ubuntu 6.06"

**9]** Reboot. That's it.


More theory and useful advices about MBR and boot sequences can be found here:
[http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd)

---

