---
title: "UBUNTU on FAT 32"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by Hammad on 2005-08-16
Hi

  I am knew to this UBUNTU craze and UBUNTU forum as well.I am from Lahore, Pakistan and i just attended Free and Open Source Software Awareness Campaign organized by our University and there main Focus was UBUNTU and i got damn excited about that UBUNTU stuff after attending that.

I am currently running Windows Xp with FAT32 file system on my 80GB hard disk
1)Is it possible to install Ubuntu Hoary Hedgehog 5.04 on FAT32.
2)How can i install Ubuntu Hoary Hedgehog 5.04 on the same partition as Windows Xp i.e C:\ leaving the file system unchanged i.e FAT32...plz tell me the detailed procedure...

Thanx 
cRaZy aBoUt uBuNtU  \\:D/ 
Hammad

---

### Post by GavinX on 2005-08-16
[QUOTE=Hammad]Hi

 I am knew to this UBUNTU craze and UBUNTU forum as well.I am from Lahore, Pakistan and i just attended Free and Open Source Software Awareness Campaign organized by our University and there main Focus was UBUNTU and i got damn excited about that UBUNTU stuff after attending that.

I am currently running Windows Xp with FAT32 file system on my 80GB hard disk
1)Is it possible to install Ubuntu Hoary Hedgehog 5.04 on FAT32.
2)How can i install Ubuntu Hoary Hedgehog 5.04 on the same partition as Windows Xp i.e C:\ leaving the file system unchanged i.e FAT32...plz tell me the detailed procedure...

Thanx 
cRaZy aBoUt uBuNtU  \\:D/ 
Hammad[/QUOTE]First of all, let me welcome you to the world of Ubuntu. It's great that your University organized such campaign. Kudos to your Institution.

Secondly, you cannot install Ubuntu on a FAT32 partition. FAT32 file system is designed for and used by Windows OS. You will need to repartition your hard drive and devote some space to Ubuntu (preferably not less than 3 gigs). You can use Partition Magic to do it. Partition Magic will allow you to create a Linux partition (Ext2 or Ext3, these are Linux type partitions).

This brings me to your second question about installing Linux on the same partition as Windows XP. Simply put, no it cannot be done. When you repartition your drive and install Ubuntu, it will automatically place Windows XP into GRUB boot manager and allow you to dual boot Ubuntu and Windows XP. In other words, XP will not be erased once your drive is partitioned and XP will be left as is. What will happen is that you will be able to access your XP partition from Ubuntu and possibly access Ubuntu from XP.

Cheers,
GavinX

---

### Post by Hammad on 2005-08-16
Hey 
Thanx GavinX for so quick reply

GavinX plz plz plz plz elaborate the second one in my last post.i mean put it in points and detail and these few points too as i am new to this...i hope you don't mind

1)what is the file system that both will support and which operating system to install first to dual boot Ubuntu and Windows XP.
2)after partition will i lost all of my data i mean i know that i will lost all data in C:\ what about D,E,F will i lost those too ??? as in DOS or in XP when you partition using  FDISK all the data in ur hard drive losts...i would certainly install Ubuntu now if the data only in C losts but if the partition removes data in all of my drives then i have to wait for few days to get my 20GB hard disk to experiment on  :mad: .....

Do I Speak Much or What  ;-) 

Cheers 
Hammad

---

### Post by DancingSun on 2005-08-16
[QUOTE=Hammad]Hey 
Thanx GavinX for so quick reply

GavinX plz plz plz plz elaborate the second one in my last post.i mean put it in points and detail and these few points too as i am new to this...i hope you don't mind

1)what is the file system that both will support and which operating system to install first to dual boot Ubuntu and Windows XP.
2)after partition will i lost all of my data i mean i know that i will lost all data in C:\ what about D,E,F will i lost those too ??? as in DOS or in XP when you partition using  FDISK all the data in ur hard drive losts...i would certainly install Ubuntu now if the data only in C losts but if the partition removes data in all of my drives then i have to wait for few days to get my 20GB hard disk to experiment on  :mad: .....

Do I Speak Much or What  ;-) 

Cheers 
Hammad[/QUOTE]
[list=1]
[*]Ubuntu and XP can both READ and WRITE to FAT32.  BUT, Ubuntu can only be installed on the Linux file systems (ext2, ext3, reiser...etc.).  This means Ubuntu and XP have to be installed on separate partitions with their own filesystems.  Install XP first, then install Ubuntu.
[*]You can resize FAT32 using the Ubuntu installation CD.  Below is some brief instruction.
[/list] 

