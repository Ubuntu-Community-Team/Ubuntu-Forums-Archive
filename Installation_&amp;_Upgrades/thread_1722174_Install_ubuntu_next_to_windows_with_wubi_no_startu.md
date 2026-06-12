---
title: "Install ubuntu next to windows with wubi: no startup"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by lamb0 on 2011-04-05
Hey everybody,

I tried to install ubuntu using wubi next to my win 7 64 bit OS following the instructions here: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

I completed the ubuntu setup wizard but when I restarted I got the following error: "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".

Now I am not able to start any OS let alone complete the installment of ubuntu... 

Sorry if the answer is somewhere on the forum but I could not find any exactly similar questions.

Any help would be much appreciated,

Thanks in advance,

Lamb0

---

### Post by coffeecat on 2011-04-05
Hi, and welcome to the forum.

Wubi is actually installed inside the Windows partition rather than next to it. There will be a virtual Ubuntu partition inside a file somewhere in C:\ubuntu.

> **lamb0 said:**
>  "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".

That sounds like a BIOS error.

First thing, switch on the machine and go into the BIOS. Is it detecting your hard drive? Is the hard drive that has Windows, and Wubi, still showing as the first boot drive? (It doesn't matter if the optical drive has first priority.)

Next - is this a desktop or laptop? If a desktop, open up the case and check the data and power cables to the hard drive. Make sure they are seated properly. Check the data cable at the motherboard end.

If that all checks out, the next thing to do would be to run the boot info script to see what is on your hard drive. But you'll need an Ubuntu live CD. Do you have one? If not, then I can show you what to do. 

If you do have an Ubuntu CD, make sure the BIOS is set to boot from the CD first, and boot from the Ubuntu CD. Choose "Try Ubuntu" rather than "install Ubuntu" when you get the choice and that will take you to the live desktop. Make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script. Now open a terminal (Applications > Administration) and run the script according to the instructions there. Post the contents of RESULTS.txt by double-clicking on it and pasting the text into your post. Please enclose the text between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the # icon on the message toolbar for this.

---

### Post by lamb0 on 2011-04-06
At the moment I am not near the computer in question. What I can tell that the it is a desktop and the hard drive is connected properly: it is recognized in the bios and is listed as third after two optical devices (I checked this too, it was the only thing I could think of). 
If an ubuntu live CD is the same as a burned ISO (like ubuntu-10.10-desktop-amd64.iso) then I have one. I will follow the rest of your instructions this evening. 

Thanks!

---

### Post by lamb0 on 2011-04-06
The results:

```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
240 heads, 63 sectors/track, 26342 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,275,919   398,275,857   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        16C0791DC07903F1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        405006A75006A42E                       ntfs       Music                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        821C90471C9037DD                       ntfs       SAMSUNG                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  67 01 c7 5f 9b c4 83 a3  e4 8a bf 56 4a c8 3b d5  |g.._.......VJ.;.|
00000010  50 2d 9d ba 50 a8 2f 75  fa 6a f4 4c 3f 39 36 b3  |P-..P./u.j.L?96.|
00000020  8d 5e 68 b4 8c 39 d8 39  a1 37 ba 9c f9 5b 90 15  |.^h..9.9.7...[..|
00000030  aa e0 5c bd a1 54 54 78  61 5b 11 25 a0 18 ab c6  |..\..TTxa[.%....|
00000040  b3 82 43 15 53 13 12 8d  40 6d f2 5e d5 ee ac 68  |..C.S...@m.^...h|
00000050  8d 38 3f ab 63 43 ce 54  51 65 22 d7 15 37 02 51  |.8?.cC.TQe"..7.Q|
00000060  96 d7 b2 9f 93 a1 9a c9  d1 20 a9 a2 59 c3 93 06  |......... ..Y...|
00000070  7f 1f 6b 5e 29 33 68 dd  8e 44 45 9a c3 a5 b3 ab  |..k^)3h..DE.....|
00000080  cb 36 e1 61 6d 49 25 3d  92 be 06 cb 7b b4 4d fb  |.6.amI%=....{.M.|
00000090  11 a1 5d ba ba 4a d3 a9  0b 8e 33 42 e2 1e 25 60  |..]..J....3B..%`|
000000a0  b0 3f d2 26 1a 01 1f 71  9c 39 49 2f 0e f8 00 9b  |.?.&...q.9I/....|
000000b0  b5 f2 d8 8d d6 c1 e3 cc  62 21 09 bf 33 a7 82 ec  |........b!..3...|
000000c0  65 ee 9b d8 b5 c6 73 b8  b1 43 56 32 dc 8d 7f 7e  |e.....s..CV2...~|
000000d0  de e7 60 90 1c 20 36 1f  b2 08 66 2e 19 80 5a 84  |..`.. 6...f...Z.|
000000e0  28 9e 4e ae 62 db 5e 6d  5c 09 dc da 0e 5c 4f 02  |(.N.b.^m\....\O.|
000000f0  8a cb 61 c1 10 8c 35 72  cd 17 38 25 37 f0 94 4a  |..a...5r..8%7..J|
00000100  f7 7c 91 c5 39 03 d6 ac  14 dc 9c da 9c 00 fd 43  |.|..9..........C|
00000110  79 f9 15 9a 8a ee 43 0b  27 6e 14 68 92 ce 97 90  |y.....C.'n.h....|
00000120  d8 39 1e 1f 39 7c 65 1a  3c ec 18 8d 3b 9c 16 ac  |.9..9|e.<...;...|
00000130  ab 6e 7e e1 17 3c 7f f2  93 ed bf 17 52 95 d7 bc  |.n~..<......R...|
00000140  6a 0a 98 eb a9 99 d4 8c  33 36 da 4e 0d b2 96 2e  |j.......36.N....|
00000150  76 bd 5f d6 c6 1e 26 6b  10 3d e3 8c 0c ca 16 45  |v._...&k.=.....E|
00000160  b5 c1 4f 3c 9e 08 24 02  7a 18 07 9a d5 4b 00 ee  |..O<..$.z....K..|
00000170  b3 88 1f 69 f5 aa ea d0  3b bc 56 16 6d 3e af 09  |...i....;.V.m>..|
00000180  0f ca 5a e0 83 de 88 54  2a e8 9d 35 06 f9 75 23  |..Z....T*..5..u#|
00000190  14 58 03 06 4d 57 25 9b  0a 03 80 52 8b 73 39 dc  |.X..MW%....R.s9.|
000001a0  25 2d 4d 1e 7e 7e f6 5e  61 bb 20 4e 29 6d 3f 08  |%-M.~~.^a. N)m?.|
000001b0  70 59 b3 20 08 a5 92 1b  4d 85 a9 3b e4 e9 00 01  |pY. ....M..;....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 59 70 74 00 00  |......?....Ypt..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200
```

---

### Post by coffeecat on 2011-04-06
The only thing I can see wrong with the Windows partition is the absence of /Boot/BCD. Whether this matters when wubi is installed, I'm not sure. I'll pm someone who knows more about wubi than I do. He's not on line at the moment so he may not post for some hours. Hang in there!

---

### Post by Rubi1200 on 2011-04-07
Hi lamb0,
coffeecat asked me to offer some help so here goes.

You are missing an essential file on the Windows partition for booting.

> /Boot/BCDneeds to be there. DO you know what happened to it by any chance?

There is also damage to the Wubi install:

> mount: unknown filesystem type ''


These are the steps I would take to try and sort this out:

1. repair the Windows boot sector

2. If you can boot normally into Windows again run the boot script again and post it here

3. we can then work on repairing the Wubi install

Good luck and let us know what happens.

---

### Post by coffeecat on 2011-04-07
@lamb0, just a couple more comments.

When you first posted, I googled the  "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key". It seems this happens with people booting Windows only - no mention of Linux - so perhaps it's related to the missing /Boot/BCD; I don't know. 

With regard to repairing the Windows boot sector, you should be able to do this from the Windows 7 repair disc. If you hadn't already prepared one when Windows was still booting, you can download one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

And here are Microsoft's instructions for using bootrec from the command line:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

My guess is that you will need 'bootrec /FixBoot' and/or 'bootrec /RebuildBcd' but whether that will over-write /wubildr, I don't know. But as Rubi1200 says, the wubi install is damaged anyway, and we'll have to look into repairing that once Windows is booting for you.

---

### Post by lamb0 on 2011-04-07
Thanks a lot guys!

I have an original Windows 7 disk. I don't know if the one you sugested can do this in a more proper way, but I already tried this disk to repair windows. It acknowledged the boot problem but was not able to fix anything. I will still try your suggestion anyway and will post the results soon (I hope this evening).

---

### Post by lamb0 on 2011-04-07
Ok so I started the command prompt from the boot disk and entered the things mentioned this:

```
bcdedit /export C:\BCD_Backup
```

I got back: 'The store export operation has failed. The registred system device cannot be found'.

It looks a bit like it doesn't recognize my hd after all so I went back in the BIOS. It was still there.

Then I entered this, just to see what it did:

```
c:
cd boot
attrib bcd -s -h -r
```

And that of course resulted in: '-bcd File not found'


I thought about just transporting my hd to another computer, get the files I need and reinstall everything. Is it neccesary, or not that bad?

And what I forgot to mention is that I can not select an operating system to repair in the boot cd menu. There simply isn't one listed there.

---

### Post by bcbc on 2011-04-07
> **coffeecat said:**
> ...
My guess is that you will need 'bootrec /FixBoot' and/or 'bootrec /RebuildBcd' ...

Lamb0, did you try 'bootrec /RebuildBcd' as *coffeecat* suggested?

---

### Post by lamb0 on 2011-04-08
Yes but I got something like /RebuildBcd is not recognized as an internal or external command...

---

### Post by coffeecat on 2011-04-08
> **lamb0 said:**
> Yes but I got something like /RebuildBcd is not recognized as an internal or external command...

/RebuildBcd is an option for the bootrec command, not a command itself. Did you try 'bootrec /RebuildBcd'?

---

### Post by lamb0 on 2011-04-11
Yeah I did. It resulted in a message saying something like this: RebuildBcd is not recognized as an internal or external command program or batch file.

---

### Post by lamb0 on 2011-04-11
So I first enetered 'bootrec.exe' and got the options there like RebuildBcd with some explanation. Then I entered RebuildBcd. Is that how it's supposed to be?

---

### Post by coffeecat on 2011-04-11
The Microsoft page:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

... is not very clear on this point. But if you managed to get to the RebuildBcd utility that seems to be the way to go.

---

### Post by lamb0 on 2011-04-11
Well, I could start the bootrec.exe but RebuildBcd was not working, it gave the error mentioned above.

---

### Post by lamb0 on 2011-04-14
I connected the HD to another computer and took off everything I needed so now I will probably just reformat it and start with a clean Ubuntu install, without Wubi ofcourse, I don't trust that anymore.

Thanks for the advice guys.

---

### Post by coffeecat on 2011-04-14
Good luck with that.

---

### Post by Rubi1200 on 2011-04-14
If you are going to have a dual-boot setup, I can highly recommend 2 things that you do before starting:

1. backups, backups, backups

2. read this fantastic guide on dual-boot setups (thanks to Herman):
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

