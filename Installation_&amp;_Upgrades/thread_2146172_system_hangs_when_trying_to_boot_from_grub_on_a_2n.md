---
title: "system hangs when trying to boot from grub on a 2nd hdd"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by j-dowsett on 2013-05-17
Hi.
I'm having trouble with a dual boot, I can't get Ubuntu to boot properly, although the install itself works fine (see below).


I've just installed Ubuntu Gnome 13.04 to dual boot alongside Windows 7.  Computer is an 64 bit i7, 8GB RAM.

As this is my uni computer I decided to add a second hard drive (WD3200AVJS) in order to leave the Windows 7 drive alone entirely.  I followed the directions given here [linuxbsdos.com - dual-boot ubuntu...windows-7...2-hard-drives/]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/")

Upon completing the installation I changed the bios settings to boot from the second hard drive first.  However the computer fails to display the grub boot options, after turning ont he machine i get the brief boot splash screen (offering the options to edit bios, go to boot menu etc), and then an empty black screen with a flashing cursor.  Nothing further happens.

If I change the bios to boot from the first drive, Windows boots fine.
I have a USB stick on which I have a full install of Lubuntu (ie it's not a LiveCD but a regular install), if I boot that I can use the grub menu it shows to boot Ubuntu installed on the 2nd HD, and I can then eject the usb stick fine - so the install itself works, it just appear to be a boot problem.

I have Windows on /sda
I have 200MB   /boot   partition on /sdb1
I have 40GB     /         partition on /sdb5    (am on a different computer right now, but i think it's sdb5, it's def on /sdb)
I have 270GB   /home  partition on /sdb6    (as above)
and i have an 8GB swap partition also on /sdb_something

I did the install from a bootable USB made from Ubuntu Gnome iso.  I don't think it's the cause of the problem, but when I did the install, the USB stick was on /sdb, optical drive on /sdc, so the hard drive onto which I installed (which is now /sdb) was at the time /sdd.  I ensured I selected /sdd as the target for the bootloader.

After booting Ubuntu (on /sdb) using the Lubuntu USB stick I have reinstalled grub (so now specifying /sdb as the target) and grub-update, and it's made no difference.
I have run gparted and set the boot flag on /sdb1.  No difference.

I won't be at the PC until monday morning, but I was hoping that I could go into Uni with a clear idea of the steps I should take to try and identify or fix the problem, or what further information I should provide (now, or on Monday depending upon what is needed).

It's fortunate I can work around this, but I'd be very grateful for any suggestions as I don't really want to spend the next 3 years using a USB stick to boot my computer!

Thanks in advance
Joseph.

---

### Post by oldfred on 2013-05-18
Grub does not use boot flag, Windows has to have boot flag, but a few BIOS will not even let you start to boot unless you have a boot flag on a primary partition. So even with grub we suggest a boot flag but it will not be used by grub.

If flash drive boots, your grub in the MBR should also, but maybe a reinstall will help.
IF you can boot just try installing grub2's boot loader to the MBR.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Or you can do this to make sure.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And if those do not work post link to BootInfo report. But I do not expect it to show anything? You can just install to your flash drive, main install, or the installer you used. Or download a full repair CD. (I do all of those).
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by j-dowsett on 2013-05-19
Thanks, I'll follow those steps on Monday.  I've not come across Boot Repair, that looks like it could be helpful.

Having googled a little more yesterday, I see there are also two possiblities for grub, grub-pc and grub-efi.  When I was looking at the gub files on /sdb, I'm pretty sure I remember seeing grub-efi references, I'd also be pretty certain that the Lubuntu USB is installed with grub-pc (I installed onto it using a VM, and it also happily boots some fairly old laptops).  If indeed the two installs do have a different type of grub then I guess that's worth investigating too.

---

### Post by j-dowsett on 2013-05-20
Good morning!

Thanks for your help, I just ran boot-repair and everything is now booting correctly.  I did notice that boot repair uninstalled grub-efi and installed grub-pc, so maybe that was the problem.  Whatever, it's fixed now...


Thank you very much.

---

