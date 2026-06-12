---
title: "Boot Failure after installation from 6.10 live cd"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by rphilli5 on 2007-02-24
I downloaded the 6.10 live cd and it worked perfectly on the machine 
amd 1.2ghz

Installed ubuntu with all default options.  The installation completed sucessfully and requested a reboot.

After reboot it appears the system can not find the hard drive / boot record.  The screen displays boot failure and requests to press any key to boot from an alternative source.

This is my first time working with linux so any help would be greatly appreciated.  I reviewed several of the previous posts but did not find any solutions that worked.

---

### Post by logos34 on 2007-02-24
Boot from the livecd, load the desktop, and open a terminal.

Type
sudo fdisk -l

Post the output.

Could be a number of things:
--grub didn't install, or installed with errors
--the grub config file is wrong or /boot is out of range of the bios 
--the bios settings are incorrect

---

### Post by rphilli5 on 2007-02-24
Here's the output from running the command.


Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2368    19020928+  83  Linux
/dev/hda2            2369        2434      530145    5  Extended
/dev/hda5            2369        2434      530113+  82  Linux swap / Solaris

Is there any different kind of bios settings needed for linux?  This machine used to run win 2000 server.  As configured now the graphics only has 8mb, does that matter?  It can have up to 32mb, but the live cd runs better with more of the the 192mb dedicated to system memory.

---

### Post by logos34 on 2007-02-24
I> s there any different kind of bios settings needed for linux? This machine used to run win 2000 server. As configured now the graphics only has 8mb, does that matter? It can have up to 32mb, but the live cd runs better with more of the the 192mb dedicated to system memory.

I'm only using 16mb (out of a possible 128mb), but have a lot more sys memory than you.  8mb should be just enough to get by (unless you try to run apps like Google Earth, in which case you'll need all 32).  192mb is the minimum recommeded for the livecd.

How old is this machine?  What motherboard? You might try flashing your bios with the latest update.

---

### Post by logos34 on 2007-02-24
Check that your hard disk detection is set for 'auto' or the like.  It may be on 'User defined'   or manual.

Then try reinstalling Grub.

Boot from the livecd and go into the desktop. 

Open a terminal and type:
> sudo grub

You'll get a grub prompt ('Grub >').  Then
> root (hd0,0) 
setup (hd0) 
quit

Reboot.

If that fails, give [SuperGrub]("http://supergrub.forjamari.linex.org/") a shot.

---

### Post by rphilli5 on 2007-02-24
Logos34 - 

Thanks for  all of your help.  The answer was actually in the bios, somewhere during the installation and reformatting process the bios stopped looking for the hard drive.  I am not sure how that changed.  Maybe I fat fingered it when changing the video setting, but I doubt it as I am very careful with the bios settings.  Setting it back to auto configuration allowed it to recognize the hard drive and the system booted with no issues.  Thanks again.

---

### Post by logos34 on 2007-02-24
> The answer was actually in the bios, somewhere during the installation and reformatting process the bios stopped looking for the hard drive...Setting it back to auto configuration allowed it to recognize the hard drive and the system booted with no issues.

I was beginning to think that might be the problem, which is why I mentioned it in my last post...It seems to be a common problem (but usually associated with people putting in new disks and then forgetting to check the BIOS).

Glad you got it working again!

---

### Post by Quibly on 2007-03-03
I have the exact same problem. When I ype "sudo fdisk -l" in the command prompt of the live CD (which can boot), this is what I get:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2401    19286001   83  Linux
/dev/hda2            2402        2494      747022+   5  Extended
/dev/hda5            2402        2494      746991   82  Linux swap / Solaris

I also think that this is a problem with the BIOS. I am just not that good with that stuff. Ill try changing the BIOS settings and Ill post if I got it or not...

---

### Post by Quibly on 2007-03-03
Wohoooooooooooooooooooooooooooooooo!!!! I finally got the computer to work!!!! Yeaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!!!!!!!!! Thanks a lot logos!!!!!!!!1 :guitar: :guitar: :guitar: :guitar: :guitar: :guitar: 

To fix it I just had to change the BIOS setting for the HD...

---

### Post by bwallum on 2007-03-05
I've got the same prob. 

I have tried the 'install grub to Master Boot Record', and it does not fix it.  I am now going to try a low level format of the hard drive. I'll let you know how I get on. If you let me know if you find a solution first, that would be great.

Regards
Bob

---

### Post by bwallum on 2007-03-05
....and then I read the rest of the thread!!

I went into the BIOS, did a default reset of the hard drive. Nothing seemed to change. Then saved the MBR, exited and rebooted Ubuntu from the hard drive... and it did!!

An odd feature to an otherwise good first time experience.

Regards
Bob

---

