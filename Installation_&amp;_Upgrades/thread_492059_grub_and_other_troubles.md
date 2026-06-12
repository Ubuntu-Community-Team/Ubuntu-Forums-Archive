---
title: "grub and other troubles"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by spiderworm on 2007-07-04
Hello,

Something has gone seriously wrong with my install and I hope someone can help me out.

I built a new computer and installed windows on it.  No problems there.  I left half of the primary hard drive (a 500 GB SATA drive) unpartitioned for later installation of Ubuntu.

When I tried the normal installer (the live CD approach) the screen would go black and nothing would respond while it was preparing the live environment.  I tried again, thinking that perhaps the resolution it wanted to use was out of scope for the monitors, so I adjusted the resolution and tried again.  This time the monitor didn't go black, but the Ubuntu loading screen would hang every time.

So I downloaded the alternative installer.  This time the installation went smoothly (or so I thought).  When I rebooted the computer, I got a message saying there had been an error loading the operating system.  Great.  So I stuck the installation cd back in and used it to reinstall GRUB.

Rebooting the computer, I got the grub menu showing Ubuntu, Ubuntu recorvery mode, Ubuntu memtest, and Windows XP.  Unfortunately selecting any of those options resulted in an error such as "no such partition" or "invalid executable".

I decided to look at the boot settings and I discovered that they were set to hd1 when they all should be hd0... editing the commands allowed me to boot both into Ubuntu and Windows.  Yay! (there is in this computer an older IDE hard drive that GRUB would recognize as hd1 but it is not bootable at all)

Unfortunately modifying these settings within GRUB does not stick, so I wanted to boot into Ubuntu and modify the grub config... however, I could not do that because neither the Ubuntu boot nor the Ubuntu recovery boot would get me to a command line.  The normal boot would cause the monitors to go black and stop responding (similar to what I was getting with the oriiginal LiveCD/installer cd) and the recovery mode option hangs at this step of the startup:

[44.987719] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 22 (level,low) -> IRQ 22

I do understand parts of that line but definitely not the whole thing.  If someone knows how to get past this step so that it can continue the boot process, I would appreciate it.

Otherwise, if anyone knows how to modify GRUB permanently without booting into Ubuntu, I would appreciate that knowledge as well.  I'll have a tough time explaining to my wife that every time she reboots the computer, she needs to modify the boot options... not so much the how-to-do-it as it's not that hard and she's a smart lady, but the why-she-should-have-to-do-that-when-windows-was-working-perfectly-before.

I've installed Ubuntu on approx 10 machines in the past and am flabbergasted at the trouble I'm having with Feisty on this one.  The only thing I can think of is that I purchased hardware that is just too new for Feisty?  Although I didn't think I purchased bleeding edge stuff.

If anyone needs a hardware inventory or more information about where in the Ubuntu startup process it hangs, please let me know, and I'll be happy to provide.

Thank you for reading my long post.
spiderworm

---

### Post by metallicamaster3 on 2007-07-04
please provide your partition table's layout, and your IDE configuration. then i will have enough information to tell yuo what is needed to do. :)

---

### Post by confused57 on 2007-07-04
Boot into Ubuntu by modifying the grub boot menu, open a terminal(Applications---Accessories---Terminal), to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

change your root from (hd1,x) to (hd0,x) and change the line with #groot from (hd1,x) to (hd0,x)...leave the # in front of groot...quit & save, this should make your grub settings permanent.

---

### Post by spiderworm on 2007-07-04
> **metallicamaster3 said:**
> please provide your partition table's layout, and your IDE configuration. then i will have enough information to tell yuo what is needed to do. :)

Thank you.

Primary hard drive is 500 GB SATA.  The first partition is 233 GB NTFS (Windows XP).  The second partition is 223 GB formatted ext3 (I believe) and the third partition is 10 GB formatted swap (I'm guessing).

I have to guess on this because I cannot get to a command prompt and am therefore not sure how to pull up the information.  I'm in Windows on the computer pulling up the information with a tool here.

The secondary hard drive is 115 GB, a single partition, formatted ext3... this is an old hard drive that has some pictures and music on it that was served up by an old Ubuntu media server I set up.

David

---

### Post by spiderworm on 2007-07-04
> **confused57 said:**
> Boot into Ubuntu by modifying the grub boot menu, open a terminal(Applications---Accessories---Terminal), to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

change your root from (hd1,x) to (hd0,x) and change the line with #groot from (hd1,x) to (hd0,x)...leave the # in front of groot...quit & save, this should make your grub settings permanent.

Thanks for the reply, but part of the problem is that I cannot boot into Ubuntu... I described the problem in my original post.  Let me know if some part of it is not clear.

Thanks,
David

---

### Post by confused57 on 2007-07-04
> **spiderworm said:**
> Thanks for the reply, but part of the problem is that I cannot boot into Ubuntu... I described the problem in my original post.  Let me know if some part of it is not clear.

Thanks,
David
I misunderstood, I thought you were able to boot into Ubuntu by modifying the boot grub menu:
> I decided to look at the boot settings and I discovered that they were set to hd1 when they all should be hd0... editing the commands allowed me to boot both into Ubuntu and Windows. Yay! (there is in this computer an older IDE hard drive that GRUB would recognize as hd1 but it is not bootable at all)

Unfortunately modifying these settings within GRUB does not stick, so I wanted to boot into Ubuntu and modify the grub config... however, I could not do that because neither the Ubuntu boot nor the Ubuntu recovery boot would get me to a command line. The normal boot would cause the monitors to go black and stop responding (similar to what I was getting with the oriiginal LiveCD/installer cd) and the recovery mode option hangs at this step of the startup:

[44.987719] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 22 (level,low) -> IRQ 22

I do understand parts of that line but definitely not the whole thing. If someone knows how to get past this step so that it can continue the boot process, I would appreciate it.

Otherwise, if anyone knows how to modify GRUB permanently without booting into Ubuntu, I would appreciate that knowledge as well. I'll have a tough time explaining to my wife that every time she reboots the computer, she needs to modify the boot options... not so much the how-to-do-it as it's not that hard and she's a smart lady, but the why-she-should-have-to-do-that-when-windows-was-working-perfectly-before.

You could boot up the live cd and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

You can then mount your Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then post your boot entries for both Ubuntu & Windows

Added:  Sorry, noticed you're not able to boot the live cd...it may help to add extra boot parameters, similar to what's described in this thread:
[http://ubuntuforums.org/showthread.php?t=448596&highlight=noirqpoll](http://ubuntuforums.org/showthread.php?t=448596&highlight=noirqpoll)

Here are a list of Knoppix cheatcodes, which will give you an idea of what they do:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by louieb on 2007-07-04
Hello spiderworm, I take it you can boot XP. Install [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  and use confused57's edits from XP  to your /boot/grub/menu.lst.

---

### Post by spiderworm on 2007-07-05
> **louieb said:**
> Hello spiderworm, I take it you can boot XP. Install [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  and use confused57's edits from XP  to your /boot/grub/menu.lst.

Thank you!  I've actually been looking for something like this for a long time!  And it did work, thanks again!

Now I have my boot menu fixed, does anyone know how I go about fixing the hang-during-startup problem I have with Ubuntu?

Thanks,
David

---

### Post by louieb on 2007-07-06
Think I need a new hardware book The GS**I 22 (level,low) -> IRQ 22 **part has me thrown. Thought there only 14 IRQ channels available. might look through [Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes") and try some of the IRQ cheats.

---

