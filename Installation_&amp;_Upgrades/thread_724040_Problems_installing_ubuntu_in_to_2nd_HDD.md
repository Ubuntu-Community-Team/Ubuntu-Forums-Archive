---
title: "Problems installing ubuntu in to 2nd HDD"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by kakashikun on 2008-03-14
Hi... i got a Harddisk (160 GB) with windows XP and a 2nd hard disk with (250 GB) with ubuntu. 

now i want to install ubuntu to my 2nd harddisk... i don't want to format it to be used by the 160GB ubuntu i wan to have it dual bootable . i.e . ubuntu on 160GB or ubuntu on 250GB in grub

but this is the problem it shows me when i try to install.


[[IMG]http://img329.imageshack.us/img329/2308/screenshotyw4.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img291.imageshack.us/img291/1266/screenshot1co7.png[/IMG]](http://imageshack.us)

[[IMG]http://img219.imageshack.us/img219/6391/screenshot2qk5.jpg[/IMG]](http://imageshack.us)


[[IMG]http://img401.imageshack.us/img401/6107/screenshot3pi9.jpg[/IMG]](http://imageshack.us) 

if you want to know the reason why i want to install ubuntu in my 160GB dive ius so that i can move my data from the 250GB ubuntu to 160GB ubuntu than install XP to the 250GB drive as sadly ... xp uses more space and adobe products which i need to use.

---

### Post by sandysandy on 2008-03-14
is it the same CD u used for the earlier install.

also post output of sudo fdisk -lu

is it live CD or alternate CD.

regards

---

### Post by kakashikun on 2008-03-14
its the same CD. its the 7.10 live CD. theres no problem with it ... i tried one of the option to check the DC and they said there was no defects

---

### Post by kakashikun on 2008-03-14
ok output of sudo fdisk -lu


 [[IMG]http://img150.imageshack.us/img150/9103/screenshot4ax0.jpg[/IMG]](http://imageshack.us)

---

### Post by sandysandy on 2008-03-14
are both ur hard disk of same type ie IDE, SATA or SCSI.

how many times have u tried to install. do you get the same error.

if so, u can consider trying the alternate CD.

also can u access ur windows partition.

however if u just want the other hard disk for [COLOR="Blue"]storing data[/COLOR], installing ubuntu is an overkill.

[COLOR="Blue"]just format it to ext3.[/COLOR]

u can also format it to NTFS if u want windows and ubuntu both to have access to this data.

regards

---

### Post by kakashikun on 2008-03-14
Both are sata.
about 13 times i tried.

nope ... i used my 250GB ubuntu to look whats in the 160GB drive i see Ubuntu files and all my XP stuff is gone.


you don get what i need.. i want to install ubuntu on it so i can move my data there than format my 250GB to XP. i have no other drives. on the bigger picture i had XP on 160GB and ubuntu on 250GB and wanted XP on 250 and ubuntu on 160. but still wanted my data.

---

### Post by kakashikun on 2008-03-14
btw ... ubuntu is not for storing data ... its for surfing web and stuff i commonly use.

XP is for work and i need adobe products. the end products are huge and  needs storage to keep.

you know what i means :D my 1 photoshoot can take up 4GB storage space Plus pictures after photoshop ... arg ... haha

---

### Post by sandysandy on 2008-03-14
seeing the output of sudo fdisk -lu, it was apparent that ur windows is gone.

also since that ur present ubuntu CD is not working u can give alternate CD a chance.

regards

---

### Post by sandysandy on 2008-03-14
> **kakashikun said:**
> btw ... ubuntu is not for storing data ... its for surfing web and stuff i commonly use.

XP is for work and i need adobe products. the end products are huge and  needs storage to keep.

you know what i means :D my 1 photoshoot can take up 4GB storage space Plus pictures after photoshop ... arg ... haha

even if ubuntu is on 250 gb, and u want more space for windows, u can do so.

with [COLOR="Blue"]gparted live CD [/COLOR]resize the ubuntu partition on 250 gb to whatever size u want. in the free space make another partition and format it to NTFS. that way windows can utilise the extra space on the ubuntu 250gb harddisk.

that way u can install windows again on 160gb hard disk.

regards

---

### Post by kakashikun on 2008-03-14
thx ok. but now how do i go about?

they don wanna read my XP CD. it just goes stright in to grub

---

### Post by sandysandy on 2008-03-14
> **kakashikun said:**
> thx ok. but now how do i go about?

they don wanna read my XP CD. it just goes stright in to grub

u will have to change the booting sequence in BIOS to CD ROM (first priority) followed by harddisk.

that way ur XP CD will load before GRUB (on hard disk) and u can do the re-install.

Backup anything important.

BIOS can be accessed by pressing Del button ( or some other button - see bottom screen for instructions during PC starting).

just keep in mind that after u install XP, ur grub on MBR will be overwritten. But that can be restored later.

see link below on restoring GRUB after winXP installation.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

all the best:)

regards

---

### Post by kakashikun on 2008-03-14
Ah thanks alot !! 

now XP is giveing my problem haha ... 

i386\kdCom.dll error code crap ... ill try to sort this out

---

