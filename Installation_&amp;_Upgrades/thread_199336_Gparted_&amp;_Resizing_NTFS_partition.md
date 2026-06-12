---
title: "Gparted &amp; Resizing NTFS partition"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by mustang on 2006-06-18
Hello everyone,

here's the current state:

/dev/hda1 == NTFS Windows Partition (149 total/44 used)
/dev/hdb1 == Ubuntu Breezy (30gb total /20 used)

Here's what I want:

/dev/hda1 == Ubuntu Dapper 
/dev/hdb1 == FAT32 Windows XP

Basically, I want Dapper on my big hard drive and windows on my small one. However, there's stuff on my NTFS partition that I want to keep. 

So here's my plan:

Create two partitions (ext3 & linux-swap) using the free space from my windows drive. Then install dapper on that, get everything I need from my windows partition, wipe the windows partition and wipe the Breezy drive and then install windows on the drive that used to have Breezy on it.

Here's what I did so far:

Download the gparted live cd. Now when I went to resize my ntfs partition, it got stuck there. I waited quite some time (30+ min) and nothing happened. Finally I quit and Window's chkdisk fixed some errors so everything is fine. 

But why did gparted freeze? Can I do something to remedy this?

---

### Post by catlett on 2006-06-18
I am surprised by your errors with gparted, I have had nothing but success with all types of filesystems.

Another route you can try is Aysiu's guide on Part Image. [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) This app lets you make a copy of your partition and then move it to another partition or drive.

You could make your process easier with this. Reformat your Breezy drive with gparted into 1 big fat32 drive. Use Part Image to make a copy of your XP partition. Move the part image copy of your xp install onto the fat32. 
Now you can reformat the entire nfts drive to ext3 and run you Daper install

---

### Post by xoros on 2006-06-18
I have had nothing but problems with gparted.  It messed up the ntfs windows partition to where I could not boot it.  

I restored it and worked with resizing/partitioning it with a program called BootitNG.   (- if you make a cd with that; on boot just hit cancel and don't install... you will then see a menu to just use the partitioning tools for free)

---

### Post by catlett on 2006-06-18
Gparted Live is very stable. Gparted as it is in Ubuntu and other linux distros has had problems because people get confused as to how to use it.
A partition or drive has to be unmounted to make changes to it. With gparted live it is unmounted because it is running off the live cd. It can do the operations right then and there.
With the other gparted, it is running off the hard drive it is trying to partition. This means you have to unmount the partitons before attempting to change them. Alot of people new to linux don't understand about unmounting partitions and get easily confused leading to errors.
I wouldn't recommend anything that I don't use myself. I install a new linux distro every weekend. I have 3 computers I mess with. I am constantly resizing/partitioning my drives. 2 of the computers have XP on ntfs. I have never had an issue with gparted live. Nor has anyone who I advised to use it came back with an error.
If you notice the gparted complaints are nor about gparted live. They come from people who ran gparted inside of Ubuntu.

Or I could be wrong. "Xoros, were you using Gparted Live or Gparted that was part of Ubuntu system when you had a problem?"

---

### Post by xoros on 2006-06-18
I was using gparted live.  I remember awhile ago I had the same problems with it.  I thought maybe the newest release would maybe have fixed issues I was having.  

All I wanted to do was resize the NTFS partition and make room for ubuntu.  Not trying to flame that program,  but I didn't experience any problem with the other program.

Edit: I actually really wished/wish gparted would work,  I guess thats why I keep going back to it every so often.

---

### Post by mustang on 2006-06-21
[QUOTE=catlett]I am surprised by your errors with gparted, I have had nothing but success with all types of filesystems.

Another route you can try is Aysiu's guide on Part Image. [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) This app lets you make a copy of your partition and then move it to another partition or drive.

You could make your process easier with this. Reformat your Breezy drive with gparted into 1 big fat32 drive. Use Part Image to make a copy of your XP partition. Move the part image copy of your xp install onto the fat32. 
Now you can reformat the entire nfts drive to ext3 and run you Daper install[/QUOTE]

Hi catlett,

I gave gparted another try (probably should have done that before posting!) and it appears to work now. No idea what was causing the hang up first time around.

Thank you for your help anyways.

---

