---
title: "How to boot Ubuntu 10.04 via Windows XP boot loader"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by Momo88 on 2010-07-28
Hi everybody,

I've been searching the internet for 2 days now, but couldn't really come up with a working solution.

I have 2 HDDs: 
HDD 1 (sda) with Windows XP installed on sda1 and four more partions.
HDD 2 (sdb) with three NTFS-Partitions (sdb1, 5 and 6) and Ubuntu 10.04 (sdb7) + Swap-Partition (sdb8).

I would like to boot Ubuntu using the Windows XP boot loader, i.e., having an entry there to choose Ubuntu and start my installation of Ubuntu 10.04.

I have installed Ubuntu 10.04 on sdb7 and told the installer to install the grub2 boot loader to /dev/sdb (should it have been /dev/sdb7?).

When using the boot selection option of my bios and choosing the second HDD Ubuntu starts without problems.

I used dd if=/dev/sdb of=bootsect.lnx bs=512 count=1 to copy the mbr of my second HDD and copied the file bootsect.lnx to my c:\ drive. Then added C:\bootsect.lnk = "Ubuntu Linux" to my Windows boot.ini.

When rebooting my computer I get the option "Ubuntu Linux" in the XP boot loader. Choosing it I come to a black screen with a blinking white cursor.

What have I done wrong? All I want to do is not use Grub 2 as my primary boot loader but instead leave my WinXP installation untouched and start Ubuntu from within WinXP boot loader. This has been working just fine with my old Ubuntu installation.

Any help and suggestions highly appreciated.

Momo

---

### Post by lechien73 on 2010-07-28
Could you supply a hexdump of your bootsect file, please?

```
hexdump -Cv bootsect.lnk
```

The problem could be that Grub is misreading the disk geometry when its triggered from NTLDR.

---

### Post by Momo88 on 2010-07-28
Hi,

thanks for the quick reply. Pls find attached the hexdump.

Thanks,
Momo

---

### Post by lechien73 on 2010-07-28
After dusting off my old assembly language skills, I think the problem lies with the fact that Grub thinks it's being booted with a single operating system.

If you have a hex editor (I use the Gnome Hex Editor), then open the bootsect.lnk file. At hex address 0040, replace "FF" with "81". This will tell Grub to look at the second hard disk in the system for its stage 2 loader file. I couldn't find it documented that "FF" means that Grub is installed on a single hard drive, but in multi-drive systems "80" is the first drive, "81" is the second and so on.

Now save the file and try rebooting via NTLDR. It has to be said that this still may not work, due to difficulties locating the second stage file.

---

### Post by Momo88 on 2010-07-28
Hi,

used the boot_info_script. Interestingly it says:

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /bootsect.lnx looks at sector 1 of 
                       the same hard drive for core.img, but core.img can not 
                       be found at this location. Grub 2 in the file 
                       /bootsect.lnx looks at sector 1 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

According to the script the file bootsect.lnk looks at sector 1 of the SAME hard drive - which would be sda instead of sdb - since I copied it via dd if=... from sdb to sda. How can I change the bootsect.lnk-File to point to my 2. HDD? Or is there a way to install Grub 2 to my 2. HDD and change the way it refers to sdb7 so I can copy it to my 1. HDD later on?

Thanks in advance.
Momo

---

### Post by lechien73 on 2010-07-28
Please see my previous reply regarding editing bootsect.lnx in a hex editor. Changing the value from "FF" to "81" should be enough :)

---

### Post by lechien73 on 2010-07-28
Further analysis of the Grub source code has confirmed what I thought.

When Grub was installed, it set the value at address 7C40 (or 0040 in the hex dump) to 0xFF.

Later in the code, Grub checks to see if the BIOS has left an index number in the DL register to show which drive is booting (0x80 for the primary, 0x81 for the secondary and so on). If the primary disk is booting (which in your case it is), or if the BIOS is buggy, then value 0x80 will be stored in the DL register.

Shortly after this, the following code:

```
movb  boot_drive, %al
cmpb  $0xff, %al
je    1f
movb  %al, %dl
```

