---
title: "PC freezes when configuring DKPG"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by solzhenitsyn on 2008-06-07
With synaptic and update manager, I get error message

As said, I open an terminal and type:

sudo dpkg --configure -a

It freezes at the following line:

updating fontconfig cache...

Only thing that works is shutting off the pc

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> With synaptic and update manager, I get error message

As said, I open an terminal and type:

sudo dpkg --configure -a

It freezes at the following line:

updating fontconfig cache...

Only thing that works is shutting off the pc

How long did you actually keep it running?

---

### Post by solzhenitsyn on 2008-06-07
Over an hour

Still the same entry in my terminal:
updating fontconfig cache...

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> Over an hour

Still the same entry in my terminal:
updating fontconfig cache...

From experience I know that that particular process takes some time. This is just a suggestion, but keep that process running for some time and see if it ends(it should).

---

### Post by solzhenitsyn on 2008-06-07
I think  that this problem comes from the upgrade

During the startup, the system does a check up every certain number of startups
During that check i get many errors

For example: 326.359687: ata1.00 : Drdy err
             326.359687: ata1.00 : Error <unc>
             etc

Get over a hundred of these errors

But the system finally starts up

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> I think  that this problem comes from the upgrade

During the startup, the system does a check up every certain number of startups
During that check i get many errors

For example: 326.359687: ata1.00 : Drdy err
             326.359687: ata1.00 : Error <unc>
             etc

Get over a hundred of these errors

But the system finally starts up

It seems like a bad sector problem. That may be a reason why you are getting those problems. 

When you reach the updating font config part, post the output of:-
```
dmesg | tail -25
```

---

### Post by solzhenitsyn on 2008-06-07
Then no sector would be OK, it keeps on giving errors till the end of time

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> Then no sector would be OK, it keeps on giving errors till the end of time

The fsck check?

---

### Post by solzhenitsyn on 2008-06-07
It 's a forced check at the start up

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> It 's a forced check at the start up

Does it happen everytime you start Ubuntu? Or after a set amount of reboots?

---

### Post by solzhenitsyn on 2008-06-07
A certain amount of reboots

I can skip it if I like and then my ubuntu starts up like there no problem (except synaptic and updates)

---

### Post by PmDematagoda on 2008-06-07
> **solzhenitsyn said:**
> A certain amount of reboots

I can skip it if I like and then my ubuntu starts up like there no problem (except synaptic and updates)

Then the bad sectors are found only in a specific place. 

As I said previously:-
When you reach the updating font config part, post the output of:-
```
dmesg | tail -25
```

---

### Post by solzhenitsyn on 2008-06-08
I ran the 'dkpg configure' thing for over  4 hours. It really freezes, it isn't just slow
How and where do I make such a output file?

---

### Post by PmDematagoda on 2008-06-08
> **solzhenitsyn said:**
> I ran the 'dkpg configure' thing for over  4 hours. It really freezes, it isn't just slow
How and where do I make such a output file?

I've had this problem myself, but to make sure, try and execute this command if possible:-
```
dmesg | tail -25 >> dmesg
```
that will save the results to a file called dmesg.

---

### Post by solzhenitsyn on 2008-06-08
Now I have this:
[  228.853133] Bluetooth: RFCOMM ver 1.8
[   87.056592] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[   87.056599] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[  101.526448] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  101.526455] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  101.526459] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[  101.527006] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  101.527182] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  101.527351] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  101.527530] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[  101.531492] [fglrx] GART Table is not in FRAME_BUFFER range 
[  101.531500] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  101.531503] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[  101.673813] [fglrx] interrupt source 20008000 successfully enabled
[  101.673822] [fglrx] enable ID = 0x00000004
[  101.674177] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  101.674373] [fglrx] interrupt source 10000000 successfully enabled
[  101.674377] [fglrx] enable ID = 0x00000005
[  101.674583] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  270.106091] NET: Registered protocol family 10
[  270.106910] lo: Disabled Privacy Extensions
[  270.108309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.403572] eth1: no IPv6 routers present
[  317.474020] UDF-fs: Partition marked readonly; forcing readonly mount
[  317.508478] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Oblivion', timestamp 2006/02/28 18:33 (1078)

