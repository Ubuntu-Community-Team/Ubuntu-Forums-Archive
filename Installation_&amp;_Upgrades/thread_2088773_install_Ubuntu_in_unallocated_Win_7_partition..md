---
title: "install Ubuntu in unallocated Win 7 partition."
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by daemoncycler on 2012-11-27
Hi,
This seems like it should be pretty simple but I am having problems determining Windows partition .vs Linux partition.

I have 350Gb of unallocated space on my hard drive & would like to install Ubuntu there.  From what I have read Ubuntu prefers to be in charge of the partitioning for GRUB.  

It looks like /dev/sda1 & sda2 are to be partitioned ntfs.  Can I allocate (thru Windows) the 350GB as Logical ntfs partition & point to that space during the Ubuntu install?  Or do I use GParted to carve up the 350GB of unallocated space (either during the install or beforehand)?

I want Windows 7&#8242;s boot manager be the primary boot manager.

At this point have four Windows partitions, System reserved, Primary boot C:, Music M: & unallocated.  Because Ubuntu will require three partitions too will the unallocated space need to be created as logical?  Think I'm stuck on Windows partition .vs Linux partition, created either during the Ubuntu install or ahead of time with Gparted.

thanks

---

### Post by darkod on 2012-11-27
1. You can't create linux partitions from windows, so don't even try it. Leave the space as unallocated, as it is now.

2. You can prepare partitions in advance but that's not necessary, you can do the same with the ubuntu installer. So, the choice is yours. Yes, all partitions you create will have to be logical since there are already 3 primary partitions.

3. It's better to use grub2 as bootloader on the MBR because windows bootloader can't boot linux. There are ways to do it, but it just adds unnecessary complications.

Do you have any particular reason you want windows bootloader on the MBR?

---

### Post by arubislander on 2012-11-27
> **daemoncycler said:**
> At this point have four Windows partitions, System reserved, Primary boot C:, Music M: & unallocated.

The above quote is causing me some concern. You mention four partitions, but you do not specify if any of them is a logical partition...

---

### Post by darkod on 2012-11-27
> **arubislander said:**
> The above quote is causing me some concern. You mention four partitions, but you do not specify if any of them is a logical partition...

Me too. Unallocated space is not treated as a partition, it's simply unallocated space.
But if you really do have a fourth partition, and it's primary, then you can't create any more partitions even if the fourth is empty. You will have to delete it and create logical partition in its place with the ubuntu installer.

I wouldn't recommend creating extended partition in advance from windows, just leave the space as unallocated and use ubuntu tools for partitioning it.

---

### Post by daemoncycler on 2012-11-27
Hi,
thanks for all this support.
 
> **darkod said:**
> Do you have any particular reason you want windows bootloader on the MBR?
I read in another forum, not Ubuntu:
[COLOR=#222222]*[COLOR=#996633]When dual-booting Windows 7 and a Linux distribution on a computer with one hard drive, the best option is to have Windows 7&#8242;s boot manager be the primary boot manager. Why? Because whenever you reinstall or update Windows 7, its installer will overwrite anything it finds in the portion of the hard drive where critical boot-related programs are installed. That portion of the hard drive is known as the Master Boot Record (MBR). Also, certain [_anti-virus programs_[IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG]]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/#") have been known to mess with the contents of the MBR, so installing GRUB in another location will ease the maintenance headache associated with your system. This point determines where GRUB will be installed.[/COLOR]*[/COLOR]
 
 
> arubislander - The above quote is causing me some concern. You mention four partitions, but you do not specify if any of them is a logical partition... 
The Music partition is Logical & the unallocated space was a Window 8 preview which I removed & formatted last night, so yes it is unallocated space now.
 
My thinking was stinking - I was imagining installing Ubuntu the way one would install a Windows partition. Have put Ubuntu up on VirtualBox & installed it on a couple laptops where removing existing OS, don't know why I'm having trouble wrapping my brain around this. Just don't want to wreck my Windows Partition.
 
> **darkod said:**
> I wouldn't recommend creating extended partition in advance from windows, just leave the space as unallocated and use ubuntu tools for partitioning it.
So during the Ubuntu installation I can point to that unallocated space & use the Ubuntu tools to partition it as logical & then proceed as normal? I guess that is exaclty what you just said.
 
thanks
 
edit: perhaps my concern is during boot.  Will Windows give me the option which partition to boot from after I install Ubuntu?  As it would if I were dual booting Windows.
If grub2 is the bootloader then probably not - it will be Ubuntu?

---

### Post by oldfred on 2012-11-27
The issue on grub2 or Windows boot loader has been on going for a while. We tend to prefer grub2 as it is designed to multi-boot where Windows is not.

There was an issue with early version of grub2 and flexnet or DRM manager in Windows. Flexnet would write sectors for your DRM software in the area just after the MBR that grub2 also used. Grub2 has a work around for that but the area after the MBR was/is for more boot code. Also some HP or Dell software would write into that space. 

If you add third party tools to modify the BCD to boot Ubuntu you force grub into a PBR or partition boot sector. Grub does not really fit and converts to hard coded addresses and on grub updates may break. 

So the real issue is MBR can only boot one system. The new UEFI system allow multiple boot loaders in one efi partition so they all can work.

Whichever system you install to the MBR, you need to have a Windows repairCD or flash drive for Windows, and you should have a current Ubuntu liveCD or flash drive. Or have other repair tools like Boot-Repair, Supergrub, and many others.

---

### Post by daemoncycler on 2012-11-28
Thanks oldfred, that's great info.  Going to take me several hours of Googl'ng (Bing'ng) to fully adsorb that.

Suppose I'm just not feeling too adventurous right now but running Ubuntu under Virtualbox has been a breeze so guess just continue doing that on the desktop.

Have couple old laptops.  One is P3 with 512 MG RAM & has been running Lubuntu for 6 months now - doing it extremely well.  That is what first got me involved with Ubuntu.  It made that old P3 usable once again.  The other laptop, a core2duo , would be a better candidate to experiment with uefi & multiboot.  Not too much of value on the laptops.

I'll find something else to do with that unallocated space.

thanks to all for help.

---

