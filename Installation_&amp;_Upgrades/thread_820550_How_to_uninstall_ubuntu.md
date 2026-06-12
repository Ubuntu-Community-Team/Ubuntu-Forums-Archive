---
title: "How to uninstall ubuntu"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by francoduina on 2008-06-06
I installed Ubuntu on my computer's hard disk and made some experiment. Now I want to uninstall it (completely), but I have no idea how to do it. Please help. Franco

---

### Post by zvacet on 2008-06-06
Boot your Ubuntu CD and when you come to the partition stage delete partitions.

---

### Post by meindian523 on 2008-06-06
or boot your Ubuntu CD,click System>>Administration>>Partition Editor and delete all partitions which have ext3/ext2/swap under the filesystem field.

---

### Post by francoduina on 2008-06-06
> **zvacet said:**
> Boot your Ubuntu CD and when you come to the partition stage delete partitions.

Thanks. When I start the computer, I am presented with an introductory page, offering a number of options (about whether to start ubuntu in different ways or Vista in two ways). If I delete the partition that ubuntu created during the installation, then when I start the computer that page starts, but then an error is detected and the computer freezes. 
Evidently ubuntu wrote something somewhere (not in C:. In fact, before installing ubuntu I created an Image of C:, that I recovered in the hope to eliminate the source of the introductory page...), resulting in the introductory page.
Any advise?

---

### Post by Rallg on 2008-06-06
May I politely contradict other users here?

In many cases, merely deleting partitions is NOT the correct way to uninstall Ubuntu (or any Linux). Here's why:

Your hard drive's Master Boot Record (MBR) starts the boot process, which must be continued via instructions elsewhere on the hard drive. On a single Windows-only system, the continued instructions are within the Windows partition.

When you install Ubuntu (or any Linux), the most common method involves changing the MBR, so that it directs continuation to the Grub bootloader software. This sofware might be located in one of your Ubuntu (Linux) partitions. If you simply delete partitions, you may delete Grub as well. Then, the MBR directs the boot process to continue at a location that no longer exists, and your computer cannot boot (not even to Windows).

Moral: Don't delete a partition that contains any part of the boot software. In Ubuntu (Linux), Grub is normally located at /boot/grub in your Ubuntu (Linux) partition. Always check to see what is there, before deleting the partition.

If you do delete the partition containing Grub, it is not the end of the world. You may be able to restore the MBR to its original code, from a Windows system install CD or DVD (without re-installing Windows). If you have two Windows systems present (XP and Vista), then that might not work properly.

As an alternative, you could probably re-create the deleted partition that contained Grub, and re-install Ubuntu (Linux) there. Then, you could remove all except Grub, leaving a small partition with only the Grub software. This won't always work, but it is worth a try if you cannot reconstruct the MBR and other way.

Sometimes, an installation of Ubuntu (Linux) will put Grub on a Windows partition. In this case, deleting the Ubuntu (Linux) partition does not trash Grub, so it is simply a matter of removing the unneeded entries from the Grub menu.lst file, or correcting the entries.

As for the exact situation for the original post, I don't know. But I did want to correct the suggestions about merely deleting the extra partitions. That won't always work.

IN THE CASE REQUESTED, it seems that Grub is still there. One possibility is that the partition numbers have changed. What used to be (hd0,3) might now be (hd0,2) or whatever, due to partitions being removed. Also, if a partition is re-sized (did you expand a Windows partition when you deleted Ubuntu?) its UUID changes. That is relatively easy to fix: Load the Ubuntu live CD. From Terminal,

ls -l /dev/disk/by-uuid

and have a look at the codes. Remember that /dev/sda5 is actually (hd0,4) in Grub (that is, subtract one from the sda number). Now, for the partition(s) containing your system(s), compare the revealed UUID to the value shown in Grub menu.lst. If there has been a change, then correct menu.lst.

---

### Post by Herman on 2008-06-06
> As an alternative, you could probably re-create the deleted partition that contained Grub, and re-install Ubuntu (Linux) there. Then, you could remove all except Grub, leaving a small partition with only the Grub software. This won't always work, but it is worth a try if you cannot reconstruct the MBR and other way. That will always work. We call that a 'dedicated GRUB partition'. That is very good and useful, I agree with that idea. :)


> If you do delete the partition containing Grub, it is not the end of the world. You may be able to restore the MBR to its original code, from a Windows system install CD or DVD (without re-installing Windows). If you have two Windows systems present (XP and Vista), then that might not work properly. Yes, it will work properly, and even if you don't have any Windows CD, there are many ways of returning your MBR back to its original condition or at least making it work as well as it used to again, look in this page here and pick out a way that's easy for you, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

