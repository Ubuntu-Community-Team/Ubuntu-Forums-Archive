---
title: "Dual boot Vista/Ubuntu"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Durrane on 2007-11-04
I recently installed Ubuntu (Gutsy Gibbon) on my hard drive, which already had Vista installed on it. I created a new partition using the install wizard with Ubuntu.

The boot loader for Ubuntu does not recognize my Vista installation at start up. After crawling some support sites I learned about about Grub and found that there was no reference to Vista in my menu.lst file, so I added this:

title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

When I try to run Vista from the boot loader I get a very quickly flashing blue screen error and then the computer restarts. If I select Vista again I get the Vista prompt about an error during startup asking me if I'd like to try booting in safe mode (this made me happy, because at least that means that Vista is still kicking around - right?) Trying to boot in safe mode gives the same problem with the blue screen.

Any help you could offer is appreciated. Obviously I am a novice at this stuff, so please bear with me.

---

### Post by Pumalite on 2007-11-04
You could try changing the Windows entry from 'root' to 'rootnoverify'. If you have more than one drive, you have to map it. Post:
sudo fdisk -lu

---

### Post by Bablefish on 2007-11-04
I literally just found out about this dual boot program you might want to give it a try

[http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by candtalan on 2007-11-04
> **Durrane said:**
> 
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1


I am  not any expert, however the hd0,0 looks a bit strange. It suggests that vista is being booted from hard drive 1 in its zero partition. Whereas hard drive 1 could easily be correct, I am not aware of a zero partition.

hth

---

### Post by Pumalite on 2007-11-04
No. (hd0,0) looks OK. to me. Windows usually installs in first partition of first hard drive, and Grub starts counting from '0', therefore: (hd0,0)

---

### Post by Durrane on 2007-11-04
Here you are, Pumalite:

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33353335

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58595797    29296875    7  HPFS/NTFS
/dev/sda2        60661440    78236549     8787555   83  Linux
/dev/sda3        59167395    60661439      747022+  82  Linux swap / Solaris
/dev/sda4        58605120    59167394      281137+  83  Linux

Partition table entries are not in disk order


I look into that boot program as well, Bablefish.

Cheers.

---

### Post by TuxTwig on 2007-11-04
I have a similar problem, although my Windows Vista boots, but after the Microsoft loading screen, all I get is a black screen. Some people have posted about Linux taking up space in Vista partition and thats why its slow, but like you, Linux hasn't touched my Vista partition. Now when I boot, all I get is a GRUB Error 15.

---

### Post by Pumalite on 2007-11-04
Did you make the changes I suggested? Did you use Vista partitioner to allocate space to Ubuntu before you installed?
All you need is change 'root' to 'rootnoverify'. But using Vista partitioner is essential, otherwise Vista doesn't let you run anything in that computer.

---

### Post by Sutukh19 on 2007-11-04
I am wanting to try out Sabayon Linux; I am currently dual booting UBUNTU Gutsy and WinXP, What is the best method for me to install Sabayon in place of Ubuntu on my system as I already have another laptop running UBUNTU. I may be interested in triple booting if that is possible also.
__________________

---

### Post by Durrane on 2007-11-04
Pumalite,

Whoops, sorry. I forgot about your "rootnoverify" point. I did this and... I almost got excited because the Vista load screen now appeared for about 0.5 seconds before I got that blue screen flash again (I don't think that this happened before, but I might have missed it).

I don't have multiple drives, so this is not an issue.

Cheers.

---

### Post by Pumalite on 2007-11-04
What about using the Vista partitioner? If you just partition with Ubuntu Live CD, you have to reinstall.

---

### Post by Durrane on 2007-11-04
Darn. I used the Ubuntu Live CD to partition my drive before installing. What does this mean? (Spell it out for me.)

Do I need to reinstall Vista? Ubuntu? Both? Is my data on the Vista partition lost?

---

### Post by Pumalite on 2007-11-04
I'd use Super Grub to restore your Vista MBR: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Once in Vista you probably have to go to Administration>Hard drive (never used Vista) and allocate space for Ubuntu. Then reinstall Ubuntu and this time there should be no problems.
(you can use your Vista installation disk too. Find 'Recovery'. I'm sorry but I've never done it. there be somewhere a command like this: FIXMBR>FIXBOOT)(in XP you hit 'r' for Recovery and then>FIXMBR>FIXBOOT)

---

### Post by TuxTwig on 2007-11-04
Pumailite, I've tried using Supergrub to both fix the boot of Windows and boot Vista. I still get the black screen and Vista doesnt load. I'm not sure but I think this will happen to Durrane as well.

---

### Post by Durrane on 2007-11-04
Well I am about to try it but you have damaged my confidence TuxTwig ;)

---

### Post by Pumalite on 2007-11-04
Maybe your Vista is hosed. Super Grub does the job. Maybe is a matter of following the instructions more carefully.

---

### Post by WeeWoh on 2008-03-29
Hmmm.. I have 45GB of free space on my 120GB hdd. The Vista partitioner wont let me resize it and i cant use the kubuntu partitioner because it'll mess up vista. Actually, you cant use anything other than the vista partitioner because itll mes up vista. This is something to do with the fact that after the partitioner has done its stuff, when you boot vista it thinks it has last been mounted by Windows NT4 which is no longer supported and crashes.

Any help here? Ive dual booted my friend's laptop using ubuntu and windows xp so why cant i do it with mine? I HATE VISTA!!!

---

### Post by Pumalite on 2008-03-29
Look, I've never used Vista, but this is the first I've seen where someone says that the Vista partitioner 'won't let him allocate free space for Ubuntu'. Can you give more details?

---

### Post by WeeWoh on 2008-03-29
Sorry ive just found out that its because i have a dell laptop and so dell locks the partitioner options

---

### Post by pieisgood4589 on 2008-03-29
> **WeeWoh said:**
> Sorry ive just found out that its because i have a dell laptop and so dell locks the partitioner options

Uh, no they don't, I just installed Ubuntu and made it dual boot with XP... :confused:

---

### Post by WeeWoh on 2008-03-30
> **pieisgood4589 said:**
> Uh, no they don't, I just installed Ubuntu and made it dual boot with XP... :confused:

I have a dell vostro 1000 with an AMD turion 64 x2 tl 60 with 2gb of RAM running windows vista buisness. The windows vista partitioner DOES NOT WORK. Apparantly this is a dell OEM thing.

I have downloaded a kubuntu 7.10 AMD 64 version because i wanted to mess around with linux and a 64 bit OS. I have used kubuntu before and prefer it to ubuntu because its prettier.

I cant shrink the vista partition using the kubuntu live cd because that will crap up vista due to some mount thingy involving microsoft not supporting NT4 anymore...

---

### Post by WeeWoh on 2008-06-26
Nope, wait done it. Woo for Debian!!! However, Vista, being Vista has tried to convert the disk to a dynamic disk and pissed everything up. Now Ubuntu works yay!!

---

