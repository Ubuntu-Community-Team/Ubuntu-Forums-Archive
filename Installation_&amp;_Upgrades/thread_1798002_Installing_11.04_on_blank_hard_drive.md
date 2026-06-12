---
title: "Installing 11.04 on blank hard drive?"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Twizlerr on 2011-07-05
I'm trying to install Ubuntu on a brand new, 1TB hard drive, but I'm having some issues. I created a 64-bit bootable USB with the universal USB installer (I think that's what it's called). My hard drive is completely blank, and BIOS recognizes it. My USB is not recognized if I plug it into a port on my mobo, but it does work on the USB port on the front of my computer case. It boots fine from the USB, but when I go to install ubuntu, it doesn't recognize my hard drive and tries to install to my USB (which doesn't have enough space anyways).

I have tried plugging my hard drive into a SATA3 and SATA2 port. It only works in the SATA3 port, even though BIOS says it's a SATA2 hard drive.

Here's my computer's setup:
ASRock H61M/U3S3
Intel Pentium Dual Core 2.6GHz Processor
2x2GB RAM
1TB Samsung Hard Drive
4GB USB 2.0 Stick

I cannot figure out how to get ubuntu to see my hard drive at all, so help is greatly appreciated.

---

### Post by YesWeCan on 2011-07-05
Hi there. I like ASRock :)
You should be able to use any SATA port for the HDD. So plug it in and then would you boot Ubuntu and run:
[COLOR=Navy]sudo sfdisk -luS[/COLOR]
and post the results?

This command just lists all the storage devices Ubuntu can detect and shows their details. This will show whether or not Ubuntu's OS can see the drive as opposed to the installer. There are some conditions that upset the installer.

---

### Post by Twizlerr on 2011-07-05
```
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 1016 cylinders, 124 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/153/50 (instead of 1016/124/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048   7817215    7815168   b  W95 FAT32
        start: (c,h,s) expected (0,40,49) found (0,32,33)
        end: (c,h,s) expected (1021,131,16) found (486,152,50)
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

```

---

### Post by 23dornot23d on 2011-07-05
ONE of the external hard drives that I use - did not show up from boot ....


Unless ..... 

1 ...... I make a point of unplugging the USB and taking the power lead out of the back of the USB hard drive .....

2 ..... Plugging the cable back in so the USB hard drive starts up

3 .... Then plug in the USB cable to the Desktop machine 

4 .... Then to cold boot up the Desktop machine ..... then it detects the drive .... ( !!! )

Bizarre I know ...... but this works every time on one Iomega Terra USB hard drive that otherwise will not show up to boot from.

( I will post this here .... as it may be useful to someone somewhere ..... and it works
every time for me ..... and its a pain ..... but its the only way I found to get the BIOS
to see it and also to boot from it .... :confused: )

I have 3 other USB drives all bootable and none of the others need this ....... others 
are 1 Terra and 500 Gig Seagate's and one 320 Gig Western Digital.

___________________________________________________

Just seen the other posts now and more information ....

1TB Samsung Hard Drive

If the 1 Terra Hard drive is not a USB one ignore this .....

---

### Post by Twizlerr on 2011-07-05
> **23dornot23d said:**
> Just seen the other posts now and more information ....

1TB Samsung Hard Drive

If the 1 Terra Hard drive is not a USB one ignore this .....

It's an internal hard drive

---

### Post by srs5694 on 2011-07-06
First, it appears that the board you've got uses UEFI firmware rather than a conventional BIOS, based on the manual I downloaded from the ASRock Web site. (You may be booting with a BIOS compatibility mode, though.) UEFI changes a lot of the rules relating to OS booting, and worse, there are still a lot of bugs to be worked out, both in Ubuntu and in at least some UEFI implementations. Thus, I have two recommendations related to the UEFI nature of the board:


