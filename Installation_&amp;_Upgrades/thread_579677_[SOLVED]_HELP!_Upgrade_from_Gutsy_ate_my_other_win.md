---
title: "[SOLVED] HELP! Upgrade from Gutsy ate my other windows drive (maybe not really)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jai_mantravadi on 2007-10-18
I just upgraded from Gutsy (Kubuntu) using the RC1 release on Tuesday. After a little bit of finagling, I had my shiny new linux desktop... (actually looks about the same). What I did notice was that one of my 2 NTFS drives (non-bootable) was no longer mounted all of a sudden (worked before upgrade, didn't work after)... OK... Maybe this new FUSE mounting system was to blame, so I tried to mount it manually and got something like "Permission denied". Ok, no prob right? I'll just boot to windows. Still, no dice, Windows can't see the disk either. Uh, oh, so standard procedure:

1) Bios detects it
2) Windows and Linux both see the disk (fdisk under both), just not the partition
3) Fdisk (linux) reports it as an NTFS partition with fdisk -l
4) pull out testdisk (never used it before) which works by the way under BOTH windows and linux: IT CAN READ THE FILE SYSTEM. It can even copy it, etc. So... I try searching for MBR/MFT, etc. and re-writing them to the disk. After multiple reboots, neither operating system can see it?! However, using Testdisk I can access the disk just fine (oh, by the way no bad sectors or any errors for testdisk accessing the disk)

Can anyone help me figure out what happened to my partition/disk? I'd like to "restore" it without copying all the files off and back on (its about 90% full).

By the way, I've got 3 disks the first one is my windows disk on the Mobo primary IDE controller, the second (the one that no longer works) is on a second IDE controller (a raid controller), and my Ubuntu disk is on the first SATA controller. All of these drives are masters of their own domain (puns intended). Any help would be much appreciated (although I'm certainly panicking less now that I've realized I've got access to my Data via testdisk)!
Jai

---

### Post by Norrbagge on 2007-10-18
i would like to bump this... I upgraded from ubuntu feisty to Gutsy earlier today...

Before i upgraded. Ubuntu was able to read my NTFS harddrive just fine... During my upgrade it said that mounting was not possible, or something like that... So after i upgraded i try to open the harddrive and it wasnt able to mount it and all i got was some folders i didnt recognize... 

I installed "NTFS config tool" from synaptic to see if that could help. which it didnt... I the tried the command it said i could try at my own risk... Didnt help either... Now, however, i am not able to see the harddrive at all when opening "my computer"

@jai_mantravadi:  Sorry. not trying to barge inn and bring up my own problem... But it seem like we have the same problem here...


EDIT: i gave it one more try with the "NTFS Configuration tool" and i got this message, that i meant to copy to this post earlier: 

Mounting /media/EGEN HD IKKE ENDRE failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/EGEN HD IKKE ENDRE -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/EGEN HD IKKE ENDRE ntfs-3g defaults,force 0 0

i can add that i DO NOT have MS installed on this computer... So choice 1 is not the cause... I have tried the "force option". when i did i got the same message as i have copied above... how i use the /etc/fstab command, i dont know...

---

### Post by Tim Watson on 2007-10-18
Try posting the output of the following command from a terminal:

dd if=/dev/sdN count=1 | xxd

where N is the disk in question (either a, b, c etc.). I'm sad enough to be able to read boot sector disk partitions in hex so I should be able to help you understand whether the partition table is OK.

All the best,

Tim.

Update: Just in case I can't reply quickly, this is what you can look at (this is my MBR for one of my disks):
-----
[root@buster ~]# dd if=/dev/sdb count=1 | xxd
0000000: eb48 9010 8ed0 bc00 b0b8 0000 8ed8 8ec0  .H..............
0000010: fbbe 007c bf00 06b9 0002 f3a4 ea21 0600  ...|.........!..
<snip>
0000170: 06be 947d e830 00be 997d e82a 00eb fe47  ...}.0...}.*...G
0000180: 5255 4220 0047 656f 6d00 4861 7264 2044  RUB .Geom.Hard D
0000190: 6973 6b00 5265 6164 0020 4572 726f 7200  isk.Read. Error.
00001a0: bb01 00b4 0ecd 10ac 3c00 75f4 c300 0000  ........<.u.....
00001b0: 0000 0000 0000 0000 c741 0500 0000 8001  .........A......
00001c0: 0100 83fe 3f0c 3f00 0000 8e2f 0300 0000  ....?.?..../....
00001d0: 010d 83fe ffff cd2f 0300 6679 1a06 00fe  ......./..fy....
00001e0: ffff 83fe ffff 33a9 1d06 6679 1a06 00fe  ......3...fy....
00001f0: ffff 05fe ffff 9922 380c de26 f406 55aa  ......."8..&..U.
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00200218 s, 256 kB/s
[root@buster ~]# 
-----
The partition table starts at 1be and has four entries at most. Here's my first entry:

