---
title: "Ubuntu 10.04 / Windows XP dual boot (using Grub2)"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by cyber-monk on 2010-05-12
I recently installed Ubuntu 10.04 on my dual boot system and noticed that my boot options were changed.  I typically have Windows XP as the default OS.  Here are the steps that worked for me to get Windows XP as the default boot using Grub2.

During my initial Window XP install I had partitioned my hard drive into 3 partitions:

```

Partition 1: NTFS format (Windows XP installation) in Linux it is called /dev/sda1
Partition 2: NTFS format (Data for Windows XP) in Linux is is called /dev/sda5
Partition 3: Unformatted (I left this because I knew I wanted to install Linux)

```This is how those partitions looked when booting to the Ubuntu installer (I used the Ubuntu installer to create the [FONT=Fixedsys]/swap[/FONT] and [FONT=Fixedsys]ext3[/FONT] partitions on [FONT=Fixedsys]Partition 3[/FONT] which was unformatted):

[FONT=Courier New]
  /dev/sda1 (Windows-XP OS NTFS)
  /dev/sda5 (Windows-XP Data NTFS)
  /swap
  /dev/sda7 (Ubuntu 10.04 OS ext3)
[/FONT]

After installation I noticed that Ubuntu was being booted by default.  The default boot entries are created from the files in the /etc/grub.d/ directory.  The files need to be executable (have a * at the end of the file name) to be included in the boot menu. To make a file executable type: [FONT=Courier New]sudo chmod +x <filename>[/FONT]

```

$> cd /etc/grub.d/
$> ll
total 56
drwxr-xr-x   2 root root  4096 2010-05-11 21:35 ./
drwxr-xr-x 130 root root 12288 2010-05-11 21:42 ../
-rwxr-xr-x   1 root root  4444 2010-04-13 06:57 00_header*
-rwxr-xr-x   1 root root  1416 2010-04-13 06:38 05_debian_theme*
-rwxr-xr-x   1 root root  4594 2010-04-13 06:57 10_linux*
-rwxr-xr-x   1 root root   918 2010-03-23 02:40 20_memtest86+*
-rwxr-xr-x   1 root root  6605 2010-04-13 06:57 30_os-prober*
-rwxr-xr-x   1 root root   214 2010-04-13 06:57 40_custom*
-rw-r--r--   1 root root   483 2010-04-13 06:57 README

```I didn't want the memory tests to be on the boot menu so I removed the executable bit on [FONT=Courier New]20_memtest86+[/FONT].  You could also disable the [FONT=Courier New]30_os-prober[/FONT] since we are adding Windows XP manually but that is optional.  I left that file active in case I screwed something up.

```

$> sudo chmod -x 20_memtest86+

```I wanted Windows XP to stay at the top of the menu because with each kernel update it will get pushed further down the boot list.  By naming the file with 06_... it gets sorted to the top of the boot list so when we edit [FONT=Courier New]/etc/default/grub[/FONT] we can set the default boot option to be 0 which is the top of the list.

```

$> sudo cp 40_custom 06_windowsxp
$> sudo vim 06_windowsxp

```Then I copied the [FONT=Courier New]menuentry[/FONT] for Windows XP section of [FONT=Courier New]/boot/grub/grub.cfg[/FONT] into [FONT=Courier New]06_windowsxp[/FONT].  The [FONT=Courier New]/etc/grub/grub.cfg[/FONT] file is auto-generated so it does no good to edit it directly.  After editing, my [FONT=Courier New]06_windowsxp[/FONT] file looked like this:

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# copied from /boot/grub/grub.cfg
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 0060ff4060ff3acc
        drivemap -s (hd0) ${root}
        chainloader +1
}

```Now I needed to ensure that we will always default to the 0th entry in the boot list. This is done by setting [FONT=Courier New]GRUB_DEFAULT[/FONT] to [FONT=Courier New]0[/FONT]. Zero is the default value so you probably don't need to edit this.  I also decreased the [FONT=Courier New]GRUB_TIMEOUT[/FONT] to [FONT=Courier New]4[/FONT] and increased the resolution G[FONT=Courier New]RUB_GFXMODE=1024x768[/FONT] (both are optional).
```

