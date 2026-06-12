---
title: "Grub / Bootloader issues with Lubuntu 16.10"
date: 2017-01-03
forum: Installation &amp; Upgrades
---

### Post by awildebeast on 2017-01-03
Hi all,
I am wtrying to update a laptop that has successfully run Lucid 10.04 (sda5) and WIndows for many years.  I am installing  Lubuntu 16.10 to sda 7, sda 8 or sda9 on a 250GB internal Harddisk.
Installing from verified DVD. I am selecting Sda as the location for bootloader but on reboot I am faced with grub error.  Sorry but I didn't record the last one but I have restored grub operation with boot-repair CD.
The partitions are not in layout order as partitions have been deleted over time.
After many attempts I copies sda5 contents to Sda8 and now grub allows me top boot to a copy of 10.10. 
The latest install of 16.10 was to sda9 but Sda 7 should also be a valid Lubuntu partition.

I note that Grub 1.97 is on the Sda  MBR  and grub2 is on sda5 and sda8.
My latest Boot info report is here [http://paste.ubuntu.com/23736522/](http://paste.ubuntu.com/23736522/)
 
Would be very grateful for any advice as to whether I need Grub or Grub 2 to be installed and whether this should be on Sda or on a partition and how can I resolve this?

Thanks,

James

---

### Post by oldfred on 2017-01-03
You must not have selected sda as location for boot loader.
The MBR of sda has old boot loader and you have newer grub in PBR - partition boot sector of sda5 & sda8.
You should be able to use boot repair & advanced mode to choose your 16.10 install in sda7 and sda as location of boot loader.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
But you have a mount of /home originally sda8, but sda8 has been reformatted and now has a different UUID. The /home mount will cause issues as that UUID does not exist. Did you overwrite /home with the copy of 10.10?
You also seem to have some corruption on sda9 as Boot-Repair is trying to run fsck.

You should plan to give up on 10.10 and XP, neither is supported anymore.
And since not updating often, you may want to use 16.04 LTS as it has longer support.

You have so many kernels, that grub menu gets clogged up.

I would also comment out the mount of /home in 16.10's fstab and run fsck on sda9.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda9 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda9
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda9

---

### Post by awildebeast on 2017-01-04
Oldfred, thanks for those comments.Yes I did overwrite Sda8 with a copy of 10.10.  This was to prove to myself that there was not a bios limitation and that lat least 10.04 would boot that far into the disk - which.It did:-)  Will progress this tonight and report back.
Incidentally, thanks for comment about 16.04 v 16.10.  This was my instinct too but when I was looking for the install 16.04 was much harder to find than 16.10 for some reason. 
James

---

### Post by awildebeast on 2017-01-04
OK. 
10.04 and windows will go just as soon as I get this working.
 I have now created and booted a 16.04 live DVD and was planning to fix partitions and then re-install 16.04. To keep things simple I was planning to install everything in a fsck'd sda9.  However, I quickly encountered the following:

sudo e2fsck -C0 -p -f -v /dev/sda9
/dev/sda9 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!
lubuntu@lubuntu:~$ sudo e2fsck -f -y -v /dev/sda9
e2fsck 1.42.13 (17-May-2015)
/dev/sda9 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!

So, rather than go too far off piste, I now plan to reformat sda9 and then install 16.04 lubuntu into that with sda as the location for bootloader.

---

### Post by awildebeast on 2017-01-04
OK - so installed 16.04 to a clean sda9.  This went OK with no errors reported. Reboot resulted in error and grub prompt as before.  I then ran boot-repair advanced with bootloader to sda and sda9 as default but this did not resolve the grub issue.  Also selected option to fix flexnet. I still get grub error and grub prompt so have not yet got to the point where I feel I can comment out all those unwanted kernels.

