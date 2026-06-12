---
title: "Major HDD+GRUB Problem, HELP PLEASE!"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by zenthor on 2008-09-05
Okey so heres my history.

Some time ago I decided to give Ubuntu a try, I installed it on my 40Gb HDD, and left the 60GB HDD that i have for media, so I had, 20Gb WinXPSP2, and other 20Gb on ubuntu+Swap. At the begin I had problems with Grub and I got it fix to boot correctly to WinXP, cause it didnt.

Time passed and i stopped useing Ubuntu cause most of my programs of University are for Windows. So yesterday I decided to plug in my CD reader, and put the WinXPSP2 Cd inside, and deleated the partitions where Ubuntu was, and SWAP too, cause I needed more space, and I got in Ubuntu and I didnt find a way to uninstall it.

I restart the computer and heres where all the "fun" begins.
First, Grub appears to still be on my system, and throws me error 17, while grub 1,5 was loading or something like that.
So I ran into my aunt computer to get help from forums, and in the Ask/Answer section i find more people with the same problem, and I anyways, posted my own, and i got replys about useing the following method:

Use Recovery Console from the WindowsXP installer CD.
Do the "fixmbr" command

This should repair you damaged mbr by the Grub.

So I did that, restarted the computer, and the problem was still there, but the grub error number changed, i cant remember very well if it was to 22... or 15.
So i read a little more, about this issue, and on the recovery console I do the "fixboot" command, and "bootcfg /scan" and "bootcfg /list" and "bootcfg /rebuild"(wich only adds an extra entry on the list, dosent change it completly), but to for my surprise, it didnt detect my old WindowsXP installation, only a uncomplete instalation of WindowsXp i had made before on the place where Ubuntu was (this i did afterfirst try with fixmbr, but couldnt complete instalation cause i couldnt boot to this new instalation, cause grub still got error)

So now, i read a little more and ask around, and i see the posible solution is copying a pair of files, from the WindowsXp installation CD, to the place I had my WinXP, such as this two:
cd drive:\i386\NTLDR (or simillar name i cant remember)
cd drive:\i386\NTDETECT.COM 
I did both, and deleated the partition where the uncomplete winxp was. And still got nothing going on, grub still appearing with diferent problems.