I don't know whether I can make a log after the dpkg configure when the system freezes

---

### Post by PmDematagoda on 2008-06-08
> **solzhenitsyn said:**
> Now I have this:
[  228.853133] Bluetooth: RFCOMM ver 1.8
[   87.056592] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[   87.056599] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[  101.526448] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  101.526455] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  101.526459] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[  101.527006] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  101.527182] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  101.527351] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  101.527530] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[  101.531492] [fglrx] GART Table is not in FRAME_BUFFER range 
[  101.531500] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  101.531503] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[  101.673813] [fglrx] interrupt source 20008000 successfully enabled
[  101.673822] [fglrx] enable ID = 0x00000004
[  101.674177] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  101.674373] [fglrx] interrupt source 10000000 successfully enabled
[  101.674377] [fglrx] enable ID = 0x00000005
[  101.674583] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  270.106091] NET: Registered protocol family 10
[  270.106910] lo: Disabled Privacy Extensions
[  270.108309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.403572] eth1: no IPv6 routers present
[  317.474020] UDF-fs: Partition marked readonly; forcing readonly mount
[  317.508478] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Oblivion', timestamp 2006/02/28 18:33 (1078)

I don't know whether I can make a log after the dpkg configure when the system freezes

If it is indeed a bad sector problem, then there will be sometime before the PC locks up. Also, put the system monitor applet on your panel and instruct it to show the load, if the load increases then it is the time to execute the command, after which you can end the process which can stop the PC from freezing completely.

---

### Post by solzhenitsyn on 2008-06-08
Here an example: [ 1538.713119] ata1.00: configured for UDMA/100
[ 1538.713142] ata1: EH complete
[ 1542.347022] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1542.347030] ata1.00: BMDMA stat 0x25
[ 1542.347038] ata1.00: cmd c8/00:40:dc:0a:d2/00:00:00:00:00/e3 tag 0 dma 32768 in
[ 1542.347040]          res 51/40:34:e8:0a:d2/00:00:00:00:00/e3 Emask 0x9 (media error)
[ 1542.347043] ata1.00: status: { DRDY ERR }
[ 1542.347046] ata1.00: error: { UNC }
[ 1542.368368] ata1.00: configured for UDMA/100
[ 1542.368391] ata1: EH complete
[ 1545.853627] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1545.853636] ata1.00: BMDMA stat 0x25
[ 1545.853644] ata1.00: cmd c8/00:40:dc:0a:d2/00:00:00:00:00/e3 tag 0 dma 32768 in
[ 1545.853646]          res 51/40:34:e8:0a:d2/00:00:00:00:00/e3 Emask 0x9 (media error)
[ 1545.853649] ata1.00: status: { DRDY ERR }
[ 1545.853652] ata1.00: error: { UNC }
[ 1545.877526] ata1.00: configured for UDMA/100
[ 1545.877552] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1545.877557] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1545.877562] Descriptor sense data with sense descriptors (in hex):
[ 1545.877564]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1545.877570]         03 d2 0a e8 
[ 1545.877573] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1545.877580] end_request: I/O error, dev sda, sector 64097000
[ 1545.877601] ata1: EH complete


During the check at the startup, I get similar errors

---

### Post by PmDematagoda on 2008-06-08
Yep, there we are. Those are bad sectors, or maybe a sign that your hard disk is failing.

Just to see, install smartmontools with:-
```
sudo apt-get install smartmontools
```
and check the drive with:-
```
sudo smartctl -H /dev/location-of-drive
```

---

