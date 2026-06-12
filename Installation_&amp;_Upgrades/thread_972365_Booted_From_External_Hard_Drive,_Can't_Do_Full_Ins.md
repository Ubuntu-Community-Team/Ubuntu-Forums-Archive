---
title: "Booted From External Hard Drive, Can't Do Full Install on It"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by MTGap on 2008-11-05
Well I was able to successfully boot Ubuntu from an external hard drive through the 'Install into Windows' option on the CD menu while on windows XP. I'm now currently on Ubuntu, but only the demo part of it. I was asked to install when I first booted, but quit because it didn't give me my external hard drive as an option to install... It only showed the internal hard drive and an external hard drive used for backup.

So how exactly do I do a full install on the external hard drive? Everytime I try it never shows the desired external hard drive... So basically right now my only option is just running the demo right now.

I have partitioned my external hard drive into two parts one for Ubuntu, the other for Files. At least I can save documents on it, but I would like it so I can have settings and appreance stuff saved so having a full installation would be nice...


Any help would be appreciated! :)

---

### Post by Pumalite on 2008-11-05
Use an Ubuntu 8.10 Live CD. Boot from it. Install, go 'Manual' and choose the partition in your external where you want to install. At step 7, go to 'Advanced Tab' and change (hdo) for /dev/???, where ??? is your external drive. Once installation is finished, before rebooting, edit menu.lst and change 'groot' and 'root' to (hd0,0).
Then change boot order in BIOS to make USB 1st.

---

### Post by MTGap on 2008-11-05
That is risky in my opinion though and I already have all the files on my external hard drive, I just need a full installation... I used Wubi to get it on the external hard drive, on one partition of it. It didn't do a full install though, how do I do get a full installation..,


Right now everytime I turn the computer off the data is lost, besides on my second partition of the drive. I'm like running a demo as of now it seems... Any way I can get it to be full installation from within here... :)

---

### Post by zwygart on 2008-11-05
If you would be sure, delete your partition where you want to install and during installation chose install on whole free space or something like that. Pumalite gives a good suggestion. I have ubuntu Live CD and others operating systems on a USB flash drive and have successfully installed ubuntu 8.04 on a external harddrive from my flash drive. If you have trouble please write back, we will try to help you.

---

### Post by MTGap on 2008-11-05
Well, if I deleted it I would be able to boot back into it... All I'm saying is that the possibility for error at doing an installation from the Live CD would be risky with the amount of hard drives hooked up to my computer, and my dad won't let me disconnect them. 

So I used Wubi to put it on the external hard drive. Everytime I boot it up from the external hard drive it prompts me to install, and then goes to this partition thing where it shows a before and after and shows how they are going to be partitioning it, but I don't want to partition it, I already did.... 

Now though when I hit install it shows this (attached image) and I can't do anything at all in it, and when I hit forward it says error: root not defined, edit partitions, but I can't do anything in that window.... 


What do I do to install it from inside the external hard drive, I've considered other options like what you stated about the Live CD, but I find those too risky for me being a Linux newbie. 



So just to make this clear, when I boot up everytime I'm asked to install, but quit bc I don't want it on the drives it attempts to install on and it basically shows me a demo. I entered in a username and password in through Wubi, but I never actually login when I boot from the external hard drive, it just tries to install.

---

### Post by zwygart on 2008-11-05
First, you can't resize a partition which is mounted (where you can see files). 
I don't understand what you are doing. You boot windows and from there Ubunut trough Wubi? I never worked with wubi.

It will help me to help you if you paste the out put off fdisk -l.
Probably you will have to write 'sudo fdisk -l' in the terminal.
Then say on which partition you are, where you want the installed ubuntu and where de Datas are. 

If your drive has one empty place and it is there you want Ubuntu Choose install on free space.
If you had putted a partition where ubuntu should go and you don't have other's free spaces then delete this partiton and go like I said. It will be easier.

If I understand correctly, you already had partitioned. This 'dangerous' stage is done and you are save. The next point you have to be very carrefull is where you put de bootloader. At the end of the installation wizard (at step 7), go to 'Advanced Tab' and change (hdo) for /dev/???, where ??? is your external drive. Like Pumalite says.
Hopping this will help

---

### Post by MTGap on 2008-11-05
I guess your confused at what I did, technically Ubuntu is already on the external hard drive...

I'm not running Ubuntu with the CD anymore, just my external hard drive...

