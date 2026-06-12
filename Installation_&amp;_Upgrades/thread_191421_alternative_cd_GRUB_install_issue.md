---
title: "alternative cd GRUB install issue"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by spookware on 2006-06-07
I had an issue with the installation (dapper) of GRUB on one of my boxes. 

On one box it installed just fine. This system has two hard disks. One for my XP installation and one for various other operating systems (BSD, Linux, etc.. )

This system worked just fine. I installed using the text mode installer and at the end it asked me where I want GRUB installed. I put it in the boot sector of the primary partition on my Linux drive. I do this because I prefer to use Windows XP's boot manager. I generally just suck out the boot sector of the primary partition and then configure NTLDR to list it. I prefer it this way as I tend to wipe my NIX partitions much more frequently than my Windows one (do lots of kernel dev stuff and tend to hose things up). So above all things I don't want to get GRUB or LILO stuck in my MBR.

Now on another system (A Dell Optiplex GX620 using SATA) I only have a single hard disk. I configure this thing for dual boot as well. The initial partition is running Windows Vista Beta 2. I went through the install and partitioned everything up just right. Only at the end where I should have received the option asking me where I wanted it to put GRUB it just automatically installed GRUB to the MBR without giving me any choice about it.

So at this point I am kind of pissed. Is this normal that if I only have one hard disk dapper just automatically installs GRUB to the MBR? IMO this is junk. The installer really should not install grub some place without asking first. Sorry to rant a bit but I just lost like 3 hours of my time to this little annoyance.

Anyway I managed to get everything configured so that I can get in to both OS's now but GRUB is now my boot loader. Can't have that. 

So now the questions. Does anyone know how I can manually install GRUB to the bootsector of a partition (not the mbr)?

Specifically I want to stick it in to the bootsector of /dev/sda2

Also if anyone knows how to reinstall the Vista MBR could you please let me know. I already tried bootsect.exe but that seems to only install the boot sector not the mbr and fixmbr seems to have disappeared from the vista install media.

Thanks

P.S. Is it normal that the installer used the i386 kernel image? (this is a P4 box). It is a problem that was easily remedied, I just installed the 686 SMP kernel and all the supporting junk just fine. Just wondering if the installer no longer tries to figure out your arch and instead just plops the i386 one down.

---

### Post by aysiu on 2006-06-07
As far as I know, the Dapper Desktop CD installs to the MBR without asking you but the Alternate Install CD asks you where you want to install it. Are you saying the Alternate doesn't ask you either?

---

### Post by spookware on 2006-06-07
Correct. I am using the alternative CD specifically because I wanted to be able to pick where GRUB ended up.

As stated on one system with two parallel ATA hard disks it worked just like breezy. IOW it asked me and I got to type in where I wanted GRUB to be installed two.

However on the dell in question it did not. I was sitting here watching it waiting for it to ask me and then it said "installing GRUB" flew right by that and then told me to reboot.

I think that it might be one of two things. The dell has SATA not parallel ATA and I see some forum members are having various issues with SATA and the GRUB installer.

That or it is the fact the bootable primary partition had windows vista beta 2 on it. Vista Beta 2 has a new boot loader (not NTLDR) and it does things differently. It is meant to unify the bootloader code for both classic BIOS based booting and EFI booting. I noticed one thing that is odd on this system. I installed gparted and took a look at what it said was there. It displayed a 1MB hole in between the start of the disk and the Windows Vista Partition (which is the bootable active primary partition). 

I wonder if Microsoft left some space there for the new fancy bootloader or maybe to support conversion to the guid based partition table that EFI uses. Any how, maybe that mucked up the installers ability to tell I had an OS installed and so it just assumed I wanted grub in the MBR.

Anyway, it is not that bad because as I said I can get in to both OS's now. However I would like to rectify the situation by installing grub to the bootsector of /dev/sda2 then extracting that bootsector and configuring windows bootloder to load it.

I need to figure out:
(1) How to install GRUB to /dev/sda2
(2) How to extract the bootsector (I already know how to do this)
(3) how to get Windows Vista Beta 2 to put it's MBR back in place.

Cheers

---

### Post by mannheim on 2006-06-07
[QUOTE=spookware]
I need to figure out:
(1) How to install GRUB to /dev/sda2
(2) How to extract the bootsector (I already know how to do this)
(3) how to get Windows Vista Beta 2 to put it's MBR back in place.
[/QUOTE]


For question (1), "info grub" turns up this advice, passed on here by me, with little understanding of grub:

```
     
grub> setup (hd0)

   This command will install the GRUB boot loader on the Master Boot
Record (MBR) of the first drive. If you want to put GRUB into the boot
sector of a partition instead of putting it in the MBR, specify the
partition into which you want to install GRUB:

     grub> setup (hd0,0)

   If you install GRUB into a partition or a drive other than the first
one, you must chain-load GRUB from another boot loader. 
```

I am pretty sure that the breezy and hoary text-mode installers **asked** whether you wanted to install grub. (I never investigated what happens if you reply "no".) So if you ever go down this road again, you could try installing breezy and then upgrading to dapper.

---

### Post by spookware on 2006-06-08
I now have a better understanding of what is going on so I thought I would update this incase anyone runs acros it in a search.