checks to see if 0xFF is stored at the value. If it is, then the AL register is abandoned, and the value in the DL register (0x80) is retained. If the value at the boot_drive address (7C40) is anything other than 0xFF, then Grub uses that value as the index number and proceeds to boot.

Therefore, changing the value from 0xFF to 0x81 in a hex editor will mean that Grub then looks to the correct hard drive, instead of attempting to boot from 0x80, which is the first hard drive in the system (aka your Windows disk).

---

### Post by Momo88 on 2010-07-28
Hi lechien73,

thanks a lot for your replies. I tried your suggestion and changed FF -> 81 in a hexeditor. Unfortunately it doesn't seem to work. I still get a blinking curser after choosing "Ubuntu Linux" in Windows XP boot loader.

Did I do anything wrong when changing the value. Attached you will find my current bootsect.lnx (had to rename it to *.txt so I could upload it).

I still have a floppy drive in my computer. Should I try reinstalling Ubuntu and telling the installer to put Grub 2 on the floppy (/dev/fd0)?
How do I have to format the floppy so the installer can write to it (I already tried FAT as file system, but the floppy was empty after the installation process had finished).

Any other suggestions?

Momo

---

### Post by oldfred on 2010-07-28
lechien73 is way ahead of me in understanding exactly how grub works in the MBR, but you have grub2 installed to the windows boot sector and windows requires its code in the boot sector.

You can use windows repairs (fixboot) or testdisk to recover the windows boot sector. I am not sure what boot screen you see as it looks like the windows boot loader will not work at all and only the grub loader in sdb will work.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

What is wrong with leaving the windows boot loader in sda, and setting BIOS to boot sdb. sudo update-grub should find windows and let you boot either from grub2 without changing sda at all.

---

### Post by lechien73 on 2010-07-28
Ok - I'm going to try replicate your problem by installing Windows and Ubuntu into a virtual machine :)

---

### Post by Momo88 on 2010-07-28
Hi oldfred,

starting Windows XP via the Windows bootloader on sda works ok. The entry I have made for Ubuntu that is pointing to a copy of the mbr of sdb however doesn't start Ubuntu. I believe that it is pointing to the wrong hdd. I don't know how to change that though.

I was able to chainload Ubuntu from the Windows bootloader with my last installation of Ubuntu (8.10) and never had any problems with that.

Since Windows XP still is my working system I don't want to tamper with anything that could break my system or create problems when doing updates. Calling Ubuntu from within the Windows bootloader allows me to delete Ubuntu without affecting my Windows installation.

Pointing my BIOS to sdb and leaving the Windows bootloader on sda sounds like a good idea. I will try this in case I can't find a solution to start Ubuntu from the Windows bootloader.

Thanks again for all your help.

Momo

---

### Post by lechien73 on 2010-07-29
Last night I created a virtual machine with Windows XP and Ubuntu installed on two separate virtual disks. Following the steps you've already done, I was able to successfully replicate your issue.

After checking out the code further, it appears that Ubuntu's version of Grub does not check the location at 7C40 for the disk address. I had made the cardinal mistake of presuming that Ubuntu's Grub would be the same as the source code I downloaded from the Grub project site. Instead, in both yours and my bootsector dump, the code looks at the value at offset 7C64. Again, this is set to 0xFF by default. I changed this value in the hex editor, rebooted and then Ubuntu booted up just fine through NTLDR.

So, the solution was:

```
sudo dd if=/dev/sdb of=./bootsect.lnx bs=512 count=1

```
To create a fresh boot sector file.

Then in a hex editor change the value at address 0064 from FF to 81. Copy the boot sector file back to the C:\ drive of your Windows installation, and it should now work. Or, at least, it worked for me :)

---

### Post by Momo88 on 2010-07-30
Hi lechien73,

I cannot thank you enough. **THANK YOU SO MUCH!** You really solved my problem. Now everything is working exactly how I wanted it. Thanks for going through all the work of setting up a test system to replicate my issue. I'm really overwhelmed by how much time and effort you put into this. For me it would have been impossible to figure out where to change something in the boot sector. You are a genius!

