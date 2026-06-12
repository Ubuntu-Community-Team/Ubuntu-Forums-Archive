---
title: "New PC - Dual Boot - Partitioning"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by c1courtney on 2005-05-05
This is a bit of a newbie question but I'll go ahead and ask.

I'm building an HTPC and I want it to be a dual boot machine w/ Win MCE 2005 and ubuntu w/ MythTV installed as I'm not too sure which I'll be going with in the long run. 

I want the following partitions on a 300GB SATA drive

Win MCE (NTFS as it's XP based) - 150GB
/ (Not sure how much I need - Guess whatever's left after the other partitions are decided)
/root - (Not sure how much I need)
/swap - 1 GB
/ringbuffer - 8 GB (For MythTV's Live TV Buffering)

So my questions are what should I use to make the partitions and what types of partitions would you suggest for the Linux partitions?

I've burned the ISOs for Ubunto 5.04 Install and Live CDs.  I'm use to install CDs immediately wanting to partition the HDD but it doesn't seem to be the case with Ubuntu am I missing something?

Should I boot with the Live CD and make my partitions and then go in and install Win MCE and then go back and install Ubuntu and use Grub? 

Would you suggest more partitions (or less)?

I use to be a Linux person but lost interest about 5yrs ago when I got married so my memory is a bit foggy.  I like the premiss of Ubuntu (not having to download ever source from ever location on the planet to get something to build and work has it's advantages.)

Searching on the web has yeilded a lot of 'see Ubuntu's installation guide, yet I can't find much and creating partions when going through the twiki docs.  Am I missing something.

CCourtney

PS: I intend to use GRUB for booting

---

### Post by sprucio on 2005-05-05
Install XP first and then install Ubuntu. It should pickup the existing partition. Then you can create the other three as you go along. You'll definetly need a root and a swap partition. Root partition is like your C:\ so leave lot's of room. The swap partition is usually double the amount of your ram.

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=c1courtney]This is a bit of a newbie question but I'll go ahead and ask.

I'm building an HTPC and I want it to be a dual boot machine w/ Win MCE 2005 and ubuntu w/ MythTV installed as I'm not too sure which I'll be going with in the long run. 

I want the following partitions on a 300GB SATA drive

Win MCE (NTFS as it's XP based) - 150GB
/ (Not sure how much I need - Guess whatever's left after the other partitions are decided)
/root - (Not sure how much I need)
/swap - 1 GB
/ringbuffer - 8 GB (For MythTV's Live TV Buffering)

So my questions are what should I use to make the partitions and what types of partitions would you suggest for the Linux partitions?

I've burned the ISOs for Ubunto 5.04 Install and Live CDs.  I'm use to install CDs immediately wanting to partition the HDD but it doesn't seem to be the case with Ubuntu am I missing something?

Should I boot with the Live CD and make my partitions and then go in and install Win MCE and then go back and install Ubuntu and use Grub? 

Would you suggest more partitions (or less)?

I use to be a Linux person but lost interest about 5yrs ago when I got married so my memory is a bit foggy.  I like the premiss of Ubuntu (not having to download ever source from ever location on the planet to get something to build and work has it's advantages.)

Searching on the web has yeilded a lot of 'see Ubuntu's installation guide, yet I can't find much and creating partions when going through the twiki docs.  Am I missing something.

CCourtney

PS: I intend to use GRUB for booting[/QUOTE]
 My suggestion is: install Windows first, creating 150 GB partition for it and leave the rest of the disk unpartitioned (or you can parition it any way you like - doesn't matter). After that, install Ubuntu. During installation you can specify partitions - tell it to leave windows partition alone and repartition the rest the way you want it. Your defaults seem reasonable.

---

### Post by mrbob33 on 2005-05-05
Hello, my first post here!

I didn't want to start a new thread as there are enough on this topic, I think.


What I have is two hard drives, 160 sata and 160 IDE, with Windows XP installed on SATA. IDE drive is currently completely empty. Both drives are set to master, as they are not on the same bus. I've set boot priority to SATA naturally.

Now, what would be the best way to install Ubuntu on IDE, while keeping XP operational? I've searched these forums without finding clear answer. Where should I install Grub and is there some files I need to modify to enable dual booting?

Or could it be possibly to boot Ubuntu with Windows boot loader? 

Thank you in advance!

---

### Post by c1courtney on 2005-05-06
Mr Bob,

Good question and I've thought about doing it myself (ripping one of my older 120GB IDE drives out and tossing it in my HTPC and having it as my Linux drive.)

Unless I'm mistaken Linux only sees partitions and doesn't see what physical disks they are.

With that I believe you can install Ubunto on the second drive and install grub over the MBR of the primary drives primary partition (i.e. your 160GB Sata w/ Windows on it) 

Confirmations anyone?

CCourtney

---

### Post by mrbob33 on 2005-05-06
[QUOTE=c1courtney]

Confirmations anyone?

CCourtney[/QUOTE]

Yes, confimation anyone? I wouldn't like to mess up my Windows installation.

---

### Post by RaffiRai on 2005-05-06
I suggest setting your boot order to CD, IDE, SATA, and install ubuntu using GRUB on the IDE.  Grub will detect Windows on the SATA, and install into the MBR, setting up the dual boot itself.  If you want Windows are your default boot then edit the GRUB file and paste the windows bit over the Ubuntu boot options.

---

### Post by mrbob33 on 2005-05-07
[QUOTE=RaffiRai]I suggest setting your boot order to CD, IDE, SATA, and install ubuntu using GRUB on the IDE.  Grub will detect Windows on the SATA, and install into the MBR, setting up the dual boot itself.  If you want Windows are your default boot then edit the GRUB file and paste the windows bit over the Ubuntu boot options.[/QUOTE]

Thank you! That worked. I installed Ubuntu and Grub to IDE and set boot priority as you said. All I had to do was add  

```
map (hd0) (hd1)
map (hd1) (hd0)
```

before Windows XP chainloader command on menu.lst to get Windows load.

---

