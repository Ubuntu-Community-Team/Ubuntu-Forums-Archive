---
title: "Lucid install fails"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-02-09
When I try to install today's Lucid Daily image, it always (3 times) fails after the Timezone selection screen. The error is "Ubiquity crashed with NameError in rewrite_xorg-conf()". I have attached my crash report to Bug 514646 on Launchpad, which is identical.

The Live CD works very well, I just cannot install to my disk drive. I have attempted installation both directly from the CD (grub) and from within the Live system. Both fail at the same point.

Any ideas to get around this? I do not think much help is forthcoming from the Launchpad bug.

Tim

---

### Post by ratcheer on 2010-02-10
Ok, a man on my Lucid Testing mailing list suggested I try the alternate CD image, so today I did. It installed successfully, then I rebooted the system to Lucid, successfully.

Then, Lucid automatically searched for and installed the "current" nVidia driver. This was also successful. It instructed me to reboot, again, for the change to take effect. This second reboot failed, as did an another attempt.

Luckily, my Karmic system still boots, just fine.

What to do?'

Tim

---

### Post by Kenny_Strawn on 2010-02-10
I ran into a similar problem on my desktop, where I rebooted twice, and after the second time, I got a "udevd: /dev/null: No such file or directory" error. Thankfully, it still boots after that, but only partially.

---

### Post by ratcheer on 2010-02-11
Never mind. I have tried every way I can think of to get Lucid working, but nothing has helped. I give up!

BTW, it was not installing the nVidia driver that messed it up. I reinstalled Lucid and booted into it immediately after installation. Then, when it attempted to install the nVidia driver, I declined. Then, I tried to reboot Lucid with no changes. It still would not boot.

I have deleted the partitions and gone back to Karmic. Lucid is quite a mess. :-|

Tim

---

### Post by VMC on 2010-02-11
> **ratcheer said:**
> Ok, a man on my Lucid Testing mailing list suggested I try the alternate CD image, so today I did. It installed successfully, then I rebooted the system to Lucid, successfully.

Then, Lucid automatically searched for and installed the "current" nVidia driver. This was also successful. It instructed me to reboot, again, for the change to take effect. This second reboot failed, as did an another attempt.

Luckily, my Karmic system still boots, just fine.

What to do?'

Tim

Tim, What you described is exactly what happens to me. First install works on first boot, then on reboot it freezes. removing plymouth fixed my freeze.

---

### Post by ratcheer on 2010-02-11
I got an email on my testing group's mail list, an hour or so ago. He said he thinks they have resolved the problem with plymouth in the latest kernel, 2.6.32.13, which was put on the server late Wednesday. So, I think I will update my iso and try again, tomorrow.

If that still fails, I will try removing plymouth.

Tim

---

### Post by VMC on 2010-02-11
> **ratcheer said:**
> I got an email on my testing group's mail list, an hour or so ago. He said he thinks they have resolved the problem with plymouth in the latest kernel, 2.6.32.13, which was put on the server late Wednesday. So, I think I will update my iso and try again, tomorrow.

If that still fails, I will try removing plymouth.

Tim

Thanks. Todays latest updates installs the kernel your referring to. I will try now to add plymouth and see if it works.

*EDIT: Your right the newest kernel,2.6.32-13-generic, fixed Plymouth. Thanks for the heads ups. BTW, what "Lucid testing group" are you referring to?*

I would like to read somewhere that the newest kernel addressed Plymouth issue.

Edit2: Sorry, but the **Plymouth problem is still here**. It took three reboots for the freeze to come back!

---

### Post by ratcheer on 2010-02-12
> **VMC said:**
> 

*EDIT: Your right the newest kernel,2.6.32-13-generic, fixed Plymouth. Thanks for the heads ups. BTW, what "Lucid testing group" are you referring to?*



I am in the Xorg Proprietary Drivers Testing group. It will be awfully hard to test, though, if I cannot come up with a bootable installation of Lucid.

Tim

---

### Post by ratcheer on 2010-02-12
On a last hunch to try to get Lucid to work, I wondered whether my Karmic installation was for some reason keeping Lucid from booting. Maybe the partitioning or something. So, today, I bit the big one and backed up my /home to a DVD, then started Lucid install and completely repartitioned the disk and gave the whole thing to Lucid. I would like to be able to report that it worked, but it didn't.

