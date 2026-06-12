---
title: "grub2 problem"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by abdorefky on 2013-02-19
[B]hi 
i have installed windows 7 then Ubuntu , all works find so far
after i installed windows xp , the grub2 got deleted ofc and windows xp was booting directly , so i repaired my grub [/B]

{
1 sudo mount /dev/sdXY /mnt

2 sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys

3 sudo chroot /mnt

4 grub-install /dev/sdX

5 grub-install --recheck /dev/sdX

6 update-grub

7 exit && sudo umount /mnt/dev && sudo umount /mnt/dev/pts && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
}

[B]grub2 is back and when choosing windows 7 it boot to windows xp :lolflag: 
so i made windows 7 repair from windows 7 install 
now i can log to windows 7 and ubuntu 
the big problem that windows xp not detected :S
i thought it will be detected when repair windows 7 boot , or at leats when i choose windows 7 from grub it will gave me 7 and xp 
to choose (like normal windows boot )
i tried grub customizer, 

i don't know how to add the windows xp entry to grub2 :([/B]
[IMG][[IMG]http://img443.imageshack.us/img443/4035/screenshotfrom201302191.png[/IMG]]("http://imageshack.us/photo/my-images/443/screenshotfrom201302191.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")[/IMG]

**ty**

---

### Post by dino99 on 2013-02-19
that script should fix that issue:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by abdorefky on 2013-02-19
i tried the automatic fix , but it just removed the memory test entries

[http://paste.ubuntu.com/1682735/](http://paste.ubuntu.com/1682735/)

---

### Post by oldfred on 2013-02-19
Grub does not use boot flag, but Windows needs it on the partition you boot from if directly booting Windows. You have boot flag on sda3, it should be on sda2 as that is the Windows boot partition(but see below if repairing XP first).

Windows only boots from the one primary partition with the boot flag. And since Windows only boots from one partition grub can only find one install of Windows and then from Windows you should get the choice to boot either Windows.

But installing XP after Windows 7 creates issues as XP is not 7 aware. You have to repair 7 and use 7 to boot and update its BCD to include both. 
You may be able to move boot files for XP to the XP partition, do XP repairs (with boot flag on that partition then)  and then grub may be able to boot from that. 

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

    
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

    
Then Boot-Repair or a sudo update-grub may find both Windows installs.

---

### Post by abdorefky on 2013-02-22
i have read some on sites you send ,
i removed all flag's
re installed windows xp because repair required password ;/
again . i got 3 options now 
1 : windows 7 ( its acully windows xp ) :evil: 
2 : ubuntu 
3 : advanced ubuntu options 

why does windows xp boot installed on windows 7 partition ....
if i went to repair windows 7 , the xp will be gone 

now ,, how to install the xp boot on its partition ? 

thx for help

---

### Post by darkod on 2013-02-22
First, MS combines the boot files for more than one version, unless you move the boot flag BEFORE you start the second install. Which means it's best to have the partition ready and with the boot flag set. And it has to be primary.

In that case the installer should put the boot files on its own partition (because the boot flag is there).

If the boot files are combined, grub2 will never show two separate entries. There will always be only one, whether it's called XP or 7.

If you are not moving the boot flag before installing the second windows version, and windows bootloader doesn't create a dual boot option, this is up to windows. Grub2 and ubuntu have nothing to do with it, grub2 only passes the boot process to the windows boot files.

---

### Post by abdorefky on 2013-02-22
what is the MS
i had no flags befor install windows xp , 
after windows xp installed the flag was on sda3 
and bootloader read the boot from sda2 
how come ,, 
and why go install the bootloader on sda2 .....

anyway, here is the new bootrepair report
[http://paste.debian.net/236767/](http://paste.debian.net/236767/)

if i repaired windows 7 boot it will give the report i sent earlier
i have noticed that there is no boot files on sda 2 or 3 . lol . 

allright iam going to repair xp with boot flag on sda3 
next repair windows 7 with boot flag on sda2
last restore grub ,
hope that work 
really thx for helping

---

### Post by darkod on 2013-02-22
MS = Microsoft

You are right, there are no boot files for XP or 7. They were probably on another partition during install, that you later deleted. For windows boot files it doesn't matter on which partition you install the OS, it matters where the boot flag is. It can even put them on another disk without you knowing anything.

Later you remove that disk and find that your windows doesn't boot.

---

### Post by abdorefky on 2013-02-27
i have added new entry from grub customizer 
and it detected the xp , but ntldr is missing 
and that was easy to fix 
but how to access the safemode or the f8 list that i can use on normal startup

is there a program that shows me , where is the basic boot (grub)
stored and the pointers to the other boot's partitions , with easy descreption ?

---

### Post by abdorefky on 2013-02-27
i guess its time for this great article 
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by dino99 on 2013-02-27
you already got it, but without seeing it i suppose; watch the grub link below :P

---

### Post by abdorefky on 2013-03-19
[SIZE=3][SIZE=2]hi ,darkod , oldfred , dino99

i have read that  [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) ,thx "oldfred" 

i have got small problem now 
i have downloaded a program called  "burg manager" which lead me to download "super boot manager " those tools wasn't very bad until i though to check the resolution.
a year ago when i downloaded my first Ubuntu and tried to change the resolution from "grub customizer"  i have got that same problem but restoring the boot was very hard at that time .

the same happened now , the burg worked great until i changed the resolution ,,, restart ,, and ,,,, boot is missing :o
of curse  this is not a problem , i restored my boot by the same command's , but
 
* windows's 7 lost it's genuine , and alert me to activate :O 
** windows xp saying missing bootmgr !! 
*** i don't know how windows 7  boot with out bootmgr :confused: 

i haven't fixed the problem yet because i want to know what happened  
1: could lilo boot windows 7 from winload.exe directly?
2: what does the resolution do !!! 
i remember that i have tried to set a picture to grub and that failed too[/SIZE], [/SIZE]
[SIZE=3]any idea's about what happened[/SIZE]

---

### Post by darkod on 2013-03-19
Sorry, I just use the default grub2 and have no clue how burg works and what it may have done. Looking back in this thread I am not even sure whether you sorted out your windows boot files or not. Your problem was with windows boot files, not grub2 or ubuntu.

Do you have separate win7 and winXP files now? Are they on the respective 7 and XP partitions?

---

### Post by oldfred on 2013-03-19
Also burg has not been maintained, so it may not work well with the newest grub2.

 Last update 2010
[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list)

Grub2 or burg only chain load to working Windows, so you have to fix Windows to get grub to be able to boot them. Grub just forces a jump to the Windows PBR - partition boot sector and then Windows takes over.

If XP says bootmgr missing, it has been converted to a Vista/7 partition boot sector. I ran chkdsk from Windows 7 repair CD on my XP and it did the same thing. It converted PBR to want to use bootmgr. You can use testdisk to restore from backup if you have only overwritten it once. Or use Windows 7 to write the old PBR.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

OR:

 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 boot sectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by abdorefky on 2013-03-25
this kind of another questions so u dont have to read the whole article ( i know i respond after some time because of study ;/) 

i am going to do is repair each windows boot with flag on it's partition to separate boot file's .

grub is great that i can boot to windows 7 without bootmgr :) but why windows activation alert's me ? does activation has something with bootmgr ? :O (1)

my grub menu sometime's get's big and the other time return small ? any idea ? (2) 

that testdisk tool look interesting :)

---

### Post by oldfred on 2013-03-25
Grub does not bypass bootmgr or ntldr. Windows boots from MBR (like all BIOS systems), but then MBR loads and finds PBR or partition boot sector with more code. The PBR will refer to bootmgr or ntldr to continue to boot Windows.
All grub does is bypass MBR and jump straight to PBR to let Windows then take over.

While mostly Vista, it shows BIOS/MBR booting which is how computers have booted since first hard drive in mid 1980s and still boot. Except the new UEFI systems.
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by abdorefky on 2013-03-26
[B]i have read the whole article on the that link , i thought the grub was booting directly from winload.exe
looks like i had an extra bootmgr on windows xp partition due to the many boot repair's before .
but i am sure that if i did tried to change the resolution from grub the boot will go down again. 

doesn't matter now , i have some exam's this week and after finishing i will repair windows xp and 7 genuine , reinstall grub again , after that i go change the resolution to see if the problem will occur again or not ;/[/B]

---

