---
title: "Yet Another GRUB problem..."
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by flyinggreg on 2007-11-25
I have a 2 HDD system - PRI MASTER IDE is 120MB (where I am trying to install Ubuntu) & SEC MASTER IDE is a 80MB with Win2k installed.

I can't seem to get Ubuntu to install on my 120MB HDD!  I have no problems with getting into my Win2k system at all...so this doesn't seem to be the typical GRUB problem.

I did notice that there was installation options for GRUB.  The install appears to go smoothly, but then when I come to removing the cd and system boot up I go straight to the Win2k drive!  I have tried selecting the Ubuntu disk at system start using the bios menu to select the Ubuntu drive and it still goes to Win2k.  During the installation...I never got any options for the bootloader or finding Win2k on my other IDE...which I thought was weird!  I then stuck in the LiveCD and analyzed my HDD and found that GRUB was never written.    So I  MKDIR /BOOT/GRUB and ran GRUB-INSTALL and it wrote the GRUB menu.lst etc.  I reboot the system and then GRUB fails with:  "Booting from local disk; isolinux: Disk Error 01, AX=0201, Drive 80"

I have installed Edgy awhile ago and loved it!  I needed the second HDD with Windows and since then I have been so frustrated!  I have tried downloading and installing from Dapper to Gutsy with no luck.  It almost appears something has changed with GRUB that is making this a nightmare (maybe I am wrong?).

Thanks ahead of time!

---

### Post by Pumalite on 2007-11-25
Is not a Grub problem. Make the drive with Windows (89) 1rst Master and the drive you want to install 2nd Master. Then install ubuntu and let Grub install to MBR.

---

### Post by flyinggreg on 2007-11-25
> **Pumalite said:**
> Is not a Grub problem. Make the drive with Windows (89) 1rst Master and the drive you want to install 2nd Master. Then install ubuntu and let Grub install to MBR.

I'll give it a shot.  Out of curiousity...why can't Ubuntu be on the PRI master?

---

### Post by Pumalite on 2007-11-25
Is better to leave that for Windows. The whole system works better. Grub installs by default in sda1. It's easier to dual boot.

---

### Post by meierfra on 2007-11-25
> Grub installs by default in sda1.

Actually  it  installs to the MBR of sda, which comes before sda1.

---

### Post by flyinggreg on 2007-11-25
Ok, I swapped the cables so Win2K is PRI master IDE & Ubuntu is SEC master IDE.  I saw during the install that GRUB should have installed to Hd0.  Now I get the infamous GRUB failed error 18!

Shouldn't GRUB install to hda since it's an IDE not a SATA drive?  I am pretty new to linux...thought SATA was sda.  Or....is that the problem...GRUB tries to install to sda instead of hda?

Geesh...I don't remember having ANY of these problems a year ago installing Edgy!

So...now what is the next step?

---

### Post by flyinggreg on 2007-11-25
Nuts!  I started Ubuntu with the LiveCD and cannot see /boot/grub in my file system nor my Win2k hard drive...what gives...?

---

### Post by meierfra on 2007-11-25
> cannot see /boot/grub in my file system

Did you mount the ubuntu partition? If you need help with that, open a terminal, (Application->Accessories->Terminal), type

```
sudo fdisk -l
```
(l is a lowercase L)
and post the output

---

### Post by flyinggreg on 2007-11-25
I checked my fdisk -l & got my 160GB drive at hdc...which is weird it should be hdb.

