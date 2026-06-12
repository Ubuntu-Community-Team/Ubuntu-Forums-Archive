---
title: "New GRUB menu no longer generated"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2011-07-19
I did a routine update to 11.04 yesterday, and as I have several OSs on this PC, launched startup-manager to set the default OS selection.

And yes, I know how to do this by editing /etc/default/grub, I've just gotten "lazy" and let startup-manager do it.

When I rebooted, first thing I noticed was that the WRONG line is highlighted in the GRUB menu.  It was NOT the line that I selected in startup-manager.

Second thing I noticed is that the latest kernel was not listed in the GRUB menu.  I should have two sets of kernel entries there, I only have one (the old one).

So, I ran "sudo update-grub" again -- and watched closely while it enumerated the things it found -- and wrote them down.  From what I wrote down, the correct OS entry should be highlighted and there should be two sets of 11.04 kernel entries.

I rebooted.

Once again, got the OLD Grub menu!

I did edit /etc/default/grub to set the default selection to what I wanted ...

But, this is the FIRST time since switching over to GRUB 2 that the GRUB menu has NOT updated.

Am I alone in this problem?

---

### Post by Elfy on 2011-07-19
Just a question - as it's the sort of thing I've done in the past. 

Are you sure that the grub you've updated is actually the grub that appears. I gopt confused once with which grub was which when I had severla OS's. 

As an aside the last update I got - though this is on Xubuntu - appeared to change the way it was doing so.

The new kernel is there - the old one is in a sort of sub-menu called "Previous Linux versions"

---

### Post by Blasphemist on 2011-07-19
Your going through something I've been studying lately and haven't completely figured out how to resolve. The last time you installed Grub2, likely when you installed you last distro, it told the mbr which partition to link to for grub. You're on a different distro now and you can update all you want and it won't be seen in your grub menu as it is coming from a different partition.

So this is a problem whenever a kernel changes on a partition other than the one linked to the mbr. I'm working on this some today and will keep you posted as I learn more.

---

### Post by Quackers on 2011-07-19
I've also tried editing the grub that wasn't in control of things :-) It's easily done with more than one of them.

---

### Post by Blasphemist on 2011-07-19
So I'll ask you very experienced guys a few questions about this if you don't mind. I'm trying to get my head fully around this and then I hope to create some documentation that I at least haven't found. I'd think this is happening to a bunch of us Mark so no, it's not only you.

1. When running update-grub how does it get the list of correct kernel options from each partition if they aren't all mounted? If I make it a practice to mount all partitions in all distro's will that help?

2. Why do some (Fedora and openSUSE) just show up as the distro name and not the kernel detail?

3. Why do some(also Fedora and openSUSE) show up more than once? I can't say that I get a new entry every time I run grub-install or every time I install a distro but I have a number of openSUSE's and a couple Fedora15's.

4. What is best practice when installing a distro on whether or not to install and what choices to make for installing the boot loader?

5. Would using a boot partition help with this mess?

---

### Post by Quackers on 2011-07-19
1. I believe the os-prober finds them, but not sure on the details.
2. It may be just a matter of what they are set up to display by default.
3. Aren't the other entries the equivalent of recovery sessions?
4. I decide which system's grub I want to have in control, and keep it. If I don't want the new system's version of grub I either don't allow it to install (if that's possible) or install it to /dev/sdb (when /dev/sda is the boot drive).
5. I don't think so.

---

### Post by MAFoElffen on 2011-07-19
> **Quackers said:**
> 1. I believe the os-prober finds them, but not sure on the details.
2. It may be just a matter of what they are set up to display by default.
3. Aren't the other entries the equivalent of recovery sessions?
4. I decide which system's grub I want to have in control, and keep it. If I don't want the new system's version of grub I either don't allow it to install (if that's possible) or install it to /dev/sdb (when /dev/sda is the boot drive).
5. I don't think so.
@All-
Not really sure what's going on. Yes I noticed something weird started up with Grub 2 nights ago.

One of my dev test boxes blew out it's config and wouldn't bring up a gnome session (dev 11.10 release)... so I fresh installed 11.04 on it again... As this box was having issues with the current liveCD image for that release.  Install went just fine.    Everything works exept update-grub...  I figure it might be a couple of days kind of thing in the repo's.

11.04 Updates went fine until it brought Grub2 to current updates.  Right before those updates, I added my personal 40_custom file with my menuitems for OpenSolaris, OpenIndiana and Solaris 11... and a generic linux text console item.

I had added 40_custom and my theming just before the grub update in question... I noticed I had a typo after that last update, so I edited and reran update-grub... os-prober failed and exited.  I edited manually to get around it.  Not sure why it's not working... but figure it's in that grub2 update.

EDIT- that one says something about /ect/default/grub... even though it's there, named correct, correct header and all the attribs are okay.  That file ran fine and was uneditted before/after the last grub2 involved updates.

@Jim- 
My Ubuntu instance is sda (hd0)... Where it was originally installed.  The only change was "that" Update Manager installed Update, which did involve Grub2.  os_prober doesn't usually find that flavor of Unix distro's so I'm used to that part...  They are on their own separate drives (using chainloader, grub2-to-grub: hd1. hd2, hd3)... Yes, for me everything is working Except for update-grub... an annoyance.

---

### Post by oldfred on 2011-07-20
Like MAFoElffen I have a 40_custom. It turns out I had a typo for a long time (missing end }) and grub2 older versions worked with it and just did not show one old boot stanza that I was not using, so I had not noticed it was missing.

Then with my adding my defective 40_custom to grub 1.99 it updated but copied it to another grub.cfg.newz file. Once I fixed typo then it worked.

---

### Post by drs305 on 2011-07-20
Another thing to check is which version of Grub 2 you are now using. Grub 1.99RC uses a different method of posting the available kernels/OSs. It introduces submenus, and I would be very surprised if StartUp-Manager can handle them.

Here is a link to the new menu structure for Grub 1.99 (you can check the version on the Grub menu or with 'grub-install -v').
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")

---

### Post by MAFoElffen on 2011-07-20
> **oldfred said:**
> Like MAFoElffen I have a 40_custom. It turns out I had a typo for a long time (missing end }) and grub2 older versions worked with it and just did not show one old boot stanza that I was not using, so I had not noticed it was missing.

