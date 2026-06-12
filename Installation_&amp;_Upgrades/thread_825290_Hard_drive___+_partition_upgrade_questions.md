---
title: "Hard drive   + partition upgrade questions"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Darth_tater on 2008-06-10
Hey all, had one quick question.

I use ubuntu on my home file server, and I desperately need to upgrade the hard drive that’s in there currently.  As of now, it has a 160 GB sata drive that is split up like so:
1)	5 gig partition for /
2)	.5 gig partition for swap
3)	Everything else for /home

I need to upgrade to a 400 gig SATA drive, and was wondering how I can move everything over (bit for bit… the data still needs to be fully intact) onto my 400 gig drive. 

I believe I can format / make the partitions in gparted, but I do not know how to copy *all* the data, files, folders over so that the permissions will remain intact.  

And as long as the partitions are created in the same order, will the /etc/fastab work once I reboot with the new drive installed?  

Thanks for the help.

---

### Post by logos34 on 2008-06-10
Use the copy and paste function in [Gparted]("http://gparted.sourceforge.net/larry/move/move.htm").
(the exanmple is ntfs, but the principle is the same for ext3). 

Or the [dd command]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html"). 

> **Darth_tater said:**
> 
And as long as the partitions are created in the same order, will the /etc/fastab work once I reboot with the new drive installed?  


Yes.  But since ubuntu uses UUIDs instead of '/dev/sdax' format, it shouldn't matter with fstab (when you image a partition, the entire filesystem is copied along with the uuid).  However make sure to edit 'groot', 'root' and 'kernel' lines in /boot/grub/menu.lst to the new partition #, if it changes. 

[Reinstall grub]("http://sudan.ubuntuforums.com/showthread.php?t=224351.") (pointing to the new root location) to whichever drive you intend to boot from

---

### Post by Darth_tater on 2008-06-10
That’s exactly what I was going to do, but I asked because I do not want to cause boot problems.

As I understand it, I was going to copy / paste the partitions in the exact order that they appear on first drive, then just expand the /home folder partition to fill the rest of the drive.

If I understand you, I shouldn’t have a problem as long as I keep the partitions in the same order?

---

### Post by logos34 on 2008-06-10
> **Darth_tater said:**
> That&#8217;s exactly what I was going to do, but I asked because I do not want to cause boot problems.

As I understand it, I was going to copy / paste the partitions in the exact order that they appear on first drive, then just expand the /home folder partition to fill the rest of the drive.

If I understand you, I shouldn&#8217;t have a problem as long as I keep the partitions in the same order?

yeah. and as I say even if root were to end up on a different partition number, all you would need to do is edit menu.lst.*

I might also add that it would probably be best to reinstall grub to the mbr of the new drive and boot from that in order to avoid any confusion.

ADD:

*e.g. going from sda2 to sdb1:

> title        Ubuntu 8.04 2.6.24-16-generic (/dev/sda2) 
root         (hd0,1) 
kernel       /boot/vmlinuz-2.6.24-16-generic root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023 ro splash quiet
initrd       /boot/initrd.img-2.6.24-16-generic
quiet

new:

> title        Ubuntu 8.04 2.6.24-16-generic (/dev/sda1) 
root         (hd0,**0**) 
kernel       /boot/vmlinuz-2.6.24-16-generic root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023 ro splash quiet
initrd       /boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by Darth_tater on 2008-06-10
Do I really need to re install it?  Won&#8217;t Gparted copy *everything* over&#8230; including the boot sector thus make the new drive bootable.

---

### Post by logos34 on 2008-06-10
it will copy the **bootsector of the root partition**, but not the MBR (master boot record) in the first sector of the hard drive.  So unfortunately you have to reinstall that part.  But no biggie

---

### Post by Darth_tater on 2008-06-10
Ah.  so then i assume a simple 

```

#grub
>find /boot/grub/stage1
>root (hd0,0)
>setup (hd0)

```

should get me sorted?

---

### Post by logos34 on 2008-06-10
> **Darth_tater said:**
> Ah.  so then i assume a simple 

```

#grub
>find /boot/grub/stage1
>root (hd0,0)
>setup (hd0)

```

should get me sorted?

'find' will output both root locations.  If the new root is located on the first partition on the new drive and it's set first in the bios boot order, then yes, what you have will work

---

### Post by Darth_tater on 2008-06-10
when i am done, the new drive will be the *only* drive in the box.

as for partition, i do believe that the '/' partition is the first one.

---

### Post by logos34 on 2008-06-10
> **Darth_tater said:**
> when i am done, the new drive will be the *only* drive in the box.

In that case, definite yes.  (I guess I was picturing you running it just after copying was completed, but before disconnecting the old drive).

---

### Post by Darth_tater on 2008-06-10
> **logos34 said:**
>  I was picturing you running it just after copying was completed, but before disconnecting the old drive).

that's when i was going to do it...

but i could always use the live cd, too.

---

### Post by logos34 on 2008-06-11
> **Darth_tater said:**
> that's when i was going to do it...

but i could always use the live cd, too.

well, you'll definitely have to operate from the live cd because root cannot be mounted during gparted or dd copy.  Then shutdown, remove old drive, turn on again and reboot to live cd, write grub to mbr, and finally reboot to hard drive.

Good luck

---

### Post by Darth_tater on 2008-06-11
yeah, thats exactly what i was going to do, but i was not aware that the MBR would not be coppied over.  Thanks

---

### Post by Darth_tater on 2008-06-12
Yeah, its up and booting from the larger disk, and my /home directory is now ~ 325 gigs

so, everything worked.

just one small thing though, Gparted *did* copy over the MBR... grub booted and threw Error 21.. which meant that it couldn't find the disk it was used to.

this was easily solved by rebooting w/ the live CD and installing grub as shown in my previous posts.

thanks, everybody.

---

### Post by logos34 on 2008-06-12
> **Darth_tater said:**
> 
just one small thing though, Gparted *did* copy over the MBR... grub booted and threw Error 21.. which meant that it couldn't find the disk it was used to.


hmm, odd.  If you are sure you actually booted to the new disk (and if you disconnected the old drive then you obviosuly did), the mbr should have been empty until you wrote grub to it separately.  You should have gotten 'boot disk failure' or the like. 

I quoth from the Gparted docs:

> From the second hard drive, XP cant boot, because there is no MBR for the moment !

The example was ntfs, maybe there's a difference when copying ext3, dunno.

Anyhoo, glad it works.  Enjoy.

---

### Post by Darth_tater on 2008-06-12
something did just occour to me.

While the Disk manager in windows Vista and Gparted both saw the *entire* drive as 'un allocated' the new drive might, at one point, have contained a grub installation.

i have used this drive before, but i don't really remember for what.  its possible that there was Linux, or at lease a multiboot setup that required grub.

oh well, all works perfectly so i ant complain.

-- thanks again!

---

### Post by logos34 on 2008-06-12
> **Darth_tater said:**
> the new drive might, at one point, have contained a grub installation.

i have used this drive before, but i don't really remember for what.  its possible that there was Linux, or at lease a multiboot setup that required grub.

now it's starting to make sense.  

enjoy your new roomy 400 gig. (my second drive is less than half that!)

---

