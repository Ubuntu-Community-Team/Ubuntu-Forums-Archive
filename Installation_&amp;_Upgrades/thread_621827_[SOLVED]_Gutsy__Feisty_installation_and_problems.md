---
title: "[SOLVED] Gutsy / Feisty installation and problems"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-11-24
Hi again!


I've completely wiped all partitions but the primary XP and hda4 one in the meantime, and have set up all other partitions new. After installing Xubuntu Gutsy and Puppy 3.01, I managed to get them finally booting up (Grub in hda5) - Gutsy only into bash and Puppy without internet. Somehow Xubuntu install-manager (also Ubunut and Mint) just won't install Grub correctly this way, I don't know why! At the end of installation there's always an error message coming up, saying 'Grub couldn't be installed. That's a serious error' or sth. like that (no menu.lst is written); that's why I always had to manually create the file!

Although there's a symlink to the actual vmlinuz-2.6.... file in /hda5/boot, simply using kernel (hd0,4)/boot/vmlinuz root=.... will NOT work; I'll have to use the full file expression AND the full initrd.img-statement (I thought booting should do without this one at first).

[COLOR="Blue"]**EDIT:**[/COLOR]
Anyway, then I tried to replace the 'bootsect.lnx' in my XP root-directory with the new hda5-bootsector and to edit 'boot.ini' accordingly. I've used the following command (in Xubuntu):
> dd if=[COLOR="Blue"]**/dev/**[/COLOR]hda5 of=~/bootsect.lnx bs=512 count=1
**[COLOR="Blue"]This (/dev/hda5) is valid, if the chainloaded Grub resides on partition 'hda5' / '(hd0,4)'! Adapt as needed.[/COLOR]**

My boot.ini looks like this (using the chainload-Xubuntu option as default):
> [boot loader]
timeout=4
default=c:\bootsect.lnx
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noguiboot /usepmtimer
c:\bootsect.lnx="Chainloading Grub/Linux"

[COLOR="Gray"]I wrote 'bootsect.lnx' to C:\ (under Xubuntu). Afterwards I couldn't boot the HDD at all - 'no bootable disk' - and hda1 isn't being recognized under Linux anymore; Gparted will show the partition as 'unknown'! I cannot imagine the 'dd'-command being the culprit, but I suspect Linux' NTFS-writing screwed up my XP-installation... or I made a mistake..? Now I wonder what I should do to revive the XP-installation - try to do 'fixboot' and 'fixmbr' from the recovery console or writing a new standard MBR with MHDD? What do you think?[/COLOR] -- by fixed now

>> [COLOR="Blue"]**Storing 'bootsect.lnx' to a stick and write it to C:\ under XP should be perfectly safe.**[/COLOR]

My current Gparted output:
Code:
/dev/hda1 'unknown'
/dev/hda2 p / fat32 - boot
/dev/hda3 p / extended
/dev/hda5 e / 'ext3' (Xubuntu 7.10 + Puppy 3.01)
/dev/hda6 e / 'reiserfs' - Set
/dev/hda7 e / 'ext3' (Xubuntu 7.04)
/dev/hda8 e / 'linux-swap'
/dev/hda4 p / 'unknown' - (ath - Syllable)



perixx[/code]

---

### Post by Pumalite on 2007-11-24
If you can boot a Live CD, post, from the Terminal:
sudo fdisk -lu

---

### Post by Pumalite on 2007-11-24
You can fix your MBR with Windows Installaion CD>Recovery>FIXMBR>FIXBOOT
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by perixx on 2007-11-27
Hi Pumalite!


I've just read you posting, but I managed to revive my XP-installation meanwhile:


```
/dev/hda1 'unknown'
/dev/hda2 p / fat32 - boot
/dev/hda3 p / extended
/dev/hda5 e / 'ext3' (Xubuntu 7.10 + Puppy 3.01)
/dev/hda6 e / 'reiserfs' - Set
/dev/hda7 e / 'ext3' (Xubuntu 7.04)
/dev/hda8 e / 'linux-swap'
/dev/hda4 p / 'unknown' - (ath - Syllable)
```


/dev/hda3 p / extended

is the 'extended' primary partition that CONTAINS all other extended partitions (marked with 'e'). So, all 'real' extended partitions within hda3 start counting from 'hda5' on (as can be seen above).

Actually, after really trying hard to get my XP-partition back to life again, I finally was successful!

Funny thing: neither 'Mbrwork' (Terabyte), 'MHDD', or 'Super Grub Disk' got me where I wanted to (I tried to zero out the EMBR, set hd0 (XP) active and use the 'Windows & MBR' option of SGD. The only result was booting into Grub of hda5 with SGD or into hda2 ('no bootable disk'-error).

I had to use the XP recovery console, switch to the inaccessible XP-partition (DSmile, install a new bootsector via 'FIXBOOT' and set that partition active again with 'DISKPART'. To my big surprise, the new bootsect.lnx file worked just fine, now pointing to hda5, where I have set up all my Linux boot options.

Either I haven't understood how SGD exactly works or it simply didn't work for the purpose of installing a new Windows-bootsector and bootloader; when using the WIN & MBR option it showed a message 'syslinux' something but nothing about writing a bootesctor or the ntldr, which apparently  was the real problem.

[COLOR="Blue"]**EDIT:**[/COLOR]
Obviously, the bootsector of hda1 (XP) was damaged - by writing the 'bootsect.lnx' I created out from hda5's bootsector with the 
```
dd if=/dev/hda5 of=~/bootsect.lnx bs=512 count=1
```
command - in Gutsy. So I think that ntfs-writing-support contains some bugs in Gutsy - like many other vital apps!
**ANYWAY, storing 'bootsect.lnx' to a stick and writing it to C:\ under XP won't harm at all! **

So far, I really can't recommend installing Gutsy from my point of view; nothing seems to work satisfying from start - if you even can start, that is (I can't). Even after installing to HDD, Gutsy only boots into root@root bash, where get stuck (Live-CD only boots into bash and needs 'startx' to kick off). Gparted will always auto-mount everything and crash after altering partitions and re-reading, 1280x1024 resolution will not boot (1600x1200 does) and so on... really a pain in the ***, so to speak. Feisty's really unproblematic in my experience, on the contrary - it just works out-of-the-iso-box.

One thing I can't explain, though - why Gutsy and Feisty wouldn't simply install / adjust the Grub on hda5. I suppose this is the reason for the most booting problems I have (no entries in the menu.lst, nor the optional parameters are auto-set as needed and I've got no clue on how to set them up). The installation simply cancelled at the point of Grub-installation -- why does Grub even HAS to be installed; why can't Ubuntu be installed without it and booted from an already installed Grub?? 


perixx****

---

### Post by perixx on 2007-12-06
Allright, this is where I have it messed up finally... :(

I got the same interruption & error message at boot-up with Feisty installation now, like I have it with Gutsy:
> [http://ubuntuforums.org/showthread.php?t=626963]("http://ubuntuforums.org/showthread.php?t=626963")

> fsck.ext3: Not a directory while trying to open ....
superblock could not be read or does not describe a correct ext2 filesystem.
.
.
.
fsck.ext3: Unable to resolve "UUID=....."
fsck died with exit status 8

filesystem check failed => var/log/fsck/checkfs
repair filesystem manually.

I've been a little careless and have played around with moving my /home partition before encountering this problem - before, everything worked perfectly (with the Feisty-installation). I was moving /home to /hda6/xub32/home in the first place and mounted it in fstab (wanted to check if it's possible to mount /home to a subdir, not root). 

Since that left me with an unusable system (Feisty not recognizing /home/USER folder + fsck-failure at boot-up), I moved /home (dupe /home/home in the first place) to /xub32 and then to /hda6. Nothing would work, Feisty wouldn't recognize the /home/USER directory anymore. That's why I renamed my original /user_backup to /home and deleted the mount-option in fstab.

Now, I can boot up my system again, but I still get the break + fsck-error!! 

Since /hda7 (Feisty) is mounted while booting, I cannot repair it with e2fsck. Should I run this from Live-CD? What options should I use? I can't think of why I have the booting problem at all, since I reverted the system as it was in the first place...

Could it be that it's because I simply changed /hda6 (my new '/home'-partition) from reiserfs to ext3, before moving the files there?

I'm really lost, please help!


perixx

---

### Post by banewman on 2007-12-06
You can mount /home in a seperate partition but it is easiest from the install
Puppy files - if your running from the cd - work best if installed to a windows partition.
Always windows first then any linux - windows refuses to recognise linux partitons.
:)

---

### Post by perixx on 2007-12-06
hm, I'm not sure how to create (and use) a /home partition along with an Ubuntu-installation; maybe when doing the partitioning (manual) and specifying a '/home' partition in addition to the '/' ?

But that won't solve my current problem with the borked filesystem...

perixx

---

### Post by Pumalite on 2007-12-06
Just in case; for future reference:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by perixx on 2007-12-06
Well, I've managed to find some clues to what caused the boot-up break and fsck-error:

- Gutsy 64 had an fstab-entry for /hda6 (which was supposed to serve as /home partition). I have transformed that partition from reiserfs to ext3 lately, maybe there was something not okay with it; after removing the entry for it, the error message vanished.

- Feisty also had the fstab-entry, but there was some wrong mounting option used.

Anyway, I've now removed the partition in question, along with an older /ath partition at the end of the HDD and the /swap partition. After moving Gutsy and Feisty partitions next to each other, I've created a new /swap at the end, along with a new empty partition.

Feisty is now up and running again - there's only a minor problem with a '/home/.dmrc' file that has 'wrong permissions'. I've set the permissions to '664' as suggested, let's see at next reboot what happens.

In Gutsy's installation, I cannot do anything that needs root-rights: it says 'set usersuid needed' or sth. like this; I suppose that file permissions were borked in the /home folder. Do all files / folders in the /home folder have the same permissions? If yes, are they as follows?

root - rw
USER - rw
others - r

perixx

---

### Post by Pumalite on 2007-12-06
[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

---

### Post by perixx on 2007-12-06
Merci, Pumalite!

But do you happen to know what standard-permissions Ubuntu's home-folders require due to the 'sudo'-architecture - and if all files/folders there are treated alike? 

perixx

---

### Post by perixx on 2007-12-09
Analog to this thread:
[http://ubuntuforums.org/showthread.php?t=341322]("http://ubuntuforums.org/showthread.php?t=341322")

I've set the permissions for /home and /xyz like follows and fixed the 'HOME/.dmrc'-error again..!
```
sudo chmod 755 /home/USER
sudo chmod 775 /home
```

perixx

---

