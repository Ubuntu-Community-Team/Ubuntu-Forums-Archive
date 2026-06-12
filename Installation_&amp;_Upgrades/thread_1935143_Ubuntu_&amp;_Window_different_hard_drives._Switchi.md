---
title: "Ubuntu &amp; Window different hard drives. Switching W/ Bios."
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by Wrekx on 2012-03-03
I want to install Ubuntu 11.10 on a second hard drive so I can choose between Windows and Ubuntu by changing the boot options. I'm assuming if I partition a hard drive, I will be forced to select between operating systems during the boot process. I don't really want to do this. I want to turn my computer on, and go get some coffee well it loads up. 

But I'm a completely new Ubuntu user. I loaded up the disc yesterday, and I already had my "wtf" face on. I wrote down the IDs for my hard drives, so I was able to identify them but the /dev/sib stuff just totally threw me for a loop (not sure if that's correct but it's an example).


So, I was reading to unplug my C: drive and then install it on D:. But if I could figure out what the "/dev/sib" stuff was I would appreciate that.

---

### Post by darkod on 2012-03-03
The hard disks in linux get labeled as devices with /dev/sdX where X changes into a,b,c, etc for first disk, second, third, etc.

So your first disk would be /dev/sda (most probably plugged into a sata port with lower number on the board), the second /dev/sdb.

Yes, you can unplug the windows disk during the ubuntu install. That way ubuntu and the grub2 bootloader will go on the second disk without a chance to go on the windows disk.

If you have more questions just ask.

I have to say I see no point in what you are trying to do. You say I want to leave my computer booting. Fine, but until you select which disk to boot with the board boot menu (or BIOS) you still have to be present to make the selection. Only after that you can leave the computer.
You can do the same by using grub2 bootloader and make a selection which OS to boot in its boot menu. In fact, it will probably be lot faster. After you make the selection you let the computer boot, same as above.

EDIT: Note that you can't install ubuntu on D:. Not literary. Windows assigns letters usually to ntfs partitions. So if it's called D: it means most probably that is a ntfs partition. Linux doesn't install on ntfs, it needs unpartitioned space to create its own partitions with its own filesystem. So you would need to delete the ntfs partition, leave it as unallocated (unpartitioned) and then start the ubuntu install. Or with the ubuntu installer use the option "erase and use this disk" or what ever it was called, to tell it to delete the disk and use it for ubuntu.
When installing you have best control if you use the manual way, but if you seem unsure what to do, you might not want to use it, even though it's not difficult at all.

---

### Post by epichacker1 on 2012-03-03
The /dev/sda is like you C drive, and /dev/sdb is like your D drive. If you set the Ubuntu partition on D drive, then that is where it will boot from. If you really want to dedicate the disk to Ubuntu, clear the disc D from the LiveCD using the erase all files on this disc. You will preseve all files on your other hard drive (/dev/sda). To boot up alternate OSes, you will have to select the hard drive you want to load. 
I hope that helps.

---

### Post by Wrekx on 2012-03-03
Oh yeah, I have a F key that brings up my boot options too.

So my computer will auto load to Windows for me, for guests, and so on. However when I want to use Ubuntu I can just easily command the computer to show me alternative boot options.

That seems like the ideal set up to me. If I become comfortable enough, I will just go into BIOS and switch my boot hard drive to the Ubuntu. I ultimately would like to get away from the Microsoft dominate market and am hoping to become a skilled Ubuntu user so I may show it to others and help them start using it.

However, I am an online student and have periods where I am just busy as heck. So, I don't have all the time to experiment with Ubuntu that I would like and will just want to go straight to windows.

---------------------------------------------------------



Yes it is NTSF. Thanks, that was another problem I had. I had assumed sdb was my second hard drive, but also had trouble loading it. Now I know why. I'll change it to unallocated, I'll also remove C: when I load it. Now that I understand better I don't have to be so hard headed. Lol.

---

