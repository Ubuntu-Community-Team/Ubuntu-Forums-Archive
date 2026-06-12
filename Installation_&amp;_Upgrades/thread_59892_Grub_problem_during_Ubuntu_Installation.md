---
title: "Grub problem during Ubuntu Installation"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by rubenjavier on 2005-08-25
The Ubuntu/Kubuntu installation goes fine until GRUB needs to be installed, It gives me an error no matter where I tell it to be installed, it can't be installed on the primary boot record or in any other partition/HD on my machine
the weird thing its that I've already installed ubuntu in another 3 different machines with no problems (including a laptop)
In the laptop ubuntu is in a secondary partition of the only HD and GRUB is on the primary boot record
One the other two machines ubuntu is on a secondary partition on the 2dn HD of each machine and GRUB is on the primary boot record of the First HD while windowsXP is on the first HD
in my machine I had XP on the first HD and Ubuntu on a secondary partition of a 2dn HD (just like the other machines I've installed) the only difference is the motherboard (msi kt6v on my machine while the other where intel), and the HD are both set to be LBA on my machine too... what can be happening?
why can't I install GRUB on my machine... I used to have SUSE in this same pair of HDs with GRUB but I formatted them and reinstalled WinXP and now Im trying to instal ubuntu in the same HD were i used to have SUSE 9.2 (when I had SUSE with this same HDs and same partitions I had them on a different mother board)
any help would be appreciated
thanks

---

### Post by amohanty on 2005-08-26
Whats the format of the partition where you are trying to install GRUB?
AM

---

### Post by rubenjavier on 2005-08-26
Its an NTFS partition, just like in the laptop and the other machines I've installed too
the only thing that catch my eye its that the first cluster MFT is 726,628 and the other machines had very small numbers there
thanks

---

### Post by amohanty on 2005-08-26
Ok if the primary partition is NTFS you need to install GRUB in the MBR not on disk. If you are already doing so, could you possibly post the error message.

AM

---

### Post by rubenjavier on 2005-08-28
*OK when I get to the installation screens that says:
 Install the GRUB boot loader to the master boot record
                                                                             <Yes>

*then the next installation screen says:
Runing "grub-install (hd0)"

*then the Error Screen appears:
Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed
This is a fatal error
<Go Back> <Continue>

***************
If I choose Go Back then Grub cannot be installed in any other HD (because the first partition on both my HD are NTFS and the EXT2 partition for Ubuntu in my 2nd HD is way beyond the 1024 mark) but in others machines including a laptop it worked well
I dont Want to use LILO because everyone that uses LILO from the Ubuntu installation ends up with their machines going directly into Linux without any start menu.
What can be happening to my MBR that I can't install GRUB on it? i used to have GRUB in the same HD months ago when I tried SUSE (In that time I also had a small FAT32 partition at the end of my first HD but I'm pretty sure that GRUB installed it self on the MBR), can my MBR be fixed? or its a GRUB thing?
I've already used chkdsk /f on both my HD but nothing seems wrong
any help would be appreciated
Thanks

---

### Post by chant on 2005-08-28
I have exactly the same problem.

I try to install kubuntu, and everything goes fine except the grub installation. It detects that I have Windows 2000, and I say "yes" to install grub in the MBR, but it gives the same error as the one posted by rubenjavier.

I also tried to install grub to a floppy disk, but again there's that fatal error (this time in fd0).

Any ideas? Thanks in advance

---

### Post by rubenjavier on 2005-08-31
If anybody has an idea please Help
Its happening now on another machine too
a Toshiba Tecra M3
There has to be a reason for GRUB to install in some MBRs and in others not
I could suspect from a laptop HD, but from a common Maxtor HD like the one in my home??? and the same CD installed GRUB on a really old and problematic 4Gig BigFoot HD
I really need to had both systems runing on this machines what can be happening to GRUB? is the ubuntu/kubuntu hoary an old buggy version of GRUB?
thanks in advance

---