Then with my adding my defective 40_custom to grub 1.99 it updated but copied it to another grub.cfg.newz file. Once I fixed typo then it worked.
Very well could be.  That test box has an if'y extra keyboard on it...

I had been testing:
```

GRUB_HIDDEN_TIMEOUT=

```As I read in the 1.99 manual to see if I could force the menu to display each time.

Here's the error I get::
```

mafoelffen@maferr03:~$ sudo update-grub
/etc/default/grub: 8: $: not found

```And here's the info on the file:
```

mafoelffen@maferr03:~$ ls -l /etc/default/grub
-rw-r--r-- 1 root root 1262 2011-07-20 11:45 /etc/default/grub

```And I don't see any syntax errors there... But the doctors are saying I'm going blind with the last 4 months of these treatments...
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT=
GRUB_HIDDEN_TIMEOUT_QUIET=FALSE
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```Am I missing something there for update-grub not to find it?

The only 3 files I usually edit is /etc/default/grub, /etc/grub.d/05_debian_theme and 40_custom... But my 40_custom has been essentially the same since Ubuntu 10.04.1

EDIT-- [COLOR=Magenta]::embarrassed::[/COLOR] The error was trying to tell me where to look!!! Found it > /etc/default/grub > Line 8 > "GRUB_HIDDEN_TIMEOUT_QUIET=FALSE" should have been "GRUB_HIDDEN_TIMEOUT_QUIET=false"... It then gen'ed fine.

---

### Post by drs305 on 2011-07-20
> # GRUB_HIDDEN_TIMEOUT=10
[COLOR="DarkRed"]GRUB_HIDDEN_TIMEOUT=[/COLOR]

If you only have one OS the Grub menu will be hidden. You have commented the GRUB_HIDDEN_TIMEOUT=10, which will normally allow the menu to display. However, you have another similar entry directly below that is not commented, and the last one in the file takes precedence. It's possible that even with no value entered on the line it still doesn't 'trigger' the display.

Remove the second entry or comment it and then update grub.

---

### Post by MAFoElffen on 2011-07-20
> **drs305 said:**
> If you only have one OS the Grub menu will be hidden. You have commented the GRUB_HIDDEN_TIMEOUT=10, which will normally allow the menu to display. However, you have another similar entry directly below that is not commented, and the last one in the file takes precedence. It's possible that even with no value entered on the line it still doesn't 'trigger' the display.

Remove the second entry or comment it and then update grub.
"I learn something new everyday..."

I know that the "GRUB_HIDDEN_TIMEOUT=10" is commented out and is not taking affect...

This test box > Grub thinks it has only one OS -->  Ubuntu is main OS. Others are Solaris derivatives, which Grub2's os-prober doesn't find... So they are added via 40_custom.  Even though it is a true multi-boot in function, as far as the display of the Grub2 menu is concerned, grub2 thinks Ubuntu is alone.

Next, I have users that go to my graphics sticky and said they couldn't get to a grub menu via holding down a shift key during boot.  I didn't know if to believe them at first, but  was wrong... Well, this test box is one of those in that respect, so was a good test case for trying to get this working... 

Here's what my tests with that come up-- with values of the GRUB_HIDDEN_TIMEOUT with[FONT=monospace]
[/FONT]GRUB_HIDDEN_TIMEOUT_QUIET=false:

value = 0 --> skips over the menu / doesn't display on this box- even while holding down <Shift> Very frustrating...

value = any positive number, such as 10 --> Timer displays and counts down for the value set.  Screen is black with the timer displaying in the upper left of screen.  Pressing any key while the timer is present brings up the menu.  This works, but still...

value = "" (meaning blank after the equals sign) > Displays the grub menu everytime without any user interaction.  Wahoo!  Success. (Written as [FONT=monospace]"[/FONT]GRUB_HIDDEN_TIMEOUT=   ")

It seems to work great... Try it Dave.

---

### Post by drs305 on 2011-07-20
> **MAFoElffen said:**
> Here's what my tests with that come up-- with values of the GRUB_HIDDEN_TIMEOUT with[FONT=monospace]
[/FONT]GRUB_HIDDEN_TIMEOUT_QUIET=false:

value = 0 --> skips over the menu / doesn't display on this box- even while holding down <Shift> Very frustrating...

value = any positive number, such as 10 --> Timer displays and counts down for the value set.  Screen is black with the timer displaying in the upper left of screen.  Pressing any key while the timer is present brings up the menu.  This works, but still...

value = "" (meaning blank after the equals sign) > Displays the grub menu everytime without any user interaction.  Wahoo!  Success.

It makes sense that "GRUB_HIDDEN_TIMEOUT=" works, since the test looks to see whether there is a value after the equal sign. I guess I misunderstood, as I thought the post indicated that the menu was NOT displaying with "GRUB_HIDDEN_TIMEOUT=". In any event, glad it's working.  :-)

---

### Post by Mark Phelps on 2011-07-20
thanks for the feedback folks.  Been out for while and only have a few minutes to respond.

1. This was not an upgrade to 11.04, it was a clean install to a separate drive.
2. Only the new drive was connected when I installed 11.04, and I let Ubuntu install GRUB to the drive.
3. Confirmed that (1) sudo update-grub DOES generate the correct GRUB stanzas and (2) the GRUB menu displayed does NOT have the correct stanzas.
4. 40_custom is an interesting observation because I have one of those, too.  So, maybe THAT is the problem -- that GRUB fails while processing the current grub.cfg file and falls back to an earlier version that it squirreled away somewhere.

When I have some time, I will try the following:
1) Reading through the current grub.cfg file to see if it has all the proper stanzas.
2) Removing the 40_custom file, rerunning update-grub and seeing if that works now.

---

### Post by drs305 on 2011-07-20
Mark,

If nothing's changed from your first post and you give us the contents of RESULTS.txt I'm sure we'd all be glad to take a look and check for any discrepancies that might exist in the Grub files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Mark Phelps on 2011-07-22
drs305:

Sorry for the late response, but I've been away ...

Anyway, have had a chance to read the grub.cfg -- and it IS correct.  It has the proper number of stanzas and the right default entry.  Also, the GRUB version is 1.99RC1.

Below is the result of running the script:

```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sdd3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdd5 starts 
                       at sector 42620928. But according to the info from 
                       fdisk, sdd5 starts at sector 187865088.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    85,239,807    85,237,760  83 Linux