The following steps are shamelessly taken from varunus, as he's taken his time to type this out, and I'm too lazy :-P:

1. Insert the install CD. Reboot and boot from CD.
2. Press enter at the boot prompt, no special options needed.
3. Choose your language, keyboard layout, etc.
4. Ubuntu may go through some network config, you can do it here, or skip it if you don't understand and do it later.
5. When it asks you about partitioning, choose MANUAL PARTITION!!!
6. Follow this guide: [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
This will guide you through shrinking your XP partition and creating a new one for Ubuntu with NO DATA LOSS.
7. Continue the rest of the install, fairly easy (create a user, set the password, reboot)

---

### Post by GavinX on 2005-08-16
What you need to do is to leave Windows XP installed. It is good that it is already installed so you need not worry too much here. WHat you need to do now is to run the disk defragmenter so that the data which you have on Windows XP can be moved to the front of the drive. Now, get a copy of Partition Magic (preferably any version after 7) and install it in Windows XP. After you have done that fire up Partiton Magic and create Linux partitions (this options is located somewhere in the Partition Magic menu (can't remember exactly where since it has been some years since I've used Partition Magic). As I said before, create at least 3 gig. It could be more, depending on how much you want to give to it. After you've done, just place in the Ubuntu CD and reboot your computer and follow the onscreen prompts from Ubuntu. When it asks where to install Ubuntu, it will tell you that it has located Linux Partitions. Just click these and Ubuntu will do the rest. After the installation process, you just remove the CD and reboot and you'll have Ubuntu and Windows installed and you can choose which to boot!

---

### Post by GavinX on 2005-08-16
[QUOTE=DancingSun]

[list=1]
[*]Ubuntu and XP can both READ and WRITE to FAT32. BUT, Ubuntu can only be installed on the Linux file systems (ext2, ext3, reiser...etc.). This means Ubuntu and XP have to be installed on separate partitions with their own filesystems. Install XP first, then install Ubuntu.
[*]You can resize FAT32 using the Ubuntu installation CD.  Below is some brief instruction.
[/list]
The following steps are shamelessly taken from varanus, as he's taken his time to type this out, and I'm too lazy :-P:

1. Insert the install CD. Reboot and boot from CD.
2. Press enter at the boot prompt, no special options needed.
3. Choose your language, keyboard layout, etc.
4. Ubuntu may go through some network config, you can do it here, or skip it if you don't understand and do it later.
5. When it asks you about partitioning, choose MANUAL PARTITION!!!
6. Follow this guide: [http://www3.telus.net/linux4u/ubuntu.html]("http://www3.telus.net/linux4u/ubuntu.html")
This will guide you through shrinking your XP partition and creating a new one for Ubuntu with NO DATA LOSS.
7. Continue the rest of the install, fairly easy (create a user, set the password, reboot)[/QUOTE] As DancingSun said, it can also be done in this way. I was trying to let you use a nice graphical interface with Partition Magic as lots of people tend to be afraid of Manual Partitioning using the Linux CD. But this process wouldn't hurt. As a matter of fact, you may find it simpler than Partition Magic. Thanks much DancingSun.

---

### Post by Hammad on 2005-08-16
Thanx DancingSun

What about this idea tell me is it possible plz...........which i have given below 

I have 2 hard drives attached to my computer 20GB (Primary Master) & 80GB (Secondary Master) i use my 20GB harddisk for my operating system I.E Windows Xp only and 80 GB for my data...i just wanted to ask about the possiblity that


[COLOR=SandyBrown]1)TELL ME THE PROCEDURE OF MAKING MY 20GB(WHICH I WILL SET AS PRIMARY MASTER) DUAL BOOT DRIVE I MEAN I WANT TO RUN BOTH XP AND UBUNTU. [/COLOR]
[COLOR=SandyBrown]
2)IF I PARTITION MY PRIMARY 20GB TO 2 EACH OF 10GB THEN IS IT POSSIBLE TO ACCESS DATA ON MY 80GB(SECONDARY MASTER) WHICH IS FAT32 FROM BOTH UBUNTU & WINDOWS XP [/COLOR]

and 1 more thing in what manner should i partition my 20GB hard disk i mean 2 partitions of 10GB are OK ?...and what should be the file system of both...........

i hope it is not messy for you ppl to understand what i want to do
Do tell me is it possible or not IF YES THEN PLZ PLZPLZ TELL ME THE PROCEDURE.

bYe

---

### Post by Hammad on 2005-08-16
Oh GOD
 
       Confusions...Confusions...Confusion.......

1 more confusion if all the above stuff which i said worked where will UBUNTU show my SECONDARY MASTER (80GB)

I mean durring UBUNTU setup i don't want to connect my 80GB(FAT 32) will it detect my 80GB if i attach it to my PC after UBUNTU is installed ? if yes then where will it show it ?


bYe

---

### Post by DancingSun on 2005-08-16
What do you mean by data?  Are these just archives, text files, music files, and video files?  Or would it include software programs and applications and settings?  If it's just for data files, then this can be much easier.  But I'll need the answer before I can guide you through.

Generally, I would not recommend mixing Windows applications and Linux applications in one partition.  Especially on a FAT32 partition.  FAT32 is not a journalized file system, and if you are familiar with Win95 or Win98, you'll know that they frequently fall victim to lost clusters and corruptions.  Unless you need to edit a file from BOTH Windows and Ubuntu, you can do just fine without the use of a FAT32 partition.

Ubuntu can READ files in NTFS partitions.  For example, if you have a movie file in the NTFS partition, you can just mount the Windows partition, and double click on that movie file and Ubuntu will play it.  On the Windows end, I know that there are some open source 3rd party programs that allows you to read a variety of Linux file systems from Windows.

---

### Post by Hammad on 2005-08-17
Hi
       By data i mean everything i have(SETUPS,SONGS,MOVIES,DOCUMENTS....ETC) EXCEPT the software which i will install after the installation of UBUNTU and WINDOWS.

AS I TOLD YOU THAT I AM HAVING 2 HARD DISKS 1 OF 20GB & 2ND OF 80GB

JUST TELL ME WHAT DO I HAVE TO DO TO INSTALL UBUNTU & WINDOWS ON MY FIRST HARD DRIVE ?

I WANT TO PARTITION MY 20GB TO 2 10GB PARTS 1 FOR UBUNTU & 2ND FOR WINDOWS leaving nothing for any software i mean as i have 2nd hard drive as Secondary Master i will save everything there.
Please Guide me through this
1)How to create partitions for Ubuntu & Windows Xp ?
2)Which OS to install first ?
3)What file system should i partition with (i want to create 2 partitions for 20GB 10 each tell me what file system should i use for both as there will be XP on 1 and UBUNTU on 2nd ?
and please do not refer me to this link [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
as i need you to guide me

thanx

bYe
4)

---

### Post by DancingSun on 2005-08-17
I'm only going to tell you how to install both XP and Ubuntu on the 20GB harddisk.  Leave the 80GB HDD disconnected.  When you reconnect the 80 GB HDD Ubuntu will not show the HDD, instead, you need to manually mount it. To do that, do a search in the forums on "adding a second HDD".

There are quite a few dual-boot how-tos in this forum.  I'd encourage you to read those as well, as I do not want to repeat to much of what is already said.  Do your own research, and make your own decisions.  No step-by-step instruction is fool proof, if you're looking for that, it doesn't exist.

These are essentially the steps that I took to setup my dual-boot XP-Ubuntu computer:
[list=1]
[*]Install Windows.   Just follow the onscreen instructions to partition and install Windows. If you can, have Windows take only the first 10GB if the HDD. If not, don't worry, the Ubuntu Installation can resize the partition for you.  I'd recommend NTFS as the file system.
[*]Follow these instructions to install Ubuntu:
[list=a]
[*]Insert the install CD. Reboot and boot from CD.
[*]Press enter at the boot prompt, no special options needed.
[*]Choose your language, keyboard layout, etc.
[*]Ubuntu may go through some network config, you can do it here, or skip it if you don't understand and do it later.
[*]When it asks you about partitioning, choose MANUAL PARTITION!!!
[*]Follow this guide: [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
This will guide you through shrinking your XP partition and creating a new one for Ubuntu with NO DATA LOSS.
[*]When the Ubuntu installer asks for installing GRUB to the master boot record (MBR), allow it to do so.
[*]Continue the rest of the install, fairly easy (create a user, set the password, reboot)
[/list]
[/list]

There really isn't much to the installation process.  Don't be afraid.  You originally said that you had a XP installation on the 80 GB HDD.  Keep it there.  If you have data on the 20 GB HDD that you don't want to lose, copy it over to the 80 GB HDD.  That way, if you screw up on the 20 GB, you can try again knowing your stuff is still on the 80 GB HDD, and if you need a working computer before you can get your dual-boot setup running correctly, just boot off of that 80 GB HDD.

---

