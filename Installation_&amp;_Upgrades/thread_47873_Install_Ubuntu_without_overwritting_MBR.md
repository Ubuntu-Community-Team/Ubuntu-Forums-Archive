---
title: "Install Ubuntu without overwritting MBR"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by godsownman on 2005-07-10
I have recently connected a 2nd HDD and loaded Ubuntu  on it. After loading Ubuntu  on it I faced a problem.

The problem is that this particular HDD is too be used on more than 1 computer.

But what happens is that when it is disconnected I cannot load windows also. But on reconnecting it I can load any one.

I get an error " GRUB boot loader error " !

What I feel is the problem is that since I loaded linux after I loaded windows the MBR file got rewritten and now for that reason I need to have the 2nd hdd connected, to it even to start my computer and work in the windows environment.

I know this may sound a bit confusing but what I want to say is that when the 2nd HDD is connected I can choose which OS I want to load. BUT with the HDD disconnected I cannot work on the computer at all. The error I get is LIKE the 'BSOD' ( blue screen of death) but its not a blue screen.

Can somebody please help me.

What I feel is the  solution

 :)  Either I load windows after I load the Linux OS
 

Also,

When i was installing Ubuntu it asked me if I want to edit the MBR .Ofcourse at that Time I said yes but later on reading on the internet I realised that if probably I had said NO then it might have not edited the MBR but it would have written it on the 1st boot record of the partition.


Will it solve my problem and will i have the choice of loading Windows or Linux as an when I wish .

And most of all ,

Will I be able to remove the HDD where linux is loaded without upsetting the windows installation.


Thanks for the patience and the solution.

---

### Post by sooqing on 2005-07-10
if u want to install the xp mbr, boot using the xp cd and choose recovery mode.. at the prompt, type: fixmbr and ur mbr will be installed again..

on the other hand, if u want windows to choose whether u want to boot xp/linux, at linux:

type: dd if=/dev/hdb1 of=/dev/fd0 bs=512 count=1

to copy ur grub to diskette (edit it to suit ur purposes).. then edit the xp boot.ini to include this (after u copied from diskette to ur xp hdd) for booting..

---

### Post by mingus on 2005-07-10
As sooqing describes, just reinstall the W$ MBR on HDD1.  If you do not have a W2K/XP install CD, you can also do this with a W98/ME/DOS bootable diskette with the "fdisk /mbr" command.

Also, be sure to remember to switch the BIOS boot sequence.  You are now booting successfully from HDD2.  When you remove that drive, you need to tell the BIOS to use HDD1.  

The other technique you can use so that you do not need to change the BIOS, is to setup dual-boot from W$ boot.ini on HDD1.  This is what sooqing is describing (except that if you have the grub loader in the MBR of HDD2, then the command should be changed to "if=/dev/hdb").  There is a HowTo in the wiki on the change to make to boot.ini.

---

### Post by godsownman on 2005-07-11
Can somebody please explaint his to me in a simpler way with the exact steps.

I am only 4 days old to UBUNTU .



In lunix where should I type this line

type: dd if=/dev/hdb1 of=/dev/fd0 bs=512 count=1

and then what should I type in the  W$ boot.ini file.

Please help me.

---

### Post by godsownman on 2005-07-11
[QUOTE=sooqing]if u want to install the xp mbr, boot using the xp cd and choose recovery mode.. at the prompt, type: fixmbr and ur mbr will be installed again..

on the other hand, if u want windows to choose whether u want to boot xp/linux, at linux:

type: dd if=/dev/hdb1 of=/dev/fd0 bs=512 count=1

to copy ur grub to diskette (edit it to suit ur purposes).. then edit the xp boot.ini to include this (after u copied from diskette to ur xp hdd) for booting..[/QUOTE]

After repairing the MBR will it be back to normal .

Then can I load any other OS.

---

### Post by mingus on 2005-07-11
*After repairing the MBR will it be back to normal .*

Yes.

[I]type: dd if=/dev/hdb1 of=/dev/fd0 bs=512 count=1
and then what should I type in the W$ boot.ini file.[/I]

The command above needs to be modifed for what you want to do.  When you create the copy to the floppy, it needs to be a file that W$ can see.  And, the "if" (input file) portion of this command above depends upon where you installed the grub loader on HDD2.  If you installed it to the HDD2 MBR (which you probably did), the command would use "hdb" without the number "1".

If you google "dual boot windows linux" you will find many flavors of instructions.  Here is a short form:
1.  Boot into Ubuntu.
2.  Insert a clean formatted (with DOS or FAT) floppy disk into the drive.
3.  Mount the floppy:  $sudo mount /dev/fd0 /media/floppy
4.  Copy the installed grub loader (again assuming the HDD2 MBR):  
$sudo dd if=/dev/hdb of=/media/floppy/ubuntu.bin count=512 bs=1
5.  Umount the floppy:  $sudo umount /dev/fd0
6.  Remove floppy and boot into Windows
7.  Insert floppy; use Explorer to copy ubuntu.bin to c:\
8.  Open c:\boot.ini with Notepad
9.  Add this line to the end:  C:\ubuntu.bin="Ubuntu"
10. Save boot.ini
11. Reboot

Windows will now present a menu with XP and Ubuntu.  When you choose Ubuntu, it should load grub from which you can boot into Ubuntu.  This is called "chain-loading" (where one boot loader hands off to another).

Note:  There is a possibility that when you choose Ubuntu from the W$ boot menu, you may get a grub error.  If you do, just post that back here and we will fix that.

*Then can I load any other OS*

Not sure what you mean by this.

---

