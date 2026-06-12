---
title: "What will happen if I remove Windows?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Puzzled Guy on 2009-11-27
Hi,
I installed Ubuntu a few weeks back. It occured to me "what will I do if I run  out of space in Ubuntu?". I would like to remove Windows (haven't used it for weeks). There is only one problem: When I installed Ubuntu, I chose to import my windows account because I still need my files (Windows can go to cyber-hell).

I'm afraid of what will happen if I delete the Windows partition. Because I imported my files from Windows during the ubuntu installation (the part that shows you the Windows accounts that can be imported), I am worried that if I delete Windows my files might be lost.

So, again, if I delete Windows, are my imported files affected (are the files copied from Windows or are they simply linked?)

So, after you read all that blather, here's the short version: My imported account settings and files, are they or are they not affected by me deleting the Windows partition?

---

### Post by KeLa on 2009-11-27
To make sure that you don't lose anything then copy all your account settings and important files from windows to usb stick or usb hd and after that remove windows.
Also make backup copy of your ubuntu files before removing action.
That way you have all you important stuff safe even if whole pc goes mad in the process.

---

### Post by SeanHodges on 2009-11-27
KeLa's suggestions about backing up before removing Windows are all very valid. 

Though in answer to your question "are my imported files copied from the Windows partition?" yes, the files are copied, and are not read from the Windows partition. You are able to remove Windows from your disk without losing the data that you imported.

---

### Post by Puzzled Guy on 2009-11-27
So they are copied over from windows and not read from Windows? Great! Thanks.
I was worried that Windows will be haunting my laptop forever :shock: But now, Windows, your days are numbered! :lolflag:

---

### Post by the8thstar on 2009-11-27
A word of WARNING: make sure you burn the recovery disc of Windows on a DVD before you get rid of Windows on your computer. Just in case you ever want to use Windows again.

---

### Post by Puzzled Guy on 2009-11-27
Just one problem with that, I don't have a CD/DVD drive. But there is another computer here home that *does* have one, would it be possible to copy the recovery DVD file onto a USB and then, using USB writing software, write it to the USB stick?

---

### Post by darkod on 2009-11-27
No need for that. What is called Recovery or Repair disc actually allows you to repair your windows installation if it doesn't boot OK. Like when you had grub on the MBR and you want to put windows bootloader back.
That disc will NOT allow you full windows installation. You need the installation media for that.
And you don't need to create that disc now because even if you need it, it's here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

That is the reason they are allowed to put it on the internet like that. It is only recovery for the boot process, you can't install windows on a computer with it. The article explains it also.

PS. One option would be to make image of your win7 using the Backup & Restore tool in Control Panel, and you can save that image file on external usb hdd. The tool will also give you option to create startup disc (or whatever it's called), and the logic is that you boot up with the startup CD and you have your usb hdd plugged in, you select your image and it will restore it on a partition of the internal hdd. Haven't done it before, but it should work like that. In that case you will have your win7 installation back. But not with only the recovery CD.

---

### Post by Puzzled Guy on 2009-11-27
Anyway, if I *do* remove Windows, it won't affect the GRUB except if I want to attempt to boot into Windows, right? Because the GRUB is stored in the Ubuntu partition, right?

But if I remove Windows, I'll also want to remove the GRUB bootloader. Is there any way to remove it from within Ubuntu or through the LiveCD? I mean, **without messing up the entire OS (**Ubuntu AND Windows**) **before I delete Windows itself?:p<DIE WINDOWS!>

---

### Post by darkod on 2009-11-27
Grub2 should be on the MBR of the drive. Deleting the windows partition wouldn't affect it. After you delete the partition, boot into Ubuntu and in terminal do
sudo update-grub

That will update grub2 and since there is no win7 to detect, it will remove it from the grub menu itself. Not sure if you will not see any grub menu after that because I never used only ubuntu. It is logical not to ask you which OS to choose because it's only one, but can't tell you that for sure.

PS. In fact, it might be better to just format the windows partition as ntfs or ext4, your choice. If that was your first partition, it's called /dev/sda1 and it's first at the start of the hdd. If you actually delete it and create new partition instead, it will be called /dev/sda3 or whatever, while it will still be first on the drive. I always try to avoid such situations partition not to be in order. If you just format it it will remain /dev/sda1. And, as always, BE CAREFUL when deleting or formatting partitions.

---

### Post by vexorian on 2009-11-27
I used an external hard drive to which I installed clonezilla ([http://clonezilla.org](http://clonezilla.org)). Then I booted the netbook using the hard drive and made a backup of the whole hard drive. 

The other alternative is to get an external optical drive...

I guess that if you had a desktop you could try a network clonezilla boot but I never tried it

---

### Post by Puzzled Guy on 2009-11-27
Thanks for the warning darkod. So, if I remove the Windows partition using gparted, use the space for Ubuntu, and use the update grub command, what will happen when I reboot after that? Will it show the GRUB with only Ubuntu on it or will it just boot straight into Ubuntu?

---

### Post by jessiebrownjr on 2009-11-28
It grub shows only Ubuntu as your OS, It should boot straight past it I think... You might want to look into how to access the recovery kernel option thought if thats the case..

And when you said what will happen if I remove windows? the first thing that came to my mind was "an angel will get their wings!" lol.

On my laptop, when I formatted, I actually erased the recovery partition of my windows... I freaked out because I was needing to reinstall windows for gaming PLUS I thought I didn't get a recovery CD. It turns out later that I had gotten one, but never had to use it.. Before I found that though, had to... bittorrent an OEM version of Vista to get it back.. I'm not sure if it was illegal or not to do that because 1) it was a dell OEM CD that was online ( i am using a dell) and 2) I put my own valid serial number into the windows upon installation. 

I have a great idea for you, take it or leave it. I have this done on my desktop. I have a windows installation with just enough extra space for swap file area and various upgrades, and then I have ubuntu installed with most of the extra space. Now the *trick* i mentioned was I have a third NTFS formatted partition where I store all my stuff like mp3s, videos, various stuff. You can use that space various things. On my laptop I didn't do that and I regret it every day :-)

---

### Post by Puzzled Guy on 2009-11-28
Can I have some step-by-step instructions (always terrified of messing up) that shows me how to remove Windows with GParted (should I also remove the WINRE partition?), give the extra space to Ubuntu, and then change the GRUB bootloader to remove Windows from the list?

And also, what are the precautions I should take before and while I do the above?

---

### Post by vexorian on 2009-11-28
> **Puzzled Guy said:**
> Can I have some step-by-step instructions (always terrified of messing up) that shows me how to remove Windows with GParted (should I also remove the WINRE partition?), give the extra space to Ubuntu, and then change the GRUB bootloader to remove Windows from the list?

And also, what are the precautions I should take before and while I do the above?
If I were you, I would back up my ubuntu /home, then do a clean ubuntu install (and reinstall packages as necessary).

Make a full disk backup somehow. Again, I would use clonezilla.

Second easier solution is possibly to grab gparted, delete windows partition. Do not delete WINRes partition unless you have that disk backup. Then you may just create an auxiliar partition in ext3 that you would use as an extra drive. Well, if you are not that lazy, you may extend the size of your home instead of creating a new partition...

grub? do sudo grub-install in your ubuntu after removing the windows partition.

But honestly, I think that what I described in my first paragraph is less work and less risky (you really need a windows backup nevertheless, restoring that backup will help you when reselling it, or when you need tech support for hardware issues)

---

### Post by Puzzled Guy on 2009-11-28
I never thought of it *that* way!

But I checked clonezilla and it seems a bit too complicated for me. I prefer backing up my files manually so that I know what files go into it and what doesn't.

Where was I, so I make a backup of all the files that I want to keep, make a note of all the packages I need to install like the ubuntu-restricted-packages and also all the fixes that I used, reinstall ubuntu as "use entire disk" (will I be able to import my Windows account there?), transfer all the backed-up files to the proper directories, done!

---

### Post by jessiebrownjr on 2009-11-29
> **Puzzled Guy said:**
> I never thought of it *that* way!

But I checked clonezilla and it seems a bit too complicated for me. I prefer backing up my files manually so that I know what files go into it and what doesn't.

Where was I, so I make a backup of all the files that I want to keep, make a note of all the packages I need to install like the ubuntu-restricted-packages and also all the fixes that I used, reinstall ubuntu as "use entire disk" (will I be able to import my Windows account there?), transfer all the backed-up files to the proper directories, done!

There will no longer be a windows account to import if you "use entire disk", you will erase it. That step is done at the end of the install I think. But yeah, keep the recovery if you can, if not, contact your PC manufacturer and see if you can afford to buy recovery software for your rig... Thats not free, but its good to have... Think about what happens if your HDD dies (ohhhh they dooo) and ALL you had was the recovery partition that is now fried?

---

### Post by Puzzled Guy on 2009-11-29
I could also do this:


[LIST=1]
[*]Boot into the LiveCD
[*]Open GParted
[*]Shrink Windows to the smallest size without making it smaller than the stuff that is already there (right you know that yellow section of the partition that represents the data?)
[*]Give the new space to Ubuntu (I have enlarged it once and it took *2 hours* to complete the task)
[*]Pray that it will be successful
[/LIST]

Shrinking a partition may cause data loss if you over-shrink it but enlarging it should do anything, since you're *giving* space instead of taking it away, right?

---

