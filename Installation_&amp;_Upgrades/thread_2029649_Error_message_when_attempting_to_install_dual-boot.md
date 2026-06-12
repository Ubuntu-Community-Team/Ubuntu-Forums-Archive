---
title: "Error message when attempting to install dual-boot of Windows Vista and Ubuntu 12.04"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by mt123 on 2012-07-20
I'm a complete newbie to Linux and Ubuntu so please bear with me. 

My goal is to be able to dual-boot Windows Vista and Ubuntu 12.04.  I  was reading some guides and saw it was recommended to leave 15-20gb  of free space for Ubuntu and that's I did (it will be for light use) via  Windows disk management.  I then created the boot CD for Ubuntu and  tried installing through "install Ubuntu alongside Windows Vista" but  was given the message "Unable to satisfy all constraints on the partition".
  
Image of "disk management" on Windows:
[http://i45.tinypic.com/hty2v5.jpg](http://i45.tinypic.com/hty2v5.jpg)

Any thoughts?

---

### Post by sudodus on 2012-07-20
Welcome to the Ubuntu Forums :-)

I think that Ubuntu should be able to grab that unallocated space. But let us do things systematically.

Can you boot a live session from the Ubuntu CD? I mean, do not try to install at once, instead 'try Ubuntu'. When Ubuntu is up and running, please run the following command
```
sudo fdisk -lu
```
and post the output in a reply.

Also please post the specs of your computer: CPU, RAM and graphics card.

-o-

One alternative is to run ***gparted*** from your live Ubuntu session, and create an ***extended partition*** of the unallocated space, and inside it create two logical partitions.

- If you want Ubuntu to hibernate, make a ***swap partition*** a little bigger than your RAM (in GiBibytes). Otherwise 1 GB swap is enough.

- Make an ***ext4 partition*** of the rest of the space in the extended partition.

- close gparted