(1) apparently the ubuntu installer has a less than spectacular system for OS detection. I ran across a cople of bug reports over on launch pad under "os-prober" that say the installer looks for C:\windows\win.com when looking for OS's. This file does not exist on vista. It seems that this is why the GRUB install screens were not ofered.

(2) instaling grub to /dev/sda2 was a piece of cake. I read through all the grub doc and found that grub-install /dev/sda2 did the trick. 

(3) You can extract the mbr or boot sector using the dd command. example:

dd if=/dev/sda bs=512 count=1 of=/home/user_name/mbr.bin

(4) You can configure vista to load this file. Get the file over to vista's cdrive via floppy, tumb drive, etc... then open a command prompt as "admin" and execute the following commands to add the boot sector to windows own OS loader

bcdedit /create /d "Linux GRUB" /application bootsector
bcdedit /set device boot
bcdedit /set path \mbr.bin
bcdedit /displayorder {ID} /addlast

where {ID} is a GUID (big long string of nummbers) that the first command spit out. if you do not see it run:

bcdedit /enum all /v

This will list all entries in the boot managers database. look for one that says Real mode bootsector and has te descripton "Linux GRUB" or what ever you types in on that first command. 

This will alow you to chain load grub from the Windows Vista bot loader.

One thing I did run in to is that the GRUB menu will not be displayed on the system I am working with. GRUB works. you can still use the arrow keys to move around and select an OS it is just that the scren in blank so you ned to have the list memorized or let the timer expire and it will pick the default option.

I don't know if that is just with my machine though. Several bug reports about grub splash screens causing that in early dapper flight tests ended up cuasing the splash screen to be removed. So I don't know if it is specific to my box or not. (IOW GRUB might be having a hard time reinitializing the video card for some reason).

I susspect that the vista boot loader runs the the bootsector in virtualx86 mode and maybe that is the problem.

So anyway long story short is that should help anyone configure a similar system. Everything now works ok except I can not seem to get Vista to rewrite the mbr with it's master bootrecord. Earlier builds of Vista included a tools called fixntfs.exe that would do this but that is been replaced with bootsect.exe and as of beta2 I can not figure out how to get it to write the MBR. It just seems to write the boot sector.

---

### Post by milon on 2006-09-01
to change back winloader in mbr try booting with windows cd and type in comline this:

C:\...> fdisk /mbr

!!! but before you'll do this, save Master Boot Record in file
then you can restore it with any live cd:

# dd if=/home/user_name/mbr.bin bs=512 count=1 of=/dev/sda

---

### Post by eduardsan on 2007-03-23
> **spookware said:**
> I now have a better understanding of what is going on so I thought I would update this incase anyone runs acros it in a search.

(1) apparently the ubuntu installer has a less than spectacular system for OS detection. I ran across a cople of bug reports over on launch pad under "os-prober" that say the installer looks for C:\windows\win.com when looking for OS's. This file does not exist on vista. It seems that this is why the GRUB install screens were not ofered.

(2) instaling grub to /dev/sda2 was a piece of cake. I read through all the grub doc and found that grub-install /dev/sda2 did the trick. 

(3) You can extract the mbr or boot sector using the dd command. example:

dd if=/dev/sda bs=512 count=1 of=/home/user_name/mbr.bin

(4) You can configure vista to load this file. Get the file over to vista's cdrive via floppy, tumb drive, etc... then open a command prompt as "admin" and execute the following commands to add the boot sector to windows own OS loader

bcdedit /create /d "Linux GRUB" /application bootsector
bcdedit /set device boot
bcdedit /set path \mbr.bin
bcdedit /displayorder {ID} /addlast

where {ID} is a GUID (big long string of nummbers) that the first command spit out. if you do not see it run:

bcdedit /enum all /v

This will list all entries in the boot managers database. look for one that says Real mode bootsector and has te descripton "Linux GRUB" or what ever you types in on that first command. 

This will alow you to chain load grub from the Windows Vista bot loader.

One thing I did run in to is that the GRUB menu will not be displayed on the system I am working with. GRUB works. you can still use the arrow keys to move around and select an OS it is just that the scren in blank so you ned to have the list memorized or let the timer expire and it will pick the default option.

I don't know if that is just with my machine though. Several bug reports about grub splash screens causing that in early dapper flight tests ended up cuasing the splash screen to be removed. So I don't know if it is specific to my box or not. (IOW GRUB might be having a hard time reinitializing the video card for some reason).

I susspect that the vista boot loader runs the the bootsector in virtualx86 mode and maybe that is the problem.

So anyway long story short is that should help anyone configure a similar system. Everything now works ok except I can not seem to get Vista to rewrite the mbr with it's master bootrecord. Earlier builds of Vista included a tools called fixntfs.exe that would do this but that is been replaced with bootsect.exe and as of beta2 I can not figure out how to get it to write the MBR. It just seems to write the boot sector.

I've been wasting all day trying to configure my new Dell Inspiron 6400 for dual booting Vista and Ubuntu and spookware's post has been very helpful. Just one commment, after writing these bcdedit commands my system directly run into Ubuntu leaving no option to choose Vista.

I think that the {ID} part needs to be written on every command (at least that worked for me), so the sequence of commands looks like this:

bcdedit /create /d "Linux GRUB" /application bootsector
bcdedit /set {ID} device boot
bcdedit /set {ID} path \mbr.bin
bcdedit /displayorder {ID} /addlast

---