I put the CD in (While in Windows XP) and my friend told me that using Wubi would work and it did besides not being a full install. I selected Install into Windows and installed it on one partition of my external hard drive. Wubi then edited the boot.ini so there was an ubuntu option at the boot screen. Now when my external hard drive is plugged in I can hit Ubuntu at the boot screen and Ubuntu will load. 

Unfortunately it isn't the full installation, because nothing saves after I shut down and it is always prompting me to install. Do I have to go through with the Live CD? Or is there any way to do it now...

---

### Post by zwygart on 2008-11-05
How do you 'install' ubuntu. If I understand you clicked in Wubi on a option to install in a partition. To install Ubuntu you have to click the install in Ubuntu. I think your picture comes from there.
The installation of wubi only copies the content of the CD, so everytime is like if you boot from the CD.
Some questions to know if you have a full install :
1. At the root of the filesystem did you have a directory 'syslinux'? Inside the /boot directory did you have a directory called Grub?
2. Did you have a swap partition?
3. Ubuntu is it in a ext partition or a fat?

Please paste the output of 'sudo fdisk -l'. It will print the partitions off your computer and help to understand.

If you don't have a linux partition (ext2 or ext3) on your drive, probably  you only have a copy of the CD.

The picture you appended, if it is from the harddrive then you have a copy off the CD.
You have to install.
You can't install on the same partition from where you are running (it is to much difficult).
Use the LiveCD or install in another partition.
If you are not sure off anything write back.
N.B.: Poste the output off 'sudo fdisk -l' from the terminal.

---

### Post by MTGap on 2008-11-06
Ok well I'll just use the Live CD to install it on there...

Will this tutorial work? [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/")

How do I know which one is the correct external hard drive when I'm installing the boot loader

[IMG]http://www.pendrivelinux.com/wp-content/uploads/advanced.png[/IMG]

---

### Post by Pumalite on 2008-11-06
To find ot; run in the Terminal:
sudo fdisk -lu

---

### Post by MTGap on 2008-11-06
Ok well I knew it wasn't a full installation and so I just deleted those files and than tried it the way you said, like in the tutorial. Unfortunately at 76% my hard drive overheated and died...

I got the following error:

Errno 30 /target/boot/vmlinuz-2.6.27-7-generic

Underneath it said this is often caused by old hard drives, which it works in good condition. And that it could also be caused by overheating... Seeing as it is only a metal casing to cool it and spread out the heat, I say it overheated as it was going find until 76%...

Now my external hard drive won't show up in Windows XP.... It appears to be fried...

The power light is on, and I hear it rotating.... 


WTF! Happened my hard drive is fried... I have icepacks around it now... :mad:


Well I've been able to cool it down and now see it in my disk management, it still won't show up on the desktop though... There are two partitions on it now, the attached image shows it:


Should I just delete both partitions and start again? I don't know why it partitioned it, I selected guided - use entire disk

Oh and a funny thing is, when I look at the free space it is 100%, there is nothing on it... It was installing though, I could hear it and see the light flashing on the case.

---

### Post by Pumalite on 2008-11-06
Boot your Live CD and from the Terminal; post:
sudo fdisk -lu

---

### Post by MTGap on 2008-11-06
Why what does that do? There is currently nothing on the external hard drive. It is completely  blank on both partitions...

---

### Post by zwygart on 2008-11-07
For the partition where to install bootloader, boot choice (sda and sda1) should work. Personnaly I prefer sda1. The bootloader will be "unbreakable", easier to find if you made something wrong. 

I also had sometime problems during installation with harddrives. Especially when in installed 2 or 3 times. What I have done is wait at the next day and installation went well.

You have two partition because linux use one of them for a RAM extension called SWAP. It is the littler one. All that is normal.

At this state I suggest you to delete the two linux partitions (ext and swap), wait some hours computer off, then when it's cold boot and install. Probably it can help when you move it in a cold place or cool it down. 

For the fdisk -l or fdisk -lu command, it shows how the drives are arranged, space from the partitions, type, letter. It contains the same information than your picture from the drives with some more infos. Here an example :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Probably you will have to add sudo before the command.

---

### Post by MTGap on 2008-11-07
Okay well, I've booted from the External hard drive! After surrounding it with ice packs I was able to cool it down enough for it to properly install without overheating. I'm so happy that it is a full install...


Now there are a lot of updates: 39.6 MB

If I hit install will it install onto my external hard drive? Or will it accidently go to one of my other hard drives. There are 3 hard drives in total currently connected.

---

