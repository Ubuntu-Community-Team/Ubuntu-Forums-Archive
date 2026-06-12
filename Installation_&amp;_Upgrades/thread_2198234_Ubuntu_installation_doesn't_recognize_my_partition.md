---
title: "Ubuntu installation doesn't recognize my partitions"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by haydenlueck on 2014-01-07
So, I won't go super into detail about the back story here, but long story short I accidentally installed Ubuntu 13.10 overtop of everything (both my broken installation of 13.04 which failed during upgrade, and my copy of Windows 8.1 which had lots of stuff on it that I lost.)

After screwing around, reinstalling Windows, and getting things back to somewhat near where they used to be, I decided to repartition my hard drive and reinstall Ubuntu alongside it. I made a 150GB partition on my 1.5TB hard drive, and rebooted to start off the installation. Any other time I've installed I've done it exactly as shown in [this video]("http://www.youtube.com/watch?v=wNCSbTyUzoM"), but once to I got to the part where you create the swap and whatnot, it didn't recognize my partitions. It just showed my hard drive as free space and that's it. [Picture here.]("http://i.imgur.com/h6JaTK6.jpg") It looks like I'm having the exact same issue the guy in [this thread]("http://ubuntuforums.org/archive/index.php/t-1746869.html"), but I'm not exactly sure what the guy's instructions were to fix it, and I'm too scared to do anything as long as I don't know what I'm doing (I really don't want to have to restart another time. Reinstalling and setting up Windows took super long.)

Should I be running FixParts from Windows? If so, how do I run it? I have the program but it's just an .exe that doesn't seem to take any of the commands, even the ones it mentions. I'd really like to get Ubuntu back on my machine but I'm not willing to uninstall Windows for it as Windows still is my primary OS.

Also, you'll have to excuse my noob-ness as that will definitely show. I'm not a huge expert, but I've been trying to get into Ubuntu lately, and as long as I can't install it that won't be easy.

---

### Post by tfrue on 2014-01-07
This could be a slew of things, so I will begin by asking does your computer support UEFI, secure boot, and fast boot? If you're not sure, then how old is the computer? You have 8.1 so I'm assuming it's within two years which supports UEFI, so I would give these articles a read but what you will generally do is disable secure boot and install Ubuntu that way.

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Let's start there and see where we go.

---

### Post by haydenlueck on 2014-01-07
That post looks like a pretty big hodgepodge of stuff.

Should I follow [this]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") tutorial?

edit: oh, also. I built my computer so I'm not entirely sure what of those things you listed it supports. I mean, I've installed Ubuntu before, so I don't know if that helps.
Here's my build:
[http://pcpartpicker.com/p/2wku5](http://pcpartpicker.com/p/2wku5)

---

### Post by haydenlueck on 2014-01-07
Okay, so I tried following that tutorial and when I got to step 4 there were no UEFI Firmware Settings. So I guess it doesn't support UEFI?

---

### Post by tfrue on 2014-01-07
You can try, but I would still read through the article I gave you and find the header that is closest to your problem and read from there. In the tutorial you posted, in step 4 towards the end it says hold shift when you boot, I'm not sure if that will let you edit the UEFI options and if it doesn't, you should still be able to edit them through the BIOS

---

### Post by haydenlueck on 2014-01-07
I couldn't find the secure boot settings anywhere. When I go into advanced settings in my BIOS it has a big "ASUS UEFI BIOS" at the top, but I couldn't find anything in there. I really don't know what I'm looking for.

I mean, the thing is I don't really know what my issue is. Like I said in the OP, [this]("http://i.imgur.com/h6JaTK6.jpg") is happening and I don't want it to. Nothing in the post mentions that, and I don't know what I'm looking for. What I've said is about all I know.

---

### Post by haydenlueck on 2014-01-07
Okay so I found [this]("http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi-2.html#post191536") post, but when I go into the "boot" menu there's no "Secure Boot" option for me.

---

### Post by tfrue on 2014-01-07
Sorry for the long wait, I was doing a lot of reading about GPT, MBR, and other related stuff. Would you be so kind and post the output of ```
sudo gdisk -l /dev/sda
``` If it's not installed, then install it using ```
sudo apt-get install gdisk
```

---

### Post by haydenlueck on 2014-01-07
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer:

---

### Post by tfrue on 2014-01-08
I don't think fix parts will work, because it doesn't address the GPT partition, just the MBR, but then again I have never used nor heard of it, just what I read now on the page. 

Just a tid bit of information, your motherboard supports UEFI, so that means that it does support GPT and will boot an OS with secure boot from GPT. The GPT uses a protective MBR sector that will allow you to boot legacy OS's that don't support GPT so that is why there is a present MBR and GPT partition. 

Ok, so I'm going to try and write down everything that is going through my brain so I can explain it and so I can make sure that I'm on the right path. Let's begin.

The reason why we are using gdisk, rather than fdisk, is because you are using a GPT partitioning, rather than MBR partitioning, but GPT uses the first logical block adress (LBA) as an MBR, called the "Proctecive MBR," so you can still boot into systems that don't support GPT. Fdisk cannot see the GPT partitions so we use a partition tool that can, which is gdisk,

This may get extensive, so bear with me please.

A few commands that I would like to see are:
```
sudo gdisk /dev/sda
p
#This is a long part
type: i
1
i
2
i
3
i
4 #Or how ever many partitions are shownt
```
This will help me determine which is your GPT partition and which is your MBR. 

So after you installed 13.10 for the first time, then reinstalled Window's, how did you do re install? Did you format the drive and use the entire disk, and let the Window's installer do the work? When you created the 150GB space. did you format it as NTFS, or delete a primary partition? Did you use the Disk Management to create the empty space in Windows? 

Sorry for all the questions and randomness, I'm just trying to make sure I've got the whole picture friend.

Thanks,
Chris

---

### Post by tfrue on 2014-01-08
Also, would you post the output of ```
sudo fdisk -l /dev/sda
```

What I'm trying to determine is if your disk is seeing the GPT disk while using fdisk. I know I have you doing almost the same thing with gdisk, but the difference is the fdisk is for MBR, and you have both so fdisk will tell us the type of partitions you have so we can see if it's GPT or MBR. 

And if it's MBR, then we can possibly wipe out the GPT data, and use only the MBR, then maybe do more partitioning to get Ubuntu installed.

---

### Post by haydenlueck on 2014-01-08
I don't know if this will help. It did the same thing for every time I typed "i".
```
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: p
Using GPT and creating fresh protective MBR.

Command (? for help): i
No partitions

Command (? for help): 1
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): i
No partitions

Command (? for help): 2
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): i
No partitions