Thank you so much again! You really made my day!

Momo

---

### Post by oldfred on 2010-07-30
I have wondered why meierfra's script reports sda  partition 7 but actually boots from sdc7. I think this helps but does not totally answer as my 40 has 80 & 64 has ff.

---

### Post by lechien73 on 2010-08-01
> **Momo88 said:**
> Hi lechien73,

I cannot thank you enough. **THANK YOU SO MUCH!** You really solved my problem. Now everything is working exactly how I wanted it. Thanks for going through all the work of setting up a test system to replicate my issue. I'm really overwhelmed by how much time and effort you put into this. For me it would have been impossible to figure out where to change something in the boot sector. You are a genius!

Thank you so much again! You really made my day!


Sorry - I was away for a few days, but thanks for your feedback and for marking the thread as solved. I enjoyed helping out - it was good to get back into assembly language, and I'm glad it eventually worked for you :)

All the best,

---

### Post by lechien73 on 2010-08-02
> **oldfred said:**
> I have wondered why meierfra's script reports sda  partition 7 but actually boots from sdc7. I think this helps but does not totally answer as my 40 has 80 & 64 has ff.

The part of the code that controls where Grub looks for the drive index is at addresses 7E, 7F and 80. In hex, the code on mine and momo88's bootsector at these addresses is:

```
a0 64 7c
```

Which is the hex representation of:

```
mov al, 7C64
```

So, if that is the same in your dump of the bootsector, then Grub is looking at offset 64 - so the value would be FF in your case. If the code in your dump reads:

```
a0 40 7c
```

Then Grub will look for the drive index in offset 40, so the value would be 80 in your case.

---

### Post by deker0 on 2010-11-12
Hi all,


I'm trying to do this now with Ubuntu 10.10 and I am having trouble.

Have tried to set offset 64 to value of 80, no good. Tried a value of 81, still no good.

Can someone help me out in getting this to work?

I should add that I was able to get grub successfully installed on a USB key and that boots Ubuntu fine. When I use dd to export the USB's MBR to a file and then add it to Windows, I get a blinking cursor, and nothing else.

Please help!


Thanks, D E K E R

---

### Post by HughR on 2010-11-12
> **deker0 said:**
> Hi all,


I'm trying to do this now with Ubuntu 10.10 and I am having trouble.


You and I are talking in IRC.  That means our discussion isn't usefully recorded (as far as I know).  So I'll add information here.

Grub2 (unlike grub-legacy or LILO) seems to want to store the initial part of itself in the space between the drive's MBR and the first sector of the first partition.

If you haven't installed Grub2 on a drive, then an MBR that tries to load from that area of the drive will fail.

(As you pointed out in IRC, [http://community.linuxmint.com/tutorial/view/102]("http://community.linuxmint.com/tutorial/view/102") might be relevant.  Looks complicated and perhaps fragile.)

---

### Post by deker0 on 2010-11-12
Hi Hugh,


Thanks for the info. Based on that...I would ask: is Ubuntu 10.04 using grub2? I'm guessing it is. That being said...a similar issue to what I am experiencing was solved earlier in this thread on a Ubuntu 10.04 install.

Perhaps lechien73 could speak on what I might be able to do to get this going?

---

### Post by HughR on 2010-11-12
> **deker0 said:**
> is Ubuntu 10.04 using grub2? I'm guessing it is. That being said...a similar issue to what I am experiencing was solved earlier in this thread on a Ubuntu 10.04 install.

Perhaps lechien73 could speak on what I might be able to do to get this going?

Yes, 10.04 used Grub2.

When I most installed 10.04, I was able to ask that it install the bootloader on a partition.  That allowed it to co-exist with 10.10.

---

### Post by deker0 on 2010-11-14
Okay guys,


I got this working....I reinstalled Ubuntu 10.10 and just had it install the bootloader to the /boot partition (/dev/sda3)...once the install finished, I used dd if=/dev/sda3 of=/ubuntu.mbr bs=512 count=1 command to export the MBR and then I copied that over to the C: drive.

Added that to boot.ini as a Windows bootloader entry and it worked just fine.

---