### Post by amohanty on 2005-09-01
Try looking at this thread:
[http://www.abxzone.com/forums/showthread.php?p=959299#post959299](http://www.abxzone.com/forums/showthread.php?p=959299#post959299)

HTH
AM

---

### Post by rubenjavier on 2005-09-01
thanks man
but Im installing GRUB on a newlly installed machines, with just XP recently installed on them (minutes of diference between XP and Ubuntu installations), so there can't be another GRUB interfering on the MBR...
Do I have to install without installing GRUB?
What would happend if I do that? will XP run at least?
should I be able to install GRUB after that?
could this be a hardware conflict probelm? one of the machines is a Laptop TOSHIBA TECRA M3, the other is a desktop with a MSI KT6V MoBo, and the third I dont have it here and I can't remember right now but I think it was a Laptop HP ze1210 or (1012 not sure)
is there a newer version of GRUB (newwer than the one on the Hoary installation CD)

---

### Post by amohanty on 2005-09-01
What format is your /boot or if you did not have one what format is your / partition?

AM

---

### Post by rubenjavier on 2005-09-01
Ext2, but its way beyond the sector 1024 and apparently thats the reason GRUB can't install there too
but the real thing that I dont understand is why GRUB can install itself in some MBR and not in others??? they are just HDs not SATA or some RAID, just simple IDE HDs???
one wierd thing is that my MSI KT6V MoBo call IDE0=IDE1 and IDE1=IDE2, ther is no IDE0 in my MoBo even in the bios IDE0 its called IDE1??? are this the kind of things that affect GRUB?, even so the rest of the instalation recognaizes the HD as hd0
I really dont know whats happening
thanks in advance

---

### Post by banjo04414 on 2005-09-01
Do you have access to a Live CD with QtParted on It? Or Partition Magic 8.0 on Windows? If you do check out your partition info on them. Also, after Grub fails, do you go back to the menu for installation? Could be you are missing a step in setting up your partition. Just a thought.

---

### Post by rubenjavier on 2005-09-03
Yes I can see my partitions with partition magic 8.0, in both cases (when GRUB worked and when it didn't) I created a 10 Gig partition for Ubuntu and 500-1Gig partition for the swap, I've alwasy created them in any format (FAT32, NTFS etc) because the Ubuntu installer formated them to the right formats (Ext2 and Swap) and I allways create them as Logicals... the weird thing is that in the machines were the installation wroked till the end, the partitions now show at partition magic as Ext2 and Swap... but in the machines were the installation didnt went beyon the GRUB istall, pertition magic show those partitions as not formated... but the Ubuntu installer did formatted them and it even copied the Ubuntu files to them...

After GRUB fails I do go back to the menu installation and I've already tried all the posibilites, but GRUB doesn't want to install in any of the partitions or HDs, it allways reach the 50% on the progress bar an then gives me  the same error in any partition
Thanks in advance

---

### Post by amohanty on 2005-09-03
Have you tried not formatting the the partition(s) where you are installing ubuntu and let ubuntu partition and format them?

AM

---

### Post by rubenjavier on 2005-09-03
Actually Ubuntu allways format them... the first thing I do when I get to the Partitioning in the installation is make Ubuntu Format both partitions to their right format (Ext2 and SWAP), even when I try to reinstall I re-format the partition with the Ubuntu installer
Thanks in advance

---

### Post by amohanty on 2005-09-03
No. I meant remove the partitions completely befo rean ubuntu install.

AM

---

### Post by MySchizoBuddy on 2005-10-21
same problem doesn't install in floppy, or /boot or mbr nothing
my /boot is ext3 and has a boot flag on

---

### Post by rubenjavier on 2005-10-21
If you have a double boot system with windows you should remove the flag from the Ext3 partition... also this GRUB problem was solved for me since the Breezy Beta, then I upgraded to th eBreezy Final and Grub is still working OK

---

### Post by MySchizoBuddy on 2005-10-21
i guess my problem is the fact that i have a controller card. and that is just messing it up
I read the wiki of fakeraid and its complicated as hell

---

### Post by Herman on 2005-10-21
[http://ubuntuforums.org/showthread.php?t=79286](http://ubuntuforums.org/showthread.php?t=79286)     
   Did you fellows end up getting GRUB working properly yet? 
Check out the above link from the Breezy install help section.
 There's a new thing no-one much has tried yet that I know of, called 'GAG', the link pretty much explains it. I'm only raising your awareness of it since it looks like you are having so much troubles with GRUB. GAG might be worth a try. I'd be real interested to hear how you go if you do decide to try it. 
Basically, you must download the GAG file , unpack it, and copy the .iso to a CD. If you want, you can instll GAG to your MBR, but I haven't done that on my PC yet so far. You are supposed to be able to copy it to a floppy too.
You have to try it out and play with it a bit to see how it works before you install Ubuntu. Then when you install Ubuntu, you don't install GRUB. Instead you choose 'Go Back' and install Lilo to the new Ubuntu partition, (not your master boot record). When the computer spits out the install CD you swap your install CD for the GAG CD. When it boots for the first time you have to be ready and make it boot into the new system you are installing using the GAG CD. 
  Apart from myself, (I tried it and got it working yesterday), I haven't heard of anyone using it except isander, who first suggested it.
  It's too early to tell if it's going to be a good thing or not, but it's interesting. If you fellows are still having trouble with GRUB, you might like to try it and let us all know if you like it or not, and if it solves your problems. (Herman)

---