/dev/sda2          85,240,890    91,795,409     6,554,520  82 Linux swap / Solaris
/dev/sda4          91,795,471   312,576,704   220,781,234   5 Extended
/dev/sda5          91,795,473   160,039,529    68,244,057   b W95 FAT32
/dev/sda6         160,039,593   312,576,704   152,537,112   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1          77,063,929   390,716,864   313,652,936   5 Extended
/dev/sdb5          83,971,818   390,716,864   306,745,047   7 NTFS / exFAT / HPFS
/dev/sdb6          77,063,931    83,971,754     6,907,824  82 Linux swap / Solaris
/dev/sdb2    *          2,048    77,063,804    77,061,757  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   113,870,847   113,868,800   7 NTFS / exFAT / HPFS
/dev/sdd2         113,946,624   187,863,039    73,916,416   7 NTFS / exFAT / HPFS
/dev/sdd3         187,863,040 1,953,521,663 1,765,658,624   f W95 Extended (LBA)
/dev/sdd5         187,865,088 1,953,521,663 1,765,656,576   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        fc0c25fb-3425-469c-be8a-0d4fc70a1167   ext4       Maverick
/dev/sda2        6c3e428c-9d4d-4c75-b5ee-c3a7b87b05c4   swap       
/dev/sda5        49F3-634D                              vfat       UBUNTUSHARE
/dev/sda6        79F3E0CB3786FEAC                       ntfs       WSHARE
/dev/sdb2        2f2082d3-89a0-480b-a549-abc883b92af7   ext4       Natty
/dev/sdb5        3779E779001BD853                       ntfs       Ushare
/dev/sdb6        978ad0ad-bb35-4a30-ab93-442ba106daf9   swap       
/dev/sdc1        0C1E303E1E3022DE                       ntfs       WShare2
/dev/sdd1        C4C0262DC0262660                       ntfs       Win7-32
/dev/sdd2        C8F45C12F45C04DA                       ntfs       Vista
/dev/sdd5        01C79ED500AE6400                       ntfs       DataVol-32

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/UBUNTUSHARE       vfat       (rw,utf8,umask=000)
/dev/sda6        /media/Wshare            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /media/Ushare            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="10"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_ugos_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
insmod png
if background_image /boot/grub/linuxugos.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_ugos_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro  splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro single  splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro  splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro single  splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 2f2082d3-89a0-480b-a549-abc883b92af7
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro splash vga=791 acpi_enforce_resources=lax quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 2f2082d3-89a0-480b-a549-abc883b92af7
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro single splash vga=791
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "ISO Clonezilla live" {
set isofile1="/boot/isos/clonezilla-live.iso"
loopback loop $isofile1
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile1
initrd (loop)/live/initrd.img
}