### Post by solzhenitsyn on 2008-06-08
I get:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Synaptic and updates don't work anymore, remember

---

### Post by PmDematagoda on 2008-06-08
> **solzhenitsyn said:**
> I get:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Synaptic and updates don't work anymore, remember

Damn, then it becomes a little more complicated. Try this, boot the Ubuntu Live CD, unmount the Ubuntu root drive/partition and then do an fsck check on it with:-
```
sudo fsck -c /dev/location-of-driveorpartition
```
after that is done, see if the problem is now fixed.

---

### Post by solzhenitsyn on 2008-06-08
I don't have the ubuntu cd anymore

I'll download the ubuntu 8.04

---

### Post by PmDematagoda on 2008-06-08
> **solzhenitsyn said:**
> I don't have the ubuntu cd anymore

I'll download the ubuntu 8.04

Ok, good luck with that:).

---

### Post by solzhenitsyn on 2008-06-08
Ok, I burned the iso on a dvd
I restart and get the menu:

Trying ubuntu without installing
Installing
Test cd 
Memory test etc

What should I do to unmount partition sda6 and do the fsck?

Thx

---

### Post by PmDematagoda on 2008-06-08
Do:-
```
sudo umount /dev/sda6
```
and then:-
```
sudo fsck -c /dev/sda6
```

---

### Post by solzhenitsyn on 2008-06-08
With the linux dvd I get a graphic menu with the possible options (test cd, install linux, etc, ..)

How can i get into a terminal screen?

---

### Post by PmDematagoda on 2008-06-08
> **solzhenitsyn said:**
> With the linux dvd I get a graphic menu with the possible options (test cd, install linux, etc, ..)

How can i get into a terminal screen?

Press Install or Use Linux(or something similar). Once you reach the desktop open up a terminal and execute the command.

---

### Post by solzhenitsyn on 2008-06-09
If I run linux from the CD/DVD and type the command in a terminal, I get th e message that dev/sda6 is not found

If I chose install, it will probably overwrite my existing version

I started up and chose ubuntu 8.04 recovery mode from my hard drive
Got following options:

Normal Boot
DPKG repair packages
Root shell promt
Repair x server

I chose dpkg

Got all these messages:

[54870.455860] ata1.00: status {DRDY ERR}
[54870.455860] ata1.00: error {UNC}
[54870.455860] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[54870.455860] ata1.00: BMDMA stat 0x25
[54870.455860] ata1.00: cmd c8/00:08:e4:0a:d2/00:00:00:00:00/e3 tag 0 dma 4096 in

Over 12 hours same messages, only the first letters in brackets are changing

If I start up, System says that the primary IDE master is bad, backup and replace and I enter my BIOS

If I exit (no changes saved), I can start up Ubuntu or windows properly

---

### Post by PmDematagoda on 2008-06-09
It looks like the hard drive is either going to fail, or the IDE controller. What I suggest is for you to get it checked and have them replaced because if you continue using this drive then it may fail suddenly without warning.

---

### Post by solzhenitsyn on 2008-06-09
I have a laptop, so I can't really replace the cable or so

Back up and fingers crossed how long it will still run?

---

### Post by PmDematagoda on 2008-06-09
> **solzhenitsyn said:**
> I have a laptop, so I can't really replace the cable or so

Back up and fingers crossed how long it will still run?

That depends on the hardware in question itself unfortunately.

---

### Post by solzhenitsyn on 2008-06-09
Hard disk is split up for dual boot
I started windows and did a disc check, no errors or bad sectors found

I started ubuntu in recovery mode
I chose root prompt

I typed:

root@solzhenitsyn: fsck dev/sda6

I get:
fsck 1.40.8 (13-Mar-2008)
Usage fsck.ext3 [- panyrcdfustDFSV] [-b superblock] [etc] device

Emergency help
-p
-n
etc

Etc means a lot of more options , too many to type

---

