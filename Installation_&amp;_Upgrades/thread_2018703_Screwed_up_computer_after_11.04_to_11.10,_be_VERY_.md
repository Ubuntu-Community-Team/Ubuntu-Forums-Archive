---
title: "Screwed up computer after 11.04 to 11.10, be VERY Cautious"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by markwestwood on 2012-07-06
Have used ubuntu  dual boot win xp  for past three years.
 c drive and a d drive  with ubuntu
Last weekend , took the online invite to upgrade from a very stable 11.04 to 11.10
.. 99% through gave an error , cannot recall an unable  to do screen grab.

then on reboot , grub ,able to load win xp, but no 'buntu
tried boot repair.
[I][B]Boot successfully repaired.

Please note the following URL: [http://paste.ubuntu.com/1069000/](http://paste.ubuntu.com/1069000/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (500GB) disk![/B][/I]
then windows worked, but still no access to ubuntu
[B]
tried another  attempt[/B]

monday nights attempt

Please note the following URL: [http://paste.ubuntu.com/1072104/](http://paste.ubuntu.com/1072104/)

still ubuntu failed to load but still had windoze

then 

again tried, live 11.04 CD.  
boot repair
"allowed updates" on this occasion
then 
[http://paste.ubuntu.com/1075580/](http://paste.ubuntu.com/1075580/)


now  have a completely "cattle trucked" system, has wiped my C drive and seems to have installed ubuntu on drive C: and D:( thelinux drive) loosing everything on a six year old c drive with windows.........  10,000 pictures is my biggest loss

no prompt about  you will loose etc etc or back up.

Sorry loosing the faith ;-( .... Redmond never never never ever did this with my stuff since 1992.

BE VERY VERY VERY AWARE about accepting prompts to update is my recommendation.

Block prompts to updates,but  redirect to forum posting on "upgrade issues" would be my suggestion.
Mark
slightly  disgruntled an understatement.

---

### Post by darkod on 2012-07-06
First of all, you have to make a difference between a wubi installation (ubuntu inside windows), and a proper ubuntu installation on its own partition.

I am saying this because you seem to be having a 9.10 wubi install inside your XP (on sda2), and a 11.10 ubuntu install on sdb1.

Your last link with the bootinfo results, if that is the current situation, clearly shows the XP partition with almost 250GB. Is that where you had your data?

Or on the other disk?

Can you explain more precisely where was the data you say is missing, not only C and D because windows really messed up the terminology with that. They started using C drive and D drive which gives you no precise information whether C and D are two partitions on the same disk, or two different physical disks.

Also, it might be best not to boot the computer from the any hdd temporarily. Boot it with the ubuntu cd in live mode (Try Ubuntu) which should give you internet access so you can post.

---

### Post by markwestwood on 2012-07-07
Hi 
my computer history, 
dell with  XP3.( C drive/Sda).. tried wubi , hence install of this...used that for a while , (never uninstalled From windows programs).. Is the drive with all the windows files

Like ubuntu, worked well, impressed teenage  sons ++

Bought another sata drive ( internal), then installed meeerkat  then upgraded  to 11:04 , all fine.

then last weekend the prompt to go to 11.10 , that is when my problems started as listed above.

used live cd to install 12.04 onto the sbd drive 500GB as suggested...

then on boot up , nothing except flashing cursor!. no grub

back to using Live CD and that is when i had the  view that SDA looks like a ubuntu file system.... no hint of anything like windows!! Argggghhh!!

---

### Post by darkod on 2012-07-07
The blinking cursor can be video driver issue or a broken grub. That is not a problem, lets forget it for a moment.

The bootinfo shows sda2 as ntfs, not linux.

Boot live mode again, open terminal and post the output of:
```
sudo parted /dev/sda print all
```

That will show all disks and partitions with the filesystems on them.

---

### Post by markwestwood on 2012-07-09
thanks for your input, but from my last post when using the Live Cd , i opted for the  intall ubuntu as i saw i had still the  ntfs file  on sda...... i selected sbd , but something went way wrong crazy  and my sda was overwritten with linux.... so bye bye windows xp.

I now have a set up with sda  with ubuntu install .. and sdb is one huge empty 500GB drive..

I only wish  i tried your flashing cursor  investigations as you had suggested , before  i took the other steps he ho:)

once again thanks for looking

---

### Post by darkod on 2012-07-09
If you still haven't started writing on the disk where XP was, you can probably bring back partitions with testdisk. Creating a linux partition on the whole disk doesn't delete your files, it only creates entry in the partition table.

You can run testdisk from live cd, download it and run it. It will do the quick search first, and then you can do the deeper search which should detect your ntfs partition. If it does, you can move with the up/down arrows to select it, and press P to try and list the files/folders. If it manages to list the correct folders, it can probably be saved.

If you need detailed instructions how to restore it back, we can look into it once you get to that stage.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

NOTE: If you want to attempt this, do not boot from your hdd regardless on which disk ubuntu is. You have better chance to save the data if you stop using the hdd. Work from live cd.

---

### Post by YannBuntu on 2012-07-10
Hello

> **markwestwood said:**
> BE VERY VERY VERY AWARE about accepting prompts to update is my recommendation.

Generally speaking, I agree with you about prompts to up**grad**es (eg 11.10 -> 12.04). Normal up**dat**es (=regular package updates) can be accepted without any fear. Before accepting any upgrade, I would also recommend to test the new release via a live-CD.

Now, about your problem:
- your initial problem was not a GRUB problem (as you could access Windows from it), but 11.10 system was broken. For information, you could have repaired it [this way]("https://help.ubuntu.com/community/UbuntuReinstallation").
- your problem became worse after the Ubuntu installer use. As suggested by Darkod, you should NOT USE NOR WRITE on the disk any more. First create a bit-to-bit copy of your disk on another disk (via ddrescue for example). Then use TestDisk from live-CD to:
1) try to repair the partition table. If this succeeds you will be able to open a file browser (from a live-CD) and backup your files.
2) If this fails, try to scan the disk with TestDisk to recover your files.

---