menuentry "ISO Gparted live" {
set isofile2="/boot/isos/gparted-live.iso"
loopback loop $isofile2
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile2
initrd (loop)/live/initrd.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=6c3e428c-9d4d-4c75-b5ee-c3a7b87b05c4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdf5 UBUNTUSHARE
UUID=49F3-634D		/media/UBUNTUSHARE 	vfat	utf8,umask=000 0 0
# /dev/sdg5 Ushare
UUID=3779E779001BD853	/media/Ushare		ntfs-3g locale=en_US.utf8
# /dev/sdf6 WSHARE
UUID=79F3E0CB3786FEAC	/media/Wshare		ntfs-3g locale=en_US.utf8
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.134307861 = 2.291695616    boot/grub/core.img                             1
  12.974113464 = 13.930848256   boot/grub/grub.cfg                             1
  39.286666870 = 42.183737344   boot/initrd.img-2.6.35-27-generic              2
   1.175071716 = 1.261723648    boot/initrd.img-2.6.35-28-generic              1
   2.258979797 = 2.425561088    boot/vmlinuz-2.6.35-27-generic                 1
   2.268692017 = 2.435989504    boot/vmlinuz-2.6.35-28-generic                 1
   1.175071716 = 1.261723648    initrd.img                                     1
  39.286666870 = 42.183737344   initrd.img.old                                 2
   2.268692017 = 2.435989504    vmlinuz                                        1
   2.258979797 = 2.425561088    vmlinuz.old                                    1

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="Windows 7 (loader) (on /dev/sdd1)"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
insmod png
if background_image /boot/grub/linuxugos.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_ugos_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
insmod png
if background_image /boot/grub/linuxugos.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_ugos_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro  splash vga=791  acpi_enforce_resources=lax quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro single  splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro  splash vga=791  acpi_enforce_resources=lax quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=2f2082d3-89a0-480b-a549-abc883b92af7 ro single  splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 2f2082d3-89a0-480b-a549-abc883b92af7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro splash vga=791 quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro single splash vga=791
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro splash vga=791 quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fc0c25fb-3425-469c-be8a-0d4fc70a1167
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=fc0c25fb-3425-469c-be8a-0d4fc70a1167 ro single splash vga=791
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdd,msdos1)'
	search --no-floppy --fs-uuid --set=root C4C0262DC0262660
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "ISO Clonezilla live" {
set isofile1="/boot/isos/clonezilla-live.iso"
loopback loop $isofile1
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile1
initrd (loop)/live/initrd.img
}

