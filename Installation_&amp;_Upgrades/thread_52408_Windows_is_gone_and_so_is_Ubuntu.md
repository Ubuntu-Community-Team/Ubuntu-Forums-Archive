---
title: "Windows is gone and so is Ubuntu"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by SlugO on 2005-07-27
Well, I must say that this is not one the most positive Linux experiences I've had...

Earlier today I forgot the Ubuntu DVD in the drive (the one that has installation
and live cd's). While I wasn't home my folks tried to start the computer and only
got the dvd's welcoming screen. They say they just shut the computer then.
I hope my little brother didn't try typing any commands then...

When I got home and removed the DVD, GRUB didn't give me the usual menu
between Ubuntu and Windows but booted straight to Ubuntu. Too bad it wasn't
there anymore. First everything seemed normal, the usual boot messages. But
then I got APT on the screen asking how I'd like to install the Ubuntu packages.
So it thinks that there isn't a working installation.

After booting again I noticed that Windows isn't in the boot menu anymore and
that Ubuntu mounts tmpfs over /dev. So it can't find the right partition anymore.

Has GRUB messed everything up? Can't it find the partitions anymore?
How can I get my system working again? ](*,)

**Clarification:** 
When I say I get APT, I mean that I get it in text mode, similar to Ubuntu installation.
And it's asking me where to get the Ubuntu installation packages, cd, folder or net.
I also noticed that boot process says root=/dev/sda1. That should be my Windows
partition and Ubuntu is in /dev/sda6. Here's also a pic of the boot messages
if it helps anything:
[[IMG]http://img207.imageshack.us/img207/3847/0000320ab.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=0000320ab.jpg)

---

### Post by ouphe on 2005-07-27
-boot from wxp install cd
-start a recovery console
-login
-type <fixmbr>
-confirm changes
-reboot
-linux gone, parents happy ;)

---

### Post by SlugO on 2005-07-27
Maybe I could just go to console with live-cd and mount /dev/sda6 where
I have Ubuntu and then try to get the mount points right in /boot/grub/menu.lst?

Now if only I could find how to get to console with the dvd... :-k

---

### Post by SlugO on 2005-07-27
I can't boot to /dev/hda6 with rescue mode, only 1,2 and 5.
I don't know what to do. Somebody please help me :( 
My computer is a total mess thanks to grub...

---

### Post by GTvulse on 2005-07-27
Well, there are some things you have left out of your story such as where you installed GRUB's loader... But as it has happened to me several times when installing some newfangled distro (I keep WinXP and several Linux and Unix distros in my box and change them from time to time). I always return to Ubuntu, btw.

Boot up the DVD in rescue mode. Chroot your Ubuntu root partition and use the command ```
parted /dev/sda print
```

If there is a partition with a boot flag, it will be shown there. If there is no partition with a bootflag, that's your problem. If you installed GRUB in the MBR, hopefully you haven't done a "fixmbr" as advised above just flag the boot partition (/dev/sda2 I would infer). Use the command ```
parted /dev/sda "set 2 boot on"
``` at the command prompt and reboot.

If you decided to install GRUB in the boot partition, then you have to mount /dev/hda6, then mount your real boot partition in /boot and install grub in the latter partition. Of course you have to make it bootable as well. 

If parted or cfdisk do not find the /devhda6 partition, not all is lost. If /dev/hda6 is the last partition in the disk, use cfdisk or other partitioner (I strongly recommend cfdisk, btw), from a rescue distro such as Knoppix (I'm not sure you can use Ubuntu's installer CD rescuemode for this) and recreate /dev/hda6 as a logial partion of type Linux, reboot and it should reappear with all its contents intact.

---

### Post by SlugO on 2005-07-27
[QUOTE=dradul]
Boot up the DVD in rescue mode. Chroot your Ubuntu root partition and use the command
parted /dev/sda print[/QUOTE] You mean chroot into /dev/sda6? I can't, it's nowhere to be found.
Here's what parted prints:
[IMG]http://img151.imageshack.us/img151/5038/000029ye.jpg[/IMG]

> If you decided to install GRUB in the boot partition, then you have to mount /dev/hda6, then mount your real boot partition in /boot and install grub in the latter partition. Of course you have to make it bootable as well. I think I installed it in MBR, do I have to reinstall it somehow?

> If parted or cfdisk do not find the /devhda6 partition, not all is lost. If /dev/hda6 is the last partition in the disk, use cfdisk or other partitioner (I strongly recommend cfdisk, btw), from a rescue distro such as Knoppix (I'm not sure you can use Ubuntu's installer CD rescuemode for this) and recreate /dev/hda6 as a logial partion of type Linux, reboot and it should reappear with all its contents intact. So obviously hda6 is gone. I'm not sure how to use cfdisk. And more importantly, how can I burn Knoppix while I'm using live-cd..?

---

### Post by SlugO on 2005-07-27
This has really shook my faith in Linux :(
How can a whole partition vanish by itself? ](*,)

---

### Post by Erucolindo on 2005-07-27
Try running testdisk ([www.cgsecurity.org/testdisk.html](www.cgsecurity.org/testdisk.html)) it has helped me to recover lost partitions before..

---

### Post by GTvulse on 2005-07-28
[QUOTE=SlugO]This has really shook my faith in Linux :(
How can a whole partition vanish by itself? ](*,)[/QUOTE]
 It isn't a problem with Linux (such kind of blanket generalizations will only get you into trouble!!!). It is a bug in the installer that blindly hitting the enter key (as either your parents or younger brother did) only made worse. But... Have you tried to install Windows XP from scratch on a SATA drive lately. I have, last week, and let me tell you: that's messy!

---