[list]
[*]Go into the firmware setup utility and adjust options related to the boot mode (BIOS vs. UEFI). These aren't always labeled in an obvious way, and a quick scan of the manual I downloaded didn't suggest any specific things to try, but I just glanced at it quickly.
[*]Check the ASRock Web site for firmware updates. I see there are several already released, and it may be worth updating the firmware. I haven't checked the release notes to see if these releases fix specific problems that might be related to what you're experiencing, though; an update might get you nothing. You should check the firmware version you've got, read the release notes, and judge for yourself whether it's worth the effort and risk. (Firmware updates can go badly and "brick" a motherboard. This occurrence is rare, but it can happen.)
[/list]


I don't think, however, that either of these suggestions will help with your fundamental problems. First, I'd like clarification of a point:

[quote=Twizlerr]I have tried plugging my hard drive into a SATA3 and SATA2 port. It only  works in the SATA3 port, even though BIOS says it's a SATA2 hard drive.[/quote]

If by this you mean that the firmware can't see the drive when you plug it into an SATA2 port, then this suggests that the hardware may be defective. To test this hypothesis, try using a different cable and a different disk. If the firmware can't see any disk on your SATA2 port, then I'd return the board as defective.

If, OTOH, you mean that the firmware sees the drive on an SATA2 port but that the Ubuntu installer doesn't when it's plugged into such a port but does on an SATA3 port, then my suspicion is that the Ubuntu installer's kernel lacks the appropriate driver. Perhaps the hardware is just too new or there's something quirky about its implementation on your motherboard. The best solution in this case would be to install using an SATA3 port. In the future, you should be able to shift the disk to an SATA2 port, once driver support arrives in the kernel.

You could also try an unrelated distribution, the newer the better. (Perhaps Fedora 15, for instance.) That will have a kernel that was compiled independently of the Ubuntu kernel, so it may have different patches and compile options that might help get the system up and running.

---

### Post by Twizlerr on 2011-07-06
Thank you, srs5694. Your reply was very in-depth. Fortunately, in short all I had to do was plug my hard drive into the SATA2 port. #-o

Here's the long version:
My computer does boot in UEFI mode instead of BIOS. I couldn't find any options to change to BIOS. Updating the firmware would have most likely taken the most time with the least outcome, so that was going to be my last resort. Next on the list was to try different cables and ports. I have a black cable labeled "SATA 6/GBs" and a red cable with minimal labels. The computer recognized the hard drive with both cables when it was plugged into the SATA3 port. The Ubuntu installer would not recognize the hard drive though. 

So I decided to give the SATA2 ports a try, even though the last time I tried those ports the hard drive wasnt recognized. I ignored the "No hard disk recognized" message (or whatever it says) and continued to boot the Ubuntu installer. The installer was then able to recognize my hard drive and Ununtu 11.04 is already installed on my PC.


Thanks everyone for all of your help! Everything is working great so far.

---

### Post by srs5694 on 2011-07-06
It could be that the "no hard disk recognized" message wasn't referring to the hard disk itself but to a *bootable* hard disk -- that is, one with an EFI System Partition (ESP) on it, which is part of the (U)EFI boot process. If so, installing Ubuntu would have fixed that problem, since Ubuntu will create an ESP when it installs.

One word of caution, though: The ESP that Ubuntu creates uses FAT16. Windows 7, however, insists on having a FAT32 ESP -- or at least, that's been true in my tests. (I've seen posts from another person who claims that Windows 7 was happy with a FAT16 ESP, so there may be some other factor at play, like an interaction with the UEFI version or some quirk of the FAT16 ESP created by mkdosfs in Linux.) If you don't plan to install Windows 7, then this obviously isn't an issue for you. If you do, though, you should be aware of it so that you can back up the ESP, convert it to FAT32, and restore its files so that Windows will be happy with it.

---

### Post by YesWeCan on 2011-07-06
> **Twizlerr said:**
> Thank you, srs5694. Your reply was very in-depth. Fortunately, in short all I had to do was plug my hard drive into the SATA2 port. #-o
:P
That made me chuckle. I'm glad you fixed it *the easy way*.
I really like my ASRock mobo so I hope yours works as well for you as mine has for me.

---