$> cd /etc/default/
$> sudo vim grub

```The resulting [FONT=Courier New]grub[/FONT] file should look similar to this (changes in bold):

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=0**
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=4**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**GRUB_GFXMODE=1024x768**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```The final step is to run [FONT=Courier New]update-grub[/FONT] to write our changes into the [FONT=Courier New]/boot/grub/grub.cfg[/FONT] file.
```

$> sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows XP Professional x64 Edition on /dev/sda1
done

```You can check that your changes worked by re-examining the [FONT=Courier New]/boot/grub/grub.cfg[/FONT] file.

May the force be with you...

---

### Post by el3ntel on 2010-05-13
I need your help my windows XP choice completely disappear from grub boot menu

---

### Post by cyber-monk on 2010-05-20
Need a few more details before I can respond to this...

---

### Post by donaldparkerii on 2010-05-22
Hello,
I today I upgraded from 9.10 to 10.04.  After the install Grub gave me an error, from which I just recovered from following the steps outlined here> [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html.]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")

I'm in Ubuntu now, but when I restart I no longer have Windows XP on boot menu.  I opened the terminal and typed sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5ddb5dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       67820   511999582+   7  HPFS/NTFS
/dev/sda3           67821      125144   460455030    7  HPFS/NTFS
/dev/sda4          125145      182401   459916852+   5  Extended
/dev/sda5          125145      180921   448028721   83  Linux
/dev/sda6          180922      182401    11888068+  82  Linux swap / Solaris


How can I get Windows XP back on my boot list?

---

### Post by wilee-nilee on 2010-05-22
> **donaldparkerii said:**
> Hello,
I today I upgraded from 9.10 to 10.04.  After the install Grub gave me an error, from which I just recovered from following the steps outlined here> [http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html.]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")

I'm in Ubuntu now, but when I restart I no longer have Windows XP on boot menu.  I opened the terminal and typed sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5ddb5dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       67820   511999582+   7  HPFS/NTFS
/dev/sda3           67821      125144   460455030    7  HPFS/NTFS
/dev/sda4          125145      182401   459916852+   5  Extended
/dev/sda5          125145      180921   448028721   83  Linux
/dev/sda6          180922      182401    11888068+  82  Linux swap / Solaris


How can I get Windows XP back on my boot list?

Start your own thread and post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cyber-monk on 2010-05-24
[donaldparkerii]("http://ubuntuforums.org/member.php?u=1080807") -- Please list the contents of 
[FONT=Fixedsys]
[/FONT] [FONT=Fixedsys]/etc/grub.d/
[/FONT]  [FONT=Fixedsys]/boot/grub/grub.cfg[/FONT]

---

### Post by cazo on 2010-08-04
I have watched if the Windows 7 IS NOT the first partition, the grub2 doesn't get it anymore; I tryied a lots of tips and nothing. I just re-partitioned again, and putting win7 in the first one and every thing works fine. So, apparently, windows don't like to be the last one! :) Keep in mind only 4 partitons is supported when using some commons buses.

---

### Post by dbeloved on 2011-10-11
> **wilee-nilee said:**
> Start your own thread and post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Compliments.

Anyone in the forum please can I know if thee above was resolved because I have exactly the same issue and I won't want to format my XP partition.

Thanks.

---

### Post by Quackers on 2011-10-11
Welcome to UF :-)
Please start your own thread giving details of what your problem is and how it came about.
This is an old thread and it is marked as solved so many people won't even look at it.

---

### Post by dbeloved on 2011-10-11
Thanks and I will now.

---

### Post by moody_mark on 2012-02-09
Thank you to cyber-monk for this very useful post. Couldnt this be made part of a "how to" and put in as a sticky?

---

