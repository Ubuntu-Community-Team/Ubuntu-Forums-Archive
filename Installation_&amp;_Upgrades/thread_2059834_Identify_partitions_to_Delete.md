---
title: "Identify partitions to Delete"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by bgold2005 on 2012-09-18
Hi! I have long multibooted Windows 7 with several linuxes.
I've removed all but the current and last recent linux-images.

But i still have extra partitions with old linuxes I want to delete. (Ubuntu was complaining about insufficient disk space...)

The problem is - Exactly how do i do this?

here's my attempts so far:

(grub lists)

eg linux 2.0.0.14 on sda 09
2.0.0.9 on sda14

sudo fdisk -l not expicit
sudo blkid was better but no joy

sudo df-h also no

sudo mount -l little use

__

GParted lists 3 "lock" icons, one at ext4 (My extended partition)
sda12 is / and sda13 is linux-swap.

so I think My linux is on sda12

But when I formatted (ok partitioned resized etc) for Linux i thought it required Four Partitions. root, home, Swap and another. So which are my other two needed partitions?
(sda13 is the highest number, sda1 and sda2 are Windows)

and can anyone tell me how to output or copy the grub menu so i can attach it to a request like this one? i cant figure it out from info grub and i can't even find menu.1st under boot->grub

thanks.

---

### Post by oldfred on 2012-09-19
The little keys are saying those partitions are mounted, so that is what you are running from. Mounting any partition in the extended mounts the extended.

To edit partitions in the extended you have to use a liveCD, either Ubuntu which has gparted or download the gparted or partedmagic liveCDs.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Even then liveCD often mount the swap, since swap is in the extended it will be mounted (in effect), so click on swap and right click swap-off to unmount it.

If you want more detail (and documentation) on what is where, run the BootInfo report & post link.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I use gparted or Disk Utility to label my partitions so then I know what is where.

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb1  vfat    MC4GB    /media/MC4GB   E489-24AF
/dev/sdc2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdc3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdc4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdd1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdd2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdd4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdd5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdd6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdd7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdd8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdd9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdd10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdd11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdd12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdd13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdd14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdd15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdd16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdd17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdd18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sde1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sde3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sde4  ext4    quantal  (not mounted)  3b72e3d4-3d56-469b-ad50-f13ac4f5f0d4


```

---

### Post by bgold2005 on 2012-09-19
thank you oldfred!

Bootinfo a great pgm - the info is too much which is much better than too little!

Still I don't know how many partitions my Linux (12.x) is supposed to have - two or four? And if four which are the other two?

yes i understand i must boot from a livecd etc to delete or resize partitions in use or in extended part.

if they still load, can i log into the old
linuxes and uninstall them from there, using the grub update to purge them from grub (and later reboot to delete partitions etc)?

or would this immediately BSOD me (I forget the Linux equivalent)

thanks again. The Bootinfo URL is

[http://paste.ubuntu.com/1214907/](http://paste.ubuntu.com/1214907/)

(Forum wont let me upload even the text version)

---

### Post by darkod on 2012-09-19
According to fstab, you only have two partitions for 12.04.1 and it tells you which ones. They are sda12 and sda13.

As always, be careful when deleting any partitions, think first if there is anything there that you need or use. :)

PS. Also, when running linux you can see what you mounted in the current installation with:
df -h

Note that the above command doesn't show the swap partition but it shows all the others, including data partitions you have mounted. That can also help you see what partitions is the current installation using.

---

### Post by oldfred on 2012-09-19
And if you look at the fstab from sda11 you had /boot, / (root), /home and two swaps. If you had something in the /home (sda8)  you may want to back that up first before deleting or you can change you 12.04 to use that /home or convert one partition to just a data partition.

Lots of choices.

---

### Post by bgold2005 on 2012-09-19
Thank you both.
So: despite my memory of older distros, my Ubuntu 12.04 DOES NOT use more than two partitions? That is, root and home and all are included in sda12, and sda13 is my swap, and if i don't care about old data I can nuke all non-windows (sda1 and sda2) and non-Grub (sda6?) partitions?

thanks again

---

### Post by darkod on 2012-09-19
You don't need sda6 either. It was a /boot partition for an older install.

As you can see at the top of the results, grub2 on the MBR is connected directly to your 12.04.1 partition, sda12. It says "look for (,msdos12)/boot/grub".

That means sda12 in the /boot/grub folder. So deleting sda6 will not affect your current booting process at all.

Note that sda3 is also ntfs partition, depending what you have there, you SHOULD NOT touch sda1, sda2 and sda3. On the linux side, sda12 and sda13.

---

### Post by YannBuntu on 2012-09-20
Hello

To avoid mistakes, you can use OS-Uninstaller.
It is a little tool, based on Boot-Repair, that allows safe remove of any OS (Windows, Linux ...):
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1340275988.png[/IMG]

---

### Post by geomatic on 2012-09-22
ooo. Nice OS uninstaller. I will need that. 
Sorry about the hijack, trying to make the 50 posts.
I am trying to partition my drive for a dual boot. Like the gparted too. Thanks and good luck.

---

### Post by bgold2005 on 2012-10-04
thanks to all. followup q'n:

(1) any feedback on the above os uninstaller?

(2) re (1) or if i delete manually, won't my hard drive partitions re-number?

if so, are the steps complicated to get grub and ubuntu to understand they are invoking new partitions?

or is easier/less risky/more advisable to just format (delete files) in the partitions and shrink them?

I wont touch sda1,2 or 3 as advised...so windoze and grub should be ok...but i'd rather not smash the current ubuntu

thanks again

---

### Post by darkod on 2012-10-04
I haven't used the mentioned os uninstaller.

As for partitions changing numbers, that will probably happen, but all recent versions of ubuntu use UUIDs and not the traditional /dev/sdXY notation, and the same applies to grub2.

So, even if the partitions change numbers the system should still work fine because it finds the partition by UUID which is the same unless you format a partition. By formatting it gets new UUID.

In worst case, you can always edit fstab from live mode.

Open fstab and check the above mentioned. If you see something like UUID=<string> and not /dev/sdaX then it's using UUIDs and you have nothing to worry about partition numbers.

---

### Post by bgold2005 on 2012-10-04
ok, i dont know how to examine fstab directly...
though i can examine the exhaustive output from boot repair...

so can ANYONE confirm for me what no one has addressed...
AFAIR when i installed  some ubuntu I had to make four partitions -
for root (/),boot,/home and swap.
Are all FOUR of these contained in my sda12 and sda13?

if not, exactly where are the others located?
if no one can tell, am I still safe in deleting all sda between 4 and 11 inclusive?

I am sorry for the  shouting - I have received some great responses here but none reassures me that all 4 are accounted for- or dont need to be.

Did ubuntu change at some point to only require the two partitions?

Thanx

---

### Post by darkod on 2012-10-05
No, sda12 and sda13 are only TWO partition, and they are the minimum ubuntu needs to work, so clearly you don't have FOUR partitions in them.

However, if this 4 partition ubuntu was one of the older installations you want to delete, it doesn't matter how many partitions it consisted of, you still want to delete all of them, right? Or not?

I was under the impression that you only want to keep the latest installation and according to what we have seen the one you are using uses sda12 and sda13. And that you don't have any important information inside all other installations/partitions.

You can have one installation installed with separate /boot and /home and another installation without them. It can work either way and they don't interfere with each other except usuallt sharing the swap partition.

The easiest way to examine /etc/fstab in terminal is:
cat /etc/fstab

That will list the content.

---

