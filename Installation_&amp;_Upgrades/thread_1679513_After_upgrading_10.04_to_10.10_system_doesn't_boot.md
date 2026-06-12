---
title: "After upgrading 10.04 to 10.10 system doesn't boot (only blinking cursor)"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by andimeier on 2011-02-01
Two days ago, I tried to upgrade to Maverick (server version) using
[INDENT][FONT="Courier New"]sudo do-release-upgrade[/FONT][/INDENT]

All went well, but on the first reboot after the installation the PC hangs with grub prompt:
[INDENT]error: the symbol grub_xputs not found[/INDENT]

I guess it has something to do with my RAID1 setup:
[INDENT][FONT="Courier New"]sda1/sdb1 ........ RAID1, bootable (system partition, 20 GB)
sdc1 ............. swap partition
sda2/sdb2/sdc2 ... RAID5 (data partition, 3 TB)[/FONT][/INDENT]

I made a bootable (using UNetbootin) USB pen drive with 10.10 desktop on it and booted into this desktop version.
After
[INDENT][FONT="Courier New"]mdadm --assemble --scan[/FONT][/INDENT]
I could successfully access (and mount) my RAID1 and RAID5 drives.

However, the system itself does not boot.


... another thing: after only having mounted /dev/md0 and browsed in the contents, the boot behavior has changed: now the PC does not end up in the grub prompt "the symbol grub_xputs not found", but instead a blank black screen with a blinking cursor left top is shown. Keyboard: no reaction (I tried Enter, Esc, any keys ... no reaction, just a blinking cursor).


Then, I tried:

[LIST]
[*]boot into USB pen drive 10.10 desktop
[*]mdadm --assemble --scan ... result: /dev/md0 is available (the RAID1 of sda1 and sdb1)
[*]mount /dev/md0 /mnt/md0
[*]in /mnt/mnd0/boot/grub/grub.cfg: I replaced the kernel file names by the current ones:
[INDENT]2.6.32-22-server ----> 2.6.35-24-server[/INDENT]
[*]reboot: still only a blinking cursor
[/LIST]

then:
[LIST]
[*]boot into USB pen drive 10.10 desktop
[*][FONT="Courier New"]grub-install --root-directory /mnt/md0 /dev/sda[/FONT]
[*]... a message prints: no problems encountered
[*][FONT="Courier New"]grub-install --root-directory /mnt/md0 /dev/sdb[/FONT]
[*]... a message prints: no problems encountered
[*]reboot: still only a blinking cursor
[/LIST]

So at the moment I end up with a system which does not boot but gives me a blinking cursor.

Any help greatly appreciated!

Thanks,
Andi

---

### Post by andimeier on 2011-02-04
bump.

I really got stuck and I need to have this prob solved.

Just to be sure: is this the appropriate forums for this kind of question?

Andi

---

### Post by kansasnoob on 2011-02-04
I know almost nothing about Raid but it should be helpful if you'd post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2011-02-04
On second thought it appears that your grub issue may be solved, the blinking cursor makes me think it may be graphics card related. Do you know what graphics card you have?

Or can you post the output of:

```
lspci | grep VGA
```

Here again I'm at a bit of a loss because I've never used the server version :confused:

---

### Post by andimeier on 2011-02-08
The output of the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) is attached to this post.

(I omitted all infos about /dev/sdd which is the USB stick for the Live system)

The most relevant infos in the bootinfoscript are IMHO:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

```

Seems perfectly ok to me.

What strikes me a little bit is the gibberish code of [FONT="Courier New"]/md0/boot/grub/grub.cfg[/FONT], although this file is perfectly legible when I access [FONT="Courier New"]/dev/md0[/FONT] from the Live system. Don't know if this is relevant.

[FONT="Courier New"]/dev/md0[/FONT] is the RAID1 device for the mirror sda1/sdb1, containing the system to boot.

So basically everything's looking fine, isn't it?

Am I missing something?

---

### Post by andimeier on 2011-02-08
... and this is the output of 
> lspci | grep VGA

02:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

However, it is not clear to me how the graphic card could interfere because it worked perfectly with Lucid - so I don't expect the graphic card to screw things up after the update to Maverick ...?

---

### Post by andimeier on 2011-02-10
I give up.

I tried almost everything:
[LIST]
[*]booting with Super Grub2 Disk and try to reinstall GRUB2 -> SG2D does not boot, stucks at the word "GRUB"
[*]booting with 10.10 Desktop AMD64 Live and try to grub-setup or grub-update -> no change, just a blinking cursor
[*]skipping through a great many forum threads in several forums, but found nothing I have not already tried for myself
[/LIST]

So, after having 3 weeks of non-working system, I gave up and am just reinstalling 10.04 LTS from scratch.

I will never again try to upgrade to a newer Ubuntu without urgent need to do so. Very disappointing experience indeed!

---

### Post by andimeier on 2011-02-10
**Update:** I reinstalled Ubuntu from scratch (10.04 LTS) without any errors and when the installer asked me to remove the installation media (USB stick) and restart the system, I did so.

**But: the system does not boot, but only display a black screen with a blinking cursor!!**

WTF? This means, I cannot even boot my system which I have just installed from scratch!

I am beginning to think that it is not GRUB2 which causes the problems ...? On some previous posting in this thread kansasnoob suggested that this could be a *graphics card issue*. I do not quite think so because it is a standard on-board graphics adapter in an ASUS board, no specialties here. And - as stated already - the entire system worked like a charm under Lucid until I decided to upgrade to Maverick. And now I cannot even get Lucid to work again.

How can I get further diagnoses?

---

### Post by andimeier on 2011-03-06
SOLVED: it was a BIOS issue (boot order not set correctly) 

I described the solution in the following thread:
[http://ubuntuforums.org/showthread.php?t=1699113](http://ubuntuforums.org/showthread.php?t=1699113)

---

