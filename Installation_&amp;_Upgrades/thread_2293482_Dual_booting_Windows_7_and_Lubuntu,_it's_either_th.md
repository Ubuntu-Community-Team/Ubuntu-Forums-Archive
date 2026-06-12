---
title: "Dual booting Windows 7 and Lubuntu, it's either this or that, help!"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-09-05
Hi guys.  

I have this desktop that initially had Windows 7 only.  Then I proceeded to install Lubuntu on another partition.  Installation went well.  GRUB appears on startup and I can boot and log in to the installed Lubuntu OS.  But if I choose Windows 7 in GRUB, I just get a blank screen, and when I push any key on the keyboard, I just get a beeping sound.  

 So I boot into Windows 7 CD, chose to repair, click the command prompt, typed "bootrec/fixmbr" and "bootrec/fixboot" (forgot if it had spaces), and it worked.  I was able to boot into Windows 7.  But the GRUB was gone so I cannot boot into Lubuntu.

So I boot into Live USB, opened terminal and, as per "https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2",  typed the following:
sudo mount /dev/sdXY /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX

I don't know if I did it correctly or if it applies to my situation, but the GRUB did come back and I am again able to boot and log in to Lubuntu, but again, if I choose Windows in GRUB, I get a blank screen, just like before.

So basically I'm going in circles.  It's either this or that.  

Help please!  Thank you.

---

### Post by ajgreeny on 2015-09-05
Sounds like you have a good candidate for **Boot-Repair**, in my signature.

Use a live system, install boot-repair to that following the instructions and run it to get the Boot-info script.  Do not at this stage accept the default repair, just run the script and report back here the link to a pastebin report that we can view with full info on your system.

---

### Post by grahammechanical on 2015-09-05
Open a terminal in Ubuntu and run this command

```
sudo update-grub
```

and watch the printout. Does it record a Windows boot loader? UEFI boot systems have been around awhile now so although it is unusual for Windows 7 to be installed in EFI mode it could be the case with your system. It is certainly something to eliminate.

To put it simply, if Windows is installed in EFI mode, then Ubuntu must be installed in EFI mode. If Windows is installed in legacy mode then Ubuntu must be installed in legacy mode. If we do not follow this rule, then I think we get this either one or the other situation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by KayeNg on 2015-09-06
Thank you ajgreeny and grahammechanical.  Before I try boot-repair or anything else, I would like to ask:

1. Why isn't boot-repair in Software Center?
2. I typed sudo update-grub and I got this:    Found Windows 7 (loader) on /dev/sda1    What does it mean?

Additionally, I also typed:
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
I got this: 
Legacy boot on HDD
What does it mean?

One more thing, I used Rufus to create the live USB.