So, now I am doing a clean install of Karmic. Lord knows how I will get everything back and configured, again. But, I will probably get rid of a lot of old garbage, too.

Tim

---

### Post by gunnar123 on 2010-02-15
From what I understand the solution has been posted here?:
[https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.0~-9](https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.0~-9)

I got rid of the issue on my laptop by removing plymouth, then reinstalled from the binary build debs you can access from there.

These are the four .deb files listed under each architecture.
First uninstall plymouth,
I found the safest way to get to a working command prompt once logged into X was to run "Log Out...", then select your username at the login console,
You should see a panel at the bottom of the screen where you find a "Sessions" dropdown menu. Instead of "GNOME", select "xterm" and then log in.
You arrive at a small xterm console and here you can remove plymouth:
sudo apt-get remove plymouth

Then install suitable debs from files you have downloaded
(in my case I need the 64-bit builds):
dpkg -i libplymouth2_0.8.0~-9_amd64.deb
dpkg -i libplymouth-dev_0.8.0~-9_amd64.deb
dpkg -i plymouth_0.8.0~-9_amd64.deb
dpkg -i plymouth-x11_0.8.0~-9_amd64.deb

Then reboot and things should be working.

I get lucid fast boots on my ASUS UL50VT with a Corsair P128 SSD...

---

### Post by ratcheer on 2010-02-15
Ok, if I understand the post at the launchpad link, plymouth has been removed from the disk. So, if I use a fresh disk download, I should be able to boot Lucid? I'll give it a try.

Thanks,
Tim

---

### Post by ratcheer on 2010-02-15
It is still a no go. I updated to Lucid CD image of 02/15/2010 and could not even complete the installation. So, things are somewhat worse than last week.  Tim

---

### Post by VMC on 2010-02-15
> **ratcheer said:**
> It is still a no go. I updated to Lucid CD image of 02/15/2010 and could not even complete the installation. So, things are somewhat worse than last week.  Tim

A couple of questions. First, this topic shows solved. Remove solved if its still a problem.

Also, using a daily-live current image, it still fails right after timezone?

I used yesterdays, and noticed that using Install instead of test the live image, it boots up as a live image. The boot string says ubiquity-only and yet it never gets to ubiquity. I have to select the install icon and then it starts. 

Also ubiquity crashes shortly after starting. I had to wait for the crash indicator, then get rid of the crash indicator and then continue on with ubiquity. Weird I know, but that's the only way ubiquity would work. If I started ubiquity and ignore the crash indicator then at some point shortly after manual partitioning the whole thing would stop.

---

### Post by ratcheer on 2010-02-15
> **VMC said:**
> A couple of questions. First, this topic shows solved. Remove solved if its still a problem.

Also, using a daily-live current image, it still fails right after timezone?

I used yesterdays, and noticed that using Install instead of test the live image, it boots up as a live image. The boot string says ubiquity-only and yet it never gets to ubiquity. I have to select the install icon and then it starts. 

Also ubiquity crashes shortly after starting. I had to wait for the crash indicator, then get rid of the crash indicator and then continue on with ubiquity. Weird I know, but that's the only way ubiquity would work. If I started ubiquity and ignore the crash indicator then at some point shortly after manual partitioning the whole thing would stop.

 Mine may have been very similar to yours, today. It did seem to go to a live desktop, even though I selected &quot;Install&quot; at the initial menu. But, there was nothing on my desktop except for the background - no icons, no menu, no taskbars. It never presented me with anything to do, at all. What a mess!  Then, after 30 seconds or so of looking at the orange background, my disk drive started clicking, repeatedly. It is not a clear clicking, it has a growling quality to it. At this, I reset the computer, removed the CD, and booted back to Karmic.    Maybe tomorrow's image will do better. I will try again, then.  Tim

---

### Post by VMC on 2010-02-15
> **ratcheer said:**
> Mine may have been very similar to yours, today. It did seem to go to a live desktop, even though I selected &quot;Install&quot; at the initial menu. But, there was nothing on my desktop except for the background - no icons, no menu, no taskbars. It never presented me with anything to do, at all. What a mess!  Then, after 30 seconds or so of looking at the orange background, my disk drive started clicking, repeatedly. It is not a clear clicking, it has a growling quality to it. At this, I reset the computer, removed the CD, and booted back to Karmic.    Maybe tomorrow's image will do better. I will try again, then.  Tim