menuentry "ISO Gparted live" {
set isofile2="/boot/isos/gparted-live.iso"
loopback loop $isofile2
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile2
initrd (loop)/live/initrd.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=2f2082d3-89a0-480b-a549-abc883b92af7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=978ad0ad-bb35-4a30-ab93-442ba106daf9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdf5 UBUNTUSHARE
UUID=49F3-634D		/media/UBUNTUSHARE 	vfat	utf8,umask=000 0 0
# /dev/sdg5 Ushare
UUID=3779E779001BD853	/media/Ushare		ntfs-3g locale=en_US.utf8
# /dev/sdf6 WSHARE
UUID=79F3E0CB3786FEAC	/media/Wshare		ntfs-3g locale=en_US.utf8
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.135009766 = 13.029867520   boot/grub/core.img                             1
  34.235542297 = 36.760133632   boot/grub/grub.cfg                             1
   3.755123138 = 4.032032768    boot/initrd.img-2.6.38-10-generic-pae          2
   2.309772491 = 2.480099328    boot/initrd.img-2.6.38-8-generic-pae           1
   3.438907623 = 3.692498944    boot/vmlinuz-2.6.38-10-generic-pae             2
   0.692810059 = 0.743899136    boot/vmlinuz-2.6.38-8-generic-pae              1
   3.755123138 = 4.032032768    initrd.img                                     2
   2.309772491 = 2.480099328    initrd.img.old                                 1
   3.438907623 = 3.692498944    vmlinuz                                        2
   0.692810059 = 0.743899136    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  46 13 2f 03 13 1c 15 a1  af 0d 08 00 14 14 00 02  |F./.............|
00000010  01 02 65 5f 5d d1 e2 27  b2 7f 13 2f 03 0f bb 11  |..e_]..'.../....|
00000020  a1 af 0c 08 00 14 00 00  02 01 02 66 63 c7 79 13  |...........fc.y.|
00000030  2f 03 12 e5 15 a1 af 0b  08 00 14 14 00 02 01 02  |/...............|
00000040  49 85 53 58 da 26 d9 c4  13 2f 03 13 12 08 df 00  |I.SX.&.../......|
00000050  79 08 00 14 14 00 02 01  02 ca 61 5d 0f 50 a0 be  |y.........a].P..|
00000060  f1 13 2f 03 13 24 08 df  00 47 08 00 14 00 00 02  |../..$...G......|
00000070  01 02 8e cc 84 63 13 2f  03 13 1b 08 df 00 19 08  |.....c./........|
00000080  00 14 14 00 02 01 02 df  a3 24 87 7f bd bd fb 13  |.........$......|
00000090  2f 03 13 11 08 df 00 19  08 00 14 14 00 02 01 02  |/...............|
000000a0  d5 dc 84 0d 54 44 1e 3b  13 2f 03 13 24 08 df 00  |....TD.;./..$...|
000000b0  19 08 00 14 14 00 02 01  02 c0 50 4e 52 6f 9d 1c  |..........PNRo..|
000000c0  11 13 2f 03 13 26 15 a1  af 05 08 00 14 14 00 02  |../..&..........|
000000d0  01 02 b7 e0 dc 9a f6 a7  f0 29 13 2f 03 12 71 09  |.........)./..q.|
000000e0  11 00 19 08 00 14 14 00  02 01 02 9b 48 a7 c2 42  |............H..B|
000000f0  d8 58 d7 13 2f 03 13 19  15 a1 af 03 08 00 14 14  |.X../...........|
00000100  00 02 01 02 30 03 ee a6  11 b7 50 a3 13 2f 03 12  |....0.....P../..|
00000110  75 09 9f 00 19 08 00 14  14 00 02 01 02 0d 42 ad  |u.............B.|
00000120  10 66 29 25 c8 13 2f 03  13 1b 15 a1 af 01 08 00  |.f)%../.........|
00000130  14 14 00 02 01 02 0d 42  ad 10 b4 8d 6c ab 13 2f  |.......B....l../|
00000140  03 13 05 15 a1 af 00 08  00 14 14 00 02 01 02 0d  |................|
00000150  42 ad 10 9d 8a ac 0f 13  2f 03 13 02 15 a1 ae 7f  |B......./.......|
00000160  08 00 14 14 00 02 01 02  0d 42 ad 10 e9 7e 6f 14  |.........B...~o.|
00000170  13 2f 03 13 05 11 a1 ae  7e 08 00 14 00 00 02 01  |./......~.......|
00000180  02 26 42 bc 2f 13 2f 03  13 04 11 a1 ae 7d 08 00  |.&B././......}..|
00000190  14 00 00 02 01 02 bb 9d  8c 9b 13 2f 03 12 61 0a  |.........../..a.|
000001a0  29 00 75 08 00 14 14 00  02 01 02 2a 12 e2 78 5c  |).u........*..x\|
000001b0  d6 62 5b 13 2f 03 13 24  09 e6 00 19 08 00 00 fe  |.b[./..$........|
000001c0  ff ff 0b fe ff ff 02 00  00 00 59 52 11 04 00 fe  |..........YR....|
000001d0  ff ff 05 fe ff ff 5b 52  11 04 57 88 17 09 00 00  |......[R..W.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  0b b9 9d 4d d8 89 03 46  36 2b 28 32 2a aa 37 0f  |...M...F6+(2*.7.|
00000010  7a 4a ad 33 4f 1c 26 6e  32 48 cd da 50 13 93 5f  |zJ.3O.&n2H..P.._|
00000020  5a 38 a2 f0 4e b9 bf eb  54 fa 8b fa 22 e8 28 8f  |Z8..N...T...".(.|
00000030  de c3 e9 39 7f 7f 7c 79  d5 1c e2 e1 bc 0a 3d 7d  |...9..|y......=}|
00000040  ea 6d e4 9a e3 73 a5 48  44 c5 5b ef 49 a5 01 06  |.m...s.HD.[.I...|
00000050  e9 fd fd ce f4 aa 4f e8  d3 a5 3d 4a 0c 50 41 c7  |......O...=J.PA.|
00000060  18 75 ce 5e 22 34 99 8b  97 b1 79 03 e3 ce 1e 83  |.u.^"4....y.....|
00000070  b8 bf 11 25 18 9d 65 9d  c6 3d 4d 4b 61 83 8b bd  |...%..e..=MKa...|
00000080  f0 98 4f 6a 6d 1a 45 65  67 8d 1c 07 23 3a 12 3d  |..Ojm.Eeg...#:.=|
00000090  4a 34 9d bd fd fe be 5d  66 11 07 3a 61 ad 06 25  |J4.....]f..:a..%|
000000a0  b6 79 e8 3d 4a c5 a7 05  62 2e 5d b0 f8 43 51 e3  |.y.=J...b.]..CQ.|
000000b0  7f 8c bc e5 f9 8a 56 5e  5e 23 27 e8 a1 99 0a a0  |......V^^#'.....|
000000c0  b8 30 b6 c7 e5 ec c2 48  2e 69 28 54 47 a4 f9 c1  |.0.....H.i(TG...|
000000d0  d8 ea 8e cb 81 29 d9 2a  29 2e 52 d4 39 71 26 1d  |.....).*).R.9q&.|
000000e0  a2 8e a8 69 59 c9 0c d8  64 45 d0 b8 9e 5f 8f 21  |...iY...dE..._.!|
000000f0  50 54 61 51 db e5 d9 9a  f0 20 a1 4d 5c 1d 5d 43  |PTaQ..... .M\.]C|
00000100  fa b4 ef 12 b3 58 ce 5a  6e de aa d1 07 73 38 2d  |.....X.Zn....s8-|
00000110  e5 28 07 ce c0 c4 9b 09  e2 0c 06 ea 82 0b c1 33  |.(.............3|
00000120  2d 10 f0 3d 4d 6f dd c7  17 9a 1e 61 67 4b ae 06  |-..=Mo.....agK..|
00000130  21 b3 f6 b7 cd e3 fa 91  2d 0b 70 6a 42 4c e4 0a  |!.......-.pjBL..|
00000140  e6 23 f0 8b 78 6e ec 33  27 36 c8 45 b1 30 a5 08  |.#..xn.3'6.E.0..|
00000150  8f 7a 06 11 4e d2 29 7d  dd 38 cb 6d 01 c6 69 f8  |.z..N.)}.8.m..i.|
00000160  0c e6 1b d1 f7 46 3d 4d  f9 f8 1e a1 a9 29 ea 4f  |.....F=M.....).O|
00000170  f6 c4 06 3d 4a e3 e2 87  03 c2 b0 74 21 a9 b5 2b  |...=J......t!..+|
00000180  f2 bb 3d 40 3f 7d e2 07  d6 15 f7 3d 40 95 fc 75  |..=@?}.....=@..u|
00000190  b1 f8 67 f0 65 9d b9 68  b5 9d c6 b0 f7 f8 64 4b  |..g.e..h......dK|
000001a0  7e 0b e5 57 68 a3 92 06  1a e1 c5 66 d8 9d b1 75  |~..Wh......f...u|
000001b0  7b fb 52 b4 7d 99 9c a6  1e 27 28 78 62 b2 00 fe  |{.R.}....'(xb...|
000001c0  ff ff 07 fe ff ff f1 67  69 00 d7 8e 48 12 00 fe  |.......gi...H...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 b1 67 69 00 00 00  |...........gi...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by oldfred on 2011-07-22
Which drive are you booting from in BIOS sda 160GB or sdb 200GB?

