---
title: "Cannot boot to grub"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by angryhomer17 on 2007-04-20
I really messed up this time:

Yesterday, I wanted to upgrade to Feisty. So I started the update-manager and it told me I needed xubuntu-desktop installed to continue. Fine, I did that and restarted the update-manager. Everything is fine until it says I dont have enough free space to upgrade, I needed at least 324 or something. Well I looked and saw I had 900, but thought, eh not going to bother with this discrepancy. This is were things start getting worse.

I had a 6 gig partition that I had windows on at one point, couldn't get all my drivers and it was really no good to me, so I figured I could delete that partition. So I rebooted to a knoppix live cd, started qtparted and deleted my windows partition. Restarted the system to go back to ubuntu and low and behold I can't. The grub selection screen doesn't show up; I get my bios choices of hard disk, cdrom, pxe lan, etc. 

I figured I did something to mess up my menu.lst file, so I went back in to knoppix and looked at my menu.lst file. It appeared to be ok. Then I tried to setup grub again.

I did the find /boot/grub/stage1, root (hd0,0), setup (hd0) thing in grub and it appeared to work fine. Rebooted and again I cant get to a grub menu. 

Ok, lets mess with partitions some more. Great idea. Went into my ubuntu live cd and started gparted, the partition manager I wanted to use in the first place (I forgot I used gparted instead of qtparted to make my windows partition in the first place) Anyway, gparted showed I had 3 paritions, one 30 gig for linux, one 6 gig unallocated and hidden, and and extended partition for linux-swap at 1.4 gig. I couldn't unhide the 6 gig partition, and I really had no idea why my linux swap was on an extended partiton. Somehow I merged the extended partiton with the unallocated one. Then I setup a new linux swap partition at 1 gig and resized my ubuntu partition to take up all the extra free space. 

So now i have a 37 gig ubuntu partiton and a 1 gig linux swap partition. Did the grub thingie that I did before and rebooted. Still no grub. I have no idea why not.

Rebooted to a slackware live cd (boots so much faster than knoppix and ubuntu) and started searching around. 

I tried setting up a boot partition and putting the contents of /boot from /dev/hda1 onto it. Didn't work. 

Tried messing with my menu.lst file and put root=/dev/hda1 in place of root=UUID=blah blah. Didn't work, put the UUID string back in.

Tried making a grub.conf file. Didn't work.

Tried a grub-install /dev/hda and grub-install /dev/hda1

```
root@ubuntu:/# grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.
```

Did a update-initramfs -u because some guy in some other forum suggested it. Really not sure what that does, supposedly something with the kernel.

```

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> kernel /boot/vm

Error 15: File not found

grub> kernel /vmlinuz
   [Linux-bzImage, setup=0x1c00, size=0x17e879]

```

None of this worked at all. Then I remembered that I installed sysv-rc-conf to mess with my boot to make it faster. I'm pretty sure I didn't uncheck anything that needed to be checked. And I figure that that shouldn't have too much to do with getting grub to show up.

Sorry for the extremely long post, but hopefully someone knows what is wrong and can help. If all else fails I guess I'll have to backup my stuff and re-install Dapper and then upgrade a couple of times. Unless there is someway I can do a network install.

Thanks for any help.

---

### Post by angryhomer17 on 2007-04-20
Well I got some help elsewhere, but that didn't help either. I don't have any more time to mess around with this. So I'm gonna backup my data and do a fresh install.

---

