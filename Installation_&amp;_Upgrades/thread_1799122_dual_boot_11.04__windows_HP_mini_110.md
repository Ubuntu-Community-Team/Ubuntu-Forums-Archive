---
title: "dual boot 11.04 / windows HP mini 110"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by jal on 2011-07-07
new netbook, HP mini 110, comes with windows7 installed <rant suppressed> but I'd like to dual boot Ubuntu. 11.04 sees the wireless so am installing that via usb boot.

Two choices: "erase disk and install ubuntu" || "something else"

Select "something else", get to partitioning, and the only option is "New Partition Table" with warnings "you have selected an entire device... all current partitions will be removed".

This is not a nice message. I want to keep the winders/HP stuff, and set up a linux partition too. 

Am I missing something simple here? I'm looking for the "we'll re-partition for you preserving your current os and install grub" option that I'm used to.

Note that HP intalled using all 4 primary partitions, I'd like to keep them, but no more partitions can be created. To create an extended partition a primary would have to go.

Note I am starting from the trial desktop, which means the wireless is working, whereas going straight to install from the boot doesn't seem to connect.

---

### Post by dasan on 2011-07-07
It is mandatory that you should loose one of your primary partitions.. 

And if you don't get wireless after installation try to connect it with wired network and check for restricted drivers tooo.....

---

### Post by jal on 2011-07-07
> **dasan said:**
> It is mandatory that you should loose one of your primary partitions.. 

And if you don't get wireless after installation try to connect it with wired network and check for restricted drivers tooo.....

This then is what I shall have to do.

Actually, I was going to just blow away the installation, but I thought I'd check before in case I was missing something simple.

Don't think I can connect wired, I can't find an RJ45 port on this netbook, although ifconfig does show eth0 with a mac address different from wlan0

---

### Post by westie457 on 2011-07-07
> **jal said:**
> This then is what I shall have to do.

Actually, I was going to just blow away the installation, but I thought I'd check before in case I was missing something simple.

Don't think I can connect wired, I can't find an RJ45 port on this netbook, although ifconfig does show eth0 with a mac address different from wlan0

Hi what are the names of the partitions on your machine?

Only asking as getting rid of the wrong one could cause problems later.

---

### Post by jal on 2011-07-07
> **westie457 said:**
> Hi what are the names of the partitions on your machine?

Only asking as getting rid of the wrong one could cause problems later.

```

/dev/sda1 	ntfs 	SYSTEM 	199.00MiB 	66.59Mib 	123.41Mib 	boot 
/dev/sda2 	ntfs 	x 	48.83GiB 	21.90Gib 	26.93Gib 	
unallocated 	unallocated 	x 	167.36Gib 	- 	- 	
/dev/sda3 	ntfs 	RECOVERY 	16.40Gib 	14.03Gib 	2.37GiB 	
/dev/sda4 	fat32 	HP_TOOLS 	103.18Mib 	11.58Mib 	91.60Mib 	lba 
unallocated 	unallocated 	x 	1.00Mib 	- 	-

```

sda1 & sda2 are my primary targets - if I ever want the windows installation back surely the RECOVERY sda3 can restore to pristine condition. It should by rights be an image of my original software purchase, albeit not on separate media.

---

### Post by westie457 on 2011-07-07
> **jal said:**
> ```

/dev/sda1 	ntfs 	SYSTEM 	199.00MiB 	66.59Mib 	123.41Mib 	boot 
/dev/sda2 	ntfs 	x 	48.83GiB 	21.90Gib 	26.93Gib 	
unallocated 	unallocated 	x 	167.36Gib 	- 	- 	
/dev/sda3 	ntfs 	RECOVERY 	16.40Gib 	14.03Gib 	2.37GiB 	
/dev/sda4 	fat32 	HP_TOOLS 	103.18Mib 	11.58Mib 	91.60Mib 	lba 
unallocated 	unallocated 	x 	1.00Mib 	- 	-

```

sda1 & sda2 are my primary targets - if I ever want the windows installation back surely the RECOVERY sda3 can restore to pristine condition. It should by rights be an image of my original software purchase, albeit not on separate media.
You are right about sda3 RECOVERY. It will return your computer to how it left the factory reformatting the c: drive -sda1.
It should not touch sda2 - an area for your files outside of your personal directories inside Windows.

Now the good news once you have backed up your files in sda2.
Not 100% sure if it is best to wipe your data partition - sd2 using Gparted and then creating an extended partition there for your Windows created personal files and also using it for your Ubuntu install, or maybe you should use the Windows Disk Management tool to wipe it and create the extended partition as above.
Not having an HP computer I cannot really give you more specific advice. However you do this take it one step at a time so the partitioning software does not get confused and turns your hard drive into a paperweight.