---

### Post by Blasphemist on 2011-07-22
I'm still investigating but I have learned this. The distro installed last that wrote grub to the mbr is important. If you run update-grub from any other distro is booted, you will not see the changes you expect. This is particularly important when kernel updates have occurred. In my case, natty recently had a kernel update. That kernel change was never reflected in the boot menu even when running update-grub from that distro. So I kept booting to the older kernel and having update trouble until I re-installed grub from that distro. Then not only did I successfully run update-grub but also update manager successfully ran an update-grub when it ran. Now the new kernel shows up in the boot menu as it should and I can boot the right kernel.

Needless to say, this means that at least until I learn something else new that I must pay close attention when a distro does an update that includes a kernel update. When that happens I will be installing grub from that distro, running update-grub, running update manager (or the equivalent in another distro) and letting it update grub, and then rebooting.

If this makes sense or doesn't seem right to any of you, by all means pass on what you know.

---

### Post by Quackers on 2011-07-22
Or you can just remember which installation has control of grub. That one will update kernel info for all installations. I would suggest that the later version of grub is the better one to have in control.

---

### Post by oldfred on 2011-07-22
It is one of the disadvantages of the grub2 update process. You have to run the update in the non-controlling grub to refresh the menu entry and then boot into the controlling one and run the update as it reads the menu from the other one. 

