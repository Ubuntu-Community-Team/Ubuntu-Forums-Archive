---
title: "Grub 2 won't detect ubuntu installation on the HDD"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by Th3D0ctor on 2013-04-30
Hi ! I've been having trouble installing ubuntu 12.04 on my laptop lately . It is a HP Compaq nc8430 . Using the stock HDD , ubuntu installs fine . Since I've upgraded my HDD to a Western Digital Scorpio Black WD7500BPKT 750GB , linux won't install properly . 

I've successfully installed Windows 7 x32 on this new HDD . Now I'm trying to do a dual boot . 

The Ubuntu install goes fine , no error whatsoever , but at the end , after I restart , I'm being shown a grub recovery console . 

I have tried BootRepair with no success . Also I've tried reinstalling ubuntu from a live cd ... again with no success . Also tried super grub 2 disk , but it doesn't detect the linux installation . And again , also tried installing grub 2 to a separate partition . I even tried EasyBCD to boot linux using the windows boot manager , locating the linux installation manually ... No luck .

Am I missing something ? Should I format the entire HDD and install ubuntu first ? Please , help me , I'm at my wits' end ..

---

### Post by darkod on 2013-04-30
Some times bios can't read boot files if they are beyond 137GB on the disk. If this affects you, it might be the reason.

So there is literary no error during the install, not even at the end? It doesn't say it can't install grub2 or similar?

You can try having a small 500MB or 1GB /boot primary partition at front, then the win7 primary partition, and then ubuntu. That will make sure the boot files are at front.

---

### Post by Th3D0ctor on 2013-04-30
"So there is literary no error during the install, not even at the end? It doesn't say it can't install grub2 or similar?"

No error whatsoever . Should I reinstall and press ctrl+alt+f1 to check the console during install ? Havent checked there .

"You can try having a small 500MB or 1GB /boot primary partition at front.."

I did create a separate boot partition with 500 mb , but I'm not sure I made it primary .  I'll try this and post results after .

---

### Post by Th3D0ctor on 2013-04-30
I deleted my entire HDD and installed Ubuntu using a separate 500mb /boot primary front partition . Ubuntu loaded successfully . I'm attempting to install windows 7 right now and dual boot .

---

### Post by Th3D0ctor on 2013-04-30
Ok , I installed windows 7 and repaired grub 2 using Boot Repair from the Ubuntu Live CD . Now grub 2 loads and detects both systems , but when  I try to boot into windows 7 grub gives me : error no such device ( a long number )  / error out of disk  / Press any key to continue . Booting into ubuntu seems to work just fine . 

This seems to be the same situation reversed ... now its windows 7 the one not detected .

---

### Post by darkod on 2013-04-30
But did you install windows after ubuntu on the disk?

You have to make sure both OSs are within 137GB. ubuntu can work just fine on the back of the disk as long as you have the /boot in front.

So, the layout you need would be like:
/boot
win7 system rserved
win7 os
ubuntu....

If you partition using the win7 installer it will automatically create the small win7 system reserved partition, which will also make sure the win7 boot files are at the front of the disk.

Or you can create the win7 partitions manually yourself in advance. On the small partition planned for system reserved put the boot flag and windows will use it for the boot files.

---

### Post by Th3D0ctor on 2013-04-30
I installed windows 7 after ubuntu  .  /boot has 500mb , / has 100 gb , /home has 100gb , /swap has 3 gb ( I have 3 gb RAM ) . I assigned windows 7 100 gb , but it didnt create the system reserved partition . Also , I reached the maximum of primary partitions and it doesnt allow me to further partition the rest of free space available ( 400 gb ) .

I'll delete everything and use the layout you gave me . Will post results after .

---

### Post by darkod on 2013-04-30
Make the ubuntu partitions logical, except the /boot. Because you need primary for windows too. If you need only 100GB for windows, no need to have the small one. Create first partitions from live mode, then simply use the in the win7/ubuntu installer.

Make them:
1GB ext4 for /boot, primary
100GB ntfs for win7, primary with boot flag
other ubuntu partitions, logical

That makes sure both /boot and the win7 partition are within the 137GB.

---

### Post by Th3D0ctor on 2013-04-30
Ok , I used the layout you gave me in your last post and it worked like a charm ! Thank you so much ! 

P.S: I had to realign one of my logical partitions and I used Boot Repair after installing ubuntu ... Don't know why it didn't make the boot configuration automatically since I installed it last ... but never mind . Every think works now !

---

