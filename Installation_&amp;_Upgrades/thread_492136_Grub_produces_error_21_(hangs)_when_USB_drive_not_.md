---
title: "Grub produces error 21 (hangs) when USB drive not pressent (Ubuntu on USB drive)"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by Declan Moriarty on 2007-07-04
I have installed Ubuntu 7.04 Feisty Fawn on a USB drive and have XP Pro on my main machine.  Grub installed OK on the Hard Drive in the PC (IDE).  It boots into Ubuntu and XP fine.  However when I remove the USB drive it comes up with Error 21.  Is there a way of bypassing grub when the USB drive isn't pressent? Or making it ignore the fact that the USB drive isn't always pressent?  Great security feature:  if your machine is stolen no one can get in to it without the Ubuntu disk attached!

Your help very much appreciated.

---

### Post by metallicamaster3 on 2007-07-04
You get error 21 because GRUB is looking for menu.lst in your Ubuntu partition on your USB Flash Drive. Since you removed it, then obviously GRUB wont be able to find it. THe only way for it to work, is to remove grub off of your IDE drive, and go back and reinstall grub on a 100MB partition that you must make on your IDE hard drive.

so, do the following:

erase grub from your IDE drive (if you can. if not, skip this)
use the ubuntu livecd/alternate disk to make a new partition, @ around 100MB.
Then, use the ubuntu livecd/alternate to reinstall grub, on the 100MB (make the mountpoint "/boot")
then, you can remove your USB dongle and have GRUB still work.

---

### Post by confused57 on 2007-07-04
> **Declan Moriarty said:**
> I have installed Ubuntu 7.04 Feisty Fawn on a USB drive and have XP Pro on my main machine.  Grub installed OK on the Hard Drive in the PC (IDE).  It boots into Ubuntu and XP fine.  However when I remove the USB drive it comes up with Error 21.  Is there a way of bypassing grub when the USB drive isn't pressent? Or making it ignore the fact that the USB drive isn't always pressent?  Great security feature:  if your machine is stolen no one can get in to it without the Ubuntu disk attached!

Your help very much appreciated.
You can also restore Window's IPL to the internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You could then use Super Grub Disk to boot Ubuntu on your USB drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can also restore your internal hard drive's mbr

or

If your bios is capable of booting first to USB, then you can install grub to the USB mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Then boot first to your USB drive, you should get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...this change is temporary and can be made permanent if it works.

---

### Post by Declan Moriarty on 2007-07-04
metalicamaster3,

I don't want to create a 100Mb partition on IDE hard drive in my machine, as windows works fine and I don't want to create any unnecessary problems or create instablities.  This is why I uses a USB hard drive in the first place.  Reading confused57's post gave me an idea.  It would be nice to have grub on a CD and not on the main hard drive MBR at all.

I have already used another flash drive to get a live CD transfered onto to boot off.  However this didn't boot at home.  It booted fine at work.  I was then able to get it to boot at home.  The problem is that I have an Award Bios that reading about creating bootable USB "Live CDs" people say has a bug that stops it booting of USB drives.  I would say that my BIOS has a design fault.  If I say I want to boot off USB-HDD and I put a non-bootable USB drive in the system at boot time it comes up with a "Non System Disk - Please press any key" type message and you press any key and it boots windows.  When you put a bootable disk in it boots windows anyway!  The solution is to go into another sub-menu in the bios "Hard Disk Boot Order" and change the order.  You can then boot successfully.  But the next time it forgets it so you boot into windows again!  You have to go into the BIOS and change this sub-menu every time you want to boot from USB!

I would dearly love to have GRUB on the USB drive but I don't think it will work, so the next best thing is a CD-ROM.  I don't have a floppy drive.

If I get rid of grub on my main hard drive (Windows XP recovery disk) aud use Ubuntu to create a bootable CD with the /boot/grub partition on it this should work?  So that the grub that is installed on the USB drive is on the CD, with the menu.lst edited to point to the USB drive (it should be anyway).  Would this work?

Any ideas about my problem BIOS would be appreciated.

Thank you very much already.

---

### Post by logos34 on 2007-07-05
Are you sure you can't save that boot order?  Try setting the USB drive in first position, then save it as a bios **profile** named, say, 'Boot usb-hdd'.  

If you are forced to make a Grub boot CD, here's the official guide:
[URL="http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html#Making%20a%20GRUB%20bootable%20CD-ROM"][COLOR="Blue"]
http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html#Making%20a%20GRUB%20bootable%20CD-ROM[/COLOR][/URL]

You'll have to make a change or two so it works in Ubuntu.  Try this:

**cd**

**mkdir iso**

Now just copy over all of /boot (initrd and kernel images, menu.lst, etc) to the new folder 'iso':

**cp -R /boot iso**

(by including menu.lst you will get a menu screen instead of just a command prompt).

The essential ingredient for making a Grub bootable CD is the file 'stage2_eltorito'.  In Ubuntu it can be found in the /lib/grub/i386-pc directory.  Copy it to iso/boot/grub:

**cp /lib/grub/i386-pc/stage2_eltorito iso/boot/grub**

Then copy and paste the mkisofs command from the official howto:
[B]
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \
         -boot-load-size 4 -boot-info-table -o grub.iso iso[/B]

Look for '**grub.iso**' in your home directory.  Write it to disc.

If you want additional boot options in your menu.lst you might consider using the sample '**menu.lst**' in the Grub-for-DOS package ([[COLOR="Blue"]grub4dos-0.4.3pre1.zip[/COLOR]]("http://sarovar.org/project/showfiles.php?group_id=320&release_id=777"))
and modifying it by adding your own kernel entries to it or vice-versa.

---

### Post by Declan Moriarty on 2007-07-13
Thank you very much.  I have now made a grub boot CD.  I needed to remove the savedefault commands from the menu because otherwise it didn't work since CD's are read only!  When booting from USB (Changing the boot order in the bios using F12) it comes up with Error 17 Cannot mount partition.  I suspect this is a timing issue with the USB drive not being quite ready when it is booted.  But the CD method works fine.  I now have .iso file and a script to make it in my home directory on Ubuntu.  Plus the iso directory.  When the kernel changes I can just create another .iso file an create another boot CD.

---

### Post by ozyank on 2008-04-11
Is it possible to get Grub to read the menu.lst from one of the Windows XP drives? This seems like such a simple solution but I don't know how to do it, if it can be done at all.

---