You have another problem then. Two things media check on the cd/dvd you burned. Then if that's ok, download Alternate install and use that.

Edit: here'a another thought. Way back when in jaunty testing, I wouldn't boot a live cd to save my life. I then tried this. When you get cd boot menu, press F6 then add to the end of the line "nomodeset" (without quotes.

---

### Post by ratcheer on 2010-02-15
I have tried both nomodeset and the Alternate CD image several times over the past two weeks. Neither has worked any better than the regular CD wit no special options.

I have also tried powering down the machine, completely and removing the plymouth package. I have tried everything I can find. Karmic installs with no problems, but I cannot install a working Lucid.

Tim

---

### Post by ratcheer on 2010-02-16
Another rough morning attempting to install Lucid. I updated the iso image to the 02/16 version. Today, I booted to the Live image and got a good desktop. I installed using the icon on the live desktop. The installation ran very well until the end.

I got a GUI dialog saying, "ubi-migrationassistant failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken." I tried the "Try again" button several times, but always received the same dialog again, immediately.

From syslog:
```

ubiquity [3221] debconffilter_done : ubiquity.components.install (current: none)
ubiquity [3221] debconffilter_done : ubi-migrationassistant (current ubi-migrationassistant)
ubiquity [3221] dbfilter_handle_status : ('ubi-migrationassistant', 141)

```So, then I told the dialog to continue and was immediately informed that the installation was complete and to reboot. When I attempted to reboot, grub2 said:
```

Grub loading.
error: out of disk.
grub-rescue>

```So, I had to boot to a Karmic Live CD and reinstall grub to get back up in Karmic.

Whew!

Tim

---

### Post by ranch hand on 2010-02-16
So what happens if you run "sudo update-grub" in 9.10?  Does the 10.04 install show up?  If so, will it boot?

---

### Post by ratcheer on 2010-02-16
> **ranch hand said:**
> So what happens if you run "sudo update-grub" in 9.10?  Does the 10.04 install show up?  If so, will it boot?

Oh, i don't know. I already cleaned it up - deleted the partitions. I will be trying again, tomorrow. Every day is a new adventure.

Tim

---

### Post by witwicki on 2010-02-16
Tim,

That's odd.  I got the same "ubi-migrationassistant failed with exit code 141" error, selected continue, got the installation complete dialog, then had to manually power off (when the reboot appeared to be hanging with the ubuntu logo on the screen), but when I powered my computer back on, the linux kernel appeared in Grub2, and Lucid booted right up.

Success!

More details:  I just installed in the last several minutes.
I used the Lucid Alpha 2 Live DVD and selected "Try..", then from within Lucid running off of the DVD, I clicked the Install link and on the second screen prompted Lucid to "Update this installer".

---

### Post by ratcheer on 2010-02-17
> **ranch hand said:**
> So what happens if you run "sudo update-grub" in 9.10?  Does the 10.04 install show up?  If so, will it boot?

UPDATE - 02/17/2010: Ah, very interesting. It does find it. If I select the normal Lucid, the disk drive access light turns on and stays on, but nothing else happens. If I reboot and select Lucid recovery mode, it informs me "no such device" with a long UUID string.

It seems that the Lucid installation is mangling its UUID and this is why it can never reboot. Maybe this is enough info to use to file a bug report.

I still have the Lucid partitions if there is anything else you want me to try. Thanks.

Tim

---

### Post by VMC on 2010-02-17
> **ratcheer said:**
> UPDATE - 02/17/2010: Ah, very interesting. It does find it. If I select the normal Lucid, the disk drive access light turns on and stays on, but nothing else happens. If I reboot and select Lucid recovery mode, it informs me "no such device" with a long UUID string.

It seems that the Lucid installation is mangling its UUID and this is why it can never reboot. Maybe this is enough info to use to file a bug report.

I still have the Lucid partitions if there is anything else you want me to try. Thanks.

Tim

I'm not sure if you know this, but there is a great script that will help you on boot related problems. Click on my "blue" bootinfoscript and download and run it. You will see everything relating to your booting and any problem areas.

---

### Post by ratcheer on 2010-02-17
Thank you, VMC. I have downloaded and run your script, but beyond that I am not savvy enough to use the info to fix anything. I can tell that the UUID's fro the Lucid partition appear to be consistent, but I have no idea whether they are right or wrong. Nor would I know what to do if they were wrong.

Here is the info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdbc9dbc9

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     4,000,184     4,000,122  82 Linux swap / Solaris
/dev/sda2    *      4,000,185    64,002,959    60,002,775  83 Linux
/dev/sda3          64,002,960   156,296,384    92,293,425   5 Extended
/dev/sda5          64,003,023   104,004,809    40,001,787  83 Linux
/dev/sda6         104,004,873   154,047,284    50,042,412  83 Linux
/dev/sda7         154,047,348   156,296,384     2,249,037  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5c5b585d-e746-4a49-bb39-69ba8e4bcc2d   swap                                     
/dev/sda2        f24aede3-5b5a-4484-a966-81828a1cb945   ext4                                     
/dev/sda5        4d56c31e-34cd-4f4e-a872-98854bdad92a   ext4                                     
/dev/sda6        2a90e663-a711-49f1-a722-2e354ff3d94d   ext4                                     
/dev/sda7        9deacfe5-a509-41d6-800d-e423b5bcaf83   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set f24aede3-5b5a-4484-a966-81828a1cb945
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f24aede3-5b5a-4484-a966-81828a1cb945
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f24aede3-5b5a-4484-a966-81828a1cb945 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f24aede3-5b5a-4484-a966-81828a1cb945
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f24aede3-5b5a-4484-a966-81828a1cb945 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f24aede3-5b5a-4484-a966-81828a1cb945
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f24aede3-5b5a-4484-a966-81828a1cb945 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f24aede3-5b5a-4484-a966-81828a1cb945
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f24aede3-5b5a-4484-a966-81828a1cb945 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-13-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    linux /boot/vmlinuz-2.6.32-13-generic root=UUID=2a90e663-a711-49f1-a722-2e354ff3d94d ro quiet splash
    initrd /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    linux /boot/vmlinuz-2.6.32-13-generic root=UUID=2a90e663-a711-49f1-a722-2e354ff3d94d ro single
    initrd /boot/initrd.img-2.6.32-13-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=f24aede3-5b5a-4484-a966-81828a1cb945 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=4d56c31e-34cd-4f4e-a872-98854bdad92a /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=5c5b585d-e746-4a49-bb39-69ba8e4bcc2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.31-14-generic
   2.9GB: boot/initrd.img-2.6.31-19-generic
   2.6GB: boot/vmlinuz-2.6.31-14-generic
   2.7GB: boot/vmlinuz-2.6.31-19-generic
   2.9GB: initrd.img
   2.6GB: initrd.img.old
   2.7GB: vmlinuz
   2.6GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-13-generic" {
        recordfail
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=2a90e663-a711-49f1-a722-2e354ff3d94d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    echo    Loading Linux 2.6.32-13-generic ...
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=2a90e663-a711-49f1-a722-2e354ff3d94d ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-13-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 2a90e663-a711-49f1-a722-2e354ff3d94d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=2a90e663-a711-49f1-a722-2e354ff3d94d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9deacfe5-a509-41d6-800d-e423b5bcaf83 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  66.2GB: boot/grub/core.img
  66.2GB: boot/grub/grub.cfg
  66.4GB: boot/initrd.img-2.6.32-13-generic
  66.2GB: boot/vmlinuz-2.6.32-13-generic
  66.4GB: initrd.img
  66.2GB: vmlinuz


```

It seems odd to me that I am consistently having this problem, but no one else has it. I have installed Karmic, twice, with no such issues. Last Friday, as seen earlier in this thread, I had to reset the partition header and reinstall Karmic from the ground up. The install went just fine, but it was a real pain getting all my stuff back. And before that, I installed Jaunty with no issues.

So, why is Lucid being such a pain, just for me?

Tim

---

### Post by VMC on 2010-02-17
Hardware is the most likely suspect. Regarding the boot output, just read it through. Your MBR is installed off of partition#2 of the sda drive. sda6 is your Lucid partition. Just read it carefully for any inconsistencies. At first look, at appears ok. 

Boot up to grub then "E" your Lucid line and remove the "quite" entry by backspacing and then Ctrl+x to boot. then look at the output messages and see if anything looks wrong.

---

### Post by ratcheer on 2010-02-17
> **VMC said:**
> 

Boot up to grub then "E" your Lucid line and remove the "quite" entry by backspacing and then Ctrl+x to boot. then look at the output messages and see if anything looks wrong.

Still no luck. After Ctrl-x, it gave a plain text screen with "Booting a command list" at the top, the disk access light on steadily, and nothing else happened. I waited a full minute before aborting.

Tim

---

### Post by ranch hand on 2010-02-17
Add these 2 entries to your /etc/grub.d/40_custom file in 9.10;
```

echo "Adding Lucid on sda6" >&2 
cat << EOF
menuentry "Lucid on sda6" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Lucid on sda6 recovery" >&2 
cat << EOF
menuentry "Lucid on sda6 recovery" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro single
        initrd /initrd.img
}
EOF