### Post by PmDematagoda on 2008-06-10
Whatever you do, don't do an fsck check on the Ubuntu root while you are running Ubuntu itself because it can cause more harm than good.

---

### Post by solzhenitsyn on 2008-06-10
Ubuntu did an automatic fsck at boot

Message:
/dev/sda6: unexpected consistency; run fsck manually
            (i.e. without -a or -p options)
fsck died with exit status 4

So i Typed:

fsck -y /dev/sda6


See some DRDY ERR, error {UNC}, buffer I/O errors
Some things are automatically fixed

Result:
/dev/sda6: **** file system was modified ****
/dev/sda6: **** reboot linux ****
/dev/sda6: 185193/5128192 files (3.9% contiguous), 332262/10239413 blocks

Is this good or bad?

---

### Post by PmDematagoda on 2008-06-10
Did you do that in the Live CD or in the normal Ubuntu install?

---

### Post by solzhenitsyn on 2008-06-10
It did a manual fsck
It said in single user mode

It's the planned fsck check every 30 boots I think

---

### Post by solzhenitsyn on 2008-06-10
didn't use the ubuntu dvd

---

### Post by solzhenitsyn on 2008-06-10
Sda6 wasn't mounted

The symstems gives a warning if you want to fsck a mounted partition

---

### Post by PmDematagoda on 2008-06-10
You should use the Ubuntu Live CD when running a manual fsck on the root since you are still using it even in single user mode and can cause some more problems.

Boot the Ubuntu Live CD and try:-
```
sudo fsck -rcM /dev/sda6
```
Post any errors or messages here.

---

### Post by PmDematagoda on 2008-06-10
> **solzhenitsyn said:**
> Sda6 wasn't mounted

The symstems gives a warning if you want to fsck a mounted partition

So are you using the Ubuntu Live CD or what?

---

### Post by solzhenitsyn on 2008-06-11
Ok, I'll try with the live cd

What does -rcM mean?

---

### Post by PmDematagoda on 2008-06-11
> **solzhenitsyn said:**
> Ok, I'll try with the live cd

What does -rcM mean?

Those are options with which fsck can be used, for more information on these options and many others, you can take a look at the manual with:-
```
man fsck
```

---

### Post by solzhenitsyn on 2008-06-11
I am running Ubuntu from live cd

copy of my terminal:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fsck -rcM /dev/sda6
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Checking for bad blocks (read-only test):          231611/       10239412

It has only reached block 231611 after 3 hours, will take over 1 day to check all blocks  
I have a laptop and cd drive has always been slow, can this influence the fsck speed as it is running from the live cd

---

### Post by PmDematagoda on 2008-06-12
It would be difficult to imagine that the Live CD would get slow while running an fsck check unless the hard drive fails or is on the verge of doing so. But try this:-
```
sudo smartctl -H /dev/sda
```
post the output of it.

---

### Post by solzhenitsyn on 2008-06-12
It started to go faster and faster
Here are the results:

