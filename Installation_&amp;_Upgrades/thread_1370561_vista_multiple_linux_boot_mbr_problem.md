---
title: "vista multiple linux boot mbr problem"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2010-01-02
hi. i had a working multi-boot system, vista on sda1,2; swap sda3; ext=sda4; ubuntu sda5; fedora sda6; data sda7 - i mount the data partition when using all of the linux releases so i don't have to have multiple copies of music, docs, etc. everything has worked fine until yesterday. i tried to install fc12 on sda6, replacing fc11. it required me to format sda6 as ext4. i wasn't sure where i had grub installed, but have a backup of menu.lst in data (sda7), so figured i could let it install to mbr or wherever it wanted to by default.
when the install completed and i reboot, i get a black screen and these messages: CLIENT MAC ADDR: 00 19 XX XX XX GUID: XXXXX PXE-E53: No boot filename received
PXE-M0F: Exiting Intel Boot Agent.
No bootable device -- insert boot disk and press any key
I tried reinstalling fc12, same exact errors.
I then thought maybe the problem had something to do with ext4 partition mixed in with ext3's, so i installed mepis on the sda6, and let it write grub to mbr (i think, not really sure where it wrote it).
anyway, i still get the identical black screen. no grub type menu or anything. the screen used to show "DHCP for a few seconds", but doesn't anymore after i disconnected the ethernet cable.
i was thinking when i originally did the shrink partitions in vista to allow me to dual boot, i had to be extra careful as to where to put grub and/or the mbr, but i can't remember since it was months and months ago.
my guess is i have hosed up grub and/or mbr, but am hopeful i can recover without wiping the hd. right now i have it booted with a ubuntu live 8.x and have ran fdisk -l. it shows all the partitions. sda6 has * under the Boot column.
i would really appreciate some help in getting this up and running without having to reload vista and also don't want to lose the linux partitions if possible. thanks for your help.

---

### Post by pastalavista on 2010-01-02
This sounds like a job for [SuperGrub Disk]("http://supergrubdisk.org").

:-D

---

### Post by Jose Catre-Vandis on 2010-01-02
If you have Ubuntu (less than Karmic - legacy-grub) on board your PC you should be able to sort out your grub using the live cd

Boot Live CD

Open Terminal

Enter: **grub**

Enter: **find/boot/grub/stage1**

You'll get an answer, something like **(hd0,X)**

Enter: **root (hd0,X)** where X is the number you got above

Enter: **setup (hd0)**

You should then get some complimentary messages about a successful grub installation

Reboot and hopefully rescued.

Oh, the messages you were initially getting on boot were because you have your bios set to boot from a network if no local boot is available. You may want to check your bios settings to ensure CD-Rom is first and HDD is second (unless you prefer a different setup)

---

### Post by vbdanl on 2010-01-02
> **Jose Catre-Vandis said:**
> If you have Ubuntu (less than Karmic - legacy-grub) on board your PC you should be able to sort out your grub using the live cd

Boot Live CD

Open Terminal

Enter: **grub**

Enter: **find/boot/grub/stage1**

You'll get an answer, something like **(hd0,X)**

Enter: **root (hd0,X)** where X is the number you got above

Enter: **setup (hd0)**

You should then get some complimentary messages about a successful grub installation

Reboot and hopefully rescued.

Oh, the messages you were initially getting on boot were because you have your bios set to boot from a network if no local boot is available. You may want to check your bios settings to ensure CD-Rom is first and HDD is second (unless you prefer a different setup)

i got Error 15: File not found when i did the above.
do i need to mount the partitions first?

---

### Post by vbdanl on 2010-01-02
> **vbdanl said:**
> i got Error 15: File not found when i did the above.
do i need to mount the partitions first?

dang, still no joy..
i found i needed to enter sudo grub instead of just grub.
the find command returned 2 entries, (hd0,4) and (hd0,5)
i ran root (hd0,4) then setup (hd0)
it came back with checking.. yes a couple of times, then embed...succeeded, and Done.  everything looked like it was going to work..
rebooted, and still get same:
PXE-E61: Media test failure, check cable
PXE-MOF: Exiting Intel Boot Agent.
No bootable device -- insert boot disk and press and key

I went back into bios, and checked boot settings.. it has the boot order:
cd rom, hdd, floppy, ethernet  (i don't have a floppy drive)
guess i can open it up and reset the cables, but i haven't had the box open for a long time.. can't imagine how anything is loose in there, plus when we boot from live cd, it recognizes everything..
help..

---

### Post by vbdanl on 2010-01-08
this can be marked solved.
i ended up having to run the Vista recovery cd.  it made the first partition bootable, and all was ok after that.

---

