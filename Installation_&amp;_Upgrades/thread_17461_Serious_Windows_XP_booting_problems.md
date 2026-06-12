---
title: "Serious Windows XP booting problems"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by Bondings on 2005-02-28
I have a hard disk partitioned into 2 partitions. On the first there is windows xp home edition. I installed Ubuntu on the second partition (with a swap) and ubuntu partitioned that one. Ubuntu loaded fine and except for a few problems like the sound everything went fine. But I suppose you can already guess what happened: Windows XP doesn't want to boot anymore. And I really need it for the university and other things. The files and everything are still there as I saw from the live cd.

My computer is a new laptop Toshiba Sattelite A 60.

I get the following message when I want to start windows:

Booting 'Windows NT/2000/XP'
root(hd0,0)
  Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

I tried to edit the menu.lst and replaced the root with rootnoverify(hd0,0). I didn't get the "Filesystem..." error, but windows still didn't load.

There is no option in my bios, at least not that I know of, that let you change the hard disk from auto to LBA or something like that.

I tried "unhide(hd0,0) hide (hd0,1) boot" but the only thing that happened was that I got an error (17 I think) and I had to reinstall ubundu again. I should have used the e button to change it.

During the installation, I had to choose to install grub in the MRE (or a name like that, I'm not used to those names) or on the hard disk, but for a dual boot system it would be better to install it on the MRE and it displayed windows xp. I chose the MRE option, but maybe I should have installed it on the hard disk.

What should I do? 
Reinstall grub? How? 
Install Lilo? How?

The only thing I want now is to boot windows. At the moment I don't have the windows cd, I can only get it in the next weekend. Keeping Ubundu or reinstalling it on a better way (maybe partition the disks before installation and not with ubundu) would be cool, but windows xp is what I need the most.

I hope you can help me with my problem. I don't want my first experience with linux to be this way.  :(

---

### Post by jdodson on 2005-02-28
please run a forum search, this is a very common problem and other threads can help you.

---

### Post by Bondings on 2005-02-28
[QUOTE=jdodson]please run a forum search, this is a very common problem and other threads can help you.[/QUOTE]

I know this is a very common problem. I noticed it. I was looking for a solution on the internet and on this forum for at least 8 hours. And I still didn't find a solution that worked. I reinstalled Ubuntu at least 4 times. I'm not someone who immediately asks a question when I experience a litle problem. But for me this is a giant one. I wanted to try out linux and I cannot even boot to windows anymore.

---

### Post by Olli on 2005-02-28
I have a triple boot system with XP, SUSE Linux 9.2 Professional, and Ubuntu (that I love!). I have never had any difficulties with Ubuntu grub nor with SUSE grub. Also your menu.lst seems to be just OK.

You may write in the consol 

      cfdisk /dev/hda

The first line should be

/dev/hda1  Boot    Primary    NTFS   []  .... (this is for the size of the partition)

If not, you should make the hda1 partition Bootable.
Hope this will solve your problem. If not I am at a loss.

---

### Post by Olli on 2005-02-28
Sorry: I forgot to tell that the boot manager is installed in the MBR of the first hard disk (hda).

---

### Post by Bondings on 2005-02-28
[QUOTE=Olli]I have a triple boot system with XP, SUSE Linux 9.2 Professional, and Ubuntu (that I love!). I have never had any difficulties with Ubuntu grub nor with SUSE grub. Also your menu.lst seems to be just OK.

You may write in the consol 

      cfdisk /dev/hda

The first line should be

/dev/hda1  Boot    Primary    NTFS   []  .... (this is for the size of the partition)

If not, you should make the hda1 partition Bootable.
Hope this will solve your problem. If not I am at a loss.[/QUOTE]

I get a whole table when I type it in the root terminal. But there was such a sentence. 

I couldn't copy paste it as in windows so I tried it again and now I get an error. I typed in cfdisk /dev/hda1  instead of hda by mistake.
Maybe this is going to help. :) 

I get:
FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk
Press any key to exit cfdisk.

---

### Post by kevinlyfellow on 2005-02-28
what is your partition table?

---

### Post by Bondings on 2005-02-28
[QUOTE=kevinlyfellow]what is your partition table?[/QUOTE]

Here is what I get when I type in cfdisk /dev/hda :

cfdisk 2.12


Disk Drive: /dev/hda
Size: 40007761920 bytes, 40.0GB
Heads: 16 Sectors per Track: 63 Cylinders: 77520

Name Flags PartType FS Type [Label] Size (MB)
-------------------------------------------------------------------------------------
hda1 Boot Primary NFTS [] 20003,89
hda2         Primary Linux ext3 19490,89
hda5         Logical Linux swap 513,00


Bootable ....
Quit ...

---

### Post by Bondings on 2005-02-28
I'm going to install everything again, including grub and I won't install grub on the MBR, instead on the /boot directory. I read it somewhere on the internet.

I hope this will work. ](*,)  ](*,)

---

### Post by Gary Powers on 2005-02-28
Bondings, I went through this problem yesterday and resolved by going into SETUP and changing the hard drive setting from AUTO to LBA.  It was that simple for me and hope it will help you.

Gary

---

### Post by Bondings on 2005-03-01
[QUOTE=Gary Powers]Bondings, I went through this problem yesterday and resolved by going into SETUP and changing the hard drive setting from AUTO to LBA.  It was that simple for me and hope it will help you.

Gary[/QUOTE]

I already heared of this and according to what I read, it solved the problem for many people. But I don't have that option in my BIOS. You mention SETUP. Is there maybe another way to change it, I mean not in the BIOS?

The thing to store grub on another part, not on the MBR, didn't work out for me.  :cry: 

I suppose I'll just have to errase linux and repair or even reinstall windows again. :sad: 

Can someone tell me how to install LILO? I saw it in the installation of Ubuntu, but I got an error when I clicked on it. Do you have to click on the Esc button when Grub is beginning to install and then click on the LILO button or is there another way?

---