ubuntu@ubuntu:~$ sudo fsck -rcM /dev/sda6
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Checking for bad blocks (read-only test): done                                
/dev/sda6: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 16386: 65186
Multiply-claimed block(s) in inode 32772: 67365
Multiply-claimed block(s) in inode 33028: 67116
Multiply-claimed block(s) in inode 33458: 265536
Multiply-claimed block(s) in inode 33514: 66359
Multiply-claimed block(s) in inode 33531: 66442
Multiply-claimed block(s) in inode 33582: 66928
Multiply-claimed block(s) in inode 33584: 66949
Multiply-claimed block(s) in inode 33746: 67032
Multiply-claimed block(s) in inode 34058: 67344
Multiply-claimed block(s) in inode 49854: 132560
Multiply-claimed block(s) in inode 49892: 132623
Multiply-claimed block(s) in inode 51149: 132711
Multiply-claimed block(s) in inode 51872: 99024
Multiply-claimed block(s) in inode 53879: 132798
Multiply-claimed block(s) in inode 53913: 132864 132886
Multiply-claimed block(s) in inode 53925: 132952
Multiply-claimed block(s) in inode 53927: 132974
Multiply-claimed block(s) in inode 54316: 133040
Multiply-claimed block(s) in inode 54342: 133062
Multiply-claimed block(s) in inode 54404: 133150
Multiply-claimed block(s) in inode 55169: 133511
Multiply-claimed block(s) in inode 65670: 133599
Multiply-claimed block(s) in inode 66336: 153806 153872 153894 153960 153982
Multiply-claimed block(s) in inode 66337: 154048 154070 154136 154158 154224 154246 154312
Multiply-claimed block(s) in inode 66338: 154334
Multiply-claimed block(s) in inode 66339: 154400
Multiply-claimed block(s) in inode 66341: 154421 154509 154694
Multiply-claimed block(s) in inode 66342: 154760 154782 154848 154870
Multiply-claimed block(s) in inode 66724: 153784
Multiply-claimed block(s) in inode 67455: 133128
Multiply-claimed block(s) in inode 67527: 133216 133238
Multiply-claimed block(s) in inode 67881: 153616
Multiply-claimed block(s) in inode 67886: 153631
Multiply-claimed block(s) in inode 67978: 153718
Multiply-claimed block(s) in inode 81941: 237632 237483 237208 261976 244019 244256 243770 243853 249056 241167 244527 237308 242764 242765 239749 238905 238909 233374 240896 240917 240918 248798 250815 239154 243832 240668 236643 240585 234776 234547 234548 240984 239745 229266 243437 243438 248408 243936 234289 236809 235379 235046 249222 243014 231362 244277 244278 237432 242265 250712 239224 248864 248888 241001 239828 239832 237566 238231 237649 244194 238988 238992 238822 239158 240751 239240 239241 237732 237733 237736 235112 242007 234264 238318 248528 248549 237816 237819 244610 231008 249306 250731 251376 236052 236053 238824 238825 239579 239582 242090 235129 236219 244344 244361 239071 239075 239237 239238 229328 262142 239911 239915 235212 235213 229349 240834 240568 249288 248632 238384 238406 239994 239998 244444 242216 235637 242348 242349 243271 243272 251405 237653 236302 236432 237968 237982 237984 237985 235296 242431 242432 242514 242515 234880 231279 248715 247715 243354 243355 251655 250990 240336 238235 238065 238069 231029 235554 243687 243504 243521 238656 238659 239648 236477 262059 261352 243604 251738 239662 239664 239665 241924 251864 247680 249368 249389 261643 242847 242848 230946 238489 238493 236792 231196 234372 234373 235616 236136 237142 234459 238148 238152 248973 241342 241408 241425 238739 238742 230904 261385 238472 237225 237059 261792 261809 261726 234963 261560 251488 229183 236892 236893 240064 240077 240078 240080 240081 242930 236976 241084 236726 237899 237902 239496 239499 249555 249562 261893 249472 240419 235720 234714 242992 243013 241591 251571 235803 249139 235969 236560 248466 234797 231112 239412 239413 239416 234631 242597 242598 242664 238808 238572 238573 240502 241508 240161 238576 242681 243080 243096 243097
Multiply-claimed block(s) in inode 98407: 231611
Multiply-claimed block(s) in inode 98435: 227192 227254 227320 227337 227420 227503 227586 227648 227669 227752 227872 227927 228011 228094 228160 228177 271955
Multiply-claimed block(s) in inode 98682: 230106
Multiply-claimed block(s) in inode 114709: 252578 252640 252661
Multiply-claimed block(s) in inode 114760: 262733 262816 262899 262982 263048 263065 263148 263231 263314 263440 263489 263573 263656 263739 263822 263888 263905 263988 264071 264154 264216 264238 264304 264321 264496 264579 264662 264728 264745 264828 264911
Multiply-claimed block(s) in inode 114761: 262720 294291 294472 294476 294564
Multiply-claimed block(s) in inode 114764: 294652
Multiply-claimed block(s) in inode 114766: 340166 340232 340249
Multiply-claimed block(s) in inode 114785: 252079
Multiply-claimed block(s) in inode 114821: 251996
Multiply-claimed block(s) in inode 115838: 230168 230189
Multiply-claimed block(s) in inode 115840: 230272
Multiply-claimed block(s) in inode 115890: 229920
Multiply-claimed block(s) in inode 115908: 252495
Multiply-claimed block(s) in inode 115940: 229940
Multiply-claimed block(s) in inode 116224: 272795
Multiply-claimed block(s) in inode 116472: 233824
Multiply-claimed block(s) in inode 116726: 252411
Multiply-claimed block(s) in inode 116877: 230023
Multiply-claimed block(s) in inode 116879: 231786 231848 231869 232036
Multiply-claimed block(s) in inode 116880: 232119 232202
Multiply-claimed block(s) in inode 116881: 232264 232285
Multiply-claimed block(s) in inode 116901: 232368
Multiply-claimed block(s) in inode 117243: 233256
Multiply-claimed block(s) in inode 117270: 233291
Multiply-claimed block(s) in inode 117313: 233882
Multiply-claimed block(s) in inode 117420: 235886
Multiply-claimed block(s) in inode 117485: 235952
Multiply-claimed block(s) in inode 117532: 241674
Multiply-claimed block(s) in inode 117586: 241736
Multiply-claimed block(s) in inode 117607: 241757
Multiply-claimed block(s) in inode 117608: 241758
Multiply-claimed block(s) in inode 117674: 241824
Multiply-claimed block(s) in inode 117691: 241841
Multiply-claimed block(s) in inode 117773: 251913
Multiply-claimed block(s) in inode 117828: 252744
Multiply-claimed block(s) in inode 117926: 252864
Multiply-claimed block(s) in inode 117941: 252919
Multiply-claimed block(s) in inode 131196: 272712
Multiply-claimed block(s) in inode 131214: 293500
Multiply-claimed block(s) in inode 131507: 272608
Multiply-claimed block(s) in inode 131518: 272629
Multiply-claimed block(s) in inode 131544: 272878
Multiply-claimed block(s) in inode 131560: 272944
Multiply-claimed block(s) in inode 131606: 272961
Multiply-claimed block(s) in inode 132342: 272463
Multiply-claimed block(s) in inode 132479: 272546
Multiply-claimed block(s) in inode 132701: 293472
Multiply-claimed block(s) in inode 133935: 273136
Multiply-claimed block(s) in inode 148475: 342936
Multiply-claimed block(s) in inode 148488: 343019
Multiply-claimed block(s) in inode 148555: 335891
Multiply-claimed block(s) in inode 148907: 343102
Multiply-claimed block(s) in inode 149002: 336066
Multiply-claimed block(s) in inode 149233: 343168
Multiply-claimed block(s) in inode 149259: 343185
Multiply-claimed block(s) in inode 149287: 336128
Multiply-claimed block(s) in inode 149289: 336141
Multiply-claimed block(s) in inode 149301: 336224
Multiply-claimed block(s) in inode 149312: 336307
Multiply-claimed block(s) in inode 149324: 336390 336391
Multiply-claimed block(s) in inode 149340: 340083
Multiply-claimed block(s) in inode 149443: 343268
Multiply-claimed block(s) in inode 164171: 340000
Multiply-claimed block(s) in inode 164250: 343351
Multiply-claimed block(s) in inode 164320: 338071
Multiply-claimed block(s) in inode 164351: 339576
Multiply-claimed block(s) in inode 164352: 339659
Multiply-claimed block(s) in inode 164353: 341072 341089
Multiply-claimed block(s) in inode 164357: 341172
Multiply-claimed block(s) in inode 164358: 341256
Multiply-claimed block(s) in inode 164359: 341376
Multiply-claimed block(s) in inode 164360: 341422 341488 341505
Multiply-claimed block(s) in inode 164461: 343434
Multiply-claimed block(s) in inode 164814: 339492
Multiply-claimed block(s) in inode 165046: 343496
Multiply-claimed block(s) in inode 165078: 343517
Multiply-claimed block(s) in inode 165151: 338216
Multiply-claimed block(s) in inode 638988: 1403685
Multiply-claimed block(s) in inode 819208: 1662999
Multiply-claimed block(s) in inode 2179133: 264994 265056 265078 265144 265161 265656 265668 265751 265834 292600 292612 292700 292788 292876 292963 293051 293139 293227 293588 293676 293764 293851 293939 294027 294115 294203
Multiply-claimed block(s) in inode 2179136: 335096 335143 335226 335608 335642 335704 335725 335808 336474 336536 336557 336640 336723 336806 336936 336981 337064 337147 337231 337314 337376 337397 337480 337563 337646 337712 337729 337904 338154 338237 338320 338403 338486 338552 338569 338652 338736 338856 338911 338994 339056 339077 339160 339243 339326 339392 339409 339834 339896 339917 340332 340416 340499 340582 340648 340665 340840 340923 341006 341588 341712 341763 341846 341912 341929 342012 342096 342179 342262 342328 342345 342428 342511 342594 342720 342769 342852 343896 343942
Multiply-claimed block(s) in inode 2179137: 337987
Multiply-claimed block(s) in inode 2179138: 366984 367015 367098 367160 367181 370504 370530 370656 370705 370788 370871 370954 371016 371038 371104 371121 371204 371287 371370 374056 374880 374896 374979 375063
Multiply-claimed block(s) in inode 2720489: 64512 99235 131735 62888 62924 129871 66728 66276 99576 66608 105088 105103 130495 66192 63672 64346 130319 130134 130047 66783 104752 104770 131976 130407 132086 63589 132152 132174 129664 63792 129695 131998 64080 64097 99480 99493 64408 64263 131696 62720 67199 62749 62750 62751 66866 63847 64429 66109 66080 65436 62753 62754 62755 62756 62757 62758 62759 62761 62762 62763 62764 67282 64180 63931 64014 130264 66525 132064 65519 66504 129959
Multiply-claimed block(s) in inode 2722087: 1613934 1396488 1475776 1523663 1527352 1530520 1530537 1528774 1519128 1532616 1623756 1616512 1523392 1523413 1614359 1527103 1614109 1530620 1614442 1519248 1518920 1530288 1554527 1623160 1623165 1527186 1476616 1614275 1519303 1614192 1530371 1614064 1530454 1396240 1527248 1527269 1532808
Multiply-claimed block(s) in inode 3817861: 63007 63091 63174 63240 63257 63340 63423 63506 63568 64596 64679 64854 64920 64937 65020 65103 133368 133423
Multiply-claimed block(s) in inode 4932342: 1532200 1531710 1373152 1373169 1373086 1373072 1532134 1531688
Multiply-claimed block(s) in inode 4932343: 1530944 1530961 1531045 1373842 1411936 1559396 1531460 1559479 1530878 1532550 1523072 1561816 1561833 1474416 1474437 1560136 1561750 1411520 1373672 1373676 1561916 1474271 1474520 1531128 1411136 1474354 1530038 1411224 1531626 1373759 1474188 1411575 1531360 1531377
Multiply-claimed block(s) in inode 4932345: 1529955 1571880 1402709 1530121 1401733 1530104 1571992 1572018 1276932 1571930
Multiply-claimed block(s) in inode 4932352: 1404037 1473514 1403597 1517706 1403949 1276872 1403236 1473472 1374408 1374424 1517648 1532633 1402973 1403149 1560319 1374032 1560236 1370808 1370828 1374092 1403061 1523192
Multiply-claimed block(s) in inode 4984300: 77844
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Error reading block 338317 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? 