```
run
```

sudo update-grub

```
When you reboot these should be at the bottom of your menu.   These are symbolic menu entries that just look at the partition defined and boot to the newest kernel available.

It may not do any good but it will tell us a little more about this.

I would also boot to you LiveCD and pull up gparted and label your partitions.  This makes the chroot process easier.

If those entries do not do anything, or if it hangs hit Ctrl+Alt+F2 and see if you get a text login.  If so log in and type "sudo service gdm start".  This will tell us if x is starting and working to some point and if gdm is working.  When this tells you gdm is already running I will be happy and you can type "sudo reboot".  That is easier on your system.

If those entries do not get you to recovery we will chroot in from 9.10 and change where you are booting from to 10.04 (better grub) and set up the menu to be all correct before trying to boot from there.

---

### Post by ratcheer on 2010-02-17
Thanks, ranch hand, I tried your main suggestion. Trying to boot to the normal Lucid entry went back to thr repeated disk drive "clicking", which sounds very nasty. It does this kind of crunching sound 6 times every 5 seconds.

Next, I tried Lucid recovery mode. It gave me a logon after making the crunching sound a few times. Then, after I entered my id it crunched a few times before giving a password prompt. After I entered the password, it went back to the 6 times per 5 seconds crunching.

The repeated crunching is what it does when I get a good install of Lucid and try to reboot. I can understand it being "a hardware error", but I don't totally understand why it affects Lucid but not Karmic or Jaunty.

I already chroot'ed to the Lucid installation from the Live CD and ran grub-install. That is why it can be seen on sda6 in the output of VMC's script (about four posts above). If I try to boot to that, it also starts the repeated crunching.

Tim

---

### Post by ranch hand on 2010-02-17
Well,  I do not know what the deal is here.

I would chroot from your 9.10 install.  It is quicker than the LiveCD.  That way you can run your updates on 10.04 and try it from time to time.  We got some kernel patches yesterday.  This next week may be kind of busy in updates to get up to the freeze for A3.

This was why I suggested labeling your partitions.  I am sure that it is easy enough to chroot without doing that but it is easier for me to do it with them labeled.

I use a script from phillinux that he shared in the 9.10-testing forum;
```

