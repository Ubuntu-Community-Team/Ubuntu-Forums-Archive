---
title: "No Grub entry for 2nd drive/OS"
date: 2022-01-17
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-01-17
So, my default install is to my nvme0 drive, but when I press ESC to bring up the Grub menu, there's no entry for my sda (SSD) drive.
 
(I'm running Linux-MATE 20.04.3 on both of those drives, now with kernel*** 5.4.0-94-generic*** on both drives.)

I'd like to create an entry in the Grub menu for my sda drive, but I'm not sure where to go (or how) to do that.  

At the moment, the only way I can boot to /dev/sda is by doing a boot override in the BIOS/UEFI.

My other main problem is that Grub (or perhaps a *separate* Grub) is on the MBR of /dev/sda, looking -- but not finding -- core.img.  

Quoting OldFred: [I]

With UEFI/gpt you should never boot in BIOS mode as that would try to  repair in BIOS mode. Grub should not then be installed to gpt's  protective MBR, but if it is and you never try to boot in BIOS mode, it  will not matter. Useing dd to erase it is more dangerous than just  leaving it.[/I]

[I][B]How can I safely delete it?
[/B][/I]
Both drives are GPT/UEFI-formatted.  Thanks for any tips toward solving either or both of these issues.

Boot-Info script [here]("https://paste.ubuntu.com/p/5fG5SbXxDW/").

---

### Post by yancek on 2022-01-17
If you have 2 Linux systems installed, you should boot directly to the Grub menu to make your OS selection and there should be no reason to use the ESC key.
If both drives are GPT/UEFI, do you have a separate EFI partition on each drive or only on one drive?
While booted into your primary drive, what result do you see when you run :  sudo update-grub? 

>  My other main problem is that Grub (or perhaps a *separate* Grub) is on the MBR of /dev/sda, looking -- but not finding -- core.img.  


An EFI install will not have any code in the MBR,  A legacy/CSM install on a gpt drive will look for a core-img file in an unformatted bios_grub partition, usually 1-2 MB in size.

---

### Post by watchpocket on 2022-01-17
> **yancek said:**
> If you have 2 Linux systems installed, you should boot directly to the Grub menu to make your OS selection and there should be no reason to use the ESC key.

Well, If you use one system more than the other, wouldn't that be a reason to boot directly into that primary system, and to hit ESC to bring up the GRUB menu only when you want to boot into your secondary, non-default-boot system?

> If both drives are GPT/UEFI, do you have a separate EFI partition on each drive or only on one drive? 

Both drives are GPT/UEFI, and I do have an EFI partition on both drives.

>  While booted into your primary drive, what result do you see when you run :  sudo update-grub? 

Wow, thank you.  Solving that problem was as simple as updating GRUB. (I ran *sudo update-grub* over on the main drive but am not there now. I'm in my sda drive because I wanted to test logging into sda with the corrected GRUB menu. 

 After doing *sudo update-grub*, upon reboot, both drives were indeed accessible from the GRUB menu.

>  An EFI install will not have any code in the MBR,  A legacy/CSM install on a gpt drive will look for a core-img file in an unformatted bios_grub partition, usually 1-2 MB in size.

I think this SSD (my /dev/sda) had a legacy install when it was inside my old computer.  Or something. Which apparently still leaves me with this:

[I]Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector-1634575840 of the same hard drive for core.img, but core.img can not be found at this location.

[/I]Even though I don't boot in BIOS-mode, that GRUB shouldn't be in the MBR, should it?

If not, I'd like to (safely) delete it.

---

### Post by MAFoElffen on 2022-01-17
> **watchpocket said:**
> My other main problem is that Grub (or perhaps a *separate* Grub) is on the MBR of /dev/sda, looking -- but not finding -- core.img.  

Let's see for ourselves... Please post the results of 
```

sudo dd if=/dev/sda bs=512 skip=0 count=1 | hexdump -C

```
If so, the bootstrap code would be in the first 446 bytes of that 512  byte sector 0...

Even if it is there, and if core.img did exist, if the BIOS is set to boot as EFI, then it doesn't matter. (No fowl / No harm) Because the EFI BIOS is going to look at the /EFI/ directory for the EFI boot files... Not for that bootstrap code.

If it is bothering you that it is there, there is a way to zero it out, but I think that oldfred already had advised/told you that might be harmful... The process of that physically overwrites the disk in specific bytes to a specific location... The math has to be correct. If you did do that, you accept the responsibility and need to ensure that that process does not destroy the GPT Header section and/or the first GPT Partition table... I have done that and know how to do that, but if you have a typo... bad news.

---

### Post by oldfred on 2022-01-18
While I still do not suggest running dd, I did post command.
[https://ubuntuforums.org/showthread.php?t=2470524&p=14073786#post14073786](https://ubuntuforums.org/showthread.php?t=2470524&p=14073786#post14073786)
And again, you have to be sure command is typed exactly correctly. 
One user did admit putting an extra space after / and deleted entire system.

If you boot in old BIOS/Legacy/CSM mode the grub in MBR will just give a grub> command line as it cannot find rest of grub. Often you can manually boot from that.
If MBR is blank and you then attempt to boot in BIOS mode, it will just fail and UEFI may or may not give a message on system not found.

Or you never should boot in BIOS mode, and with any USB flash drive always chose the UEFI:flash drive option, not any other.

---

### Post by watchpocket on 2022-01-18
> **MAFoElffen said:**
> Let's see for ourselves... Please post the results of 
```

sudo dd if=/dev/sda bs=512 skip=0 count=1 | hexdump -C

```
If so, the bootstrap code would be in the first 446 bytes of that 512  byte sector 0...


```
--> sudo dd if=/dev/sda bs=512 skip=0 count=1 | hexdump -C   
[sudo] password for rj: 
00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
1+0 records in
1+0 records out
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 e0 a5 6d 61  |..............ma|
512 bytes copied, 0.00801054 s, 63.9 kB/s
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  f6 07 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |...t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d 5a 84 d2 0f  |...p.v....s.Z...|
000000f0  83 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  02 00 ee ff ff ff 01 00  00 00 af 1a c8 6f 00 00  |.............o..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

You'll likely be able to decipher this, but the only part of it I understand is the *"GRUB .Geom.Hard Disk.Read. Error"* at the lower right.

> Even if it is there, and if core.img did exist, if the BIOS is set to boot as EFI, then it doesn't matter. (No fowl / No harm) Because the EFI BIOS is going to look at the /EFI/ directory for the EFI boot files... Not for that bootstrap code.

So essentially I should stop worrying myself about it and leave it there because it's 99% harmless. Point taken.


> If it is bothering you that it is there, there is a way to zero it out, but I think that oldfred already had advised/told you that might be harmful... The process of that physically overwrites the disk in specific bytes to a specific location... The math has to be correct. If you did do that, you accept the responsibility and need to ensure that that process does not destroy the GPT Header section and/or the first GPT Partition table... I have done that and know how to do that, but if you have a typo... bad news.

Right.  I get it.  I'm not going to go there.  Thanks (to you and OldFred both) for clueing me in.

---

### Post by watchpocket on 2022-01-18
> **oldfred said:**
> While I still do not suggest running dd, I did post command.
[https://ubuntuforums.org/showthread.php?t=2470524&p=14073786#post14073786](https://ubuntuforums.org/showthread.php?t=2470524&p=14073786#post14073786)
And again, you have to be sure command is typed exactly correctly. 
One user did admit putting an extra space after / and deleted entire system.

As mentioned in my reponse to MAFoElffen above, I'm not going to touch that MBR GRUB. I think I didn't want to believe you first time around, thinking [I]"it just doesn't belong there, it might mess something up."

[/I]But in fact you're saying that it's very, very unlikely to mess anything up.

> Or you never should boot in BIOS mode, and with any USB flash drive always chose the UEFI:flash drive option, not any other.

Aha, OK, so the one thing I do need to be careful with, then -- because of this GRUB in MBR -- is making sure to boot flash drives in UEFI mode.  Some flash drives may not automatically do that, I guess depending on how they were formatted?

I've marked this thread as *solved*.

---

### Post by MAFoElffen on 2022-01-19
Yes... Decoded, the first 446 bytes of sector 0 contains grub bootstrap code... 

Yes, if it were booted mistakenly in a Legacy mode, it would look for the core.img file... (which is not there.) Not find it and error out. But if it were booted in Legacy boot mode, and if it were not there (zeroed out), it would also error out, but saying there were no bootable media found. Both would error and not boot, just with different errors. Functionally/basically the same results.

---