/dev/sda6: e2fsck canceled.

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

---

### Post by PmDematagoda on 2008-06-12
Can you please post the output of the command given previously?

---

### Post by solzhenitsyn on 2008-06-12
which previous command?

---

### Post by PmDematagoda on 2008-06-12
This command:-
```
sudo smartctl -H /dev/sda
```
if that gives a command not found, install smartmontools with:-
```
sudo apt-get install smartmontools
```
and try again.

---

### Post by solzhenitsyn on 2008-06-12
ubuntu@ubuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

---

### Post by solzhenitsyn on 2008-06-12
ubuntu@ubuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

---

### Post by PmDematagoda on 2008-06-12
Hmm, that looks good, so it might be something with the file system more than anything.

If you wish to run an fsck check without having to control what it does or fix(be warned that this might cause problems), run:-
```
sudo fsck -acM /dev/sda6
```

---

### Post by solzhenitsyn on 2008-06-12
ubuntu@ubuntu:~$ sudo fsck -arM /dev/sda6
fsck 1.40.8 (13-Mar-2008)
/dev/sda6: clean, 184792/5128192 files, 3314930/10239413 blocks
ubuntu@ubuntu:~$

---

### Post by solzhenitsyn on 2008-06-13
ubuntu@ubuntu:~$ sudo fsck -acM /dev/sda6
fsck 1.40.8 (13-Mar-2008)