#!/bin/sh

sudo mkdir /mnt/MAIN
sudo mount /dev/sda6 /mnt/MAIN/
sudo mount -o bind /proc /mnt/MAIN/proc
sudo mount -o bind /dev /mnt/MAIN/dev
sudo mount -o bind /dev/pts /mnt/MAIN/dev/pts
sudo mount -o bind /sys /mnt/MAIN/sys
sudo cp /etc/resolv.conf /mnt/MAIN/etc/resolve.conf
sudo chroot /mnt/MAIN /bin/bash

fi

```
You need to edit to fit your labels.  It is for my sda6 which is a 8.04 install.  You need all that to be able to connect  and run updates.

If it will not connect use nautilus and check the /etc/resolv.conf file and see if it is complete. Compare with your 9.10 file.  Copy/paste from there if not right.

---

### Post by ratcheer on 2010-02-17
ranch hand - OK, I have all that working, in a raw way. I'm not sure I understand what labels have to do with it, but I am up as root in a chroot terminal. Also, what is the hanging "fi" at the end of the script for?

Also, I have this info from the chroot session:

```

root@tim-desktop:/# sudo grub-probe -t device /boot/grub
/dev/sda6

```

Tim

---

### Post by ranch hand on 2010-02-17
Lets the terminal know it is at the end of the script.

---

### Post by ratcheer on 2010-02-17
Ok. What should I do, next? Are there specific updates you want me to install? Or configuration changes? This installation was made from this morning's updated iso image.

Thanks,
Tim

---

### Post by ranch hand on 2010-02-17
Nope.  Not a clue.  I would just ride it out and hope that some update gets it right.

I forget exactly how long it was but I had a 9.10-testing install that went south on me and wouldn't boot for almost 2 weeks.  Couldn't hurt the bugger so I just ran a "dist-upgrade" on it every day and one day I tried it and it booted up fine.

Quit throwing "dist-upgrades" at it then and started back up being careful.  9.10 was a rough ride.

EDIT

I would not try anything but the "recovery" entries.  If you get to that menu definitely run the dpkg option.

I would run "dpkg --configure -a" once in a while in chroot too.  If it starts throwing up errors you will be on the road to recovery.

---

### Post by ratcheer on 2010-02-17
Ok, thank you very much. I am on one of the Ubuntu testing teams, though, and I think I am supposed to insttall a fresh image every week. But, I suppose that doesn't mean much if I can't get any image to reboot!

Tim

---

### Post by ranch hand on 2010-02-17
That would only really be good for testing the ISO.  If you are getting the updates you have the same installation that you would from a fresh install (unless you have modified it).

If you have modified it I would do a fresh install if you think it will go.  Leave the bugger alone and update it after that until it will boot.

---

### Post by ratcheer on 2010-02-17
No, I have not modified anything. I have just been trying to get it to boot. ;)

I ran a full-upgrade and got 15 package and library updates. It still won't boot, though.

I really appreciate all your help. If nothing else, I am learning a lot about managing my installations.

Tim

---

### Post by putxi on 2010-02-18
hi, interesting, i had (have) the same problem ...
gui window with "2ubi-migrationassistant failed with exit code 141. Further information may be found in /var/log/syslog." at the end of the installation of lucid.

i put it on context, to see if it can give more light to the issue, and to see if someone knows how to proceed.

* laptop (from early february'2010): dell 1558, intel i5 520
* hd partitions:
1: Dell self-made.
2: Recovery (for windows).
3: windows7
4:
5: lucid current daily (17/02/10)
6: swap

After poping that error gui window, i continued ... and it seemed everything was ok: rebooting, login, ..., updating via synaptic, ...
But, slightly after, problems apperard (mainly **frozen** login window when pressing key(s) ) - that is being discussed on that [thread]("http://ubuntuforums.org/showthread.php?p=8845545#post8845545").

I'll keep an eye on how this post continues ...

Regards,
jordi

PS: ranch, good to see you here, too ;)

---

### Post by VMC on 2010-02-18
> **ratcheer said:**
>  Also, what is the hanging "fi" at the end of the script for?

Also, I have this info from the chroot session:

```