After that you can start to install Ubuntu (and at the partitioning screen select 'something else' to select the ext4 partition for your root partition and install grub to the head of the drive /dev/sda (not to a partition /dev/sda5 or /dev/sda6 ...)

-o-

But, don't rush, the advice will be better if you answer those questions and wait for further instructions :-)

---

### Post by mt123 on 2012-07-20
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I think that Ubuntu should be able to grab that unallocated space. But let us do things systematically.

Can you boot a live session from the Ubuntu CD? I mean, do not try to install at once, instead 'try Ubuntu'. When Ubuntu is up and running, please run the following command
```
sudo fdisk -lu
```and post the output in a reply.

Also please post the specs of your computer: CPU, RAM and graphics card.

-o-

One alternative is to run ***gparted*** from your live Ubuntu session, and create an ***extended partition*** of the unallocated space, and inside it create two logical partitions.

- If you want Ubuntu to hibernate, make a ***swap partition*** a little bigger than your RAM (in GiBibytes). Otherwise 1 GB swap is enough.

- Make an ***ext4 partition*** of the rest of the space in the extended partition.

- close gparted

After that you can start to install Ubuntu (and at the partitioning screen select 'something else' to select the ext4 partition for your root partition and install grub to the head of the drive /dev/sda (not to a partition /dev/sda5 or /dev/sda6 ...)

-o-

But, don't rush, the advice will be better if you answer those questions and wait for further instructions :-)

Appreciate the response.

I'm going to work on this a little later when I have some free time to deal with it.  As I alluded to I'm an absolute beginner so I'm not 100% sure on how I'm even supposed to apply that code but I'm thinking that I would use "terminal"?  Do I just plug this in by itself or does there need to be any type of code beforehand?  

Thanks

---

### Post by sudodus on 2012-07-20
> **mt123 said:**
> Appreciate the response.

I'm going to work on this a little later when I have some free time to deal with it.  As I alluded to I'm an absolute beginner so I'm not 100% sure on how I'm even supposed to apply that code but I'm thinking that I would use "terminal"?  Do I just plug this in by itself or does there need to be any type of code beforehand?  

Thanks
Yes, you use a terminal window, and the code is interpreted by bash (a shell program), so you need 'nothing else'.

It is important that you reboot your computer and make it boot from the CD. If necessary, change in the BIOS menu, so that it tries to boots from CD (if there is a bootable CD) before booting from the internal HDD.

---

### Post by mt123 on 2012-07-20
> **sudodus said:**
> Yes, you use a terminal window, and the code is interpreted by bash (a shell program), so you need 'nothing else'.

It is important that you reboot your computer and make it boot from the CD. If necessary, change in the BIOS menu, so that it tries to boots from CD (if there is a bootable CD) before booting from the internal HDD.

Thanks for the explanation.

Here is the result:

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x820d0dbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   583196670   291598304    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.

---

### Post by sudodus on 2012-07-20
There is no other partition (hidden from Windows). So you should be able to use the free space as I suggested in post #2.

But before deciding what flavour of Ubuntu to test (and later install), please post the specs of your hardware, at least

- CPU
- RAM
- graphics card/chip

---

### Post by mt123 on 2012-07-20
Right, forgot.

> ------------------
System Information
------------------
Time of this report: 7/20/2012, 11:38:35
       Machine name: USER-PC
   Operating System: Windows Vista™ Home Premium (6.0, Build 6001) Service Pack 1 (6001.vistasp1_gdr.101014-0432)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP G60 Notebook PC
               BIOS: Default System BIOS
          Processor: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz (2 CPUs), ~2.0GHz
             Memory: 3002MB RAM
          Page File: 1056MB used, 5178MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6001.18000 32bit Unicode

---

### Post by sudodus on 2012-07-20
I think the hardware is good enough to run 'vanilla' Ubuntu: HP G60 Notebook PC

What about the graphics chip, is it: NVIDIA GeForce 8200M?

So I suggest you get started: boot the computer from the Ubuntu CD. If you have problems, try some boot option,
start with ***nomodeset*** according to [[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
but chances are that you need no boot option.

---

### Post by mt123 on 2012-07-20
> **sudodus said:**
> I think the hardware is good enough to run 'vanilla' Ubuntu: HP G60 Notebook PC

What about the graphics chip, is it: NVIDIA GeForce 8200M?

So I suggest you get started: boot the computer from the Ubuntu CD. If you have problems, try some boot option,
start with ***nomodeset*** according to [[COLOR=Red]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
but chances are that you need no boot option.

Graphics chip:
> Mobile Intel(R) 4 Series Express Chipset FamilyI'll report back a little later what happens when I get a chance to fool with the installation.

---

### Post by mt123 on 2012-07-24
> So I suggest you get started: boot the computer from the Ubuntu CD. If you have problems, try some boot option,
start with ***nomodeset*** according to [[COLOR=Red]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
but chances are that you need no boot option.I tried the "nomodeset" option and got the following the follow pieces of an error message which I had write down before it then in turn went to the desktop:

cie04: Link training error occurs (this may have started out with 'p' as that seems to be bring up some results in google)
Failed to check link status

Also, I'm not exactly sure what you mean by "no boot option" so could please explain? 

Thanks

---

### Post by aimwin on 2012-07-24
> **mt123 said:**
> I tried the "nomodeset" option and got the following ...............

Also, I'm not exactly sure what you mean by "no boot option" so could please explain? 

Thanks

From
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
No.6 F6. Other Options. ACPI (Advanced Configuration and Power Interface).............

That page gave you options after press F6 key,
you need to use space bar or enter key to select (enable) that options
in which you did.

Those options has so many other "noXXXXX" options in which you have chosen "nomodeset"

SO that is "no boot option" sudodus suggested in earlier post.
I hope that is what sudodus meant.
===============================

Now back to your problems,

You said
"I tried the "nomodeset" option and got the following... of an error message which I had write down before it then in turn went to the desktop:......."

Just ignore the error you have and just start using UBUNTU desktop.

I do not suggest you to install UBUNTU on to hard disk ( at all **_at this stage_** for reasons.

1. We don't know if UBUNTU will work flawlessly or have problems with your hardware. 

It showed some sign of troubles already, that you have reported. 
(on my HP dv1000 - all version perform 100% except Ubuntu 12.04)

So if it does has compatibility issue, you could be in big trouble when you installed it.

(I did wipe off my friend hard disk, during installation.
Though only once out of my hundreds Ubuntu Installations,
And lucky for him, I could recovered everything back for him.)

S[COLOR="Blue"]So you must back up all data, including doing your Ghost or Cloning of you windows[/COLOR] , just in case you got jackpot like my friends.

2. IF you use Ubuntu 12.04 LTS, it is still new and has many bugs during installations at present. 
(I do use 12.04 LTS in another partition, with many clashes and minor bugs that I can live with, I would not recommend you to use it as real working day to day at present day.)

3. You should use live CD desktop for a while,
it perform exactly as Ubuntu on hard disk, except speed is slower,
and you can't save configurations.
(But if you use the Live CD desktop to created live USB Ubuntu,
you can save your configuration and it is like hard disk and it is fast,
but again as newbies to Ubuntu, I would say don't try it at the moment)

And if you have problems, try 10,04 or 11.04 or 11.10 live CD.

Many times different versions give different compatibility issues.
So after you find good normal usage versions that give you no troubles,
or the least troubles.

Then install only after that.
====================================

The boot error you found could disappear after successful installation too.

It will update and find your hardware drivers automatically majority of the time.

---

### Post by mt123 on 2012-07-29
> **aimwin said:**
> From
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
No.6 F6. Other Options. ACPI (Advanced Configuration and Power Interface).............

That page gave you options after press F6 key,
you need to use space bar or enter key to select (enable) that options
in which you did.

Those options has so many other "noXXXXX" options in which you have chosen "nomodeset"

SO that is "no boot option" sudodus suggested in earlier post.
I hope that is what sudodus meant.
===============================

Now back to your problems,

You said
"I tried the "nomodeset" option and got the following... of an error message which I had write down before it then in turn went to the desktop:......."

Just ignore the error you have and just start using UBUNTU desktop.

I do not suggest you to install UBUNTU on to hard disk ( at all **_at this stage_** for reasons.

1. We don't know if UBUNTU will work flawlessly or have problems with your hardware. 

It showed some sign of troubles already, that you have reported. 
(on my HP dv1000 - all version perform 100% except Ubuntu 12.04)

So if it does has compatibility issue, you could be in big trouble when you installed it.

(I did wipe off my friend hard disk, during installation.
Though only once out of my hundreds Ubuntu Installations,
And lucky for him, I could recovered everything back for him.)

S[COLOR=Blue]So you must back up all data, including doing your Ghost or Cloning of you windows[/COLOR] , just in case you got jackpot like my friends.

2. IF you use Ubuntu 12.04 LTS, it is still new and has many bugs during installations at present. 
(I do use 12.04 LTS in another partition, with many clashes and minor bugs that I can live with, I would not recommend you to use it as real working day to day at present day.)

3. You should use live CD desktop for a while,
it perform exactly as Ubuntu on hard disk, except speed is slower,
and you can't save configurations.
(But if you use the Live CD desktop to created live USB Ubuntu,
you can save your configuration and it is like hard disk and it is fast,
but again as newbies to Ubuntu, I would say don't try it at the moment)

And if you have problems, try 10,04 or 11.04 or 11.10 live CD.

Many times different versions give different compatibility issues.
So after you find good normal usage versions that give you no troubles,
or the least troubles.

Then install only after that.
====================================

The boot error you found could disappear after successful installation too.

It will update and find your hardware drivers automatically majority of the time.

Thanks for the info.  I guess it's not a big deal to just use the Live CD for now since I'll just be working with "terminal" for a project I'm about to undergo.

---

### Post by sudodus on 2012-07-31
> **mt123 said:**
> Thanks for the info.  I guess it's not a big deal to just use the Live CD for now since I'll just be working with "terminal" for a project I'm about to undergo.
*aimwin* chipped in with good advice during my absence :-)

Good luck, and please let us know how it works to run live from the CD! Your results can help other people with the same or similar hardware. So please let us know what boot options or other special settings you need (if you need any, maybe the standard set-up works after all)!

---

### Post by mt123 on 2012-08-26
So I just attempted to install 10.04, an older version as suggested.  Unfortunately I got the same " "Unable to satisfy all constraints on the partition" message so maybe it's not an issue with the 12.04 but rather something with my PC.  

Any other thoughts?

---

### Post by sudodus on 2012-09-06
Is you computer running well from a live CD or USB drive?

In that case, check what kind of partitioning system that you are using. Do it in a command line terminal
```
sudo fdisk -lu
```
or with the GUI program

***gparted***

in both cases when you are running Ubuntu live.

---

