---
title: "GRUB bootloader. How to fix it or remove it?"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by jambog on 2010-01-22
Yet another GRUB question, but this is different from the one posted an hour ago by a different user. I have checked other forums and tried the advice there and it hasn't worked. Any help will be greatly appreciated!

   I recently installed Ubuntu 9.10 x64 on my PC. I had Windows 7 pro x64 already installed and I installed Ubuntu on a separate hard drive. When I installed ubuntu it also installed GRUB 1.97b4 bootloader, which worked fine. I am new to linux so I was messing with ubuntu and thought I messed something up so I reinstalled ubuntu again. 

After I reinstalled it GRUB wouldn’t load so I couldn't boot either ubuntu or windows. It was bringing up a prompt that said “rescue.grub>” then said to hit TAB for a list of commands. I did, and tried some of the commands (although I had no idea what they were) but nothing was happening. So I completely removed the hard drive that I had ubuntu installed on thinking that GRUB was installed on only that disk and anticipating that my windows drive would boot fine after I removed the ubuntu drive. Nope, now I get an error “GRUB loading….no such disk found” then it brings up the prompt “grub rescue>”. 

I figured that I would just repair the windows MBR, so I boot up my Windows 7 repair disc and choose the repair option then went to the cmd prompt and repaired the MBR using the bootsect command, it said it repaired successfully but windows still will not boot, it just keeps giving me the prompt “grub rescue>” so how do I either fix GRUB so I can choose to boot to windows or remove GRUB completely. Once I get the problem solved I do plan on reinstalling ubuntu but for now I would be happy just to be able to boot my windows.
  Thanks.

---

### Post by darkod on 2010-01-22
Sometimes you need to run that windows repair process few times. Or you can try with manual commands (not the automated process) as per the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

When you decide to reinstall ubuntu, first go nto BIOS and make the ubuntu disk first in boot order. Then in step 4 note what is your ubuntu disk called, usually /dev/sdb (if /dev/sda is windows disk), and in the last screen, before clicking Install, click on Advanced and make sure the bootloader (grub2) will go to /dev/sdb (or what ever the disk was called in step 4).

Note: it should be /dev/sdb for example, not with a number lke /dev/sdb1.

With multiple disks it's always wise to check where grub2 will go by clicking Advanced, do not assume it will go where you think. :) Because you left the windows disk to be first in boot order (common case), grub2 installed itself there because that's the disk you're booting from. Windows also installs its bootloader on the hdd that is first in boot order regardless on which hdd you are installing windows.

---

### Post by kansasnoob on 2010-01-22
Boot your Ubuntu Live CD and from the live desktop run the command:

```
sudo fdisk -l
```

BTW that's a lower case L. At the top it'll look something like:

> Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9


We only care about the drive designation like I highlighted above, ie: /dev/sda because we'll need to use whatever that is when you run:

```
sudo apt-get install lilo
```

And:

```
sudo lilo -M /dev/sda mbr
```

You see I've used the /dev/sda there!

That should be it, reboot and hopefully you can boot Windows. If not we'll need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by jambog on 2010-01-22
Thanks! I'll have to wait a few hours when I get home from work to try that. I noticed the tutorial said that 9.10 uses Grub 2, any reason why it would have installed 1.97 beta4 on my system?

From reading the tutorial I think the reason repairing the bootloader for windows didn't work is because I was using bootsect which is what the other forums I went to said to do, but on the tutorial you gave me it says to use the command bootrec, so hopfully it will be as simple as that. Thanks for the quick response!

---

### Post by darkod on 2010-01-22
It sounds strange but 1.97 is grub2, 0.97 is grub1 or legacy grub. Don't ask why. :)

PS. The kansasnoob way will work just fine too.

---

### Post by kansasnoob on 2010-01-22
> **darkod said:**
> It sounds strange but 1.97 is grub2, 0.97 is grub1 or legacy grub. Don't ask why. :)

PS. The kansasnoob way will work just fine too.

I was only addressing this:

> for now I would be happy just to be able to boot my windows.

I figure we'll need the output of the Boot Info Script as described in the following link to deal with the rest:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Of course both drives will have to be plugged in.

---

### Post by jambog on 2010-01-23
Go it! I used the bootrec /fixmbr command and after doing that by windows drive booted fine. After it booted okay, I hooked up the second drive again and reinstalled ubuntu on it. Now the GRUB bootloader is working correctly again. Thanks for the help.

---