Nothing happpens
Laptop is processing (third light on my laptop indicates activity)
Everything freezes
Left it open all night
Everything still frozen

---

### Post by PmDematagoda on 2008-06-13
So it looks like a bad sector problem, in this case it may render your hard drive worthless. Is there no way for you to change the hard drive at least?

---

### Post by solzhenitsyn on 2008-06-13
I know how to change a hard drive, cd-writer in a pc.
But I've never opened a laptop
Are laptop pieces very expensive?

---

### Post by solzhenitsyn on 2008-06-13
Why don't I have any errors when I scan my hard drive in Windows?
May it help to re-install Ubuntu?

---

### Post by PmDematagoda on 2008-06-13
> **solzhenitsyn said:**
> Why don't I have any errors when I scan my hard drive in Windows?
May it help to re-install Ubuntu?

Did you check the drive for bad sectors? 

It may help, but it most likely may not.

About laptop parts, they aren't really expensive and hard drives themselves are rather cheap, the price depends on the capacity, features and the brand itself.

---

### Post by solzhenitsyn on 2008-06-13
Is replacing a hard drive in a laptop as easy as changing one in a desktop?

Never opened a laptop before

---

### Post by PmDematagoda on 2008-06-13
> **solzhenitsyn said:**
> Is replacing a hard drive in a laptop as easy as changing one in a desktop?

Never opened a laptop before

I have a Presario V3000 and I can change the hard drive on that. About your particular laptop, just take it to a service center so that nothing goes wrong and even if something does go wrong, you won't be held accountable for it:).

---

### Post by solzhenitsyn on 2008-06-13
I have an old desktop, I'll look if ubuntu may run it on.
Just looking for a wireless network card which runs on linux ;)

Keep windows on laptop? i only use it for updating my gps, so if It breaks down completely, no one will miss windows :)

---

### Post by PmDematagoda on 2008-06-13
> **solzhenitsyn said:**
> I have an old desktop, I'll look if ubuntu may run it on.
Just looking for a wireless network card which runs on linux ;)

Keep windows on laptop? i only use it for updating my gps, so if It breaks down completely, no one will miss windows :)

The choice is completely yours:). About the wireless, you may want to wait until Ubuntu 8.10 comes out since there are plans to improve networking on Ubuntu a lot.

---

