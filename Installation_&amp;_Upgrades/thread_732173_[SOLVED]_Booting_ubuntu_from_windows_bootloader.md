---
title: "[SOLVED] Booting ubuntu from windows bootloader"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by toMeloos on 2008-03-22
Hi,

I'm running Ubuntu from an external USB hard disk on my company's laptop. I had one that had booting from USB enabled. Yesterday they've issued me a new laptop and it does not have booting from USB enabled. I cannot enter the BIOS because it is password protected and because this is one of those small tablet laptops it does not have a floppy or a cd-rom drive.

So the problem is I can't boot Ubuntu on this laptop (yet).

I figured the way to solve it was to use the Windows bootloader to start GRUB. I've looked at several instructions (including [this one]("http://computertakure.blogspot.com/2008/01/ubuntu-start-with-windows-xp-bootloader.html"), [thinkwiki]("http://www.thinkwiki.org/wiki/How_to_setup_boot_loaders"), [bootpart]("http://www.winimage.com/bootpart.htm") and [this thread]("http://ubuntuforums.org/showthread.php?t=56723")) but can't get it to work. I've followed the instructions and when I select linux from the windows boot menu all I get is a blank screen with the word "GRUB " and a blanking cursor _ behind it.

The external drive was always booting just fine so I don't understand why I don't get the GRUB boot menu as usual. Grub is installed on the MBR of the external disk. Besides that it has the following partition layout:
1: NTFS
2: EXT3 /boot
3: EXT3 /
4: extended
5: SWAP
6: EXT3 /home
On the external disk GRUB is configured to find the GRUB and kernel files on (hd0,1) or /dev/sda2.

The big question is: what can I do to get this to work?!?

---

### Post by Kiri on 2008-03-22
can you post your boot.ini here?

---

### Post by dstew on 2008-03-22
> Yesterday they've issued me a new laptopThis might be your problem. The grub boot loader in the MBR of your external drive was configured in a different computer. The external drive may have been enumerated by the BIOS in the old machine in a different way than in the new machine. The grub boot loader has a block address of the stage1.5 or stage2 portion of grub embedded into it when it was installed originally. When you copied the boot loader, and put it in the new machine, it still has the block address from the old machine, and it probably cannot find its stage1.5 or stage2 now. If you look at the instructions, usually they are using Windows to boot Linux that was originally installed on the same machine.

---

### Post by anantshri on 2008-03-22
simple answer to your porblem is that GRUB prompt means that grub is not available in partition as well as MBR so all you have to do is to get a bootable disk and grub-install /dev/<partition of linux> 


and after that the thing to do is to add an entry in boot.ini.


but for this also you can check a utility named "bootpart"

that easily do all the stuff for boot loader entries.

---

### Post by theoptimist on 2008-03-22
I'm having a similar issue and I wonder if it might be related.

Here's where I'm at:

Installed Ubuntu 7.10 from alternate install cd
For grub step, installed it to /dev/sdb1 (197 mb bootable partition mounted as /boot)
Copied 512kb sector from sdb1 to windows to use in boot.ini
(dd if=/dev/sdb1 of=ubuntu.bin bs=512 count=1)
When booting, get GRUB _ and that's it.

Copied /boot/grub folder to a floppy and installed grub on the floppy (root (fd0), setup (fd0))
Can boot to floppy, menu shows up and all is good booting to Ubuntu.
Copied 512kb sector from fd0 and tried to use that in boot.ini to boot Ubuntu.
(dd if=/dev/fd0 of=ubuntu.bin bs=512 count=1)
Got to GRUB _ again.

Installed GRUB on /dev/sdb using root (hd1,0), setup (hd1).
Copied 512kb sector from /dev/sdb and tried to use that in boot.ini.
Got to GRUB GRUB GRUB GRUB Hard disk error.


So, here are my questions.

1.When booting from the floppy, I see it say GRUB Loading stage2...........  So, what might be preventing my other attempts from reaching the Loading stage 2...... part?

2.Why would the last attempt list GRUB multiple times instead of either stopping after 1 or getting to the stage 2 load?

Not trying to hijack the thread, I was about to post this when I saw your post and thought it might be related and/or helpful.

---

### Post by logos34 on 2008-03-22
> **theoptimist said:**
> I'm having a similar issue and I wonder if it might be related.

Here's where I'm at:

Installed Ubuntu 7.10 from alternate install cd
For grub step, installed it to /dev/sdb1 (197 mb bootable partition mounted as /boot)
Copied 512kb sector from sdb1 to windows to use in boot.ini
(dd if=/dev/sdb1 of=ubuntu.bin bs=512 count=1)
When booting, get GRUB _ and that's it.

Copied /boot/grub folder to a floppy and installed grub on the floppy (root (fd0), setup (fd0))
Can boot to floppy, menu shows up and all is good booting to Ubuntu.
Copied 512kb sector from fd0 and tried to use that in boot.ini to boot Ubuntu.
(dd if=/dev/fd0 of=ubuntu.bin bs=512 count=1)
Got to GRUB _ again.

Installed GRUB on /dev/sdb using root (hd1,0), setup (hd1).
Copied 512kb sectorS  from /dev/sdb and tried to use that in boot.ini.
Got to GRUB GRUB GRUB GRUB Hard disk error.


So, here are my questions.

1.When booting from the floppy, I see it say GRUB Loading stage2...........  So, what might be preventing my other attempts from reaching the Loading stage 2...... part?

2.Why would the last attempt list GRUB multiple times instead of either stopping after 1 or getting to the stage 2 load?

Not trying to hijack the thread, I was about to post this when I saw your post and thought it might be related and/or helpful.

To install grub to your (separate) boot partition you should have done:

**sudo grub-install --root-directory=/boot /dev/sdb1**

or

[B]sudo grub
root (hd1,0)
setup (hd1,0)[/B] (-->writes grub to the bootsector of the /boot partition, not the MBR as in 'hd1' or 'hd0')
**quit**

Your entry in boot.ini should be:

**c:\ubuntu.bin**="ubuntu"

Maybe there's some problem with the path, dunno.  You have a separate /boot...normally the path to 'grub' folder with menu.lst is /boot/grub/menu.lst, but in this case it's /grub/menu.lst.  But I'm not really sure why it freezes at grub prompt on hard disk

Add:
> Copied 512kb sector from sdb1 to windows to use in boot.ini
(dd if=/dev/sdb1 of=ubuntu.bin bs=512 count=1)...

Youd did copy 'ubuntu.bin' to the c: windows drive, right?  Or is it still sitting in home dir?  Just thought I'd ask

---

### Post by dstew on 2008-03-22
> all you have to do is to get a bootable disk and grub-install /dev/<partition of linux>The problem the original poster has is that he does not have an external bootable disk option. He can plug in a non-bootable USB drive, that's it. He is also locked out of his BIOS. To me, this problem seems very difficult to solve. I can't figure out a way to do it yet, but I am thinking about it.

---

### Post by toMeloos on 2008-03-23
The problem is solved, kind of:

USB boot actually is on. I didn't notice it because:
[LIST=1]
[*]The USB drive is too slow starting up at power-on to be recognized by the BIOS
[*]The USB drive is placed behind the internal drive in the boot sequence
[/LIST]

So now I seem to have to boot into Windows, select restart at the login screen and then press F12 during boot to get the boot sequence menu to be able to select the USB drive. It seems that the Windows bootloader completely depends on the BIOS disk information as well, so I can't use it to start linux because it dan't chainload to a drive that is not recognized...

Turning off quick boot on this ThinkPad might solve the first problem, but would require access to the BIOS. So does the solution to the second problem...:(

---