### Post by SlugO on 2005-07-28
[QUOTE=dradul]It isn't a problem with Linux (such kind of blanket generalizations will only get you into trouble!!!). It is a bug in the installer that blindly hitting the enter key (as either your parents or younger brother did) only made worse.[/QUOTE] I'm already in trouble, my computer is messed up. So how could I use cfdisk to
restore my /dev/sda6? Seems quite difficult to burn anything with live-cd...

[QUOTE=Erucolindo]Try running testdisk ([www.cgsecurity.org/testdisk.html](www.cgsecurity.org/testdisk.html)) it has helped me to recover lost partitions before..[/QUOTE] Well I booted into Tomsrtbt and tried to execute testdisk_static. After doing something
for a while it gave me an error message: Illegal instruction
So that doesn't work.. :?

Anyone know how I could get /dev/sda6 back?
Or atleast boot to Windows? Please..? :(

---

### Post by GTvulse on 2005-07-28
To boot into windows, follow ouphe's advice. That will restore the Windows partition as the primary booting OS in your system. I'm sorry to read about your troubles, btw, because I also messed up my box badly the first time I tried to install Ubuntu  :cry: .

---

### Post by SlugO on 2005-07-28
Well, it's much worse than I thought...
Here's what bootable PartitionMagic has to say:
[IMG]http://img181.imageshack.us/img181/1957/0000224pe.jpg[/IMG]
Oh. My. God. :shock: 
NTFS is gone, Windows is gone. I have much more important stuff there than on the Linux partition. :cry: 
Before giving the above report, PartitionMagic asks this:
[IMG]http://img181.imageshack.us/img181/6656/0000121nt.jpg[/IMG]

I clicked No coz I'm not sure what it will do. Somehow I think It's not gonna fix my problems though...

Is there any way of restoring my NTFS partition? :(

---

### Post by SlugO on 2005-07-28
So if NTFS is permanently gone I guess I'll repartition my drive and 
start installing Windows... I'd just like to be sure that there isn't any
way to get it back.

---

### Post by SlugO on 2005-07-28
Still waiting for that miracle cure... :neutral: 
Could I atleast get my files from the ntfs partition somehow?
Or is it absolutely certain that they're gone? ](*,)

---

### Post by Buffalo Soldier on 2005-07-28
[QUOTE=SlugO]While I wasn't home my folks tried to start the computer and only
got the dvd's welcoming screen. They say they just shut the computer then.
I hope my little brother didn't try typing any commands.[/QUOTE]To me it seems your little brother or someone probably hit the ENTER key repeatedly and subsequently chooses the option of wiping out all previous available partitions in your harddisk and created new partitions.

If that is the case, I'm sorry to say that there is no way (that I know of) to get all your lost data in the NTFS partition.

---

### Post by AgenT on 2005-07-28
And of course this cannot be blamed on Linux or Ubuntu. If someone had put in a Mac or Windows install CD and had pressed enter like mad and did a format it is that persons fault (or yours since you left the disk in the PC - guess that's up for you to decide).

Is there a way to restore? Actually, your biggest mistake was to use NTFS. A POS filesystem because it's so locked (much more than fat) by Microsoft. What you could do is try and recreate the partition exactly how it was before using fdisk (on linux - windows is too stupid). If you are lucky, all that happened was that your partition information was wiped which means you could restore it. Of course, you used NTFS which was a big mistake and this means that it probably is not restorable because, well, it's locked and fdisk is unable to create it. But if it can create NTFS, try it!

What you want is to create the partition by hand (that is, telling fdisk exactly where the partition starts and where it ends). You have to get this exactly right which actually should be easy because it looks like your partition started from the start of the HD to somewhere before the next one begins. And if all that was erased was the partition info and the data is still there and not overwritten you have a chance of restoring it. Again, you are using NTFS so I doubt this is possible. And of course, even if you do restore it, you screwed yourself again by using NTFS because now you have to pray Windows will boot since NTFS cannot be fixed in Linux (again, because it's locked).

Use Windows and you pay the price I guess. ;)

---

### Post by aveline on 2005-07-28
[QUOTE=AgenT]Use Windows and you pay the price I guess. ;)[/QUOTE]

no need to rub it in I'm sure he feels lousy enough.

if you can get a friend to dl & burn the ultimate boot cd, it has partition rescuing utilities. They are pretty good I think & worth a try.

Aveline

---

### Post by Buffalo Soldier on 2005-07-29
[QUOTE=aveline]no need to rub it in I'm sure he feels lousy enough.

if you can get a friend to dl & burn the ultimate boot cd, it has partition rescuing utilities. They are pretty good I think & worth a try.

Aveline[/QUOTE]Agree. Well at least he had the good intention of trying Ubuntu or Linux. Here's the Ultimate Boot CD link [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by SlugO on 2005-07-29
Okay, I'll try the Ultimate Boot CD. Which tools should I use?

---

### Post by AgenT on 2005-07-29
[QUOTE=aveline]no need to rub it in I'm sure he feels lousy enough.[/QUOTE]

Sorry, I did not mean to sound like I was trying to "rub it in". :-# But then again, he shouldn't be so quick to blame Ubuntu either.

 > Okay, I'll try the Ultimate Boot CD. Which tools should I use? 

Use [size=2] Active@ Partition Recovery. See the link to the CDs website above for more info. It also has a link to the programs homepage which explains a lot more.[/size]

---

### Post by SlugO on 2005-07-29
Active@ Partition Recovery has been running for quite a while now...
Status indicator doesn't show any progress. The hard drive light is on
so it's probably scanning it but otherwise nothing.
Oh well, not very probable that I'll get the partitions back.. :?

---

