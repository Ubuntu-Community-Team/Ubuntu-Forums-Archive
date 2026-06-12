---
title: "New install of Hardy, dual boot problems"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by roncrump on 2008-08-14
Hi,

I have installed Ubuntu 8.04.1 onto a computer onto what was the D drive under windows (ie a second HDD). The C Drive was not touched, other than to install GRUB (I believe).

After installation I had to enter the BIOS and switch the second drive to AUTO rather than OFF, but after this Ubuntu would boot.

PROBLEM 1: intermittently, Ubuntu comes up to the login screen but after logging in, the screen goes black and does not bring up the desktop. PC has to be switched off.

However, the bigger problem is-

PROBLEM 2: when trying to boot into Windows 2000, I get an error message that ntoskrnl.exe is missing. I'm assuming that there is a glitch and it is just not looking in the right place any longer.

Did a bit of looking about but find bootloaders and all the hd* and sda/b stuff very confusing.

Anyway, output from fdisk -l is:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4862    39021885    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217        4741    28314562+  83  Linux
/dev/sdb3            4742        4865      996030   82  Linux swap / Solaris

while my /boot/grub/menu.lst contains (after a heap of commented out lines):

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d00e3cfc-cf9e-41b4-be72-0418d7b33234 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d00e3cfc-cf9e-41b4-be72-0418d7b33234 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows 2000 Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Any suggestions appreciated.

Thanks,
Ron.

---

### Post by wilbbe01 on 2008-08-14
I hate grub, it always boggles my mind.  Maybe root(hd1,0) instead of the root (hd0,1) line under the Microsoft Windows 2000 Professional section?  Not sure on that though.

Edit: I meant root (hd0,0) I think.

---

### Post by roncrump on 2008-08-14
> **wilbbe01 said:**
> I hate grub, it always boggles my mind.  Maybe root(hd1,0) instead of the root (hd0,1) line under the Microsoft Windows 2000 Professional section?  Not sure on that though.

Edit: I meant root (hd0,0) I think.

Thanks for the suggestion(s).

Tried (hd0,0) and that fired up the Dell utilities, which seem to have a little partition on that disk. First time I've ever seen them.

Anyway, also tried (hd0,2) and there was no partition found.

Will give (hd1,0) a try, but given the (hd0,0) result, I don't hold out much hope as I do seem to be looking at the right device.

Ron.

---

### Post by roncrump on 2008-08-14
> **roncrump said:**
> 
Will give (hd1,0) a try, but given the (hd0,0) result, I don't hold out much hope as I do seem to be looking at the right device.


Decided against trying that as (hd1,0) appears as the root for the ubuntu boot, so surely that can't be right for the w2k boot?

Ron.

---

### Post by wilbbe01 on 2008-08-14
Shoot, the root for sure(hd1,0) won't do it.  I screwed up when I said that, that is what the ubutnu drive is.  The root (hd0,1) which was there initially is probably right based off of the dell resources firing up successfully.  I just looked for some stuff and I found what looks promising a ways down an archived thread located at the link listed below.  If you can get windows booting on it's own without grub, using the windows recovery console, windows should boot fine.  I think the fixmbr should suffice to fix it.  If you do need to try the other command listed in a lot of places "fixboot" I think, you should add something as a paramter when it asks.  It's been a while but I think it is \fastboot or something like that.  Put grub on your ubuntu drive.  Put your ubuntu drive at the front of the boot order in bios.  Hopefully that makes some sense, it's now a few hours past when I should have gone to bed, I'll check back tomorrow and see how things are going.  Good luck.

