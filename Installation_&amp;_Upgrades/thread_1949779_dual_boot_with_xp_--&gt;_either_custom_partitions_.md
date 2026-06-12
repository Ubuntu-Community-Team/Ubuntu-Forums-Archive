---
title: "dual boot with xp --&gt; either custom partitions or dual boot but not both allowed"
date: 2012-03-30
forum: Installation &amp; Upgrades
---

### Post by thane1 on 2012-03-30
Having a bit of trouble installing the latest lubuntu lxde with both a dual boot setup and also with custom partitions for lubuntu.  The install process doesn't seem to want to let me do both.  If I select the option to manually set my partitions, I can set up my multiple partitions for lubuntu with no problems.  However the installer won't recognize my xp partition, which is on a separate drive.  The newly installed lubuntu runs fine, but there's no dual boot option screen shortly after Post.  I've set up ubuntu a number of times in the past with xp on the second drive and used custom ubuntu partitions.  But I really dislike unity and I want to use the latest version of lubuntu lxde on my other computer.  Thanks.

---

### Post by Rex Bouwense on 2012-03-31
Can you post a screen shot of your drive using Gparted?  Are you sure that the Lubuntu install didn't install over the whole drive?

---

### Post by Bucky Ball on 2012-03-31
> **Rex Bouwense said:**
>   Are you sure that the Lubuntu install didn't install over the whole drive?

Appears XP is on a separate drive ...

Could you open a terminal and try:

```
sudo update-grub
```... then reboot and see if XP gets picked up?

Also, if you are just not getting to select an OS (there is no menu) at boot, try hitting escape (or shift depending on release) at boot after the BIOS. That should show your grub list and hopefully Win will already be there.

---

### Post by Rex Bouwense on 2012-03-31
I misread that one.  Sorry.

---

### Post by Bucky Ball on 2012-03-31
> **Rex Bouwense said:**
> I misread that one.  Sorry.

;)

---

### Post by oldfred on 2012-03-31
As Rex Bouwense commented, is Windows really a separate drive? Windows uses drive for both partition and physical drives.

I have had a separate XP drive sda that booted that gparted would not see. Long timeout then only showed sdb & sdc. But XP booted? So I ran chkdsk and XP booted a bit faster and then gparted saw it right away.

Post this from terminal in Ubuntu or liveCD:

sudo fdisk -lu

---

### Post by thane1 on 2012-04-01
Sorry for delay in replying.  I do in fact have xp on the sda drive.  My lubuntu is on sdb, as well as one ntfs partition used to hold xp's my documents, etc (the reason for that, is that the original windows drive was dying, and I had to move the personal stuff to another drive.  Windows itself is however on the _new_ sda drive and it will boot fine by itself, if there's no other operating system installed.  I'll try the two terminal commands in your posts and also check the gparted again and get back in a bit today with the results.  Many thanks.

---

### Post by thane1 on 2012-04-01
Progress as follows:

Gparted checked with results below:

<sudo update-grub> in terminal:

Rebooted.  Lubuntu is still the only boot option - automatically starts.

<sudo fdisk -lu> in terminal, results below:

---

### Post by oldfred on 2012-04-01
Easier if you just post output. If longer or has any format use code tags which are easy to use by hightlight the info and click on the # in the edit panel at the top of your message.

Run the boot info script to see if all the files are in the correct locations. 
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you moved Windows from one drive to another the PBR - partition boot  sector of Windows will not be correct and you need to run both fixBoot  and chkdsk from Windows repair consolue.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If you have grub in the MBR of sda a fixMBR will overwrite that copy of grub with Windows boot loader. It may be better to have grub in sdb and set BIOS to boot from sdb. But lets see boot_info script first and then we can make better suggestions.

---

### Post by thane1 on 2012-04-01
Many thanks oldfred!  I'll plug away with your suggestions and see, what I can achieve.  Will report back.  cheers

---

### Post by Bucky Ball on 2012-04-01
Again, just wondering if you are simply not getting the menu to choose an OS to boot at boot; machine is going straight to Lubuntu.

As mentioned, hit shift (or escape depending on release) after boot and that should give the menu list. Windows may already be there ...

---

### Post by thane1 on 2012-04-06
Many thanks for the advice friends!  However there have been new developments.  I'm now looking at a hardware problem, which I'm sure is at the root of my problems.  The original drive, which was dying and was the reason for putting xp on a second drive, has now been joined by the fairly new linux drive for a total of 2 dead hdd's and also 2 dead ram modules.  Also in quick order the whole system was getting flaky and then wouldn't even make it to Post on startup.  So I swapped in a newer power supply and it started up with my one remaining drive.  Now it will not recognize the good drive, although one of my other boxes will.  So I think I've got a flaky mobo or cpu.  I'll change those out and get this other box running again.  Many thanks again.  I'll mark this post as solved.  cheers

---

### Post by qqww on 2012-04-30
i have a dual boot with windows xp which is now corupted and wont work

so i need to reinstall  windows

in ubuntu i see a windows file


are there instructions on how to reinstall windows

thaks for your time and information

---

### Post by Bucky Ball on 2012-05-01
> **qqww said:**
> i have a dual boot with windows xp which is now corupted and wont work

so i need to reinstall  windows

in ubuntu i see a windows file


are there instructions on how to reinstall windows

thaks for your time and information

Please create a new thread with a title describing your problem. This one's old and you probably won't get much help buried in it. ;)

---