00001b0: <snip>                                                      8001  .........A......
00001c0: 0100 83fe 3f0c 3f00 0000 8e2f 0300

From the beginning of the entry, the 80 shows it's a bootable partition, the 01 0100 shows that its cylinder 0, head 1, sector 1 (it's little endian and so is read backwards in pairs), the 83 is a linux partition (it would be 07 for NTFS), the fe 3f0c is the end position in CHS format, the 3f00 0000 is the start sector in logical block addressing (this is sector 63, the 64th sector and conventionally the start of the first sector on a disk) and the 8e2f 0300 is the size of the partition in sectors (512 bytes per sector and the number should be read as 00032f8e = 102M). A partition type of 05 rather than 83 or 07 is an extended partition. Go to the start sector and you'll find another record in the same form as the MBR with another partition table.

Windows tends to believe the bootable flag and the partition type but linux tends to ignore them. Thus a valid NTFS partition with a type shown as 83 would be ignored by Windows but could be mounted in linux.

---

### Post by jai_mantravadi on 2007-10-18
Tim,
Thanks for the help. Here's my output. Just an FYI, I don't know what it was before, but testdisk found it as a bootable NTFS partition, so I presume it gets its info from what you're saying. Here's the results:


```

0000000: fc31 c08e d031 e48e d88e c0be 007c bf00  .1...1.......|..
0000010: 06b9 0001 f3a5 beee 07b0 08ea 2006 0000  ............ ...
0000020: 803e b307 ff75 0488 16b3 0780 3c00 7404  .>...u......<.t.
0000030: 0806 af07 83ee 10d0 e873 f090 9090 9090  .........s......
0000040: 9090 9090 9090 9090 9090 9090 9090 9090  ................
0000050: 9090 9090 9090 9090 9090 9090 9090 9090  ................
0000060: 9090 9090 9090 9090 9090 9090 9090 9090  ................
0000070: 9090 9090 9090 9090 9090 9090 9090 bebe  ................
0000080: 07b0 00b9 0400 803c 0075 6efe c083 c610  .......<.un.....
0000090: e2f4 31db b40e be9d 078a 0eaf 07ac d0e9  ..1.............
00000a0: 7302 cd10 08c9 75f5 b03a cd10 31c0 cd16  s.....u..:..1...
00000b0: 3c00 74f8 be8b 07b9 0200 e8ba 003c 0d74  <.t..........<.t
00000c0: b43c 6172 063c 7a77 022c 2088 c3be 9d07  .<ar.<zw., .....
00000d0: 8a0e af07 acd0 e973 0438 c374 0608 c975  .......s.8.t...u
00000e0: f3eb afb8 0d0e 31db cd10 8d84 6200 3c07  ......1.....b.<.
00000f0: 7507 b01f a2af 07eb 9931 d2b9 0100 3c04  u........1....<.
0000100: 7411 73f3 30e4 b104 d2e0 bebe 0701 c68a  t.s.0...........
0000110: 16b3 07bf 0500 56f6 c280 7431 b441 bbaa  ......V...t1.A..
0000120: 5552 cd13 5a5e 5672 1e81 fb55 aa75 18f6  UR..Z^Vr...U.u..
0000130: c101 7413 8b44 088b 5c0a be8d 0789 4408  ..t..D..\.....D.
0000140: 895c 0ab4 42eb 0c8a 7401 8b4c 02b8 0102  .\..B...t..L....
0000150: bb00 7c50 c606 8f07 01cd 1358 5e73 054f  ..|P.......X^s.O
0000160: 75b4 eb93 813e fe7d 55aa 75f6 ea00 7c00  u....>.}U.u...|.
0000170: 00be 8307 b90a 0050 b40e 31db accd 10e2  .......P..1.....
0000180: fb58 c354 6573 7444 6973 6b0d 0a10 0001  .X.TestDisk.....
0000190: 0000 7c00 0000 0000 0000 0000 0031 3233  ..|..........123
00001a0: 3446 0000 414e 4454 6d62 7200 0202 021f  4F..ANDTmbr.....
00001b0: c700 0080 0000 0000 0000 0000 a501 8001  ................
00001c0: 0100 07fe ffff 3f00 0000 828a a112 0000  ......?.........
00001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.

```

