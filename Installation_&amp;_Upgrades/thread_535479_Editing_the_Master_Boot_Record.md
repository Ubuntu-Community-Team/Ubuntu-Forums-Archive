---
title: "Editing the Master Boot Record"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by The Bird Man of Alcatraz on 2007-08-26
Hola,
   A few days ago, I messed up my Master Boot Record by installing Windows 2000 on my Ubuntu 6.06 system.  Does anyone have a Live CD-type program they'd recommend for editing the Master Boot Record?  I need to see and edit the MBR code itself.
   Someone has already recommended Super GRUB to me, which has been helpful but doesn't seem to be able to edit the actual MBR code.  Maybe I just don't know how to use it well enough.
   To the best of my knowledge, the MBR looks something like this  (this has been slightly garbled from copying and pasting)--

> Absolute Sector 0 (Cylinder 0, Head 0, Sector 1)
       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F
0000  33 C0 8E D0 BC 00 7C FB 50 07 50 1F FC BE 1B 7C  3.....|.P.P....|
0010  BF 1B 06 50 57 B9 E5 01 F3 A4 CB BD BE 07 B1 04  ...PW...........
0020  38 6E 00 7C 09 75 13 83 C5 10 E2 F4 CD 18 8B F5  8n.|.u..........
0030  83 C6 10 49 74 19 38 2C 74 F6 A0 B5 07 B4 07 8B  ...It.8,t.......
0040  F0 AC 3C 00 74 FC BB 07 00 B4 0E CD 10 EB F2 88  ..<.t...........
0050  4E 10 E8 46 00 73 2A FE 46 10 80 7E 04 0B 74 0B  N..F.s*.F..~..t.
0060  80 7E 04 0C 74 05 A0 B6 07 75 D2 80 46 02 06 83  .~..t....u..F...
0070  46 08 06 83 56 0A 00 E8 21 00 73 05 A0 B6 07 EB  F...V...!.s.....
0080  BC 81 3E FE 7D 55 AA 74 0B 80 7E 10 00 74 C8 A0  ..>.}U.t..~..t..
0090  B7 07 EB A9 8B FC 1E 57 8B F5 CB BF 05 00 8A 56  .......W.......V
00A0  00 B4 08 CD 13 72 23 8A C1 24 3F 98 8A DE 8A FC  .....r#..$?.....
00B0  43 F7 E3 8B D1 86 D6 B1 06 D2 EE 42 F7 E2 39 56  C..........B..9V
00C0  0A 77 23 72 05 39 46 08 73 1C B8 01 02 BB 00 7C  .w#r.9F.s......|
00D0  8B 4E 02 8B 56 00 CD 13 73 51 4F 74 4E 32 E4 8A  .N..V...sQOtN2..
00E0  56 00 CD 13 EB E4 8A 56 00 60 BB AA 55 B4 41 CD  V......V.`..U.A.
00F0  13 72 36 81 FB 55 AA 75 30 F6 C1 01 74 2B 61 60  .r6..U.u0...t+a`
0100  6A 00 6A 00 FF 76 0A FF 76 08 6A 00 68 00 7C 6A  j.j..v..v.j.h.|j
0110  01 6A 10 B4 42 8B F4 CD 13 61 61 73 0E 4F 74 0B  .j..B....aas.Ot.
0120  32 E4 8A 56 00 CD 13 EB D6 61 F9 C3 49 6E 76 61  2..V.....a..Inva
0130  6C 69 64 20 70 61 72 74 69 74 69 6F 6E 20 74 61  lid partition ta
0140  62 6C 65 00 45 72 72 6F 72 20 6C 6F 61 64 69 6E  ble.Error loadin
0150  67 20 6F 70 65 72 61 74 69 6E 67 20 73 79 73 74  g operating syst
0160  65 6D 00 4D 69 73 73 69 6E 67 20 6F 70 65 72 61  em.Missing opera
0170  74 69 6E 67 20 73 79 73 74 65 6D 00 00 00 00 00  ting system.....
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 2C 44 63                          .....,Dc

Is that correct?

Thanks!

---

### Post by Pumalite on 2007-08-26
Is better to let Lilo or Grug install themselves to the MBR than messing around with numbers. If you want to re-install Grub : [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kellemes on 2007-08-26
For this you need a diskeditor, google will be the answer..
Why would you want to edit the MBR?

---

### Post by The Bird Man of Alcatraz on 2007-08-26
Ok, I've simply reinstalled GRUB, and GRUB looks fine.  I can boot into Ubuntu 6.06, but then I run into what seems to be a common bug:

> /bin/sh: can't access tty; job control turned off

I've been working on this for a few days now, and yesterday I finally got GRUB to load, thanks to you guys' help.  Then, I ran into that bug while loading Ubuntu.  I searched for it in the forums, and it seems to have a lot to do with GRUB pointing to the wrong place, or something along those lines.  So, for the last day, I've been trying to fix GRUB, and now I realize that GRUB seems to be fine.

So what else could this bug be stemming from?  Thanks a million!

---

### Post by Pumalite on 2007-08-26
A problem with many faces and many fixes. Extensively discussed in this forum: check this:

/bin/sh:can't access tty;job control turned off

when I boot, the screen shows



f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); jStarting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.
ust a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by The Bird Man of Alcatraz on 2007-08-26
Thanks for the bug fix, Pumalite, but I'm having a hard time following  your instructions.

Am I supposed to enter "modprobe piix" into the BusyBox console that I get thrown into while booting?  Or do I type in "modprobe piix" in a console under a Live CD?

I entered "modprobe piix" into the BusyBox console, typed "exit", rebooted, and ended up back at BusyBox.

Thanks!

---

### Post by Pumalite on 2007-08-26
I can help you with this:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