One work around is just to boot the partition, not the kernel. I first saw this from Ranch hand, you have to add it to 40_custom:

Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by Blasphemist on 2011-07-22
I'm nearly sure that I had run an update-grub from the "controlling" distro Quakers and that it hadn't found the new kernel on a different partition. I will soon enough be able to see for sure as one of my distros is 11.10 and I'm sure it will have more kernel updates. I tried having it be in control since it has the most recent kernel and would have the most recent grub if any of my distros would have a new version. It is the only development distro I run.

If any of you know exactly how osprober runs for sure it would help me understand this better.

---

### Post by Blasphemist on 2011-07-22
> **oldfred said:**
> It is one of the disadvantages of the grub2 update process. You have to run the update in the non-controlling grub to refresh the menu entry and then boot into the controlling one and run the update as it reads the menu from the other one. 

One work around is just to boot the partition, not the kernel. I first saw this from Ranch hand, you have to add it to 40_custom:

Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
Thanks oldfred! I didn't see this before my last post. I'll try to create a 40_custom today that covers all of my distros. If I understand this right, does it not look at grub on the partition but rather the kernels themselves? Or more specifically the initrd.img which is linked to the kernel? In this case, does running update-grub matter for any partition?

---

### Post by oldfred on 2011-07-22
As I understand it whenever a new kernel is install the link in root is updated. There also is the old link if you want to use it to boot the previous kernel. This works for Debian based, not sure that all distributions put a link into root.

---

### Post by Blasphemist on 2011-07-22
> **Blasphemist said:**
> I'm nearly sure that I had run an update-grub from the "controlling" distro Quakers and that it hadn't found the new kernel on a different partition. I will soon enough be able to see for sure as one of my distros is 11.10 and I'm sure it will have more kernel updates. I tried having it be in control since it has the most recent kernel and would have the most recent grub if any of my distros would have a new version. It is the only development distro I run.

If any of you know exactly how osprober runs for sure it would help me understand this better.

Well, this didn't take long to have a kernel update. I processed the update to the 3.0.0-6 kernel today using update manager in oneiric today. And yes the update manager did work today. I watched the details as it happened. It did run update-grub and it did find the new kernel. I did the recommended reboot after the update and of course my grub didn't show the new kernel as the controlling distro hadn't had update-grub run. I booted to that controlling distro and ran update-grub. That update-grub didn't display that it had found a new kernel on the oneiric partition but rather showed oneiric 11.10 (development branch). I rebooted and grub did show the new kernel as well as the previous kernel versions. Needless to say the grub menu gets longer each time this happens, with each distro and I have 7 plus windows.

So the next effort for me is the 40_custom creation described by oldfred from ranch hand. If anyone reading this has a good example of one please post it. I've never created one of these and I'd like having one to compare mine to.

---

### Post by Blasphemist on 2011-07-22
> **oldfred said:**
> As I understand it whenever a new kernel is install the link in root is updated. There also is the old link if you want to use it to boot the previous kernel. This works for Debian based, not sure that all distributions put a link into root.

Maybe that is why or related to the fact that each update of kernel for Fedora 15 openSUSE 11.4 just show another entry with just the distro name and no kernel identifier. I just have to be sure to always pick the top one. For the debian based distros at least should I expect to just see an entry for the text I put between quotes in your example? Or will I still see entries for each kernel version unless I implement sub menus for all distros?

---