> Sometimes, an installation of Ubuntu (Linux) will put Grub on a Windows partition. In this case, deleting the Ubuntu (Linux) partition does not trash Grub, so it is simply a matter of removing the unneeded entries from the Grub menu.lst file, or correcting the entries.Neither Ubuntu nor GRUB will write to your Windows partition, but if you installed [EasyBCD]("http://neosmart.net/dl.php?id=1") or [WinGRUB]("http://users.bigpond.net.au/hermanzone/p9.html") in Windows yourself then this scenario could be a possiblity. The Ubuntu installer doesn't install anything in your Windows partition normally though. Oh, except maybe if you use Wubi.

> In many cases, merely deleting partitions is NOT the correct way to uninstall Ubuntu (or any Linux). Here's why:

Your hard drive's Master Boot Record (MBR) starts the boot process, which must be continued via instructions elsewhere on the hard drive. On a single Windows-only system, the continued instructions are within the Windows partition.

When you install Ubuntu (or any Linux), the most common method involves changing the MBR, so that it directs continuation to the Grub bootloader software. This sofware might be located in one of your Ubuntu (Linux) partitions. If you simply delete partitions, you may delete Grub as well. Then, the MBR directs the boot process to continue at a location that no longer exists, and your computer cannot boot (not even to Windows).

Moral: Don't delete a partition that contains any part of the boot software. In Ubuntu (Linux), Grub is normally located at /boot/grub in your Ubuntu (Linux) partition. Always check to see what is there, before deleting the partition. I agree with all of that. :)

Regards, Herman :)

---

### Post by meindian523 on 2008-06-07
It's understood,IMHO,that once you delete Ubuntu's partitions,you also have to restore the MBR with fixmbr from the Windows CD.Why would you want a small partition restricting the number of partitions you can build on your HDD,when it can be removed and the computer booted with fixmbr?You save an insignificant amount of space,but more importantly,you save the potential of creating a partition if you need to in future.
Still,that was an enlightening post.Thanks for the lesson on how to do things a better way.

@Herman
Do you mean "a dedicated Grub partition"==" a partition for /boot"?

---

### Post by Herman on 2008-06-07
> It's understood,IMHO,that once you delete Ubuntu's partitions,you also have to restore the MBR with fixmbr from the Windows CD.Why would you want a small partition restricting the number of partitions you can build on your HDD,when it can be removed and the computer booted with fixmbr?You save an insignificant amount of space,but more importantly,you save the potential of creating a partition if you need to in future.:) Well, for one thing, not everyone is supplied with a Windows XP 'Installation Disc' when they purchase their new computer. Many computers come with a 'Recovery CD' instead, or, even worse than that, no CD at all, but a 'Recovery Partition' instead. Therefore, it might not be so easy for every Windows user to gain access to a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), so not everyone can use FIXMBR.

You don't *have* to run FIXMBR, there are lots of other things you can do with a MBR instead, Windows is quite independant from the MBR, and will boot just as readily from almost any boot manager, as long as Windows' boot sector is okay. 
The MBR, is not in fact part of the Windows partition at all. Well, Vista does tie itself to a MBR's 'Disk Signature' though, apparently, (however, GRUB doesn't touch that).

