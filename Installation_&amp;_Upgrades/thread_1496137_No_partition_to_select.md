---
title: "No partition to select"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Mr. Cardholder on 2010-05-28
So I've installed Ubuntu before on this machine, but this time around with Lucid, it's just not working.

It all works fine until step four, where you choose your partition. There are no choices. Simple as that. Continuing just tells me to fix that there are no partitions, but I cant. There are questions similar to mine on here, but none are answered.

I really need this installed and cant use the live version where I'm posting from now.

Help me out?

---

### Post by srs5694 on 2010-05-28
See [my Web page on such problems.](http://nessus.rodsbooks.com/missing-parts/index.html) If that doesn't help, please post the output of "sudo fdisk -lu" typed at a shell prompt in an Ubuntu live CD or some other Linux emergency disc.

---

### Post by wilee-nilee on 2010-05-28
> **srs5694 said:**
> See [my Web page on such problems.](http://nessus.rodsbooks.com/missing-parts/index.html) If that doesn't help, please post the output of "sudo fdisk -lu" typed at a shell prompt in an Ubuntu live CD or some other Linux emergency disc.

Your link is not working, at least on my computer.

---

### Post by garvinrick4 on 2010-05-28
If you want to make a partition you use the install CD and choose Try UBuntu and then
when it boots go to System/Administration to gparted. Now in gparted you can see your
drive and its partitions and you can make a new partition. Click on the space you want to use go to Partition and select New. Up will pop a screen with a slider on it to choose how much space you want to use.  If you feel comfortable that you have a grip on it continue.
If not post the product of this code on thread and we will help. Now remember in gparted nothing is done until you apply it by clicking green check mark on upper panel.

```
sudo fdisk -l 
```

That is a small L.

---

### Post by Mr. Cardholder on 2010-05-28
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x562bfce7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89913   722226141   83  Linux
/dev/sda2           89914       91202    10346496    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


```

Now since that, I created a new partition, and nothing. I formatted it, also nothing. Still no display for partition choice in the installer.

---

### Post by garvinrick4 on 2010-05-29
You have a Linux partition in sda1 and a Fat32 formatted partition is sda2.

If you want go back to gparted  in live CD and right click on sda1 the large partition
and choose to format to Fat32 then click on the apply check mark in upper panel. Nothing
happens in gparted until you apply it. Then click on sda1 and go to resize and take the whole drive and apply it. Now we have one big FAT32 formatted drive.
 Close gparted and Click the install icon on desktop. Choose manual and make a /boot partition of 200 meg first and make it a Primary and ext2. Next choose to make a extended partition of the rest of drive in ext4 format. Now put your / in a logical partition and choose how big you want it, maybe 10 gig in ext4 format. Now make a big partition for /home logical partition that is where all your music,downloads ect. ect. ect. go make it ext4 format. If you want to leave room for maybe a new install anything else in the future leave some space on drive. . Now if you have 2 or more gig of Ram do not worry about swap. If smaller than that make a 3 gig or so Swap. Now it will ask for your password and such and if you want to go straight to Ubuntu or need a password. Then next page will be an advanced tab in lower right corner make sure you put  the grub in sda. Not sda1 or sda5 or anything else just sda.
It will automatically make your mbr in that 200 meg /boot we have already made.
Done. install.  Now remember you have a big drive so if you choose do leave some space for things you might want later. You now have a small sda1 then a 10 gig for / or the ubuntu operating system and a huge /home for your stuff. And whatever left over for future or not up to you.  Remember /boot is primary ext2 format.  All others are ext4 format the extended partition and the / and the /home are logical. If swap needed it is logical also.

---

### Post by Mr. Cardholder on 2010-05-29
While that seems the correct way to do that, I don't see a way to manually run the installer. I also have no idea what / on its own is either. So after all that, I am only to the one big fat32.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> While that seems the correct way to do that, I don't see a way to manually run the installer. I also have no idea what / on its own is either. So after all that, I am only to the one big fat32.
It will come up at the beginning to run side by side, use whole drive and last one is manual install about a inch or two below use whole drive.

/ is like your C: drive in Windows it is your whole Ubuntu install they just call it / in Linux.

Sometimes I see it as /root. Just means the Operating system. You only need 10 gig because it will most likely be about 4 gig or so when you download all the stuff you want.
So with the /home being seperate partition you do not need a big partition for your /.

Take your time ask questions if you need let me know when you are done I will stay online.

Click on the installer icon in live Cd and start the install. First page I think is where you choose manual install.

---

### Post by Mr. Cardholder on 2010-05-29
Yeah those options don't come up...it goes straight to language choice then time zones.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> Yeah those options don't come up...it goes straight to language choice then time zones.
Keep going choose your language, keyboard and such it will get there.

---

### Post by Mr. Cardholder on 2010-05-29
Right, and when it gets to prepare partitions, there's nothing there and I can't click anything but forward, back, and quit.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> Right, and when it gets to prepare partitions, there's nothing there and I can't click anything but forward, back, and quit.
Ok next screen will be gparted and you will have one big sda1 partition.

---

### Post by Mr. Cardholder on 2010-05-29
But if I hit forward, it comes up no root file system is defined, please correct this from the partitioning menu.
So I'm stuck there.

---

### Post by garvinrick4 on 2010-05-29
In the screen that has your drive that says sda1 click on that to make it colored then click on change on the bottom and make it 200 when comes up ext2 format and /boot. and Primary.
It will make your first partition now it will come up to drive and have sda1 and sda2 click
on sda2 and then click change make it extended partition and ext 4 and click on it.
next will be click on sda2 and now make it / and 10 gig or 10000 meg and logical partition.
next click and make the next logical /home and big as you want.

---

### Post by Mr. Cardholder on 2010-05-29
Again, the partition screen I'm stuck at is blank...it doesn't list any partition.

---

### Post by garvinrick4 on 2010-05-29
Ok lets start over and when you get to screen where you choose the manual partition. Don't Instead choose use whole drive.

---

### Post by garvinrick4 on 2010-05-29
This trouble is not your fault I am making it to hard on someone that is doing there first install. When you choose use whole drive it will be a lot easier for you to install. You just have to choose a / file system  on last page in advanced tab in bottom right make sure it says in sda.

---

### Post by Mr. Cardholder on 2010-05-29
Well going from the beginning, it's language, location, keyboard, prepare partition. That's where there's nothing. Nowhere is there manual or whole partition.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> Well going from the beginning, it's language, location, keyboard, prepare partition. That's where there's nothing. Nowhere is there manual or whole partition. Right after keyboard layout it should go to prepare disk space
is next screen takes about a minute to get there. I am running a install to a usb drive so I can check out where you are.

---

### Post by Mr. Cardholder on 2010-05-29
Right....and at the prepare partition after keyboard there is nothing listed, and wont let me continue without that error I gave a few posts ago.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> Right....and at the prepare partition after keyboard there is nothing listed, and wont let me continue without that error I gave a few posts ago.
There is a page that says prepare disk space is there a anything at all on that page? Has to be something not just a blank page?

---

### Post by Mr. Cardholder on 2010-05-29
That's been my original problem. No listed partitions to use at all.

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> That's been my original problem. No listed partitions to use at all. You saw your drive in gparted and formatted it. Go back to gparted and see  if your drive is still visable.

---

### Post by Mr. Cardholder on 2010-05-29
Yep, just not visible in the installer. Should it be formatted any specific way? Or primary or extended or anything?

---

### Post by garvinrick4 on 2010-05-29
> **Mr. Cardholder said:**
> Yep, just not visible in the installer. Should it be formatted any specific way? Or primary or extended or anything? I just made a
16 gig flash in Fat32 and it showed up in installer. Was tab in middle of page to select sdc drive. You only have an sda. If gparted sees it then installer should see it. It is a nice green color in gparted that says Fat32 and not black color or anything that is not good?
If it is green and says sda1 750 gig or how big your drive is. Things should be cool.
 If it is leave cd in and reboot and try choosing install from when cd boots up instead of Live Cd or (try ubuntu). I am going to google for a minute.

---

### Post by garvinrick4 on 2010-05-29
If you think you can do it you can make your 200 meg partition, the rest extended partition and a logical partiton of 10 gig and a logical partion of how ever big you want your /home partition. Then they will be made before you start to install.

---

### Post by Mr. Cardholder on 2010-05-29
I've tried every angle to install. I'll just redownload and burn a new disc to see if that is the issue. My internet is down and I've been responding from my phone the whole night. If you find any more answers or possibilities throw them out and I'll get to them when I get up. Thanks for the help so far.

---

### Post by Mr. Cardholder on 2010-05-29
That's another thing, I can't make logicals from gpart either.

---

### Post by garvinrick4 on 2010-05-29
3 or 4 forums I read came up with this fix. They all had to get rid of this package.
Had same problem as you exactly. I would think it would have nothing to do with your
machine but they thought so to and it worked so here it is. Open a terminal and remove this package.

```
sudo apt-get remove dmraid

```gparted saw there drive but installer did not. After you run this, try to install again.

Hopefully it works if not time to do more Googling and looking for what is wrong.

---

### Post by Pathfinder73 on 2010-05-29
> **garvinrick4 said:**
> 3 or 4 forums I read came up with this fix. They all had to get rid of this package.
Had same problem as you exactly. I would think it would have nothing to do with your
machine but they thought so to and it worked so here it is. Open a terminal and remove this package.

```
sudo apt-get remove dmraid

```gparted saw there drive but installer did not. After you run this, try to install again.

Hopefully it works if not time to do more Googling and looking for what is wrong.

I had exactly the same problem a moment ago - Partition Magic partitioned HDD and wanting to do a fresh install of 10.04 (had previously 9.04 on it). This fix worked perfectly for me and I went from blank partition (step 4) to the same step now showing the partitions. Many thanks.

---

### Post by garvinrick4 on 2010-05-29
> **Pathfinder73 said:**
> I had exactly the same problem a moment ago - Partition Magic partitioned HDD and wanting to do a fresh install of 10.04 (had previously 9.04 on it). This fix worked perfectly for me and I went from blank partition (step 4) to the same step now showing the partitions. Many thanks.
I am glad I could help someone now if it works for Mr. Cardholder and gets him up and going I will be a happy camper. Thanks for letting me know it is a viable solution.

---

### Post by Mr. Cardholder on 2010-05-30
Didn't have the internet to respond, but it did indeed work. Strange. Thanks for the help so much though!

---

