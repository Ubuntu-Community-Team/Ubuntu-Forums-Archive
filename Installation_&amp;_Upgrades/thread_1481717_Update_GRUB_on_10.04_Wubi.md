---
title: "Update GRUB on 10.04 Wubi?"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by ozjimbob on 2010-05-12
I had a bad experience with 9.04 - I installed some recommended system updates, and the updated GRUB killed my installation (which is WUBI), not letting me boot.

I've now installed 10.04, and some updates have come through, one of which is GRUB.  So I'm now looking at the "Configuring grub-pc" dialogue box that's popped up, and there's an option to "Continue without installing GRUB?".  

What are the risks here?  Is my 10.04 WUBI system going to die if I upgrade GRUB again? Or is it going to die if I *don't *upgrade GRUB?

Advice required before I click the CONTINUE button...

---

### Post by lmsurprenant on 2010-05-16
I checked the box to continue without installing Grub (because I only saw my physical hard disks in the utility and wanted to make sure I didn't overwrite the windows bootloader).  

Anyway, turns out this was the **wrong** thing to do...now when I but into my ubuntu partition, all I see is the grub command line--with no options to boot any loopback / kernels.

From [http://ubuntuforums.org/showthread.php?t=977225](http://ubuntuforums.org/showthread.php?t=977225) it sounds like we're not the only ones with this problem...still looking for answers.

---

### Post by bigwigbaz on 2010-05-20
@ozjimbob, 

have you upgraded your system from 9.10 through wubi? If not it's no real bother to go back and reinstall through windows as long as you have a reasonable speed connection. If you have upgraded and need to save your data, you can use a live USB or live CD if you cannot boot into ubuntu after failed grub update, open terminal and type; 

sudo fdisk -l
sudo mkdir /win   (can be anything you like)
sudo mount /dev/sdxy /win
sudo mkdir /vdisk   (again, can be anything you like)
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

where the "x" and the "y" in "sdxy" is replaced with the correct HDD letter (starting at a of course), and the correct partition number (starting at 1), of the Windows partition your Wubi install is on. The first command will have given you the location.
Once running those commands, open up Places>Computer>Filesystem>vdisk, and you should find the contents of your root.disk in there. Now you can backup your data to external media, and reinstall Ubuntu with Wubi if you like.


Even if it makes a right mess of the boot, you will be able to recover using the above method (from [http://neosmart.net/forums/showthread.php?t=5004]("http://neosmart.net/forums/showthread.php?t=5004"))

I have used it myself to do exactly the same thing, but just to find out how to recover data on wubi install, not through boot problems. 

I think the grub 2 is better anyway. 

Sorry if I have misunderstood the problem.

---

### Post by monkeyMonk on 2010-05-21
Hi,
   I had have the same problem, and by searching around, find a solution finally!
   Now I can boot into ubuntu 10.04 !

   The fix procedure (or say workaround?) is simple, but need to be done in Windows.
   
   Login into Windows, find the location where you install your wubi. For example, if you installed wubi on the C: drive, you should see a file named wubidir in C:\. Go online to get latest wubidir file and replace it. That's it. After all, I'm be able to boot into 10.04!

  Follow to link to read more  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

 There is one thing that I don't fully understand the explanation. It says this is a bug in Grub 2, but the fix (or workaround?) is to be done in Wubi, update the file of wubidir.  What really is the contains of wubidir? I'm curious what the fix really is.

---

### Post by J D Bradley on 2010-07-05
Last night applied lots of updates to Ubuntu 10.04, when rebooted choosing Ubuntu from the Windows XP boot menu would cause the machine to reboot, there was an error message but I couldn't read it as too quick.

My fix was found in the link below:

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

Basically the file system appears to have become corrupted when updating, fsck found errors and fixed them.

---