This has happened to me several times in the past and probably will in the future.

---

### Post by Mark Phelps on 2011-07-07
If your HP has the option to create Restore Media (i.e., CD/DVD), you could do that and then remove your Recovery partition.

Also, a possibly better alternative would be to download and install Macrium Reflect (free edition) -- and use that to do an image backup of your Win7 partitions (the first two) to an external drive.

THEN, you could remove the Recovery partition because you have a way of restoring Win7 the way it exists today.

---

### Post by jal on 2011-07-08
> **Mark Phelps said:**
> If your HP has the option to create Restore Media (i.e., CD/DVD), you could do that and then remove your Recovery partition.

Also, a possibly better alternative would be to download and install Macrium Reflect (free edition) -- and use that to do an image backup of your Win7 partitions (the first two) to an external drive.

THEN, you could remove the Recovery partition because you have a way of restoring Win7 the way it exists today.

That looked like the answer. I checked, there is installed a tool to create a recovery disc and remove the recovery partition. It was able to create a recovery media on a usb stick which is good considering there are no optical drives on the netbook.

Then I found it wanted a 15GiB stick. Woa! Ain't got one a those.

I could go with option two though, I've a usb drive I can image the partition onto.

Thanks.

---

### Post by jal on 2011-07-08
westie457, thanks for the thoughts, I shall go carefully in this dangerous world of partitioning.

Although, between you 'n me, (and at risk of going thoroughly off topic) I think the partition is already borked - every time I fire up windows I get my face filled with bright yellow, full screen "BUY NORTONS, NO OPTIONS, PRESS THE AGREE BUTTON NOW!!!!"

---

### Post by westie457 on 2011-07-08
> **jal said:**
> westie457, thanks for the thoughts, I shall go carefully in this dangerous world of partitioning.

Although, between you 'n me, (and at risk of going thoroughly off topic) I think the partition is already borked - every time I fire up windows I get my face filled with bright yellow, full screen "BUY NORTONS, NO OPTIONS, PRESS THE AGREE BUTTON NOW!!!!"

Let me guess here, you have been using this box for about 6 weeks and are half way through the trial period for Norton Anti-virus.
If you are getting that message your Windows partition is still there. This is Norton's way of getting you to buy their product.

Two choices. Click to buy it to see what happens then click on cancel, to get in to Windows. Or do a factory restore which unfortunately will wipe any of your personal items stored in the Windows partition.

Somewhere in these forums someone has found a way to legally download a Windows 7 iso. You can always use that to repair Windows startup problems.

Anyway back to topic. If accepting the 'option' to buy allows you to boot into Windows IMO opinion this would be a good time to uninstall Norton. Be aware however that this is not a very easy thing to do as Norton hide 1 file which has to be deleted manually. This file stops the uninstall process from working.

---

### Post by coffeecat on 2011-07-08
@jal, I have a HP Mini 110, and it is now successfully booting both Windows 7 and Ubuntu 11.04.

You need the HP_TOOLS partition only to make the restore media. You need the RECOVERY partition to set the machine back to its factory condition if you haven't made restore media.

This is what I did.

1 - created a set of recovery DVDs using an external USB optical drive.

2 - deleted the HP_TOOLS partition.

3 - installed Macrium Reflect Free in Windows 7 and created a restore image just for good measure.

4 - Shrunk the Windows 7 partition using the Windows Disk Management utility. It looks as though you've done that already.

5 - created an extended partition in the space freed between the Windows sda2 partition and the Recovery partition.

6 - created ext4 and swap logical partitions in the extended partition using Gparted on the live USB.

7 - installed Ubuntu 11.04 to my Linux partitions, choosing the "something else" option in the installer's partitioning stage.

8 - enjoyed using Ubuntu. :)

By the way, two things. Norton will uninstall with its own uninstaller. I did so successfully and replaced it with AVG free. 

Also - if you have a Broadcom wireless chipset and it is working with the new default open source driver that comes with Natty/11.04, ignore the pestering you will get from Jockey (Additional Drivers) to install the proprietary STA driver. There is no need.

---

### Post by jal on 2011-07-08
@coffeecat, An excellent plan and welcome advice.

Thank you.

This answers my original question, I think, if I knew how I would mark the thread as "resolved".

(the Nortons thing only came up because I was really really annoyed with my new machine being pre-infested; but thanks too for that bit of info)

---