The boot info report is here [http://paste.ubuntu.com/23742303/](http://paste.ubuntu.com/23742303/)

I am wondering if I need to repair the MBR?.  Grateful if someone could advise once again.

Many thanks.
James

---

### Post by oldfred on 2017-01-04
Is drive set to AHCI? 
My old XP would not work with AHCI, as XP used IDE setting. But when I added SSD, I had to change to AHCI to support trim.
Some old BIOS could only boot with IDE when all boot files/grub were in first 137GB of drive. 
Did sda9 go beyond 137GB? And other installs are inside it?

---

### Post by awildebeast on 2017-01-05
No explicit reference to ACHI in the BIOS Boot or device options.
I had wondered about this 137GB limit.  Does this only apply to linux partitions? because one of the XP partitions has been outside of 137GB for years but I suspect it was being booted from the MBR.

Anyway, as of now the first partition is 50GB with XP, the second is 25 GB with 10.04 this does boot and then there is a large extended partition for much of the rest of the disk which contains SDA 9 which is less than 30GB - that said the overarching extended partition does extend beyond the 137GB mark.

For reference the latest boot info report is here [http://paste.ubuntu.com/23742303/](http://paste.ubuntu.com/23742303/)

Many thanks.
James

---

### Post by oldfred on 2017-01-05
Windows boots from partition with boot flag. So if more than one Windows its boot files are really in partition with boot flag, unless you manually configure otherwise.

But sda9 look like it is inside 137GB, so probably not the issue.
 At line 2622
9      74.8GB  103GB   28.1GB  logical   ext4 

Flexnet issues were fixed years ago. It used to be that both grub & flexnet would write into the same sectors after the MBR and before the first partition. Grub has core.img which is a lot more boot code that does not fit into MBR.
Flexnet is from some proprietary software you are running in Windows and it hides it security in similar sectors. But now grub check for flexnet and does not use those sectors.

---

### Post by awildebeast on 2017-01-05
Thanks for that  Old Fred - I have now made progress :-)
I got it booting both 10.04 partitions and windows again - recovered with Boot-repair default option. 
Grub 1.98 was now  back in the frame and listing the 16.04 and 16.10  partitions.  However grub reported no such partition when either of  those menu options are selected.

I decided to try using the  original sda5 partition as my partition for 16.04 given that I had a backup in sda8 and given that it had  previously always worked and booted reliably.
I reinstalled 16.04 /  to sda5 and bootloader to sda but this time I did not format the  partition.  (my thinking was that I didn't want to disturb the grub  files that seemed to be working

After 16.04 had finished  installing I saw some message about some applications that could not be  restored and rebooted.  Bingo ! Grub 2 with all partitions listed  correctly.  Interestingly, as a bonus all my data folders were retained  too.
It will take me a while to check this out properly but apart from the fact that the mouse is not working it looks like I may have cracked it.
Its been a bit of a struggle but it looks like we have go there.

Thanks for moral and practical support. Does the above provide any clues as to what the problem may have been all along?

--- Edited later to say that after 16.04 had updated itself I rebooted the laptop only to find that the default grub option had reverted back to the copy of the original 10.04 on sda8 and sda5 was not listed. 

Will do some more investigating tomorrow....

James

---

### Post by awildebeast on 2017-01-06
mmm ... After a large software update prompted by and on the first boot of 16.04 I had to reboot at the end.  Since then the default entry (top of the list)  seems to be for hd0,msdos5 sda5? and the partition seems to be the one previously used for 10.04 but instead of booting 16.04 it is booting 10.04 :-(

Its almost as if that update was a downgrade to 10.04 - is that possible?

I have just done a default repair again.  [http://paste.ubuntu.com/23751236 ]("http://paste.ubuntu.com/23751236")

---

### Post by oldfred on 2017-01-06
It looks like it is configured correctly, but the way it shows kernels it is as if you did not press/check the format option.
That is what is called a "dirty" install which leaves all your data, and only the new programs and configuration files are installed and used. But if you have all the old kernels, grub on an update will find those & add them to menu.

---

