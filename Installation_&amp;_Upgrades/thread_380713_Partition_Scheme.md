---
title: "Partition Scheme"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by j o e l on 2007-03-10
Hello.

I was wondering if anyone would mind providing a couple of recommendations on a partition scheme for me.

I just purchased a new PC that came with Windows Vista on it.  I want to install at least two other derivatives of Ubuntu on this box, also.  I am going to install UbuntuStudio when it comes out later next month, and I'd also like to add regular Ubuntu or Xubuntu right now.  Specifically, I'm thinking about just installing Dapper on here, as I want to be able to use the Mono apps (they didn't work when I installed Edgy on my laptop).  So, those are the plans in terms of OS's.

Physically, I have two 320 GB HDD's.  Vista is only on one of them at the moment.  My other question is whether or not to create a separate partition any of the OS's could write backups to.  Would it be best to just devote one of those 320 GB HDD's to that, and use the other HDD to partition for the OS's?  Or do you have some better ideas?

Thanks for all of your help, in advance!

j

---

### Post by Kateikyoushi on 2007-03-10
Why do you want to have 3 versions ? Basically the core is the same the desktop environtment and applications are different. You can install ubuntustudio and gnome-desktop and xubuntu-desktop on it at login select which DE you want to use, or any other way around.

---

### Post by j o e l on 2007-03-10
Oh, good point, Kateikyoushi.  But I guess I was thinking with different versions, I needed separate partitions.  By separate versions, I mean 6.06 vs. 6.10, not Gnome vs. XFCE.  Sorry, I guess, I wasn't very clear.

---

### Post by Kateikyoushi on 2007-03-10
Then you will need a / partition for each version, the swap and /home can be shared. I doubt you need the whole hard drive for backups a partition will do, with using ext driver for windows you can read and write to ext partitions as well.
I do not see real difference in which drive you use for the OSes except for the installation. Do what you feel most comfortable with.

You can not hibernate if the swap is shared due to if  you boot another version then it will overwrite the swap partition what is used for storing the hibernation data.

---

### Post by zvacet on 2007-03-10
Make separate partition for home.In that case you can re-install upgrade.fresh install...without losing your data.
1.root / 10-15(maybe 10 is enough,but...)
2.swap 1GB(maybe more,it depends of your ram)
3.home rest of HD

---

### Post by j o e l on 2007-03-10
Ok, I'm hoping someone can help me out of a mess I have myself in, now.

I decided to just go with Dapper for the time being, so I installed that on my second HDD.

BEFORE:
(1) 320 GB - Windows Vista Ultimate
(1) 320 GB - NTFS

AFTER:
(1) 320 GB Windows Vista Ultimate
(1) 320 GB partitioned as....
      4 GB - linux-swap
  100 GB - /
  216 GB - NTFS

When I rebooted my machine, grub loaded without any entries for Windows.  Once it booted into Dapper, networking was not working (Default Ethernet/DHCP) despite the fact it has always worked on any machine I've loaded Dapper onto.

Well, I thought I would remove Dapper and resize the NTFS partition back to its original state to try again, but with Dapper and Vista installed on the same drive.

CURRENTLY:
(1) 320 GB - Windows Vista Ultimate
(1) 320 GB - NTFS

The problem I'm having is at bootup now, Grub is still loaded and stopping with an error, obviously since I removed Dapper.  I wanted to put Vista and Ubuntu on two separate drives and have grub control the booting process.  Could I reinstall Dapper and just create an entry in Grub for the first hard drive that Vista is on?  That's what I started to do, but I couldn't remember what the kernel entry looked like for Windows?  Or how can I remove grub so I can return my machine back to its original state?  

I'm really not sure what the answer is here.  I really want to dual-boot with both Vista and Ubuntu on separate drives.  I'm just not sure how to make this work, or if it is possible?

One other note: I did try changing the drives around in BIOS in an attempt to boot into Vista that way, but it gave me a disk error.  So, it seems that boot information for both OS's is on the same drive?

Thanks again for your help!

---

### Post by j o e l on 2007-03-10
Ok, I had to try something else while I was waiting for any suggestions....

I reloaded Ubuntu to see about fiddling around with the menu.lst to see if I could add the entry in there manually.  I grabbed my Edgy disk, instead of Dapper, and there are a few changes now.

CURRENTLY:
(1) 320 GB Windows Vista Ultimate
(1) 320 GB partitioned as....
      4 GB - linux-swap
  100 GB - /
  216 GB - NTFS

Now, when I reboot, I see Windows Vista displays in the Grub.  However, selecting that doesn't do much.  The screen shows it begin to boot into Windows, and then it goes blank.

menu.lst entry:
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Anything missing?

Thanks again...

---

### Post by j o e l on 2007-03-10
Ok, I saw this in another thread and tried it.

Grub device map looks like this...
(hd0)   /dev/sda
(hd1)   /dev/sdb

...so I added the following to the menu.lst file under Vista...
map (hd0)(hd1)
map (hd1)(hd0)

Not really sure what it's supposed to do, as it didn't work.  And actually, I get the same result.  Begins to boot into Vista, switches to a black screen and hangs.

---

### Post by zvacet on 2007-03-11
I don know about that but i see that you put wrong format for Ubuntu home partition.it is not NTFS it is ext3 format.

---

### Post by j o e l on 2007-03-11
Hello, zvacet.

Thanks for your help.  I guess I wasn't very clear.  The drive Linux is installed on was originally formatted as NTFS by the computer manufacturer.  I resized the partition and reformatted the new space to a swap and ext3 (/) for Ubuntu.

So, you are correct.  Although, I already had that drive formatted as ext3.  The 216 Gb NTFS partition is just what was originally there.

Thanks again for your input, zvacet.  

I'm afraid I'm going to need to reformat that drive and start over.  I'm going to hold off on that for a bit longer, though.  It's such a pain getting thing setup the way you want them.  Unfortunately, I need Windows for school - all MS.  They did send me an XP disk, but if I have to use Windows, I'd like to use Visa.  At least it looked much nicer than before. :-P 

j

---