UPDATE:   I typed [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"   and got this:
Installed in Legacy mode
So the Lubuntu is installed in Legacy mode.  And as stated above, "Legacy boot on HDD".

UPDATE:  I typed sudo parted -l  , and got this, among other info:
Partition Table: msdos
which means Windows 7 is booting in Legacy mode.

So, does that mean both Windows 7 and Lubuntu was installed in Legacy mode? If so, then what's the problem? Why can't I have both OS's boot? If I repair Windows, Lubuntu won't boot, and vice versa.

Time for Boot-Repair?

UPDATE: I really don't get it.  I thought it was because I created the Live USB using Rufus with the UEFI option, but upon looking at Rufus images online, it seems the default choice is "MBR partition scheme for BIOS or UEFI computers", which means that the created Live usb SHOULD work with Legacy/BIOS.  I'm stumped.

---

### Post by yancek on 2015-09-06
> 
2. I typed sudo update-grub and I got this:    Found Windows 7 (loader) on /dev/sda1    What does it mean?

It means it found boot files on the windows partition which is the first partition on the first hard drive.  The other output you posted indicates you are using MBR legacy to boot rather than UEFI.  After running the update-grub, did you reboot and fail to boot windows?  Your first post indicates that when you select windows from the Grub menu, you get a black screen.  Once you make that selection, you are out of Ubuntu/Grub and in windows.  You could post the output of the Create BootInfo Summary from boot repair and someone might see something.

---

### Post by KayeNg on 2015-09-07
I got this from Bootinfo

[http://paste.ubuntu.com/12306531/](http://paste.ubuntu.com/12306531/)

UPDATE:  Booted to Live USB, installed and run boot-repair, finished without problems, boot-repair provided a link in case problem persists [URL="http://paste.ubuntu.com/12306531/"]http://paste.ubuntu.com/12306596/
[/URL]
Still cannot boot into Windows!

---

### Post by yancek on 2015-09-07
You have Grub in the MBR pointing to sda7 where the Ubuntu/Grub files are.  The grub.cfg file has two entries for windows, one on the first partition of the larger drive and one on the first partition of the smaller drive.  Do you see two entries for windows in the Grub menu?  Have you tried booting the second entry.  Both windows entries point to the correct partition with the correct UUID so that isn't the problem.  Have you set the second drive to boot windows on that drive and does that work as it has windows code in the MBR and should boot?

I don't see anything wrong with the Grub files.  The only thing unusual on the sda1 windows partition is the 'grldr' file which is an EasyBCD file.  Don't think that would effect booting windows but I don't really know.  If you select windows from the Grub menu, you are out of Ubuntu/Grub and in windows so there is nothing you can change in Grub to make it boot.

---

### Post by KayeNg on 2015-09-07
Do you see two entries for windows in the Grub menu?
Yes I do.  One is in sda, the other in sdb, I think.

Have you tried booting the second entry?
Yes I have.  Both returned black screen and if I hit any key on the keyboard, I get a beeping sound.

"Have you set the second drive to boot windows on that drive and does  that work as it has windows code in the MBR and should boot?"
------If you're referring to the smaller drive as you stated earlier, I think I did set it to boot Windows months ago, HOWEVER, as this particular desktop computer had a really nasty virus infection, I formatted both larger HDD and smaller HDD, and since then I have not used EasyBCD.  I installed Windows 7, and now I'm trying to install Lubuntu along side it (both in the same HDD)  (I don't know what I'm going to do with the smaller HDD yet)

Don't know if it's worth mentioning but when I formatted both drives and began installing Windows 7 by booting the Windows 7 cd, I deleted all partitions on the larger drive, then proceeded with the install, then Windows automatically created the 100MB on the first partition.  I allowed the installation to finish, then I boot into the installed Windows 7, used a partitioning tool to get rid of the 100MB partition and move everything to the left, and everything was fine.  This was before I tried to install Lubuntu. 

Also, the MBR is separate from any partitions, is that correct? I thought formatting would delete all info including the MBR.  Should I delete the MBR of the smaller HDD?

---

### Post by yancek on 2015-09-07
A standard installation of windows will usually create a 100-200MB partition at the beginning of the drive.  This is the boot partition with the windows boot files.  You do seem to have the correct boot files on sda1, the first partition of the first drive with windows. 

> . Also, the MBR is separate from any partitions, is that correct?

Yes.

> I thought formatting would delete all info including the MBR.  

No.  Generally the formatting is applied to specific or multiple partitions.

> Should I delete the MBR of the smaller HDD? 		

If it has a virus and is unusable, just unplug it until you get the current problem resolved and then decide what you want to do with it.

I would suggest you do an online search for black screen when booting windows 7.  The link below is to the microsoft site.  Doesn't look very hopeful.

[http://answers.microsoft.com/en-us/windows/forum/all/windows-7-black-screen-when-booting-up/93a2c6e2-9418-4f45-b217-2a152fcce665](http://answers.microsoft.com/en-us/windows/forum/all/windows-7-black-screen-when-booting-up/93a2c6e2-9418-4f45-b217-2a152fcce665)

---

### Post by KayeNg on 2015-09-09
In the end, this is what I did:

Boot into Windows 7 CD, click repair, opened command prompt, typed:
diskpart --> list disk --> selected the hard drive in question by typing "select disk #" where # is 0, 1, 2, etc.  --> typed clean

Boot the windows 7 CD again, insalled on the clean drive, which windows cd did so by automatically setting aside a 100MB partition for system reserved.
Installation successful.

Since I don't want the 100MB partition, I boot the windows cd again.  Clicked repair, opened command prompt, followed this guide 
[http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html](http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html)

Follow up to the previous step should be this:  [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
but did not quite work for me.  So I boot the windows cd again, clicked repair, opened command prompt, and typed:
bootrec /fixmbr
and
bootrec /fixboot

Then I was able to boot into installed windows 7 despite having deleted the 100MB partition.  

However, the 100MB partition is still there, albeit empty.  I simply used EaseUS partition manager to move sda1 (windows 7) to the left.  The computer had to reboot to finish moving sda1 to the left, but it was successful.  

Next I installed a fresh Lubuntu on a separate partition (on the same hard drive).  During installation, I chose dev\sda as the location for bootloader installation.  NOT dev/sda1.  

Now I have a dual boot system of windows 7 and lubuntu, with GRUB as the main bootloader or whatever it's called =)  (I could have used EasyBCD but I figured it's better to learn to use grub)

Now my problem is with my other computer, a laptop.  [**[COLOR=#000000]yancek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724") suggested this 
sudo grub-install /dev/sda 
in my other question "Dual boot Windows XP and Lubuntu: Want GRUB as bootloader"

I think the laptop became unbootable.  It was a black screen with a message.  I don't have the laptop with me right now, so maybe I'll post again later.  Or should I post in the other thread?

By the way, if I set aside a 300MB primary partition and install freedos there, would GRUB automatically detect it?

---

### Post by yancek on 2015-09-09
> (I could have used EasyBCD but I figured it's better to learn to use grub)

Yes it is.  EasyBCD is basically a graphical front end of something the people at neosmart created and called 'neogrub' which in itself is a modification of 'grub4dos' which again is a modification of the original Grub.

> I think the laptop became unbootable.  It was a black screen with a  message.  I don't have the laptop with me right now, so maybe I'll post  again later.  Or should I post in the other thread?


Start another thread.  Post the message when you can.

> By the way, if I set aside a 300MB primary partition and install freedos there, would GRUB automatically detect it?         

I haven't used FreeDOS so I'm not sure but I expect it would boot.  Most likely chainloading as it does with windows.

---