[http://ubuntuforums.org/archive/index.php/t-588676.html](http://ubuntuforums.org/archive/index.php/t-588676.html)

---

### Post by wilbbe01 on 2008-08-14
Wow it took me more than 8 minutes to type that :(.  Yes you are right, don't try the hd1,0 it is indeed the ubuntu drive.

---

### Post by roncrump on 2008-08-14
> **wilbbe01 said:**
> Wow it took me more than 8 minutes to type that :(.  Yes you are right, don't try the hd1,0 it is indeed the ubuntu drive.

I thought you were off to bed.

Anyway, it will take me a wee while to try the options in your previous reply - I'll have to track down the w2k CD to start with. So since I have footy training soon and am off to the seaside tomorrow, it will probably be after the weekend before I get round to it. So if you don't see any further replies it isn't because I've fixed it, but because I'm off having fun.

Unless I can remove grub/repair the MBR from Ubuntu, which would speed it up a bit.

Cheers,
Ron.

---

### Post by wilbbe01 on 2008-08-15
> I thought you were off to bed.

I was, but it is a big process to pull oneself away from the computer :).  It seems like I've heard of people installing windows boot stuff without the windows recovery console.  However, I know a thing called "supergrub" may be capable of doing it, it has been a while, but I think it had that feature.  If it were me I would go with the proven win2k disk, as I find windows to do the best job of fixing windows of anything, but again, it is up to you.

---

### Post by roncrump on 2008-08-18
> **wilbbe01 said:**
> <snip>If you can get windows booting on it's own without grub, using the windows recovery console, windows should boot fine.  <snip>.  Put grub on your ubuntu drive.  Put your ubuntu drive at the front of the boot order in bios.

Quick update.

I used Super Grub Disk to correct the MBR and get Windows going. All good.

Reinstalled GRUB on (hd1) (ie MBR of the second drive, I believe). So far so good.

On rebooting, made the unfortunate discovery that the second drive does not show up in the boot sequence list of my BIOS.

So currently I can boot to Windows, as there is no GRUB in my primary HD's MBR and I can boot to my ubuntu install if I go via the Super Grub Disk bootable floppy.

Which leaves either
(a) finding a way of adding the second drive to the BIOS boot sequence list/making the second HD bootable. I'd rather not re-format it to achieve this; or
(b) fixing it via some Super Grub Disk option (of which there are so many I'm terrified).

Ron.

---

### Post by wilbbe01 on 2008-08-18
I'm a bit confused.  Earlier on you said you switched your second drive to auto in the bios.  What exactly was that accomplishing?  I thought you were saying there you set that drive to boot.  Anyway, I think what I would try (I'm definitely not amazing at grub configuring) to install grub to mbr now (again I guess), and as far as I can tell your original configuration looks accurate.  (hd0,1) is indeed where windows needs to boot, and (hd1,0) is indeed the linux.  If that fails I would try a fixboot from a windows 2000 recovery console, which I think will set up that partition of windows to correctly boot when given the go from the chainloader stuff from grub.  Also, if you get to the fixboot part and you are going through that, there is a prompt which asks you for parameters (or a synonym of it) and in xp anyway you would want "fastboot" included there, I assume 2000 is the same as xp with that.

---

### Post by confused57 on 2008-08-19
> **roncrump said:**
> Quick update.

I used Super Grub Disk to correct the MBR and get Windows going. All good.

Reinstalled GRUB on (hd1) (ie MBR of the second drive, I believe). So far so good.

On rebooting, made the unfortunate discovery that the second drive does not show up in the boot sequence list of my BIOS.

So currently I can boot to Windows, as there is no GRUB in my primary HD's MBR and I can boot to my ubuntu install if I go via the Super Grub Disk bootable floppy.

Which leaves either
(a) finding a way of adding the second drive to the BIOS boot sequence list/making the second HD bootable. I'd rather not re-format it to achieve this; or
(b) fixing it via some Super Grub Disk option (of which there are so many I'm terrified).

Ron.
You could try physically switching the order of your hard drives:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Since you already have grub installed to the mbr of the Ubuntu drive, you shouldn't need to reinstall Ubuntu.  However, when you boot up in this configuration and get the grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.

In the link I gave you above, see how I installed Ubuntu with 2 drives on a Dell Dimension 4550.

---

### Post by roncrump on 2008-08-19
> **wilbbe01 said:**
> I'm a bit confused.

Welcome to my world. Unfortunately it isn't just bootloaders that leave me in this state.

> **wilbbe01 said:**
>  Earlier on you said you switched your second drive to auto in the bios.  What exactly was that accomplishing?  I thought you were saying there you set that drive to boot.

I thought that was what I was doing - since GRUB didn't boot from it beforehand and did afterwards. Now, I think maybe the effect was to "switch it on" automatically, rather than letting the booting OS start it up, and hence this allowed GRUB to see the disk and find the root partition to boot from.

Having another play with it now.

Ron.

---

### Post by roncrump on 2008-08-19
We have a winner!

I used Super Grub Disk to firstly "Fix Boot of Windows", which was what I had previously done to get Windows booting again without access to Ubuntu via GRUB. Then I used this Super Grub Disk option:

GRUB => MBR & !LINUX! (1)         AUTO     ;-)))

