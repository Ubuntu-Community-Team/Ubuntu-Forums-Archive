---
title: "Multi-drive boot issue"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2016-09-12
For a good year-and-a-half or so I've had a good working custom grub (thanks to Cavsfan's help), but something just happened to my grub that I can't figure out. 

Grub is installed on /dev/sdb (mainly because sdb used to be sda).  Usually I boot into /dev/sda (UbuntuMATE 16.04, on an SSD) by setting "GRUB DEFAULT" in /etc/default/grub to 3, but my 16.04 at the moment is not well, so right now I'm booting into my UbuntuMATE 14.04, on  /dev/sdb by setting "GRUB DEFAULT" at 0, which logs me into Trusty.

But somehow today when I booted to Trusty, instead of moving into the Trusty Plymouth and Greeter, I was simply cycled back to the Grub menu. ( I believe I did something while working in Aptitude to cause this.) Right now if I try to boot to Trusty, the grub menu disappears, my grub graphic remains, and it freezes there.  I have to hit the re-set button.

So for the moment, I've set "GRUB DEFAULT" at 5, which logs me into the "advanced options" Trusty, where before I get to the greeter, a whole lot of info flies by, but at least I can get to trusty that way.

Obviousy I'd like to return to what passes for normal for me right now, which is being able to log normally into Trusty.  (I *can* log into Xenial.)

Would anyone know where I might start to track down the problem? (Below:  I can't see anything wrong with any of these files, maybe someone else can.)
```

--> [COLOR=#0000ff]cat /etc/fstab[/COLOR]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#   UbuntuMATE-14.04:
#             <file system>           <mount point>   <type>      <options>     <dump>  <pass>
UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f   /          ext4    errors=remount-ro   0     1    # /dev/sda1
UUID=a88c33fd-88b5-43b2-92f6-457430d206fd   none       swap    sw                  0     0    # /dev/sda2

```

```

--> [COLOR=#0000ff]sudo blkid [/COLOR]
[sudo] password for rj: 
/dev/sdb1: LABEL="UbuntuMATE-16.04" UUID="010dab65-d950-47dc-ac77-a3760775104d" TYPE="ext4" 
/dev/sdb2: UUID="d6a2bc73-6ec4-4465-a9ab-8447e13ac6f9" TYPE="swap" 
/dev/sda1: LABEL="UbuntuMATE-14.04" UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" TYPE="ext4" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 
/dev/sdc1: LABEL="WeirdBeard" UUID="c801726e-7a01-4963-989a-38482e6658cf" TYPE="ext4"

```

```

--> [COLOR=#0000ff]cat /etc/default/grub[/COLOR] 
# If you change this file, run 'sudo update-grub' afterwards to update /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=5
GRUB_TIMEOUT=10
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset=1 #=1 quiet splash video=uvesafb:mode_option=1600x1200-32,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

# The resolution used on graphical terminal:
# Note that you can use only modes which your graphic card supports via VBE.
# You can see them in real GRUB with the command `vbeinfo'.
GRUB_GFXMODE=1600x1200-32

# Uncomment to enable BadRAM filtering, modify to suit your needs.
# This works with Linux (no patch required) and with any kernel that obtains
# the memory-map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux:
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries:
#GRUB_DISABLE_RECOVERY=true

# Uncomment to get a beep at grub start:
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=keep

```

```

--> [COLOR=#0000ff]vim /etc/grub.d/06_custom[/COLOR]
  1 #!/bin/sh
  2 echo 1>&2 "Adding Ubuntu-MATE 14.04 (Trusty Tahr) and Ubuntu-MATE 16.04 (Xenial Xerus)"
  3 exec tail -n +4 $0
  4 # This file provides an easy way to add custom menu entries.  Simply type the
  5 # menu entries you want to add after this comment.  Be careful not to change
  6 # the 'exec tail' line above.
  7 menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
  8     set root=(hd0,1)
  9         linux /vmlinuz root=/dev/sda1 ro quiet splash
 10         initrd /initrd.img
 11 }
 12 menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
 13     set root=(hd0,1)
 14         linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
 15         initrd /initrd.img
 16 }
 17 menuentry "Ubuntu-MATE 16.04 (Xenial Xerus)" {
 18     set root=(hd1,1)
 19         linux /vmlinuz root=/dev/sdb1 ro quiet splash
 20         initrd /initrd.img
 21 }
 22 menuentry "Ubuntu 16.04 (Xenial Xerus) (Recovery Mode)" {
 23     set root=(hd1,1)
 24         linux /vmlinuz root=/dev/sdb1 ro single
 25         initrd /initrd.img
 26 }