So i give on asking on forums, and stuff and tryied to use a little logic in here, and i thought, re install Ubuntu, so it reinstalls grub, or repairs it, and then check if im able to boot to my old WinXp.
So i did so, and installed ubuntu+swap on 9GB, and left free space of about 11Gb, and at the end of the disc was the 20Gb partition with my WinXP. After successfully installed ubuntu, I entered ubuntu again to see if i had some more replys on my problem (cause after installing ubuntu, i tryied to boot to winxp with no luck, got problem saying couldnt find ejecutable or something like it), so I thought maybe i install a new winxp on 7gb from the 12gb i had free in the middle of the disk, so as it would be new installation, grub would see it, and i would have access to that new winxp partition, do a rescue of my files on the old one, and then deleat both, and install just one on all the space (stupid me, i could rescued the information from ubuntu already but i didnt notice back then), so i tryied to install again winxp, so i finish doing the "blue/yellow" part of it, and it asks me to restart the computer, so it was supoused to boot to the new winxp, finish installation and continue but here then i couldnt boot to the new or old winxp, so i then i try to boot to ubuntu to search for more help, and then it says cylindre out of maximum allowed by the BIOS, or simillar problem, something wrong with a cylindre :( so i proceed to deleat the "new" winxp partition, the old ones of the ubuntu and re install ubuntu again, with no luck, i tryied for 3th time and no luck, throws me again the same problems on the same partitions, if i try to boot to windows, it says there was no ejecutable or something like it, if i try to boot to ubuntu it says the problem with the cylindre out of BIOS.

So now im useing the LiveCD, i see my old winxp is ok, is still here, all complete aparently, and all the media on the 60GB HDD too, and i cant rescue my information from the livecd since i need to do an update to ubuntu so it recognizes my 20GB portable HDD/mp3 (toshiba GIGABEAT).

please help me, i dont know what else to do.

Maybe someone can guide me to edit from the livecd the grub, to check if its commands to mount points are ok, and try this, or a way to rescue my information from the 40gb hdd (on the 20 gb partition where the old winxp is), and then format the whole hdd correctly so the grub is gone, or will it remain since it is on the mbr? T_T

please please help me :'(

---

### Post by pytheas22 on 2008-09-05
From the errors regarding malformed cylinders, it sounds like you have a corrupted partition table or other problem with the disk structure, which makes sense given all of the changes that you've made to the partitions.  There's a program called testdisk that might be able to help.  You can install it from the Ubuntu live CD with:
```

sudo apt-get install testdisk
```

And run it with:
```

sudo testdisk
```

I don't have time right now to explain completely how to use testdisk, but it's pretty intuitive.  You can check your disk structure for errors and, if you want, try to repair them.  testdisk saved me once when I had a similar problem caused when Windows XP tried to install itself in an invalid partition that partially overwrote one of my Linux partitions.

testdisk also comes with a useful program called photorec for recovering files.  There may be better ways for you to try to recover your files now--photorec is meant to be used when your file system is completely dead, but your situation isn't that bad yet--but it might still be useful.  You can run it with:
```

sudo photorec
```

Also, you may want to check out [Super Grub Boot Disk]("http://www.supergrubdisk.org/").  I've never used it myself but I know that it's useful for repairing corrupted boot partitions (I *think* that it can repair Windows mbr now as well as grub).

Let me know if you make any progress.

---

### Post by zenthor on 2008-09-05
thanks pytheas, u give me hope saying my problem isnt that bad, i hope i can get my hdd to work again and maybe my winxp too would be awsome. I downloaded and installed testdisk as you said and intuitively used it to i presume fix my problem, im going to restart my computer to see the changes, if it works ill let you know instantly, else, ill have to load live cd of ubuntu again wich may take a while, i hope you are still around back then to see the changes.

A really really deeply thanks,
Esteban

---

### Post by zenthor on 2008-09-05
okey pytheas, first of all, i want you to let me know where we are going, with the testdisk i deleated succesfully the last ubuntu and swap partitions i had i couldnt get in windowsXP, and when i try to access the hdd where the winxp is, appears grub error 22, now tell me, where are we going>

1. Shall I part the 40Gb disk again, leave the old 20GB XP, and on the 20GB left, install Ubuntu, so the grub menu/list works again, and then haveing ubuntu working, try to resurect my XP partition/boot. And in a future later lets say a week later try to correctly uninstall ubuntu, to aboid haveing grub menu problems ever again.

or

2. Shall I leave as free disk space the 20Gb left on my 40GB disk, leave the old XP partition as it is, and work with the liveCD of ubuntu/Xp installer CD to try to fix the MBR/partition table of the hdd to make it work, and then use the free disk space freely.


Let me know so i know what to do again.
Right now, the situation is like this
from Gparted

/dev/sda (38.29GiB)

Partition unallocated
Filesystem unallocated
Size 18,60GiB

Partition /dev/sda1
Filysystem ntfs
Label Zet
Size 19,68GiB
Used 14,23GiB 
Unused 5,45GiB
Flags boot

Partition unallocated
Filesystem unallocated
Size 7,84MiB

Zet partition, is where my old WinXP is.

Thanks a lot again.

---

### Post by zenthor on 2008-09-05
so now i was just trying to check testdisk, since im still on the ubuntu livecd, and i tryied to install/open testdisk again, and the following error comes from terminal

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ 

any ideas why this happend?

---

### Post by caljohnsmith on 2008-09-05
Zenthor, if for some reason "fixmbr" didn't work, you can reinstall a Windows MBR by doing the following from the Live CD:
Download the "ms-sys" package; if you are using 32-bit Ubuntu, use:
```
wget "http://debian.oregonstate.edu/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_i386.deb"
```
Or if you are using 64-bit Ubuntu:
```
wget "http://debian.oregonstate.edu/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_amd64.deb     
```
Next install it:
```
sudo dpkg -i ms-sys*.deb
```
Next, make sure you know which HDD you want to install the Windows MBR to:
```
sudo fdisk -l
```
Check which HDD it is: sda, sdb, etc. Then run:
```
sudo ms-sys -m /dev/sdX
```
Where sdX is the HDD. That will overwrite Grub with a Windows MBR. Let me know how it goes or if you need more details/info.

---

### Post by pytheas22 on 2008-09-05
I think that the best course of action for now is first to try to get your files off of the Windows partition at /dev/sda1.  If you run these commands:
```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
sudo nautilus /media/sda1
```

you will hopefully see your Windows partition mounted, and can copy the files off to external media (if you get errors trying to run those commands, please post them here; you may need to try force-mounting the Windows partition if it's damaged).  That's the most important thing for now, because you don't want to lose your files.

Once you have your files saved, I would first try caljohnsmith's suggestion for repairing the MBR.  If that doesn't work, I would next try using the Windows XP CD to repair it.  If even that fails, then I'd reinstall Ubuntu, and hopefully you will get grub fixed and be able to boot to Windows again.

Once you can boot to Windows, we can reformat the Ubuntu partition into NTFS or FAT so that you can have that space to use on Windows.  grub would not be harmed, so you could still boot to Windows using grub.

In a worst case, if you are entirely unsuccessful in getting Windows to boot again, you can erase all partitions on the drive completely using the Ubuntu live CD, and reinstall Windows.
> 
so now i was just trying to check testdisk, since im still on the ubuntu livecd, and i tryied to install/open testdisk again, and the following error comes from terminal

testdisk probably wouldn't install because you need to reactivate the Ubuntu repositories.  Go to System>Administration>Software Sources and make sure that all the boxes are checked under the "Ubuntu Software" tab.

Let us know how it goes.

---

### Post by zenthor on 2008-09-05
thanks to both, i did what caljhon said and still not working, i can access the media from the windows partition, and i copyied all the important information from the windows partition to other partition on my 60GB hdd, but im still concerned about the cilindre thing, if i deleat all the partitions and re install windows, should the frub thing go away or part of the grub menu is still on the mbr?

right now im on my gf house, and i cant access my computer since its a desktop one i left at home, ill return on monday afternoon there so ill try to eliminate all the partitions then and install windows again only and let you know how it goes.

Thanks a lot again, ill be writeing you soon

Kind regards,
Esteban

---

### Post by pytheas22 on 2008-09-06
I'm glad you have your data recovered at least.

If you wipe the drive completely, that should solve the cylinder errors.  The easiest way to wipe the drive is to boot to the Ubuntu live CD and install gparted:
```

sudo apt-get install gparted
```

Using gparted, you can erase all partitions on the disk so that you can install Windows again cleanly.  gparted should be enough to solve the problem with the boot record, but if not, there are more intense ways to clear out the disk, so let us know.

---

### Post by zenthor on 2008-09-06
You dont have any idea of how thankful I am pytheas, you gave me hope my hdd wasnt totally ruined with the cylindre thingy and the grub getting on my mbr. Again you save me, thanks mate, i really hope once i begin to work at the university i save enouth money to get a new hdd where i have more than enouth space to install ubuntu again.

A very thankful,
Esteban

---

### Post by pytheas22 on 2008-09-06
I'm glad it's solved :)

If you still need more help getting Windows working again, of course let us know.

---

### Post by zenthor on 2008-09-09
Thanks a lot mate, i couldnt save my windows partition as i firstly wanted, but at last i saved all my data and i did what you said about deleating all partitions and doing it all over, from the beginning and its working. So thanks again :)

Esteban

---