root@tim-desktop:/# sudo grub-probe -t device /boot/grub
/dev/sda6

```

Tim

I think that was left over from original script. Loops usually come in pairs: if ..loop.. fi, you don't need it.

---

### Post by ratcheer on 2010-02-19
Today was the worst installation attempt, to date. I zsync'ed to this morning's iso image, booted to the Live CD, and started the "Install" icon on the desktop. This has been the method that has been giving the closest approximation to success, i.e., installation frequently runs to completion and tells me to reboot; then, reboot fails.

Anyway, this morning, it barely got started and Ubiquity crashed. Maybe I'll try the alternate image, a little later.

Tim

---

### Post by ratcheer on 2010-02-20
Today was much better. The 02/20 Lucid iso installed without any hint of a problem.

It still won't boot, though. :(

Tim

---

### Post by ratcheer on 2010-02-24
Today, I was finally able to boot into installed Lucid. It still will not boot normally, but I can boot recovery mode to a root prompt and then start gdm, bringing up the desktop.

This is not perfect, but it is progress. At least I can perform my Lucid Xorg Drivers test team duties. For the time being, anyway.

Tim

---

### Post by jppr on 2010-02-24
[http://cdimage.ubuntu.com/daily-live/20100224.1/](http://cdimage.ubuntu.com/daily-live/20100224.1/)   That works perfect = )  This is first time after 9.10 alpha 3 when live  cd works me

---

