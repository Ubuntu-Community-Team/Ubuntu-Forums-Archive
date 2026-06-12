---
title: "Can't dual boot XP any more"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by abstract51 on 2006-06-10
Having a problem loading XP via Grub on my X64 Gateway laptop.  Ubuntu 6.06 loads just fine via Grub but after installing Ubuntu my windows XP HOME boot doesn't work any longer.  

After selecting XP to boot, I do get the initial Windows installing screen...but after a few seconds it gives up loading XP and then reverts back to the Grub menu.  

I can not longer boot Windows XP as a result.  How would you suggest I fix this?

Thanks,
abstract51

---

### Post by InsaneBeast on 2006-06-10
Could you post your /boot/grub/menu.lst file?  My windows Partition boots from:

```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Do you know what HDD and which partition your windows install is on?

---

### Post by abstract51 on 2006-06-10
Hello:

My /boot/grup/menu.lst file reads exactly as yours with the exception that I am using Home instead of Professional.

I believe my windows partition is as follows..

/dev/hda1   which reads as a windows file system on partion 1.

Thanks,
abstract51

---

### Post by clparker on 2006-06-10
You guys talk like not booting windows is a bad thing!

---

### Post by Herman on 2006-06-10
Hello, abstract51, First, check to make sure all your Windows booting files are there by looking in the mounted partition as in this picture, [*click here*]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP"). It would be extremely rare for them not to be, but it did happen to me once because of a fumble I made with a partitioner, which cause my Windows partition to be truncated at the start. If there is any damage to Windows, which again, would be extremely rare, you can fix that with a Windows CD, but I'm sorry, I've forgotten exactly how, I'd have to look that up.
Now providing Windows is intact, which is normally the situation, you can always boot Windows with a [GAG Boot Manager]("http://gag.sourceforge.net/") floppy disk or CD. These are very simple to make, here's a web-page with all the help you need. [*click here*]("http://users.bigpond.net.au/hermanzone/p12.htm"). I recommend people make a GAG Boot Manager disk before any Linux install if they feel that booting Windows is important to them.

clparker,:D> You guys talk like not booting windows is a bad thing!:D He-He, it may be funny to us, but to someone with vital info in Windows it might not be so funny. What if they happen to be yours or my doctor or dentist? Then it might not be funny for me or you either. But I agree, I don't really need Windows for much anymore either. Besides, this is a freindly web forum, so let's keep the spirit alive by helping rather than making fun of peope. ;)

abstract51
Okay, so GAG should 999 times out of 1000, boot Windows for you, now you can relax and be in a better mood to fix grub. GRUB should boot Windows for you okay too, normally there's just a small typo or something simple like that to be fixed. If you want specific help with GRUB, then, like insane beast requested, someone needs to see a copy of your bottom part of /boot/grub/menu.lst, and not only that, but also the output from sudo fdisk -lu please.
```
sudo fdisk -lu
```:D Regards, Herman

---

### Post by abstract51 on 2006-06-11
Hello Herman:

Thank you for the suggestions and courses of actions.  I'll study and try it out when I get some cycles.  I'll let you know how things turn out.

Abstract51

---

### Post by Herman on 2006-06-11
abstract51, Okay, then here's a link to my Grub Page for even more stuff you might find handy in case I'm not available when you are ready to get around to it. [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")
Regards, Herman :D

---

### Post by abstract51 on 2006-06-18
Hi Herman:

Well, I studied all of the information you referred me to very carefully.  I decided to load Lilo and then use GAG as my boot loader.   I followed your instructions very carefully using the AMD alternative install CD.  The one problem I had was when I was installing Lilo.  I followed your instructions to  Go Back when prompted to install Grub and I was able to locate the "Lilo install to your hard drive" option...i elected to install it to my Ubuntu installation.  So far so good...but when I tried to install it to my Ubuntu partition, it asked me if the partition should be active..this prompt was not in your instructions and I had a decision to make...the verbage in the prompt implied that for Lilo to work properly the partition had to be active.  Well, I selected the active option and then i promptly got the following error...
"/sbin/lilo"  failed with error code "1".   I tried Go Back...but no luck..Lilo would not install..so I tried Grub once more..and once again I lost my ability to boot to windows XP.  So I deleted all of the partitions on my HDD (ubuntu and xp) and I am in the process of restoring my image to get me back to my standard XP configuration.  I really wanted to make this work but I must have a problem in my particular configuration.  :( 

abstract51

---

### Post by Herman on 2006-06-20
Hello, abstract51, I am very sorry to read of your problems continuing in spite of everything I could think of to help.
> but when I tried to install it to my Ubuntu partition, it asked me if the partition should be active..this prompt was not in your instructions and I had a decision to make...the verbage in the prompt implied that for Lilo to work properly the partition had to be active. Well, I selected the active option and then i promptly got the following error...
"/sbin/lilo"  failed with error code "1".   I tried Go Back...but no luck..Lilo would not install.. Sorry about that, but that doesn't happen in my machine with the 'alternate CD' I'm using. I just went through another test install in my own machine and I was ready to make an extra image of htis in case I missed something, but I didn't get the extra question you describe. I believe you though, I have noticed that the installer can ask different questions in different computers depending on how it detects the hardware. I think you chose the correct answer to the quesiton probably, that's what I would have chosen. I have read that Lilo won't install unless you set the partition an active.

The only thing I can think of now that might help you is to (if you still feel like it), install GRUB to floppy disk (fd0) instead and leave Windows on your MBR and use the GRUB flopy disk when you want to boot Ubuntu. -Oh- it's a laptop, so it probably doesn't have a floppy drive! Darn! 
Okay, there is one last way you can try if you want Ubuntu, make a [GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")
on another computer with Ubuntu in it, if you have a freind with Ubuntu maybe?
That will be a little bit of a challenge for you if you are new to Linux. You might have to be pretty good to be able to guess the right way to edit the menu.lst in advance. An experienced GRUB enthusiast would be able to do that, but it might be a little bit of messing around.  It depends how hard you feel like trying. I have other ideas you could try too. If time is a big factor, sadly, you might be better off trying another distro, I hate to say it though. Knoppix with a /home partition on your disk?
Sorry my suggestions didn't work yet, I regret taking up your time. I still hope you have an improvement in your luck. Regards, Herman

---

### Post by abstract51 on 2006-06-20
Herman:

Thanks for all of your help even though it hasn't resulted in completed success so far.  I'm determined to get Ubuntu to work on my Gateway 7510GB laptop.  Noticed in another thread or two it appears that one or more people have been successful with dual booting.  

I don't have a friend who has Ubuntu installed but I have another computer that I can load Ubuntu on and try your suggestion of putting GRUB on a CD-RW.  Also interested in your other ideas so I'd be most grateful if you could share those other ideas so I can consider those as well.  Speaking of other options...what about using the XP bootloader, NTLDR?

Thanks in advance.

abstract51

---

### Post by Herman on 2006-06-21
I think NTLDR is kind of a last resort. Although it is possible, NTLDR is nowhere near as interesting or as useful as either GRUB or GAG. You would still need either GRUB or Lilo installed to the first sector of your Ubuntu partition to boot with NTLDR anyway.

I was thinking maybe we should make a backup copy of your MBR first, *[click here to see how]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")*. The IPL code in the MBR is only 446 bytes, so even if you only have a small USB device like an' MP3 player, you should be able to use one of those for a USB drive to store your old mbr image in.
Or mount the Windows partition with a mount command and store the old mbr image there instead.  
Then install Ubuntu again, but choose 'No' when asked if you want to install  GRUB to MBR, and  type  (hd0,1) on the dotted line for where you want to install GRUB instead. (If /dev/hda2 is your Ubuntu partition), [*Click here to see illustrations*]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location"). Then reboot Ubuntu with either your GAG or GRUB CD for now, and this will leave your MBR untouched. 

Then later we can experiment and try to decide on a more convenient way to set your computer up to dual boot without needing any bootloader CDs. Since your MBR will be backed up this time, it should be okay to experiment with GRUB again some more, or maybe install GAG to MBR instead. I am wondering why Windows won't boot with GRUB? I wonder if it has anything to do with the partition being set 'active' (boot flag), or something like that. Maybe if we are lucky we can discover a problem that we can fix.

---

### Post by abstract51 on 2006-06-21
Herman:

Failure again unfortunately.   I made a copy of my MBR (live CD version of Ubuntu) and put it on a USB disk per your instructions...that went fine.  I then installed the alternate CD version of my Ubuntu and partitioned via your instructions creating root, home, FAT32 data partition and Swap partitions.  I had two partitions already prior to this partitioning...#2 primary at 3.8 GB k Fat32 (this is my Gateway laptop recovery partition) /media/hda2 and #1 primary at 92.6 GB B K NTFS /media/hda1 which is my windows partition.  

I elected to select NO for installing GRUB to my MBR.  I then selected (hd0,2) as the place to write GRUB which I presume is my third partition with Ubuntu (if you recall, I already had two previous partitions..my Gateway recovery partition and my regular Windows partition).  That all went fine and GRUB wrote to the partition that I requested.  I then shut down my laptop and assumed that since I didn't touch my MBR, I would be able to boot into windows as normal...well, I did get the initial Windows splash screen indicating it was loading...after about 2 seconds, it disappeared...some text appears on the screen for a split second (making it unreadable) and I proceeded to go back through the boot process...again, windows started...stopped...and back to the boot process again.  :(   I thought by installing GRUB to a different location (hd0,2) I wouldn't mess up my MBR but apparently it did.  Dazed and confused at this point but still willing to try and figure this out with your help.

OK...then I decided to see if I could get GAG to load Ubuntu..I attached my USB floppy to my laptop, turned it back on, did some configuration with the GAG menu to load Ubuntu and it did indeed load...no problem running Ubuntu at this point...so I decided to restore my MBR.  I dragged and dropped the OLDMBR.img from my USB drive to my Ubuntu desktop, opened a terminal window and ran the following command...11) Restore command: sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1

It prompted me for my password which I entered and then nothing happened.  Nothing.   Did I put OLDMBR.img in the wrong location?  or was the recovery command from your instructions incorrect?  

So after a failed attempt at restoring the OLDMBR.img file, I can't load Windows any longer but I can load Ubuntu.  Small victory at least. 

So I'm back to restoring my original image to get me back to my regular Windows XP partitions.   

Open to any other suggestions or questions you would like for me to explore in order to get this to work.

Thanks,
abstract51

---

### Post by Herman on 2006-06-22
Hello abstract51,
> I elected to select NO for installing GRUB to my MBR. I then selected (hd0,2) as the place to write GRUB which I presume is my third partition with Ubuntu (if you recall, I already had two previous partitions..my Gateway recovery partition and my regular Windows partition). That all went fine and GRUB wrote to the partition that I requested. I then shut down my laptop and assumed that since I didn't touch my MBR,Yes, that should be correct. > OK...then I decided to see if I could get GAG to load Ubuntu..I attached my USB floppy to my laptop, turned it back on, did some configuration with the GAG menu to load Ubuntu and it did indeed load...no problem running Ubuntu at this point.. Good, that proves GRUB must be written to your first sector of /dev/hda3 where we want it. (hd0,2).
You should also be able to boot Windows with GAG, and then be given the opportunity one more time in your GRUB menu as well. Windows seems to be beginning to load okay, it's just unable to complete the process. Very odd.
> I did get the initial Windows splash screen indicating it was loading...after about 2 seconds, it disappeared...some text appears on the screen for a split second (making it unreadable) and I proceeded to go back through the boot process...again, windows started...stopped...and back to the boot process again.
 extremely strange behaviour!
> I thought by installing GRUB to a different location (hd0,2) I wouldn't mess up my MBR but apparently it did. Dazed and confused at this point but still willing to try and figure this out with your help. Maybe it's not related to the presence of one bootloader's 'IPL' (first stage) in the master boot record. Perhaps it has something to do with the partition table, boot flag, or your BIOS or something else.
> Restore command: sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1 That command should work if you apply it 'as is' from your Ubuntu 'desktop DC' (live/install), as the default username is 'ubuntu'.
To use this command from your own personal hard-disk installed Ubuntu system, you would need to replace 'ubuntu' with your own username, say 'abstract51', if that's your username you log in as, so:```
sudo dd if=/home/abstract51/OLDMBR.img of=/dev/hda bs=446 count=1
``` 
should be the correctly modified command for those circumstances. (Or whatever your actual login username is).  I will be interested to read what happens if you can successfully restore the Windows IPL in your MBR. 
abstract51, would you please try the command 'sudo fdisk -lu' in your Ubuntu terminal and post a copy of the output from that command here, maybe there will be something we can see there that will shed some light on this problem.
> sudo fdisk -lu 
Hang in there, abstract51, you are doing great! Regards, Herman :)

---

### Post by abstract51 on 2006-06-22
Hi Herman:

Here are the results.   Still no success but let's see where we can go from here.

I installed Ubuntu again via the alternate CD AMD install cd.  Installed GRUB in (hd0,2) and Ubuntu boots fine via GAG on a USB floppy.  However, as previously, I can't boot Windows XP anylonger.  MBR I presume got hosed somehow.  So far everything is the same as before.

I followed your suggested restore command with the correct username path for my previously copied OLDMBR.img file on my USB disk.  The restore command worked this time now that the correct path was keyed in.

So I shut down Ubuntu to reboot (without the USB floppy to test the restored OLDMBR.img) and I got the following error message...

first line stated "Missing OS or Unformatted Active Partition"  second line stated "Press Any Key To Boot Floppy".

Bummer.  OK, so now I manually shut down the laptop, reattach my USB Floppy with GAG, and reboot.  I get the GAG menu and I select windows XP to boot and I get the Windows splash screen as before and after a second or two of attempting to load, it quits the load process and goes back through the boot process again.  Exactly the same as before.  

OK.  I did run the sudo fdisk -lu command and here is the result.  Let me know what steps to take next.  Thanks, abstract51

bsa@ubuntubob:~$ sudo fdisk -lu

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1         7486290   117258434    54886072+   7  HPFS/NTFS
/dev/hda2              63     7486289     3743113+   b  W95 FAT32
/dev/hda3   *   117258435   127025954     4883760   83  Linux
/dev/hda4       127025955   195366464    34170255    5  Extended
/dev/hda5       127026018   173903624    23438803+  83  Linux
/dev/hda6       173903688   193438664     9767488+   b  W95 FAT32
/dev/hda7       193438728   195366464      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 2500 MB, 2500485120 bytes
255 heads, 63 sectors/track, 304 cylinders, total 4883760 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     4883759     2441848+   b  W95 FAT32

Disk /dev/sdb: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders, total 2880 sectors
Units = sectors of 1 * 512 = 512 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1        17367303    34996753     8814725+   3  XENIX usr
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1, 0, 4) logical=(5789101, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(1, 1, 5) logical=(11665584, 0, 2)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?    18415895    37093937     9339021+  13  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 17) logical=(6138631, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(1, 1, 21) logical=(12364645, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?    19464487    39191121     9863317+  23  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 33) logical=(6488162, 0, 2)
Partition 3 has different physical/logical endings:
     phys=(1, 1, 37) logical=(13063707, 0, 1)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     3016192    50988919    23986364   33  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 49) logical=(1005397, 0, 2)
Partition 4 has different physical/logical endings:
     phys=(1, 1, 53) logical=(16996306, 0, 2)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by Herman on 2006-06-24
Hello, abstract51, I can't see anything wrong with your partition table that can be seen in your sudo fdisk -lu output for the disk Ubuntu and Windows is on.
Obviously fdisk doesn't like your sdb disk very much, but that shouldn't affect booting on hda as far as I know.
Here's a link I came across this morning to a thread that is from some time back, but it seems to illustrate my suspicions that it has to do with something we can't see to do with your partitions, or rather, the way software interprets your partitions.
[*Click here. *]("http://ubuntuforums.org/showthread.php?t=2689")I think that post was written for 'Warty' edition of Ubuntu, some time back, but it serves to describe my suspicions very nicely. You could try that solution given there for 'Warty' and see if it will work for your problem, it would be worth a try I think.
Regards, Herman :D

---

### Post by Malac on 2006-07-14
Hi,
If your GRUB was starting to boot Windows then failing I would suspect a blown XP file these can usually be fixed by booting to the recovery console off the install CD, login as Administrator issue fixmbr and fixboot commands.
Although this may wipe out your GRUB too, which you would then have to redo as per the other instructions.

Hope this helps.

---