To put GRUB into the MBR of the first HD again and boot Ubuntu. I think this is the SGD equivalent of Ben's last suggestion.

Thanks for all your help.

Ron.

---

### Post by adrian15 on 2008-08-22
> **roncrump said:**
> We have a winner!

I used Super Grub Disk to firstly "Fix Boot of Windows", which was what I had previously done to get Windows booting again without access to Ubuntu via GRUB. Then I used this Super Grub Disk option:

GRUB => MBR & !LINUX! (1)         AUTO     ;-)))

To put GRUB into the MBR of the first HD again and boot Ubuntu. I think this is the SGD equivalent of Ben's last suggestion.

Thanks for all your help.

Ron.

Nonsense.
This history makes no sense to me. You only have fixed the first boot hard disk mbr with windows and then reinstalled grub to the first mbr and the hard disk boot priority on the bios has not been changed.

The only possible change (what made it fix) that I can see is that **Fix Boot of Windows makes (hd0,0) active** (or did you use another advanced option) to Fix Boot of Linux of an specific Windows partition)? (Maybe Ubuntu installation left mbr without any windows partition active?)

Are there any steps that you have not written here so that I can see how you have it fixed better?

Thank you.

adrian15

---

### Post by wilbbe01 on 2008-08-23
> Nonsense.
This history makes no sense to me. You only have fixed the first boot hard disk mbr with windows and then reinstalled grub to the first mbr and the hard disk boot priority on the bios has not been changed.

The only possible change (what made it fix) that I can see is that Fix Boot of Windows makes (hd0,0) active (or did you use another advanced option) to Fix Boot of Linux of an specific Windows partition)? (Maybe Ubuntu installation left mbr without any windows partition active?)

Are there any steps that you have not written here so that I can see how you have it fixed better?

Thank you.

adrian15

He said he got it working didn't he?  Why does it matter to you?

---

### Post by adrian15 on 2008-08-23
> **wilbbe01 said:**
> He said he got it working didn't he?  Why does it matter to you?

I am the main Super Grub Disk developer, I need to know **what made his computer work again**. My bet is activating a partition but I am not quite sure.

adrian15

---

### Post by wilbbe01 on 2008-08-23
> I am the main Super Grub Disk developer, I need to know what made his computer work again. My bet is activating a partition but I am not quite sure.

adrian15

Ahh, that makes sense then.  Yeah, I think the way he described his computer being set up in the beginning matches what got it working in the end (so yeah, what is the change?).  I might agree with you except when I searched for the error he had with windows in the beginning, "ntoskrnl.exe" problems appeared to be related to other issues.  However, I suppose activating may very well have been his issue.

---

### Post by redester on 2008-08-23
[LEFT][/LEFT]I will be moving from a 80g HD to a 500g unit and want to expand the partitions. What I have at present;


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         261     2096451    6  FAT16
/dev/hda2   *         262        4857    36917370    c  W95 FAT32 (LBA)
/dev/hda3            4858        4889      257040   82  Linux swap / Solaris
/dev/hda4            4890        9729    38877300   83  Linux

hda1 is DR-DOS
hda2 is Windows xp

I am thinking to use DD to transfer partition contents to the new and MUCH expanded size of the 500 gigger after FDISKing. I expect to create only the same size partition as hda1, which is DR-DOS, swap drives making it the master.  Then boot with a floppy diskette containing DR-DOS tools, format/sys the drive, switch drives again and dd the contents to that partition.      

