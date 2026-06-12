---
title: "Ubuntu Install Wont Boot"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by fornews on 2007-12-14
I've installed both XP and Ubuntu

Partitions roughly and in order :  XP 15 Gig, Ubuntu ext3 15 gig, FAT share 6 Gig, Swap 1.5 Gig

I've had a number of problems trying to get both XP and Ubuntu on this PC so I'm trying the approach here   [ http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")

That basically says no Grub and in stead use the Windows Bootloader.

Both OSes are installed.  I can boot to XP and I've created the ubuntu.bin using the share, copied to my XP C:\ and when I reboot I get the option of booting either Unbuntu or XP.  I can boot no problem to XP

When I select to boot Ubuntu I get nothing but a black screen and cursor.

Help appreciated

Jon

---

### Post by scurry7 on 2007-12-14
I'm not familiar with using windows boot loader, why not use grub?

So you get blank when you try and boot to Ubuntu...absolutely nothing?

---

### Post by fornews on 2007-12-14
When I try to boot to ubuntu it leaves the Windows Bootloader screen which implies it is attempting to boot the ubuntu image but nothing happens other then going to a blank screen with only a cursor in the upper left hand corner.

Why not use grub... It just wouldn't work. I reinstalled XP and Edgy several times with varying results of failure. Found that link which says no grub so figured I'd try that.

Do you have a link to another approach using grub ?

I have an IBM Aptiva. It came with a 30 Gig drive that went bad so replaced with an extra 40 Gig

Thank you !

Jon

---

### Post by xeth_delta on 2007-12-14
It would seem like the boot loader cannot find the small file you created from the linux partition, or that the contents is not what it should be. dd should have taken data from your boot or root partition (if you don't have a boot one).

What were the problems you had with grub?

---

### Post by logos34 on 2007-12-14
personally, I think this is a bios issue, maybe 1024 cylinder limit or something...it's an old computer.  Grub can't see that far out to the linux root.  If that's the case then the solution would be to shrink windows a tad and add a /boot partition at the front of drive. I could be wrong though.  Maybe it could be solved simply be reinstalling grub to bootsector of the root partition and redoing the dd command, etc.

---

### Post by scurry7 on 2007-12-14
right, it is an old comp.  have you tried lilo? (im just shooting in the dark, im not that knowledgeable...yet) sorry...
logos34 seems to know what he is talking about. so partition the drive with the /boot at the beginning of the hd? worth a shot i guess...

hope you figure it out...

---

### Post by fornews on 2007-12-15
Thank you .. 

It is an old PC... in relative terms... younger then me :)

Assuming it is the 1024 cylinder issue can you point me to some directions for installing XP and Ubuntu ?

This PC had Win98 on it, 30 Gig HD crashed so replaced with a 40 Gig from another PC.
So I can reinstall everything and start from scratch if that makes sense, but if there is an outline somewhere I can follow that has a high probability of success that would be really appreciated.

Again thank you !!

---

### Post by logos34 on 2007-12-15
The easiest way is probably to reinstall both OSs--it will take less time ultimately than resizing windows from the left (I've done it and it still amazes me how long it takes to push just a few gigs worth the files over from left to right).  Use gparted on the ubuntu live cd to delete the partitions on the drive and create a small 50-100 MB ext3 partition at the front.  Then install windows right after that.  Next, reinstall ubuntu but tell it to make a separate ext3 boot partition in that new space, with mountpoint '/boot'.  

Give that a shot.

---

### Post by fornews on 2007-12-15
I think I got it now.

What I did was remove my / and swap partitions.
I tried this before but had trouble totally removing the swap but this time it worked.
Then I moved the extra FAT partition all the way to the end of the drive.
I received some warnings/errors when I moved that partition as if it wouldn't take place but it did.

I then followed the instructions I found on this page
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

And in particular let the install process do the partitioning. 

Appreciate the help..

Thank you

---

