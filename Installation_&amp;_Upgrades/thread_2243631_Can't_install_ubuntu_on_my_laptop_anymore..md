---
title: "Can't install ubuntu on my laptop anymore."
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by yossi_cohen on 2014-09-10
I used to run linux distros back then on my laptop asus k52jt but now i seem to not be able to install ubuntu 14.04.

The installation(out of a dvd) sees my HDD as a huge 500.1gb free space instead of seeing my partitions:
Basic disk 500 gb
- system reserved, primary ~300 MB
- The "C" drive of windows 8.1, primary ~405 GB(pc came with 7 uefi is disabled no secure boot option at all).
- 60.0 GB unallocated.
Tried this:
-formatting free space into a volume
-using fixparts-windows pressed p saw everything is fine pressed w.(I didn't delete GPT when asked if i want to i didn't know if it was safe.)
-at first i could shrink c only by 40 gb instead of the free 170gb so i used defraggler and it fixed it i could shrink up to almos tthe full free space,
-entered live couldnt see the partitions there as-well
-checked if i'm on dynamic disk, im not.
-uefi was enabled in bios i disabled it.
-confirmed that my drive is an MBR drive.

Any further ideas that could help ubuntu see my partitions? should i delete that GPT signature?
Thank you very much, Yossi Cohen

ps:  this is fixparts notice... 
[FONT=Verdana]NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition![/FONT]
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):

Also it said something about the first partition not starting in the first sector and that it might cause problems with some OSes.

---

### Post by yossi_cohen on 2014-09-10
bump (hope it works here) i already went down to the second page...
i really need help in this manner...

---

### Post by QIII on 2014-09-10
Hello!

Although we have relaxed the 24 hour rule for bumping, please do not abuse it.

8 hours is not much time for a forum with members in all time zones around the world to see your question.

Having bumped it, you have made it so that the query used by those who look specifically for unanswered posts (we have a team that does that) will now not be able to find it.  24 hours, although not rigidly enforced any longer, is still the recommended cycle time for bumps.

Thanks.

---

### Post by yossi_cohen on 2014-09-10
oh sorry didnt know that...
i just know that most people look at the first page and move on... so i thought that bumping was not about time but about how much further you went down the list.
will not do it again so short noticed...
glad you have a team that  specializes in finding question posts with no replies.

could you please delete our last 3 posts and leave only the OP so this Thread stays kinda cleaner? thanks...

---

### Post by oldfred on 2014-09-10
Not sure now whether you have UEFI or BIOS install.
Windows only works with UEFI from gpt partitioned drives and only BIOS from MBR(msdos) partitioned drives.
And if you converted a gpt drive to MBR with Windows it did not do it correctly.

But you do not want to erase gpt with fixparts if really gpt.

Post this:
sudo parted -l

This will not work if gpt. If correct gpt it should only have one entry in protective MBR saying it is gpt.
sudo fdisk -lu

---

### Post by yossi_cohen on 2014-09-11
running the commands now from a live dvd will post the results in an edit soon...
first command
**warning: /dev/sda contains **[COLOR=#333333][FONT=UbuntuRegular][B] GPT signatures indicating that it has a GPT table. However, it has a fake msdos partition table as it should. Perhaps it was corrupted-- possibly by a program that doesn't understand GPT partition tables. or perhaps you deleted the GPT table and are now using an msdos partition table. Is this a GPT partition table?
Yse/No?[/B]

the second command gives
[/FONT][/COLOR][FONT=Roboto Slab][B]ubuntu@ubuntu:~$ sudo fdisk -lu
  WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.   
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xf7894b75     
Device Boot      Start         End      Blocks              Id System 
/dev/sda1 *       2048      718847      358400              7  HPFS/NTFS/exFAT 
/dev/sda2          718848   850941951   425111552    7  HPFS/NTFS/exFAT

[/B]ps it shows my partition fine on the second command shows exactly like fixparts...[/FONT]

---

### Post by yossi_cohen on 2014-09-11
fixed my problem by doing this
[COLOR=#333333][FONT=UbuntuRegular]To fix your problem, follow these steps:[/FONT][/COLOR]

[LIST=1]
[*]Boot the emergency disk and open a text-mode shell.
[*]Type "gdisk /dev/sda" (change "/dev/sda" to whatever is appropriate to access your hard disk, if necessary). The program is likely to complain that it's found both MBR and GPT data, and will ask which to use. It doesn't matter which you tell it to use.
[*]At the "Command" prompt, type "x" to enter the experts' menu.
[*]At the "Expert command" prompt, type "z" to "zap" (destroy) the GPT data.
[*]Type "y" in response to the confirmation about destroying the GPT.
[*]Type "n" in response to the query about blanking the MBR. **Caution: If you answer "y" here, you'll destroy your Windows partition(s)!**
[/LIST]
[B]files remained intact now installing ubuntu 14.04 
the installer now recognizes that win 8.1 exsists and of course i xhoose something else and not alongside^^[/B]

---

