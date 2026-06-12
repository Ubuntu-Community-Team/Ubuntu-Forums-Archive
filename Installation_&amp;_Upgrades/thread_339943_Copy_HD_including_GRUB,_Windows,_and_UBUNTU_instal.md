---
title: "Copy HD including GRUB, Windows, and UBUNTU install"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by allwin on 2007-01-16
On my sandbox PC, I have a 20GB internal drive formatted with GRUB, a Windows ME partition (fat32), Linux, and swap.  It dual boots nicely, but I think the drive is about to flake out.  I have another 45 GB drive here in a USB enclosure.

I'd like to figure out the easiest way of copying the 20GB contents to the 45 GB drive to end up with a bootable HD which I could then just replace inside the sandbox.

Any suggestions?  I'd hate to have to reinstall UBUNTU and Windows ME if I don't have to!

---

### Post by raptor95368 on 2007-01-16
my suggestion is acronis true image or the latest ghost solution...they both hand the linux partition, which earlier versions of ghost did not do...

---

### Post by seasidedave on 2007-01-16
I just bought Acronis True Image 10 *Home* which is excellent.  It has a range of tools, one of which is to clone a hard drive in just that situation.  It has worked perfectly for me with complete backups, under Windows XP home.
The acronis site allows a download of the fully functional software, which is limited for 15 days use.  I used that trial to take a total backup and to make a rescue DVD.  My PC catasrophically failed when installing ubuntu 6.06.1, which none of the windows xp home discs could sort.  I put the acronis rescue DVD in (with bios set to boot from dvd first) and it took the backup from my external drive.  PC now perfect again.  So I bought acronis!

---

### Post by ajgreeny on 2007-01-16
You may be able to use *partimage* as well which is in the universe repository.  I'm not sure if these programs will transfer grub as well but it is easy to reinstall that with a live CD afterwards if you need to.

---

### Post by dakota34 on 2007-01-16
[G4U]("http://www.feyrer.de/g4u/") (ghost for unix) has always worked for me.  You would want the disk-to-disk option I guess, and that's the option that has never failed me. (I've had some problems getting my storage pc's FTP program to interact with G4U's 'slurpdisk' function, but it's an FTP issue only.  It's worked for fine for Linux disks, and I've succesfully copied an XP disk with a grub boot sector using G4U, however I've never had occassion to copy a combined XP/Linux disk, so it's slightly different from your case I suppose.

---

### Post by allwin on 2007-01-17
I was worried about the GRUB business, too.  What I ended up doing was downloading the official GPARTED live CD, mounting the second HD in the box, and doing the PARTITION copy function from the old disk to the new one, which even allows you to resize the destination partitions.  Then I created the swap partition.  I tried booting, but alas no grub.

So I used the UBUNTU Live CD, brought it up, and ran GRUB from a terminal and put it on the hard drive.  I had to use the SET(hd0) option to stick grub in the MBR (I guess) and not just the partition.

To my amazement, the grub menu came up on reboot, and Windows ME came up, and so did UBUNTU.  This was not Windows XP here, so no NTFS stuff to worry about.

One little problem...upon reboot, UBUNTU came up WITHOUT a swap file.  This is because, since it's a new disk drive entirely, for some reason FSTAB was messed up because UBUNTU codes the UUID of the disk, and not the device name!  WHY DOES IT DO THIS?

It's unfortunately illustrative of the number of easy to fix fribbles which plague Linux IMHO.  Geminis, you copy files from one HD to another and things don't work because somewhere in the bowels of the beast it uses the serial number of the drive and hard codes that somewhere.  Arrrggghhh.

Anyhow I found a vol_id command which displays the UUIDs of the partitions on the disk, fixed FSTAB and everything took off just swell, if you pardon my rant, to which I think I'm entitled.

BTW, UBUNTU runs quite well without a swap file at all...for a while...

---

### Post by dcstar on 2007-01-18
> **ajgreeny said:**
> You may be able to use *partimage* as well which is in the universe repository.  I'm not sure if these programs will transfer grub as well but it is easy to reinstall that with a live CD afterwards if you need to.

The "dd" command can be used to copy the Boot sector (including Grub) to a file for later restoration.

You should be able to do a web search for the specific details on how to do this sort of thing.

---

### Post by glabouni on 2007-01-29
dd is the command you need. it can do what you need, including copying MBR.
I can't give you the specific parameters, but you'll find an abundant documentation on the web.

---

### Post by suamme1 on 2008-03-05
> **allwin said:**
> One little problem...upon reboot, UBUNTU came up WITHOUT a swap file.  This is because, since it's a new disk drive entirely, for some reason FSTAB was messed up because UBUNTU codes the UUID of the disk, and not the device name!  WHY DOES IT DO THIS?


Just my 2 cents... When installing my new drive, this really helped because the new drive didn't end up stealing /dev/sda.

---

### Post by uncloned on 2008-03-08
Ok, this is a bit of a variation.

I have a laptop with three partitions
One hidden factory reinstall - want to leave that alone
Two fat 32 XP partitions
I am cleaning off the "data" partition of 52 gigs  for Ubuntu.

Currently I run Ubuntu from a USB hard drive (40gig) as a boot option.

I've done quite a bit of work un Ubuntu and would like to simply transfer it to the laptop "data" partition.

I'm thinkng I can do a fresh install of Gutsy to get the dual boot to work.
That seems to be common.

But... is there a way I can transfer all of my programs/data/settings/etc
and get the new install to work like my USB hard drive install?

Thanks,

Chris

---

