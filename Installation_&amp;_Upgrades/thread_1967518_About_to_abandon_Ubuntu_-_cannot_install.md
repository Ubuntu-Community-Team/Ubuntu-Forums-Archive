---
title: "About to abandon Ubuntu - cannot install"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2012-04-28
Hi,

I have been using Ubuntu for about 4 years. I am a developer, so need a fast, safe and stable machine. I am on my 3rd spinning HDD failure in those 4 years. So now I want to take advantage of 2 60GB SSDs I bought. To me that means RAID1 for /boot (safe), and a LVM striped for speed (fast) (I also need about 120BG, in fact my / on the failed HDD is 119GB). Also like to rsync my ~ across, dd proved to be a disaster, so slow.

Sadly, this seem impossible to achieve on Ubuntu 11.10 see here - 
[http://ubuntuforums.org/showthread.php?t=1887094&page=4](http://ubuntuforums.org/showthread.php?t=1887094&page=4)

So is there a distro that can support this type of configuration? Is there an alternate way of installing on Ubuntu that will support the configuration? Also researching to see if this is easy on Windows 7, £80 is a small price to pay for an easy life.

Thx.

David

---

### Post by darkod on 2012-04-28
I assume you tried 12.04 and it doesn't work too?

One thing I would try and that I mentioned in your other thread, is to configure the SSDs with msdos table. You have no benefit from the gpt table that I can see, and using a msdos table will allow you not to need the bios_grub partition. Makes it simpler. Who knows, maybe it will change something for the better.

The bios_grub is not needed just because of grub2. It is needed for grub2 only on gpt because the MBR section of gpt disks is smaller. If you use msdos table grub2 works just fine without that small partition. I would give it a shot.

---

### Post by olddave1 on 2012-04-28
So I just delete that 1MB partition at the start of the disk and then run boot-repair and that by default will add a mbr? 

I don't want to waste yet more time trying 12.04, unless someone actually knows it has changed from 11.10 in terms of supporting 2 SSD with RAID1 for /boot and LVM striped for /. At the moment I am losing lots of work time, not a good thing.

I also made a discovery on the recovery mode boot, I'll document in the original thread

---

### Post by darkod on 2012-04-28
No, you need to write new msdos partition tables. Of course, that will destroy all data on the disks. The fastest way to write new msdos tables is from parted in live mode, you simply do:
sudo parted /dev/sda
mklabel msdos
quit

You do that for the other disk too. Now you have msdos table. You can create partitions with what ever program you are familiar with and then continue with the mdadm/lvm setup.

---

### Post by olddave1 on 2012-04-28
I put msdos partition tables on, recreated the /dev/md0 and /dev/vgssd/lvssd. Then I used dd to duplicate my existing disk across, (this disk will no longer boot, but it mounts fine and all files seem to be there, assume it is just GRUB that is on sectors that have errors). Then I used boot-repair to make sure that grub was correctly installed on the ssds and to also make sure that /boot was put on /dev/md0. This time dd was much faster than the last 35 hour run time, it consistently perfomed at about 44+MB/s whereas last time is was 950KB/s
But this last step fails, it seems that boot-repair cannot cope with the striped LVM, at the step "dpkg --configure -a mapper/vgssd-lvssd. This may require several minutes" it just sits there, so far for about 45 nminutes, I assume it is not going anywhere...

I am going to have to buy a normal spinning hard disk and straightforward installs do seem to work with Ubuntu.

---

### Post by darkod on 2012-04-28
Why boot-repair? Simply install grub2 from live mode. It should be something like (for 11.10 and later):
sudo mount /dev/vgssd/lvssd /mnt
sudo mount /dev/md0 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

But in your place I would have tried making a new install first. I know you are pressed for time and fed up with this, but now you won't be able to tell if you have some issue with the dd-ed system, or in general.

If a new install worked on your /dev/md0 and LVM combination at least you can be sure that it works. Any issues later would be related to the dd and making the dd-ed system function.

---

### Post by olddave1 on 2012-04-28
I tried your method with grub-install etc.. It booted to the grub> prompt. boot-repair comes up with a blank dialog. 

The reason I would use boot-repair is that like most Ubuntu users we do not have the time to learn dozens of commands with hundreds of combinations of options. Ubuntu supports a single disk installation really well, it just seems to get very complicated fast when you want an optimal installation involving 2 SSDs

---

### Post by darkod on 2012-04-28
There were no errors during the grub install?

For the first command I am not sure if it's /dev/vgssd/lvssd or /dev/mapper/vgssd-lvssd.

And you did install lvm2, mdadm and activated the /dev/md0 and the LVM first in live mode, right? Remember that you need to do this in live mode every time, so that you can use them in commands later.

The reinstall of grub2 to the MBR takes only two commands. In your case with separate /boot and two disks as destination, it goes to four. It's very simple and no complicated options. You mount /, you mount /boot and you do the grub-install telling it where you mounted /boot.

One thing that could be an issue here is the UUIDs. You are using dd so the /boot/grub/grub.cfg will have the UUIDs from the old partitions. The new partitions will have different UUIDs. Did you do something about this? Transferring your root over is not simply dd-ing it.

That is why I suggested to try a clean install first, to see how that will work. If that works fine, you know your issue is with the dd procedure and how to fire up the cloned partitions. Also, with a new install you probably wouldn't have needed to add grub2 manually, it should install on its own.

---

### Post by olddave1 on 2012-04-29
I pulled out the SSDs and used a new hdd from my wifes machine, she is not happy :( 

There were no errors on grub-install. Because I pulled out all drives except the new spinning HDD I expected there to be no UUID clashes. But the grub> was all I got.

But on looking at this [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)
And thus having a look at the grub.cfg, I found it empty except 6 lines of comments. I can only assume boot-repair had done this. 

So I put back I nmy old drive and cut and paste the content from it's grub.cfg and then generated a new UUID for the new drive and substituted the new UUID into the grub.cfg on my new disk. I also updated the fstab file and ran grub-setup as instructed in that link. I removed all drives except my new one and rebooted and I saw the altered label I put in. On selecting the top entry I get a black screen and no boot no prompt. Probably something wrong with grub.cfg, but no idea what.

---