Command (? for help): 3
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): i
No partitions

Command (? for help): 4
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): i
No partitions


```

> **tfrue said:**
> So after you installed 13.10 for the first time,  then reinstalled Window's, how did you do re install? Did you format the  drive and use the entire disk, and let the Window's installer do the  work? When you created the 150GB space. did you format it as NTFS, or  delete a primary partition? Did you use the Disk Management to create  the empty space in Windows? 


After I reinstalled 13.10 I simply threw the disk in, rebooted, and the Windows installer had all of my partitions and I ended up having to format the first partition (can't remember what it was called. Main or something?) and delete all of the other ones because Windows couldn't be installed to them.
When I created the 150GB partition I did it just as shown in the video I linked earlier. I shrunk the volume of my main partition.

As for the second thing you wanted me to paste:
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf81e1af7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  2623074303  1311433728    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 


```

Oh, by the way. Thank you so much for all of your help. Even if I don't get this fixed, I really appreaciate all of the time you're putting into helping me.

---

### Post by tfrue on 2014-01-09
I just finished wrting the bottom portion of this huge post, and I would really like to look at your boot-info of your computer.
You first need to install boot-repair, so type:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```
enter
Type:```
sudo apt-get install -y boot-repair && (boot-repair &)
```
enter again
After it's finished installing, type:```
boot-repair
``` and select the second option, make sure you are connected to the internet and post the url that you are given here so I can look at your boot-info.

You can wait to do all this that I typed, but I spent too long writing all of it to just erase it, because I still think that that is what we will have to do anyway, but I would like to make sure that we have all of our cards on the table before we continue.

 The video showed how to create a dual boot with a virtual machine, and this normally would work, and I hate that I can't point you to an article or anything, but that's completely different and a wild animal. One thing to note, when he did the live boot, it booted right to the purple Ubuntu screen. So that means he either didn't use EFI boot, or the live OS was not 64bit. So that means that his BIOS is using legacy boot, then again he was using a VM. But the same principle applies, that you will get a purple screen if legacy boot is on, or you will get a screen asking about your boot options if you are using EFI boot.

Is the Win 8 version you are using 32/64 bit? What about the Live boot being 32/64 bit?

I've determined that you can only use a GPT partition with Win 8, I don't think you can even install with MBR so that means that you are probably using a GPT disk. The reason that I'm making a big deal about GPT, MBR, and UEFI is because it will make a difference depending on how the BIOS is set to boot, if you are using GPT, which you probably are, then the partitioning will be different than the video I believe. And depending on if you want secure boot or use EFI rather than BIOS boot.

What my end goal is with you, is to get your HDD to use GPT with a protective MBR, and install Ubuntu using EFI as the boot option.

The reason I wanted to see the output of ```
sudo fdisk -l
``` earlier was to see if the disk identifier was "0xee" That would've meant that you are using GPT with a protective MBR, but you are not. I'm thinking that you have a a Valid GPT partition, but something went wrong with the MBR, or when you tried to install linux it went wrong and might have messed up the MBR. I'm not too sure. But there are a few things I would like for you to try but they will take some time, maybe. 

I do suggest backing up your data from the Win side because any time that you play with your partitions you are likely to mess something up and loose everything. So again, back up your important files.

The first thing I would like for you to do, is type and if you are asked
Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Then type 2.

CODE]sudo gdisk /dev/sda[/CODE]
It may be helpful to recreate the protective MBR, and since you were unable to install Ubutnu, we may be able to simply create a new GPT partition and go from there.
```
x #To go into the expert console
n
m #To go back to the normal console
n
enter
enter
+150GB
enter
w
```

That will create a new partiton that is 150GB and uses the GPT partiton table, and should also try and fix the MBR problem.

Now let's create a file system for our new partition, be **CAREFUL** not to use one of the other partitons.

Type:```
sudo mkfs.ext4 /dev/sda3 # **MAKE SURE SDA3 IS THE NEW PARTITION!**
```

Let this finish and you should be ready to install Ubuntu. I would however, restart and boot into the live boot again. When you get to the installer, use the "Something Else" option

From the "Something Else" option, double click the new /dev/sda3 partition, and select *ext4* as the File System type, then select */* as the "Mount Point" option, and make sure the "Device for boot loader installation" is set as /dev/sda.

Good luck, 
Chris

---

### Post by oldfred on 2014-01-09
Windows has a bug, where if you reinstall in BIOS mode when original install was UEFI, it converts drive to MBR(msdos), but leaves the backup gpt partition table. Then gdisk sees both MBR & gpt. All other Linux partition tools then do not know if you really have MBR or gpt.
Fixparts is the best way to resolve the issue, but you do need to know if you are UEFI booting or BIOS booting. And must be consistent. Both Windows and Ubuntu install in the mode you boot installer UEFI or BIOS and you really need to install both systems in same boot mode.

A lot of the info my in how-to is extra explanation as there are many different types of installs and issues depending on vendor configuration. First three links on install and boot-repair are the most important if UEFI. 

But now you seem to have standard BIOS/MBR and the older issues like the 4 primary partition limit, that BIOS may have, but are better known.

---

### Post by tfrue on 2014-01-09
I thought you couldn't install Win 8 into a MBR partition? I assumed that after he re-installed Win8, it formatted the drive as GPT, and used UEFI, since his motherboard supports it. I also assumed that when he used the Ubuntu installer for the 150GB partition, it tried to use MBR therefore causing an MBR partition on the GPT that might have a boot flag. I'm not sure, what is your take on what I wrote and his problem?

Thanks,
Chris

---

### Post by oldfred on 2014-01-09
If you do not have Windows 8  pre-installed you can install in BIOS or UEFI depending on your system. And is system is UEFI, then you can also install in either mode.
But a pre-installed Windows 8 has its product license key in the UEFI, so you cannot reinstall in BIOS mode using the recovery mode. You have to buy a full install copy with new product key.

---

### Post by haydenlueck on 2014-01-09
Okay, so it looks like there's a few things that need to be figured out, so hopefully you guys can figure it out!
If it comes down to me having to run Fixparts, that's fine, I just need to know what to do. I'm not sure if I'm supposed to run it from Windows, or Ubuntu, or what, and what I'm supposed to do in it. It seemed to fix it for the guy I linked in the OP that was having the exact same issue, so it looks like there MIGHT be hope there.

For now I followed the instructions in the first section of tfrue's post and here's the URL it gave me:
[http://paste.ubuntu.com/6723680/](http://paste.ubuntu.com/6723680/)

edit: also, I doubt this will help at all but here's what my partitions look like in Windows Disk Management:
[http://i.imgur.com/EZKdPfV.png](http://i.imgur.com/EZKdPfV.png)

---

### Post by oldfred on 2014-01-09
You seem to have a standard Windows install with a 100MB boot partition and the main install.

I would run fixparts from Ubuntu live installer. You will have to install it. Instructions on rodbooks site.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
    
Use Windows to shrink Windows and reboot so it can do chkdsk. It looks like Windows is still hibernated which causes issues. Applies to all Windows 8 whether UEFI or BIOS. In BIOS there is no secure boot, so that will be or must be off. Then I would make entire rest of drive as the extended partition and only use logical partitions for shared NTFS and all Linux partitions.

Since now BIOS be sure to always boot in BIOS mode. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by haydenlueck on 2014-01-09
> **oldfred said:**
> WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
That shouldn't be an issue cause I don't use separate partitions to store any media. I keep everything on my OSes separated.
> **oldfred said:**
> Use Windows to shrink Windows and reboot so it can do chkdsk. It looks like Windows is still hibernated which causes issues. Applies to all Windows 8 whether UEFI or BIOS. In BIOS there is no secure boot, so that will be or must be off. Then I would make entire rest of drive as the extended partition and only use logical partitions for shared NTFS and all Linux partitions.
Alright, so... What is the exact order I should be doing everything in? I don't want to take any risks with this. I don't really have any super important files on Windows I need to backup, it's just a pain to get back to Windows back because I only have the 7 installation disk and then I need to upgrade to Windows 8 OTA because I don't have a physical copy. Plus reinstalling games is annoying cause they're huge files and internet speeds in Canada are terrible.
How much of the partition do I shrink? What do I do with the empty space after? I'd like as much detail as possible cause I really don't want to mess up again.

---

### Post by tfrue on 2014-01-10
Since we have determined that you have installed Win 8 with BIOS boot, then we need to make sure that you are booting the live session in BIOS, from lines 127-128 > BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled.
Another way to determine if using GPT or MBR, or even EFI boot, is from the fdisk command. Fdisk should output a drive with EFI boot with a disk identifier: 0xee which you don't have on your /dev/sda drive:> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: **0xf81e1af7**

I have been able to edit the BIOS from pressing one of the 'f' keys, but I have read multiple times that you will have to do this from Win 8. Go to your settings, then click on General Settings, then Advance Options, and finally UEFI Firmware Settings. You should be prompted to restart, and you may be able to search for UEFI settings from the tile screen.

I would disable EFI boot, secure boot, and enable legacy boot to make sure that we are booting and installing with BIOS when you live boot, so with legacy boot enable you should be good.

I would say run the Fix Parts before trying to install again, just to be safe and make sure that you are getting rid of all the GPT data. It doesn't really matter when you disable secure boot, and legacy boot since Win 8 installed as BIOS. We want to do that just to make sure we live boot with BIOS.

Disable fast start up first, then do a complete shut down, live boot linux and run Fix Parts, I would then shut down and re boot with BIOS into the live boot but that's just me, then go and try and install Ubuntu on the 150GB partition.

Oldfred said to shrink the volume and make it as an extended partition, which you don't have to do, it will work the way you have it. You will just use one more primary partition of the 4 that you have, since MBR only uses 4 and Win 8 is already using two.

The only thing that I'm concerned about is when you do install Ubuntu, it will ask where do you want to install the bootloader, which would be /dev/sda, but it will replace the boot loader for Win 8, but you should still be able to boot into Win 8 with grub

---

### Post by oldfred on 2014-01-10
Yes, run fixparts first, then shrink Windows, reboot Windows so it runs chkdsk,  and install Ubuntu.

But the always on hibernation and/or chkdsk needed flags hide Windows from the Ubuntu installer. So the installer usually does not see Windows. And often then just installs to entire drive erasing Windows. 
Best to use manual install or Something Else and create the partitions yourself.

With Windows you can shrink as much or little as you want for Ubuntu. But leave at least 30% free space in the NTFS partition as Windows works best with lots of extra space. At 10% free it will slow to a crawl.
I prefer to have smaller system partitions for both Windows & Ubuntu and larger data or /home partitions.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by haydenlueck on 2014-01-11
> **tfrue said:**
> Go to your settings, then click on General Settings, then Advance Options, and finally UEFI Firmware Settings.
Those options aren't there.
There's settings, then "change PC settings" if that's what you mean, but then no advanced options or anything like that.
> **tfrue said:**
> The only thing that I'm concerned about is when you do install Ubuntu, it will ask where do you want to install the bootloader, which would be /dev/sda, but it will replace the boot loader for Win 8, but you should still be able to boot into Win 8 with grub
That's what I did when I had it installed before. At boot it would show me the grub and I would choose Windows 8, Ubuntu, or whatever other settings were there.
> **oldfred said:**
> Yes, run fixparts first, then shrink Windows, reboot Windows so it runs chkdsk, and install Ubuntu.

But the always on hibernation and/or chkdsk needed flags hide Windows from the Ubuntu installer. So the installer usually does not see Windows. And often then just installs to entire drive erasing Windows. 
Best to use manual install or Something Else and create the partitions yourself.

With Windows you can shrink as much or little as you want for Ubuntu. But leave at least 30% free space in the NTFS partition as Windows works best with lots of extra space. At 10% free it will slow to a crawl.
I prefer to have smaller system partitions for both Windows & Ubuntu and larger data or /home partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt - all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
So with all of this stuff are you just saying to do what the guy did in the video I posted at the beginning of the thread? Cause that's what it sounds like unless I'm missing something.

---

### Post by tfrue on 2014-01-11
I would say it's just like the video because that's how you install Ubuntu, or any other OS, the difference is making sure that your drive is healthy with Fix Parts, making sure you're BIOS booting, install with "Something Else", and you should be good!

Good Luck,
Chris

---

### Post by haydenlueck on 2014-01-11
> **tfrue said:**
> making sure you're BIOS booting
That's the one thing I don't know how to do. There's all this links on [this]("http://ubuntuforums.org/showthread.php?t=2147295") page but I don't see one on how to make sure I'm BIOS booting. I have no way of getting to UEFI settings and disabling secure boot and all that from what I can tell.
And in this post from earlier:
> **oldfred said:**
> Fixparts is the best way to resolve the issue, but you do need to know if you are UEFI booting or BIOS booting. And must be consistent. Both Windows and Ubuntu install in the mode you boot installer UEFI or BIOS and you really need to install both systems in same boot mode.
I still don't even really know what the difference between booting in EUFI or BIOS is, and how to switch between the two, and I'm not sure what Windows is installed on.

---

### Post by oldfred on 2014-01-11
If your system was Windows 8 pre-installed, then you must have a way to turn secure boot off. That is a contract requirement from Microsoft to all vendors with Windows 8. We have not seen a system without that setting, but a few have required the user to add a password to let them turn it off. If you have to set a password never lose that password as then system would become a brick. 
If an older system with Windows 7 originally, you may not have even have secure boot setting, but still may be both UEFI and BIOS.

Some other UEFI screens from various systems. If you have secure boot on, only secure boot systems are shown. 
Some only show BIOS boot systems if BIOS/CSM/Legacy boot set, other let you boot either BIOS or UEFI but not secure boot. And others have just a UEFI only setting that is not secure boot nor BIOS mode, but just UEFI.

---

### Post by haydenlueck on 2014-01-11
I built my own PC and installed Windows 7 OEM on it, then upgraded to Windows 8 Pro digitally from there, and then digitally to 8.1 since it's a free upgrade.

edit: mine looks like the one in the fourth attachment since I have an ASUS motherboard.

---

### Post by haydenlueck on 2014-01-11
Actually, I just remembered. I mentioned this in another post.
I found [this]("http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi-2.html#post191536") post from earlier where a guy says how to do it in my BIOS, but when I go in there's no "secure boot" setting like he shows in the picture.

---

### Post by haydenlueck on 2014-01-11
Okay so here's the question I need answered. (By the way, I've decided to install Elementary Luna instead of Ubuntu now. Should work the same though since it's based off of Ubuntu 12.04 from my understanding.)

I installed fixparts, typed
```
sudo fixparts /dev/sda
```
and it came up with:
 ```
NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N): 
```
and I don't want to continue until I know what I'm doing. Should I hit y? I hit n for now cause I don't even know what it's talking about really.
If I type "p" from the start of the program, I get:
```
MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!


** Extended partitions are not displayed, but will be generated as required.


Disk size is 2930277168 sectors (1.4 TiB)
MBR disk identifier: 0xF81E1AF7
MBR partitions:


                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary     Y        Y      0x07
   2                206848   2623074303   primary              Y      0x07


MBR command (? for help): 



```

So, what do I do?

---

### Post by oldfred on 2014-01-11
We are running fixparts to remove the backup gpt table or extra gpt info on drive. We want just the MBR table with the two Windows partitions you currently have. 
You need to get fixparts to do its thing. I have never had to run it, but say yes and if it needs a w to write final do that also.

If not Ubuntu I have to move thread to Other OS as we do not directly support non Ubuntu flavors.

---

### Post by haydenlueck on 2014-01-11
Alright. Ran FixParts, booted back into Windows. Seems to be working fine. Guess I'll try installing now.

---

### Post by oldfred on 2014-01-11
Do the p to list and a w to write MBR partitions if it shows the two partitions.

---

### Post by haydenlueck on 2014-01-11
Sorry, I edited my post because I went ahead and hit w. Windows seems to be working still so that's a good sign.

---

### Post by haydenlueck on 2014-01-11
Alright! Went into the installer and it recognized my partitions! I went through with the installation, and Windows 8 still boots fine from the grub! Looks like the solution from the beginning was just to run fixparts.

Also just ignore the fact that I switched the Elementary Luna last second. The issue wasn't with Elementary, it was just an issue that I'm sure other people will get when installing Ubuntu, so it's probably best to leave the thread where it is for future Googlers that are looking for the solution.

Anyway, thanks for your help guys!

---

### Post by tfrue on 2014-01-12
Not a problem! Glad it's fixed.

Chris

---