I can, using Toms/rt/bt... Fdisk for the windows partition using a much larger size. I intend to use a fat32 formatter for the windows much the same as I did for DR-DOS.  After DD'ing the windows contents across comes a question;

Will windows XP recognize the larger partition in which it resides and if not , should I make the partition the same size as the old and expect to be able to extend it using the Live 8.04 cd?

If that be true... can I expect to do the same for the Linux partition after fdisking to the original size?  (I would keep the swap size the same."

A lot of work coming up to be sure and any help/comments will be welcome. 

Ray

---

### Post by wilbbe01 on 2008-08-23
You should probably post that as a new thread Ray as it doesn't really go along with this one.

---

### Post by roncrump on 2008-08-24
> **adrian15 said:**
> Nonsense.
This history makes no sense to me. You only have fixed the first boot hard disk mbr with windows and then reinstalled grub to the first mbr and the hard disk boot priority on the bios has not been changed.

It surprised me that it worked having read the description of what it was doing - it appeared to be putting it all back as it was originally. 

> **adrian15 said:**
> The only possible change (what made it fix) that I can see is that **Fix Boot of Windows makes (hd0,0) active** (or did you use another advanced option) to Fix Boot of Linux of an specific Windows partition)? (Maybe Ubuntu installation left mbr without any windows partition active?)

Where should I look to see this? I didn't use any advanced options, I used fix boot of windows to re-enable access to windows 2000 (without access to linux), then the boot into linux option to get back into ubuntu. Reading what was on here looked a bit daunting so took the option of trying the route mentioned as a simpler step before going into this.

> **adrian15 said:**
> Are there any steps that you have not written here so that I can see how you have it fixed better?

I don't think so. Mind you, I was trying to flip back and forth between work and this, so it is possible I may have forgotten something.

My current /boot/grub/menu.lst follows, in case that helps (haven't compared it to the originally posted version).

Ron.

```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d00e3cfc-cf9e-41b4-be72-0418d7b33234 ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d00e3cfc-cf9e-41b4-be72-0418d7b33234 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows 2000 Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by adrian15 on 2008-08-25
> **roncrump said:**
> I used fix boot of windows to re-enable access to windows 2000 (without access to linux),

Did you ever try to boot your system in this step? Did not  you boot the Dell Utility ?

adrian15

---

### Post by roncrump on 2008-08-25
> **adrian15 said:**
> Did you ever try to boot your system in this step? Did not  you boot the Dell Utility ?

adrian15

Having run fix boot of windows, I did boot into Win2k. I had previously booted into the Dell Utility partition, but that was a bit of an accident - I modified the /boot/grub/menu.lst to have (hd0,0) for Windows as per Ben's (first?) suggestion. I didn't run any of the Dell Utility programs.

Ron.

---

### Post by adrian15 on 2008-08-26
> **roncrump said:**
> Having run fix boot of windows, I did boot into Win2k. I had previously booted into the Dell Utility partition, but that was a bit of an accident - I modified the /boot/grub/menu.lst to have (hd0,0) for Windows as per Ben's (first?) suggestion. I didn't run any of the Dell Utility programs.

Ron.

So in order to boot into Win2k you went through the grub menu although this is impossible because you just removed it with Fix Boot of Windows?!

:confused:

Can you please detail? Thank you.

adrian15

---

### Post by roncrump on 2008-08-26
> **adrian15 said:**
> So in order to boot into Win2k you went through the grub menu although this is impossible because you just removed it with Fix Boot of Windows?!

:confused:

Can you please detail? Thank you.

adrian15

No. Once I had run the fix boot of windows option, the boot was straight into Win2k. The booting into the Dell Utility partition having edited /boot/grub/menu.lst was prior to this, when GRUB was still in the MBR.

Ron.

---

### Post by adrian15 on 2008-08-27
> **roncrump said:**
> No. Once I had run the fix boot of windows option, the boot was straight into Win2k. The booting into the Dell Utility partition having edited /boot/grub/menu.lst was prior to this, when GRUB was still in the MBR.

Ron.

I still do not understand it (it should have booted Dell Utility partition) but let's stop the questions here.

adrian15

---