### Post by oldfred on 2011-07-22
You just have to paste into 40_custom the entry I posted above and change to your partition number. I have turned off os-prober so my 40_custom is a bit more complex.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry " " {
set root= 
}

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    insmod part_msdos
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Ubuntu, Maverick Meerkat (on /dev/sdc7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos7)'
    search --no-floppy --fs-uuid --set 5e25282c-9c54-45df-9e79-514011e98648
    linux /vmlinuz root=/dev/sdc7 ro quiet splash
    initrd /initrd.img

menuentry "Karmic Koala on sdc5 (on /dev/sdc5)" {
    insmod ext2
    insmod part_msdos
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 117412d5-2dbe-4011-8aec-ae310d1ee6c7
    linux /vmlinuz root=/dev/sdc5 ro quiet splash
    initrd /initrd.img
}


menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}

menuentry "Chainboot hd2" {
set root=(hd2)
chainloader +1
}


menuentry " " {
set root= 
}
menuentry "Chainboot hd1" {
set root=(hd1)
chainloader +1
}

```If you have multiple drives, your boot drive in BIOS will always be hd0, which can add to confusion on booting. I boot sdb or sdc and sometimes have to edit menu entries if I do not adjust 40_custom for each drive. Even worse with USB drives as sometimes the drive sdd is sdf or sdg but is still hd0 when directly booted.

---

### Post by MAFoElffen on 2011-07-22
> **oldfred said:**
> You just have to paste into 40_custom the entry I posted above and change to your partition number. I have turned off os-prober so my 40_custom is a bit more complex.

If you have multiple drives, your boot drive in BIOS will always be hd0, which can add to confusion on booting. I boot sdb or sdc and sometimes have to edit menu entries if I do not adjust 40_custom for each drive. Even worse with USB drives as sometimes the drive sdd is sdf or sdg but is still hd0 when directly booted.
I really like some of those entries!!!  I have mine real similar... My main box- I have a separate boot drive, I keep my main OS'es as 2 per drive (3 drives).  Then I have 4 travel bays (hot swapable) that I have 12 trays for... 2 drive bays I mark for Grub Legacy booted sys'es and 2 bays as Grub2 booted sys'es.

The Grub Legacy bay sys'es are booted just like your chainloader entries in my 40_custom.  All that does is start that drive's Legacy Menu.  The Grub2 bay sys'es are booted just like yours from Ranch hand... 

I get 10GB drives for free.  They come in real handy for testing Dev builds.  They are used/older drives.  As test/dev builds... If they fail, there wasn't anything critical on them anyways.  I can take these same trays and use them on other test boxes here with those same bays.. As long as I allow for the graphics and don't get too specific with it's graphics config's.

Making things work via being less specific and more generic... Has gotten to be a recent interest of mine.  I'm thinking that "that" includes doing that with config's for pendrives and LiveCD's.

---

### Post by Mark Phelps on 2011-07-22
> **oldfred said:**
> Which drive are you booting from in BIOS sda 160GB or sdb 200GB?

The sdb-200GB

Also, looking more closely at the grub.cfg file, I noticed that there IS a new submenu for older Ubuntu versions -- so, maybe, the GRUB menu is OK after all.  I just wasn't looking closely enough.

---

### Post by Blasphemist on 2011-07-22
Mark, since I kind of hijacked this thread as it turns out, are you good?

oldfred, I used the menuentry section you originally pasted in and added to my 40_custom file. I added entries for all my distros, nothing yet for windows. This is in order what I have now and it does seem to work though I haven't tried all distros yet.

1. Normal entries for the current kernel of my main natty partition. 
2. The previous version sub-menu for that same distro.
3. Mem test lines for that same distro.
4. My custom partition specific entries in the order listed in 40_custom.
5. All normal entries for each partition as found by os prober I believe.

I like this for now. I think I just want to leave it like this for a while and go through some kernel updates to see how that affects things, if it does. I see from the Grub2 documentation how to clean this up by changing some files in /etc/grub.d to not executable. When you next install grub2 do those files end up executable again? 

I see the differences in the sample you originally pasted and what is in the grub2 documentation and the sample 40_custom file you posted. I don't expect any partition changes since I already organized my drive so I don't expect to implement using UUID. I'll remember to change 40_custom on the controlling partition whenever I change the distro on a given partition. I'll look at your example and also my /boot/grub/grub.cfg file for how to move windows and keep it in there if I turnoff os prober.

Thank you so much! I very much like this approach of booting to the partition!

---

### Post by oldfred on 2011-07-22
I have not paid close attention on grub updates, but do not remember any issues.

I normally do this:
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

And reset to false if I need it to rerun, but cannot remember doing that.:)

But I have been one to chainboot with grub legacy and am used to manually editing grub's files.

---

