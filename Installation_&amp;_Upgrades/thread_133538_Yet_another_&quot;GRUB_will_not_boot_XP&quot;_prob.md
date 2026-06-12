---
title: "Yet another &quot;GRUB will not boot XP&quot; problem..."
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by sesty on 2006-02-20
well, i installed ubuntu on my laptop (one 80gig harddrive repartitioned during install)  and ubuntu works well (although really really quiet sound--any ideas on this as well?) but the main problem isi that i cannot boot my winxp install anymore. 

basically when i select windows xp in GRUB it just hangs after the root (hd0,0)
etc etc... (also have tried rootnoverify AND boot at the end) 

looking around the forums, i cannot seem to find a solution for this. 

i tried the "ultimate boot cd" but that didn't work. 
the best i've got is a "disk read error press alt+ctrl+delete to reboot" and that's not quite the "best" i was looking for.

i can still mount the windows partition (NTFS) in ubuntu and see the files...

is there a boot disk i can make that will just "work" or what do i need to do?
is the MBR totally naffed? how can i fix it? 

i don't have a winxp cd anymore as i've moved house and it must've got mixed up with some old demo disks that i threw out cuz it ain't here anymore...

really really cannot afford to format this windows install as it contains many important documents...


any Ubuntu-GRUB-WinXP-MBR guru out there to help me?

thank you

---

### Post by Coelocanth on 2006-02-20
Here's a bit of advice given by Bartender from another thread:


> "When you install the boot loader on the MBR, it replaces the MS-DOS boot loader, or any other boot loader that may be there, such as the Windows NT loader. (Used in NT/2000/XP) If you have problems w/ your installation or you simply want to restore the original boot loader, you can do one of the following:

-If you have the capability, boot to DOS & run the fdisk command with a special option that rebuilds the MBR:

C:> fdisk /mbr

I think this may prevent you from booting into Ubuntu though, so you should create a boot floppy for Ubuntu beforehan just in case. Or you can do the following if you can borrow an XP install CD from a friend:

> -For W2K & XP, which don't have an fdisk cmd, boot from the Windows CD (or the Windows boot floppies). When you see the "Welcome to Setup", press R (for repair) and, in W2K, then press C. Select your Windows install from the numbered list, enter admin password at the prompt. Enter the command fixmbr at the command-line prompt, confirm Y. After mbr's restored, type exit to reboot."

Again, that will restore your MBR, but you may need to have a boot floppy for Ubuntu (or the install disc).

---

### Post by sesty on 2006-02-20
is there no way to install a boot loader that can just boot the selected OS??
i remember a few years ago this was possible on an old dual boot system of mine. have the times changed so much that i need to use a bootdisk everytime i want to load an OS?

---

### Post by lha on 2006-02-20
Posting the output of
```
sudo fdisk -l
```
and
```
cat /boot/grub/menu.lst
```
would provide useful info.

---

### Post by Coelocanth on 2006-02-20
[QUOTE=sesty]is there no way to install a boot loader that can just boot the selected OS??
i remember a few years ago this was possible on an old dual boot system of mine. have the times changed so much that i need to use a bootdisk everytime i want to load an OS?[/QUOTE]

Yes, you can. I was just trying to provide a solution so you could immediately get into your Windows install. That way you could back up your Windows files. Then, you could go about mucking with your MBR and setting it to a dual-boot. I figured you might want to be sure you can recover your Win files right away.

Anyhow, follow Iha's advice and post the results of those commands. I'm pretty sure someone can walk you through the process of editing GRUB to perform a dual boot.

---

### Post by sesty on 2006-02-20
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7441    59769801    7  HPFS/NTFS
/dev/hda2   *        7442        9631    17591175   83  Linux
/dev/hda3            9632        9729      787185    5  Extended
/dev/hda5            9632        9729      787153+  82  Linux swap / Solaris

================

and i assume you didn't need the commented bits at the beginning...

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1

===================

have tried rootnoverify and adding boot at the end but still it doesnt work...

---

### Post by sesty on 2006-02-20
ah, thank you Coelocanth.
can i just backup files from linux?

---

### Post by lha on 2006-02-20
[QUOTE=sesty]
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1
[/QUOTE]
It should be
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
**makeactive**
chainloader     +1
```

---

### Post by sesty on 2006-02-20
nope, 
i tried that, then i tried the same thing with rootnoverify and including boot as the final command but it still just hangs after those commands....

---

### Post by sesty on 2006-02-20
well that was savage...

tried the     "fdisk /mbr" from the "Ultimate Boot CD" and the only message that would appear was "A disk read error occurred. Press Ctrl+Alt+Del to restart"

i just reinstalled ubuntu which was a bit grimey. 

any other ideas?...

---

### Post by sesty on 2006-02-20
sorry to get you guys back to this but i'm still having quite some problems....

is it a wise move to use the "chainloader --force" option and direct it to boot.ini (basically is this possible??)
or do i need to make a boot disk for windows (how do i get GRUB to see this bootdisk with no floppy drive on my laptop?...)
or is this just not possible to recover?

Sesty

---

### Post by sesty on 2006-02-21
Well that was a mission...

It seems that the new coaster I was using (Ultimate Boot CD) was not quite the coaster I had thought:


after many reboots and reinstalls of ubuntu (not to mention trawling the forums and google...) and many many screens of death relating to an "unreadable disk" and other various errors, I decided to give this UBCD another shot;


Using the "TestDisk v6.1" app found in "Filesystem Tools" (and enabling NTFS support through the "UBCD loading") I opened the Advanced menu (Filesystem Utils) and performed a "Bootsector Recovery" and "Rebuild BS" on the NTFS partition. It took about 10 minutes to work through and asked for some figures for the part to input-- I just hit enter through the defaults it provided. Then I removed the boot flag (why the hell did I do that? I'm not too sure...) and set all partitions to Primary then rebooted. GRUB messed up saying that there was no bootable volume (or something like...). Went back into UBCD and ran "Smart Bootmanager" which dumped me in GRUB and booted WinXP successfully (after an auto scandisk job).

My laptop now dual boots Ubuntu and XP **AND** I didn't lose any data.

---

### Post by lha on 2006-02-21
That's great! I was getting a bit worried becouse of that "A disk read error occurred. Press Ctrl+Alt+Del to restart" message you got with fdisk /mbr.

---