I also read [http://users.bigpond.net.au/hermanzone/p15.htm#Edit_usrsbinupdate-grub](http://users.bigpond.net.au/hermanzone/p15.htm#Edit_usrsbinupdate-grub) for Error 18...I think this is a REALLY stupid mistake on MY part....I think my IDE cable is installed incorrect...DOH!!!

I just installed this as a new drive with a 40-pin cable...so I am going to open up the box and see if I boneheaded this one.

---

### Post by flyinggreg on 2007-11-25
Ok...well, I checked the cables, bios setting, etc.  Everything looks in order.  Here's the output from fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19270   154786243+  83  Linux
/dev/hdc2           19271       19457     1502077+   5  Extended
/dev/hdc5           19271       19457     1502046   82  Linux swap / Solaris

```

Also, when I run GRUB it cannot find stage1...granted I think that is from the LiveCD and not from the system.

BTW - my system is only 2 years old with a AMD Athlon64 3500+ running @ 2.2G

---

### Post by meierfra on 2007-11-25
This sounds more and more like another case i was involved in (and still is unresolved).

In particular, the 40pin cable and   the "isolinux: Disk Error 01, AX=0201, Drive 80"".
Check this out:

[http://ubuntuforums.org/showthread.php?t=609548#12]("http://ubuntuforums.org/showthread.php?t=609548#12")

(Start at post 12)
The basic recommendation (by Herman) was to check all the connections and replace the 40pin by a 80pin,

---

### Post by flyinggreg on 2007-11-25
Yeah - I read that and it got me wondering.... maybe the 40-pin can't be used above certain GB and it's causing all the problems.

Guess, I just need to run to the parts store tomorrow...

---

### Post by flyinggreg on 2007-11-26
Oh man...I finally solved...and it's so simple it's silly...

I opened up the computer and rechecked the cabled one more time and realized that I had the DVD & CD-RW set as masters on both IDE buses **_CABLES_** even though the **_jumpers_** on the DVD, CD-RW, IDE1, IDE2 were all set correctly.  So I swapped the cable positions...and everything WORKED!!!  


meierfra, I had the SAME exact issue:
> This sounds more and more like another case i was involved in (and still is unresolved).

In particular, the 40pin cable and the "isolinux: Disk Error 01, AX=0201, Drive 80"".
Check this out:

[http://ubuntuforums.org/showthread.php?t=609548#12](http://ubuntuforums.org/showthread.php?t=609548#12)

(Start at post 12)
The basic recommendation (by Herman) was to check all the connectios and replace the 40pin by a 80pin,

What worked for me was:
[LIST=1]
[*]Setup IDE bus cables as:  PRI MASTER Windows; SEC MASTER Ubuntu
[*]Reinstall Ubuntu to hdb (hdc in my system)
[*]Ensure the bios is set to boot from the Windows drive
[/LIST]

MOST IMPORTANT!!!!!   Make sure the IDE cables are connected correctly as if they were CS (Cable Select) - the HDD is closest to the motherboard & CD/DVD is at the end - it didn't matter to the system whether or not the components were jumpered master/slave

Hope this helps!

---

### Post by Herman on 2007-12-03
>  The basic recommendation (by Herman) was to check all the connectios and replace the 40pin by a 80pin,:) That is not so important for booting, I'm sorry if I confused anyone in that other thread.  If you have a damaged cable, then that could affect booting.  
It is important for the speed of your data transfer but not really for booting. 
 :)...and I said '80 conductor', not 80 pin, there isn't any such thing as an 80 pin plug to my knowledge, it's the number of wires in the ribbon that we're counting here, but the plugs are still the same old 40 pin plugs.  It has something to do with electrostic intereference or induction between conductors in the ribbon cable, the 80 conductor cable is far superior in performance to the 40 wire cable, even though the wires are smaller. :)


What IS most important is the way your cable is plugged in and how your IDE hard drive jumpers are set.
> MOST IMPORTANT!!!!! Make sure the IDE cables are connected correctly as if they were CS (Cable Select) - the HDD is closest to the motherboard & CD/DVD is at the end - it didn't matter to the system whether or not the components were jumpered master/slaveIt probably doesn't matter to an operating system once it has booted.

To the BIOS, and GRUB, it **does** matter how the IDE hard drive cables are plugged in and jumpered. I think so anyway, I will try to find out more and do some tests in case there is something more I can learn about this.

If you have the master/slave type of IDE cable, (with black plugs), you need to set your hard drive jumpers in the Master and Slave positions.
If you have a 'Cable Select' IDE hard drive ribbon cable (it has a blue plug to plug into the motherboard, a black plug for the 'Master' drive, and a grey plug for the 'Slave' hard disk.

Often, people who "know what they are doing", can rig IDE hard drives and jumper setting up in strange ways and still get an operating system to boot up. but the problems show up when someone else tries to add another hard drive to the system.

Once again, I'm sorry if the other thread is a little misleading, but it reflects the order I thought of things in, not the order of their importance to booting. It's my fault if that thread misleads anyone.

Regards, Herman :)

---

### Post by Pumalite on 2007-12-03
:

   1. Setup IDE bus cables as: PRI MASTER Windows; SEC MASTER Ubuntu

So. I wasn't so far in my first post.
' Make the drive with Windows (89) 1rst Master and the drive you want to install 2nd Master. Then install ubuntu and let Grub install to MBR.'
__________________

---

### Post by meierfra on 2007-12-03
> and I said '80 conductor', not 80 pin, there isn't any such thing as an 80 pin plug to my knowledge, 

Sorry for mixing-up things. I'm completely ignorant with respect to any kind of hard ware. 


> I'm sorry if I confused anyone

Don't be sorry for my ignorance.:)

---