GRUB is actually a far more advanced and useful boot manager even for multibooting Windows than anything Windows has been able to come up with so far. 
The default method for Windows to dual boot, makes the new Windows OS give up it's vital boot files to the older system in the hard disk, (without warning the user), and makes the new system fatally dependant on the older system. Too bad when the old system gets a virus and needs to be re-installed. Read this to learn more, [Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")
After you have read all that, (sorry it's a lot of reading), you'll understand why it's advantageous to keep GRUB in a Dedicated Grub Partition even if you are primarily a Windows user, if you want to dual or multi boot Windows. (Pre Vista). Grub can be used as your 'third party boot manager', to 'hide' your earlier Windows install while Windows XP is installed so that it will retain its boot loader files.

 I don't think having a 'dedicated GRUB Partiiton will be quite as useful for Windows+Windows multibooting any more nowadays with Vista though. It may still be handy for Windows+Linux. From what I have learned so far about Vista, it seems as if they try to discourage people from having more than one operating system per computer. In my opinion, Vista's new boot manager doesn't make things easier for dual or multi booters, it makes things more complicated instead. A good website about Vista's boot loader is this one, [Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/"). 
A 'Dedicated GRUB Partition' might still be useful for continuing to boot the same Vista OS though, if GRUB is installed in the MBR and the user doesn't have the right CD.
ComputerGuru, the developer of NeoSmart Technologies [EasyBCD]("http://neosmart.net/dl.php?id=1"), has some help for Vista users though, they can download a Windows Vista Recovery Disc from here, [Windows Vista Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

> @Herman
Do you mean "a dedicated Grub partition"==" a partition for /boot"?      No, a 'Dedicated Grub Partition' contains only GRUB files, it does not contain any Linux kernel, and it is not part of any operating system. (GRUB is almost a small operating system on its own, it has its own [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), and can run commands all by itself, no OS required. 
The first place I read the term 'Dedicated Grub Partition' was in the following linked excellent web page,  [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm") by Steve Litt. That's a great site for reading up about how to use GRUB as well. :)

A 'Separate /boot partition' is a little different. It contains GRUB files, but it also contains a Linux kernel and some other related files, and is 'owned' by an operating system, and registered in that operating system's /etc/fstab file as the /boot partition, (belonging to that OS). Usually, a 'Separate /boot Parition' is created during the installation of an operating system if the user chooses that. The most command reason for needing one is to overcome a BIOS/harddisk size limit.
You could use a 'Separate /boot partition' as a 'Dedicated GRUB Partition', if the rest of the operating system was deleted.

Regards, Herman :)

---

### Post by meindian523 on 2008-06-07
> **Herman said:**
> 
You could use a 'Separate /boot partition' as a 'Dedicated GRUB Partition', if the rest of the operating system was deleted.

Regards, Herman :)

That was what I meant.Suppose you did make a /boot partition while installing Linux,then destroyed all the Linux partitions,save the /boot partition,what you have is a "Dedicated Grub partition"

---

### Post by Herman on 2008-06-07
> Suppose you did make a /boot partition while installing Linux,then destroyed all the Linux partitions,save the /boot partition,what you have is a "Dedicated Grub partition":) Yes, that's right.
You wouldn't necessarily need to have created a separate /boot partition during installation for that ide to work though, as Rallg posted earlier:
> As an alternative, you could probably re-create the deleted partition that contained Grub, and re-install Ubuntu (Linux) there. Then, you could remove all except Grub, leaving a small partition with only the Grub software. This won't always work, but it is worth a try if you cannot reconstruct the MBR and other way.
 :) Rallg is also correct, you could just have a normal default Linux installation and delete all of the files except /boot/grub and you would effectively have a dedicated GRUB partition. 
The only difference would be that you would have a boot folder in it named 'boot' with a 'grub' folder inside that, whereas in a normal dedicated GRUB partition you would only need the GRUB files, but that's only a trivial detail.

A dedicated grub partition would occupy very little space in a hard disk, and can be a primary or logical partition. If it's a logical partition then it won't interfere with the number of partition you can create per hard disk.

Regards, Herman :)

---

### Post by francoduina on 2008-06-09
Hello guys.

I've been absent for a couple of days, and only now I can realize that I opened a can of worms. Gee, thanks to all of you for your contributes, especially to Rallg.

After reading all the replies, I understand that on my HD the installion of Ubuntu modified the MBR to accomodate the address to the new /boot partition. I also understand that by deleting that partition the poor MBR was left with a non-existing address. BTW, I installed Ubuntu again and everything started working properly again.

But now I am still back to square one, with the same original problem: how do I uninstall Ubuntu? BTW, I have Vista, no CD, only a recovery partition. And I am far from being a guru.

Thanks...

---

### Post by Rallg on 2008-06-09
As long as you can boot to Windows (one way or another), then you don't "uninstall" Ubuntu or any Linux. You just get rid of it. That's because Ubuntu doesn't have a validation code, the way that Windows does.

If you have any personal files (documents) in Ubuntu, copy them to a Windows partition or to external storage.

Then, you could:

1. Re-format the Ubuntu partition(s) to NTFS or FAT32. That would make the partitions recognizable by Windows.

2. Delete the Ubuntu partition(s) and expand your Windows partition to occupy the released space. Do that using GParted from the live CD.

3. A combination of the above.

I recommend that you do not move the starting point of your Windows partition. On my old system, the information was somehow part of the Windows key validation (genuine). I don't know about now.

The next time you boot to Windows, it may claim that there are disk errors, and run the disk checker automatically. Don't worry. Then, when Windows appears, it may say that it "found new hardware" and ask to re-boot. Do it. All that's happening is that it is recognizing your new disk partition(s).

Again, if you find that the system becomes un-bootable, you will either need to restore the MBR from a Windows installaion CD or DVD if you have one, or install a minimal Grub in a small partition, just for boot purposes. (Or, there are other tricks.)

---

### Post by francoduina on 2008-06-09
Rallg, I followed your advise step by step, although I was pretty sure that this was the path I followed the first time. In fact, once deleted and reformatted the partition, and after having expanded the Window partition from which ubuntu had stolen the space. the partitons where exactly like they were at the very beginning, before my first ubuntu installation.

