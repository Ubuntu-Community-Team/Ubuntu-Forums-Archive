---
title: "Clean Install Ubuntu without WUBI"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by RealisticDave on 2014-03-23
Is it possible to install Ubuntu on a totally separate HDD, without using Wubi?  I would like to be able hit 'ESC' at start-up, go to the boot order menu, and select which OS to boot up into. (FYI, I currently have Win XP on one HDD, Win 7 on another. My default is to boot into Win7, but I select XP by doing what I described above.)

I've had Ubuntu on a third HDD---installed using Wubi---for about a year, to try it out.  That particular HDD just died (hardware issue) and I've ordered a replacement.  (I've removed any Ubuntu files on my Win 7 drive, now.)  When the new drive arrives, I _can_ just reinstall Ubuntu in the manner that I've had it (on a separate drive, but using Wubi, and select Ubuntu with the boot menu option screen that comes up).  But I'd prefer---if possible---to have it as a totally separate OS, and choose it at power-up by using the 'ESC' key.  

I've done a search in this forum, as well as in search engines, and I can't seem to find a situation whereby someone has done this before.  Maybe I'm using the incorrect search parameters or terminology? Is this---perhaps---because this setup will simply _not_ work? Or is it difficult to accomplish, or ___________?  I'd appreciate some advice, and if possible, point me to a webpage that would provide information on installing Ubuntu separately, without 'involving' Windows.  Thanks!

---

### Post by Mark Phelps on 2014-03-23
> Is it possible to install Ubuntu on a totally separate HDD, without using Wubi?

Not only is it possible; in fact, it's the preferred approach...

To do this, install just like any other OS:
1) Disconnect all but the drive you want to install to
2) Boot from the install medium
3) Take the defaults and reply to any prompts

When done, Ubuntu will be installed, as will GRUB to boot it.

After that, you can launch whichever OS you want the way you're already doing it.

---

### Post by RealisticDave on 2014-03-23
Thanks, Mark.  I was hoping that I could do just that.  I don't believe I'll have any issues, but if I do (after my new drive arrives), I'll come back to the Forum. Appreciate the reply!

---

### Post by deadflowr on 2014-03-23
> **Mark Phelps said:**
> Not only is it possible; in fact, it's the preferred approach...

To do this, install just like any other OS:
1) Disconnect all but the drive you want to install to
2) Boot from the install medium
3) Take the defaults and reply to any prompts

When done, Ubuntu will be installed, as will GRUB to boot it.

After that, you can launch whichever OS you want the way you're already doing it.

You forgot to mention to reconnect. :D

but +1.
if you do disconnect and then reconnect, the other system(s) won't be listed in grub. You can add them with this simple command
```
sudo update-grub
```
I would also suggest make the system boot from the disk Ubuntu is on
(this should be done in the BIOS)
This avoids the chance that the other disk boots first and the ubuntu install never shows up.
If that makes sense.

---

### Post by RealisticDave on 2014-03-23
DF, just to be certain that I'm understanding you: your suggestion is to not disconnect (and reconnect) the other two drives, but rather to go into BIOS first and force the system boot into the F Disk (the HDD that I'll be installing Ubuntu on).  Then after my Ubuntu installation, I can set whatever OS (drive) that I choose as my system boot---but I can still hit ESC during POST, and choose an alternative OS (drive) than my default.  Did I understand you correctly?  Thanks!

---

### Post by oldfred on 2014-03-23
Just changing Boot drive may not change which drive is sda. BIOS enumerates devices and grub always installs to sda drive (not BIOS boot drive) with all the auto install options. Only the Something else or manual install gives the option to choose which drive to install grub2 boot loader. 

I believe Windows installs its boot files into the drive set by BIOS to boot from which also can create issues if one does not pay attention as Windows has been known to overwrite part of a Linux install in a boot drive corrupting it.

If you want to be safe, and willing to disconnect drives then just install to new drive. Otherwise we can show examples of installing to a second drive using Something else.

---

### Post by deadflowr on 2014-03-23
Edit: oldfred's advice on using something else is usually the best option, really.

---

### Post by oldfred on 2014-03-23
Some examples.
 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

My screenshot installing over an old install in sdc, Boot loader location in combo box at bottom is still on sda.

---

### Post by RealisticDave on 2014-03-23
I think I'll just disconnect the other two drives. I'll be inside my case anyway to add the new drive, so no problem.  I'll read over the attachments you have (oldfred), I'm not familiar with the "something else," but I can see where the option is located, on your thumbnail.  I'll have a few days to read the material over, my drive is coming "Free Shipping"...which usually means by Pony Express.

Thanks to all who offered their advice!

---

### Post by mastablasta on 2014-03-24
well if you disconnect the windows drive you do not need something else option, but you might want to update grub. that way computer will always ask on boot what system you would like to boot with a timer. if there is no change it will continue to boot default OS. grub can be customized using GUI app called grub cusotmizer.

so anyway no need in hitting esc key on boot. plus youi will see all your systems in startup menu including windows 7 and xp, various recovery partitions...

---

### Post by Mark Phelps on 2014-03-24
To the OP, you mentioned that you use the "esc" key to select the boot drive during startup.  I presumed you wanted to CONTINUE doing this, which is why I didn't mention doing anything about changing the boot order of the drives in the BIOS or using Ubuntu to generate a GRUB menu containing the other OSs.

Of course you would have to reconnect the other drives, otherwise, HOW would you then gain access to them again!

If you're pressing a key to select the drive every time you boot, it really doesn't matter which drive is first in the BIOS order.

If you want to use GRUB to select boot order, then you need to boot from the Ubuntu drive (where GRUB got installed).  Then, when you run "sudo update-grub", it will regenerate the GRUB  default config file and add entries for the Windows OSs.

---

### Post by ubfan1 on 2014-03-24
With so many disk coming and going, the first boot of your full configuration may have grub fall on its face, looking for a root filesystem on the wrong disk.  Where disk uuids are used, those are OK, but where you see disk designations like hd0, expect to have to edit (type e at the grub menu, instructions on screen), those to another disk.  You might even encounter an actual device like /dev/sda? which needs to be changed to another letter.  You can figure out what disk is which by looking at them with ls or even just using command completion with the tab.  Type something like set root=(hd TAB and see what disks are offered, then select one and keep typing tab until you see the files you are looking for.
After a successful boot, immediately run sudo update-grub to fix the grub.cfg file.

---

### Post by RealisticDave on 2014-03-28
My new drive arrived and I installed it today.  I decided to leave my existing (two other) drives connected. (I didn't realize until it was pointed out that I had an option to the ESC method.)  I booted up into my new drive, followed the helpful hints that were in this thread, and I'm happy to say I now have Ubuntu installed.  At power up, it goes into the GRUB menu and gives me my choice of Ubuntu, Win 7, or Win XP. I'm fine-tuning my Ubuntu installation now, and everything seems to be just the way I want it.

Thanks to all who gave me the advice and assistance.  (I can't figure out how to show this thread as [solved]...but it is.)
Cheers!

---