```

---

### Post by watchpocket on 2016-09-12
Also, kernel info for 14.04: ```
 --> [COLOR=#0000ff]dpkg -l linux-image-\* && dpkg -l linux-headers-\*[/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                           Version                      Architecture                 Description
+++-==============================================-============================-============================-=================================================================================================
un  linux-image-3.0                                <none>                       <none>                       (no description available)
ii  linux-image-3.13.0-92-generic                  3.13.0-92.139                amd64                        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-95-generic                  3.13.0-95.142                amd64                        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic            3.13.0-92.139                amd64                        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic            3.13.0-95.142                amd64                        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                            3.13.0.95.103                amd64                        Generic Linux kernel image
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                           Version                      Architecture                 Description
+++-==============================================-============================-============================-=================================================================================================
un  linux-headers-3.0                              <none>                       <none>                       (no description available)
ii  linux-headers-3.13.0-92                        3.13.0-92.139                all                          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                3.13.0-92.139                amd64                        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-95                        3.13.0-95.142                all                          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                3.13.0-95.142                amd64                        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                          3.13.0.95.103                amd64                        Generic Linux kernel headers 
```

---

### Post by oldfred on 2016-09-12
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

What you have so far looks ok. Which drive are you booting from? Report should show rest of details.

I tried moving this from Cavfan's thread as posts there should be just on issues or details on his instructions, not a specific boot problem. But forum gave me one of its hiccups and said it did not work. 
Is this thread one you posted, or did forum actually move it, even though it told me it errored out?

---

### Post by watchpocket on 2016-09-12
> **oldfred said:**
> May be best to see details:
Post the link to the Create BootInfo summary report.

Thanks. Check [here]("https://paste.ubuntu.com/23170294/").

> What you have so far looks ok. Which drive are you booting from? 

/dev/sdb/ , I believe.

> Report should show rest of details.  Is this thread one you posted, or did forum actually move it, even though it told me it errored out?

My post was moved from the GRUB tutorial to the Installation & Upgrades forum.

---

### Post by oldfred on 2016-09-12
Do not run Boot-Repair's auto fix. That just installs one grub to all MBRs.
Best to have each drive's system installed to the MBR of that drive, and then set BIOS to boot the one you use the most.

Your grub in sdb, is configured to use the install in sda.

Did you edit grub.cfg at some point. It looks like standard entries are not standard?

I typically turn off os-prober (after backing up last grub.cfg using os-prober) when using my 40_custom entries. That is to avoid too many entries.

You can use Boot-Repair to install each version's grub to that drive's MBR, by using advanced mode and choosing an install and choose drive's MBR to install grub intl.
If you run Boot-Repairs's full reinstall of grub, you may lose 06_custom and 40_custom. Not sure if it creates new folder, if not then only the grub scripts would be overwritten. But I always back up my 40_custom. I copy it into a folder in /home and normally only backup /home.

I would use Boot-Repair to reinstall grub to MBR of each drive. Then boot each drive and run sudo update-grub. Then see if each drive's MBR does work to boot into that install with default settings. Then review 06_custom & 40_custom settings & if they work turn off os_prober.

---