Then I re-booted, and the process froze, confused because, as you said, the MBR couldn't find the address it was looking for. 
So I installed ubuntu again, and all went well.

All this seems to confirm that my problem is a MBR that after the deletion of the partition is not anymore updated. Now my question is: how can I update the NBR after deleting the ubuntu partition?
I repeat, I have no CD, only a recovery partition. I hope you can help me, and I thank you for your patience.

---

### Post by Rallg on 2008-06-09
I sympathize. My previous computer had no CD, only a recovery partition.

If I understand you, at the current situation: After eliminating Ubuntu, you could not boot to Windows. You cannot restore the MBR because you don't have the Windows installation CD (it cannot be done from Recovery partition). So, you re-installed Ubuntu, and now you can boot to either Windows or Ubuntu.

Is that correct? If so, no problem. Don't bother attempting to restore the MBR. You don't really need to do it. Try this:

1. Using the Ubuntu live CD (NOT the installed Ubuntu), go to the installed Ubuntu partition, and delete everything except the /boot folder and contents:

gksudo nautilus

launches your file manager (Nautilus) with privileges. If that doesn't work, then you may need to do it with root privileges. Do that by closing the Nautilus window, and in Terminal:

sudo -s
nautilus

However you do it, the goal is to clear the Ubuntu partition of everything except /boot and contents.

When you do that, the remaining /boot folder will have some 50-60Mb of contents, and the rest of the partition will be free.

Then, from the live CD launch GParted. Shrink the installed Ubuntu partition so that it is big enough to hold the /boot folder, with some extra wiggle room.

If you have a linux-swap partition, you can delete it.

Now, your hard drive has quite a bit of unallocated space. You can expand the Windows partition to fill unallocated space, or you can create new partitions accessible to Windows (NTFS or FAT32 format) in the unallocated space. DO NOT move the starting point of Windows, or the starting point of the residual partition containing /boot.

After closing GParted, go to Terminal from the live CD. Do this:

ls -l /dev/disk/by-uuid

(note that there is the letter l, not the numeral 1, above) Write down the response. It will list your paritions by sda numbers, and their UUID codes. Find the one containing Windows (you may have to identify it by size, or relative location).

Keep in mind that Grub numbers partitions differently. For each sda, subtract 1 to get the Grub equivalent (when you have a single hard drive). Thus, sda5 equals (hd0,4) for Grub.

Now, using the live CD, you will need to manually edit a file in the residual /boot folder on your hard drive. Be sure that you have located he folder on the hard drive, not the one on the live CD. In Terminal:

gksudo gedit DEVICE/boot/grub/menu.lst

where "DEVICE" is the location of the residual folder on the (formerly) installed Ubuntu. The file will open. Remove references to Ubuntu installations. Leave only the reference to Windows. Be sure that the Windows (hdx,y) numbers, and the UUID, are correct. Also be sure that the default number is 0, which will be the only one listed (Windows) after editing. There will be a timeout listed; you can change that to 0 (if that bombs, use 1). Save the changes.

If all is well, you can then re-boot, and your system will go to Windows directly. There may be a brief blink of Grub, as the boot process passes through; but that does not affect Windows. When Windows boots, it may request a disk check becuase you changed partitions, and it may ask you to re-boot after they are recognized.

Did that work? If all is well, then continue as if nothing happened. You lost a few disk tens of megabytes to the partition containing /boot, and (depending on how you had things set up), maybe you have a smaller Windows main partition with an extra Windows-usable partition. Life will go on, and Windows shouldn't give you a problem later.

What if the above did NOT work? Still, you can do something. In that case, instead of shrinking your existing Ubuntu partition, leaving only /boot, you will create a new, small partition in ext3, and re-install Ubuntu, placing /boot alone in the small partition. But first try what I wrote above.

---

### Post by francoduina on 2008-06-12
Rallg, thanks again. I did not follow your suggestions because I am not expert enough, but I solved the problem. Here is my solution, in case you will find something interesting:

My laptop is an HP 12" pavilion with a 250GB HD. It came with a big partition for system and programs and a smaller one for the Recovery stuff. I partitioned C: in four. Now C: has only system and programs, no data at all. I backup daily the three data partitions, and weekly I recover/update/make an Image of C: (I like a clean HD).

So today, after a data backup, I ran the Recovery feature that is supposed to bring the computer to the original situation. I expected it to wipe all the partitions that I added, plus the one created by Ubuntu; and to reset the MBR, the purpose of all this.

But surprise!, Recovery respected the partitions, as well as their content! All I had to do was to to recover the Image and erase Ubuntu's partitions. Problem solved.

Thanks again, ciao
Franco

---