Any help would be great, I'm wondering whether to delete the partition and start over, but... I just want to figure out "what went wrong" first before doing any major changes. I've just about got my data saved off, but if I can just restore the drive, that would be better. As you can see, I've got 8001 which seems to indicate that testdisk is still seeing it as a bootable/NTFS partition, and yet neither windows nor linux can see it (but testdisk reads it fine). The partition type and size (160GB) check out. Its one partition the size of the whole disk, and it should be a primary partition which according to what you said is correct. 


don't know if this helps, but using the same dd command with sdb1 rather than sdb dumps (I believe) the first bit of the partition, so if there's anything this can help with here it is:

```

0000000: eb52 904e 5446 5320 2020 2000 0208 0000  .R.NTFS    .....
0000010: 0000 0000 00f8 0000 3f00 ff00 3f00 0000  ........?...?...
0000020: 0000 0000 8000 8000 818a a112 0000 0000  ................
0000030: 0000 0c00 0000 0000 a818 2a01 0000 0000  ..........*.....
0000040: f600 0000 0100 0000 dea4 1c08 de1c 0870  ...............p
0000050: 0000 0000 fa33 c08e d0bc 007c fbb8 c007  .....3.....|....
0000060: 8ed8 e816 00b8 000d 8ec0 33db c606 0e00  ..........3.....
0000070: 10e8 5300 6800 0d68 6a02 cb8a 1624 00b4  ..S.h..hj....$..
0000080: 08cd 1373 05b9 ffff 8af1 660f b6c6 4066  ...s......f...@f
0000090: 0fb6 d180 e23f f7e2 86cd c0ed 0641 660f  .....?.......Af.
00000a0: b7c9 66f7 e166 a320 00c3 b441 bbaa 558a  ..f..f. ...A..U.
00000b0: 1624 00cd 1372 0f81 fb55 aa75 09f6 c101  .$...r...U.u....
00000c0: 7404 fe06 1400 c366 601e 0666 a110 0066  t......f`..f...f
00000d0: 0306 1c00 663b 0620 000f 823a 001e 666a  ....f;. ...:..fj
00000e0: 0066 5006 5366 6810 0001 0080 3e14 0000  .fP.Sfh.....>...
00000f0: 0f85 0c00 e8b3 ff80 3e14 0000 0f84 6100  ........>.....a.
0000100: b442 8a16 2400 161f 8bf4 cd13 6658 5b07  .B..$.......fX[.
0000110: 6658 6658 1feb 2d66 33d2 660f b70e 1800  fXfX..-f3.f.....
0000120: 66f7 f1fe c28a ca66 8bd0 66c1 ea10 f736  f......f..f....6
0000130: 1a00 86d6 8a16 2400 8ae8 c0e4 060a ccb8  ......$.........
0000140: 0102 cd13 0f82 1900 8cc0 0520 008e c066  ........... ...f
0000150: ff06 1000 ff0e 0e00 0f85 6fff 071f 6661  ..........o...fa
0000160: c3a0 f801 e809 00a0 fb01 e803 00fb ebfe  ................
0000170: b401 8bf0 ac3c 0074 09b4 0ebb 0700 cd10  .....<.t........
0000180: ebf2 c30d 0a41 2064 6973 6b20 7265 6164  .....A disk read
0000190: 2065 7272 6f72 206f 6363 7572 7265 6400   error occurred.
00001a0: 0d0a 4e54 4c44 5220 6973 206d 6973 7369  ..NTLDR is missi
00001b0: 6e67 000d 0a4e 544c 4452 2069 7320 636f  ng...NTLDR is co
00001c0: 6d70 7265 7373 6564 000d 0a50 7265 7373  mpressed...Press
00001d0: 2043 7472 6c2b 416c 742b 4465 6c20 746f   Ctrl+Alt+Del to
00001e0: 2072 6573 7461 7274 0d0a 0000 0000 0000   restart........
00001f0: 0000 0000 0000 0000 83a0 b3c9 0000 55aa  ..............U.

```

Doesn't the fact that I can read sdb1 mean that linux "senses" the partition and can see it? Why can't I mount it? Thanks!

---

### Post by jai_mantravadi on 2007-10-19
Weird,
After rebooting (yet again), it appears that I can now mount my drive. I *know* I was attempting to mount the correct drive before and it wouldn't mount. Looking at the fstab, one thing that probably tripped up Ubuntu is that somehow my drive went from sda1 to sdb1, even thought they're the same in the bios boot priority, and my ubuntu drive and my other drive are on two different controller chipsets. Don't know *why* gutsy decided to make the change for me and I had fun figuring it out, but it works now (we'll see after rebooting a few times if it still holds up)


Norrbagge
first do a: "sudo fdisk -l" to list off all partitions. That'll tell you if linux is detecting the disk itself and what partition type its seeing. Check if your drive and your fstab don't match. If not, that may be your problem (i.e. your fstab/you are looking for sdb1 when gutsy switched on you to sda1 or sdc1 or something...)

I'd encourage you to try out testdisk either on linux or on another Windows machine with the drive attached. It looks and works the same under both OS's. You can get it here:
[Testdisk wiki]("http://www.cgsecurity.org/wiki/TestDisk")
Copy a file or 2 to your linux partition/disk to verify that it works correctly and that you can read from it.

If you can read the drive (there's also an option to look at files), you should be able to mount it (although I had trouble for a while). After copying some stuff off, I switched the partition from bootable to non-bootable and back a couple times (rebooting each time), and this last time it worked.
Don't know if that helps you, but maybe you can post your boot sectors like Tim suggested above and maybe he can help if your problem lies more in the other direction. 
Hope it helps!
Jai

---

### Post by Tim Watson on 2007-10-19
The first boot sector listing looks fine and I'm glad that you can now mount your partition. The second listing is the first sector of your NTFS partition, as you guessed. Confusingly, NTFS marks the end of this sector with 55aa (really, 0xaa55) even though this isn't a DOS partition system, or a basic MBR partition as Microsoft calls it (don't ask!).

It seems this random disk device swapping is a problem with ubuntu. I've been teaching a lab on installing ubuntu and we used removable drive caddies - to cut a long story short, ubuntu seemed to install the bootloader on the wrong drive sometimes, seemingly at random. It would also think that the drives were the wrong way round (sda was sdb and vice versa). Even after correcting /boot/grub/menu.lst it would get it wrong again if the kernel was updated. I think that it's not mapping the drives consistently. At least it gave me a chance to give an impromptu lecture on boot sectors and partition tables!

Must go now and avoid the temptation to try gutsy before the major bugs have been ironed out :-)

All the best,

Tim.

---

### Post by djfdat on 2007-10-19
> **Norrbagge said:**
> i would like to bump this... I upgraded from ubuntu feisty to Gutsy earlier today...

Before i upgraded. Ubuntu was able to read my NTFS harddrive just fine... During my upgrade it said that mounting was not possible, or something like that... So after i upgraded i try to open the harddrive and it wasnt able to mount it and all i got was some folders i didnt recognize... 

I installed "NTFS config tool" from synaptic to see if that could help. which it didnt... I the tried the command it said i could try at my own risk... Didnt help either... Now, however, i am not able to see the harddrive at all when opening "my computer"

@jai_mantravadi:  Sorry. not trying to barge inn and bring up my own problem... But it seem like we have the same problem here...


EDIT: i gave it one more try with the "NTFS Configuration tool" and i got this message, that i meant to copy to this post earlier: 

Mounting /media/EGEN HD IKKE ENDRE failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/EGEN HD IKKE ENDRE -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/EGEN HD IKKE ENDRE ntfs-3g defaults,force 0 0

i can add that i DO NOT have MS installed on this computer... So choice 1 is not the cause... I have tried the "force option". when i did i got the same message as i have copied above... how i use the /etc/fstab command, i dont know...


im getting the same error only thing is that mines is /dev/sda2 and i have vista (which isnt workin after i installed gutsy). i tried umount (one of the few things i kno) and it says  /dev/sda2 is not mounted (according to mtab

when i try choice two it says only root can do that and the stuff past or i dont kno what its tryin to tell me to do (i found fstab, but the thing isnt the same as whats in it

More info: Gutsy 64-bit n nething else helpers need to kno just tell me n ill try to find out how to do that

---

### Post by jai_mantravadi on 2007-10-19
djfdat,
Not sure exactly what you mean or isn't working for you other than that vista isn't loading since you've installed gutsy. First thing: try changing boot order in the bios, and boot of your vista disk first. If that doesn't work (or it loads linux), try downloading and burning [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to make a liveCD and boot from it. It will then automatically find bootable partitions (via menu option) and you can hopefully then boot vista (I've only used it for windows XP). It should also have an option to put a new master boot record on, but I've never used it with Vista, so I'm not sure how it'll work.
Good luck.

---

