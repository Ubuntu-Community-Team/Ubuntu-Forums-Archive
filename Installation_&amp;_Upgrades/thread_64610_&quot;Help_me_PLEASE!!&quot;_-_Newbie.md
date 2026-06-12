---
title: "&quot;Help me PLEASE!!&quot; - Newbie"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by ojpd on 2005-09-11
Hello Ubuntu Gurus! 

Well I have a copy of Ubuntu 5.04 and I really really wanna install it but I'm afraid I might ruin my Windows MBR and can't get windows to work and at the same time I wouldnt be able to ask for help becoz the last time I successfully installed ubuntu in my pc it messed up my windows and I didnt get my dial up internet to work with ubuntu becoz it doesnt seem to support/detect my external Dial Up Modem. Anyways, I hope there's somebody out there who can teach me how to Dual Boot my XP with Ubuntu.. I've found a couple of solutions already and one is to install GRUB/Bootloader to a floppy and do the copy thingy.. honestly I have no problems with Windows and editing the boot.ini file, when it comes to linux though.. I am a dumbass hehe The thing is I cant do the Copying to a floppy disk drive method becoz I don't have a floppy disk drive and I can't really afford to buy a new working one.. Would it be possible to install ubuntu in my HD's 2nd partition but then install GRUB/Bootloader to a CD-R/CD-RW and then do the whole "copying the Bootsect.lnx" method and not ruin my Windows MBR... 

Or maybe is it possible to just download a ready made bootsect.lnx and not install the GRUB/Bootloader when I install Ubuntu in my 2nd partition?

Hope somebody can help me get through this crappy situation.. I really love ubuntu! problem is I cant give up San Andreas in windows hehe Thanks in Advance!  :smile:

---

### Post by dave9191 on 2005-09-11
You can get grub to boot you into windows. Thats what I do and I find it far easier then copying stuff to windows each time you make a change to linux. And if you mess up your windows xp mbr and cant boot to windows. Then put the win xp cd in and boot into the recovery console and type fixmbr. That will restore it and give you windows back. 

I guess that you could get grub onto a bootable mem stick or cdrw and have a menu appear when you put the cd / mem stick into your comptuer. 

What I do to dual boot is install windows, creat some unpartoned space at the end of my drive, put the ubuntu cd in and install and let it install to the unpartioned space. It detects windows and creates a boot menu for me and installs grub into the mbr. When I boot I have a choice of windows or ubuntu. 

As for your modem, if its an external usb one, it might not be a proper modem, juts a winmodem and you might have a hard time getting it to work. Look up linmodems.org for help. 

And it might be possible to play GTA SA under linux [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3804](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3804) . But it probably wont work as well as windows. 

Dave

---

### Post by palough on 2005-09-13
Hi Hope this helps also if you have not found the solution already.

I use Partition Magic 8, you can use anything you like but PM8 can set up Linux partitions.

Under Windoze I peel off a slice of the Hard drive and then partition it into 3 partitions.  One big enough for the Root Partition, I used 4 Gig, then one for the swap partition (PM8 allows you to select partition type as Linux Swap), the final one for Home, as big as you like.

I then label each partition so I can identify it easily when Ubuntu gives you the partition manager although this is not necessary as the first linux partition in the list is root, swap is easy to identify as it is labeled as such and home is the last partition on the list.

Then simply follow the instructions in the Ubuntu partitioner, remember to format each partion to be doubly safe and set the flag to bootable on the first partition.

Ubuntu will format the partitions and set them up for installation, after installation it automatically installs Grub and dual boot.

Really easy.   Hope this helps.

Cheers  \\:D/

---

### Post by impeteperry on 2005-09-13
[QUOTE=ojpd]Hello Ubuntu Gurus! 

Well I have a copy of Ubuntu 5.04 and I really really wanna install it but I'm afraid I might ruin my Windows MBR and can't get windows to work and at the same time I wouldnt be able to ask for help becoz the last time I successfully installed ubuntu in my pc it messed up my windows and I didnt get my dial up internet to work with ubuntu becoz it doesnt seem to support/detect my external Dial Up Modem. Anyways, I hope there's somebody out there who can teach me how to Dual Boot my XP with Ubuntu.. I've found a couple of solutions already and one is to install GRUB/Bootloader to a floppy and do the copy thingy.. honestly I have no problems with Windows and editing the boot.ini file, when it comes to linux though.. I am a dumbass hehe The thing is I cant do the Copying to a floppy disk drive method becoz I don't have a floppy disk drive and I can't really afford to buy a new working one.. Would it be possible to install ubuntu in my HD's 2nd partition but then install GRUB/Bootloader to a CD-R/CD-RW and then do the whole "copying the Bootsect.lnx" method and not ruin my Windows MBR... 

Or maybe is it possible to just download a ready made bootsect.lnx and not install the GRUB/Bootloader when I install Ubuntu in my 2nd partition?

Hope somebody can help me get through this crappy situation.. I really love ubuntu! problem is I cant give up San Andreas in windows hehe Thanks in Advance!  :smile:[/QUOTE]
 If your Windows is XP and it come factory installed on your computer there is a "system recovery" partion where grub wants to put the dual boot. After a week trying to get a dual boot to work I resorted to buying "system commander" which works for me.

---

