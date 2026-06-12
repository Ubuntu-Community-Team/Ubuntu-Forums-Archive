---
title: "What should I know before moving the start location of the boot partition?"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2012-08-08
The attachment shows my current partition layout. I'm going to move the partition back to the left - and then extend it to the right to (finally) give me more hard disk space. (reducing the windows partition was a project in itself).

I'm going to put Ubuntu 12.04 on a USB stick (CD drive is broken on this laptop) and use gparted.

My question is, given the above; how can I be sure grub will still boot? (And windows)

Thanks!

---

### Post by dino99 on 2012-08-08
First clean the windoz partitions and defrag, do the same with ubuntu.
Secondly, boot on a live cd (liveusb), then start garted and: 

move sda4 to the left (extended) and validate the change
then move sda5 to left (/) and validate again the change

note:
- the / partition seems used to store your data & settings, you'd better to create a separate /home partition for security (instead of a home folder inside the system partition)

- the swap partition is a bit small if you want to use "suspend" or/and "hibernate": should be at least 2 Gib but 4 Gib for hibernation (or twice the ram amount)

After rebooting you will have trouble with grub, because uuids have changed. So reboot again with the liveusb to collect the new uuids.
Into a terminal:

sudo blkid
take note of them, you will need to "edit" the grub menu line on witch you boot on.

Now you are ready to boot on the hdd; when you will get the grub menu line, edit it (hit the E key) to set the new uuid, then hit ctrl+X to boot. After booting you need to run :

sudo update-grub

and voila :)

---

### Post by oldfred on 2012-08-08
Dino covers the partition moves. If it is just a move the UUID should not change, but best to know how to resolve the issue if it does. I prefer not to move partitions, but housecleaning first means less data to move. Any power failure or interruption during a move will cause corruption, do good backups are important. But I never have had issues except those I did to my self.

I also agree with the separate /home or a separate data partition. I usually suggest a shared NTFS data partition for those dual booting with Windows. I used that for years and even not booting XP now, I still have some data in my shared NTFS data partition.

Windows often does not like too many writes into its system partition, so best to mount it read only. Then you use a shared NTFS for all the data. I also copied any other Windows data that was not easily stored in the data partition by default just to make it easier to backup my NTFS data.

---

### Post by QwUo173Hy on 2012-08-13
Thanks Dino99,

I can't actually move sda4 from gparted. I don't think extended partitions can be moved. I'm going to move sda6 and assume that the UUID trick will work the same.

Oldfred, thanks - I'll keep it plugged in. We're phasing out windows altogether so the shared partition won't be necessary - but I may need to in future.

Best,
Ten

---

### Post by QwUo173Hy on 2012-08-13
Mission accomplished. Thank you both for your guidance -  I was well prepared!

The main difficulties I had were moving the extended partition in gparted, but thanks to a bit of googling, I learned that I had to right click the swap partition and choose 'swap off' - even though I was using a live usb.

Then I just moved and resized. I also upped the swap to 2GB as advised by dino99. Then I rebooted and everything was cool!

I've attached the new partition layout in case you'd like to see the results. Thanks so much again. I had wanted to do this for ages but it wasn't until I had some community support that I would have taken the risk.

Best,
Ten

---

