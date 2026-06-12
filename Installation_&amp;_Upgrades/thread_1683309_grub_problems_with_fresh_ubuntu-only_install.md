---
title: "grub problems with fresh ubuntu-only install"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by ben178 on 2011-02-07
Hi,

I'm a complete newbie to Ubuntu (only Win yet).

In short: I tried to install Maverick on a new Notebook, re-installed a few times thinking I used wrong settings as booting from the hard disk didn't work.
Now I only get
```
file not found
grub rescue
```All the other threads I came across seemed to only deal with grub problems connected to dual boot installations.




Now, the complete story is:
As I had to replace my old notebook, I decided to try Ubuntu on the new one. I got an Asus X52F-EX513D with only a freeDOS installation on it.
Booting Maverick from CD went fine.
I made a copy of everything that was on the disk (was surprised something was there, guess that was the freeDOS and stuff Ubuntu saved there. wanted to be sure not to delete drivers).
I used the included tools to format the hard disk and installed Ubuntu. I guess I messed up with assigning the partitions, as I'm new to the OS. As booting from hard disk didn't work, I thought I'd simply reinstall, and actually I thought this a couple of times...:rolleyes:
Booting from hard disk never worked, now I only get
```
file not found
grub rescue
```I tried ```
startx
```from there, as I had found in a forum that that should start the OS, but it seemed to just stop somewhere halfway. When I then used the power button to shut down, the purple shutdown screen appeared before it went off.

I hope you can help me, I thought of overwriting the whole disk with zero's (it's new and empty anyway) and then reinstalling, but I don't want to just keep on repeating the same error.
Thanks in advance for answers.

---

### Post by ashickur.noor on 2011-02-07
you have to restore the grub. See the thread of restoring grub.

---

### Post by Rubi1200 on 2011-02-07
Hi and welcome to the forums ben178 :-)

Before you continue, please do the following so we can see what is really going on with the current setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ben178 on 2011-02-07
thanks for answers and welcoming words :)

first, I'm sorry, but I missed out on something when pointing out my problem above; I had formatted my drive using the disk utility before posting, only it didn't show the results then.
hence, after I read the post about restoring grub, I realized,  thus installed again (guess once more or less doesn't make the difference), using
swap     4000
/boot     1000
/          16000
/home [the rest]
I did not change the boot loader destination, so the drop-down menu showed just /dev/sda and the name of my disk.
when rebooting, I get a text screen prompt saying
```
ubuntu 10.10 [computer_name] tty1
[username] login:
```after logging in, I get a text screen saying
```
Welcome to Ubuntu!
*Documentation: [...]
[username]@[computer_name]: ~$
```entering ```
startx
``` makes the screen go black and stay so. when shutting down using the power key, before switching off, I get a purple screen with a lot of text, the end being
[no such file or directory]
then something about the power button and shutting down.


next, I read Rubi1200's post and did as said. The boot info script returned the following:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     7,813,119     7,811,072  82 Linux swap / Solaris
/dev/sda2    *      7,813,120     9,766,911     1,953,792  83 Linux
/dev/sda3           9,766,912    41,017,343    31,250,432  83 Linux
/dev/sda4          41,017,344   625,141,759   584,124,416  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6245b881-1670-4bbd-929a-8eeb449be5ec   swap                                     
/dev/sda2        bddc896b-419c-4c9f-bf1e-9eb7a472c404   ext4                                     
/dev/sda3        134f21b3-380b-4745-8361-345d7b81ff86   ext4                                     
/dev/sda4        45c3509a-8129-42ad-83fa-197db82040d8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda2/grub/grub.cfg: =============================

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
set default="0"
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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 134f21b3-380b-4745-8361-345d7b81ff86
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set bddc896b-419c-4c9f-bf1e-9eb7a472c404
set locale_dir=($root)/grub/locale
set lang=de
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set bddc896b-419c-4c9f-bf1e-9eb7a472c404
    linux    /vmlinuz-2.6.35-22-generic root=UUID=134f21b3-380b-4745-8361-345d7b81ff86 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set bddc896b-419c-4c9f-bf1e-9eb7a472c404
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=134f21b3-380b-4745-8361-345d7b81ff86 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set bddc896b-419c-4c9f-bf1e-9eb7a472c404
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set bddc896b-419c-4c9f-bf1e-9eb7a472c404
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda2: Location of files loaded by Grub: ===================


   4.1GB: grub/core.img
   4.1GB: grub/grub.cfg
   4.1GB: initrd.img-2.6.35-22-generic
   4.1GB: vmlinuz-2.6.35-22-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=134f21b3-380b-4745-8361-345d7b81ff86 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=bddc896b-419c-4c9f-bf1e-9eb7a472c404 /boot           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=45c3509a-8129-42ad-83fa-197db82040d8 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=6245b881-1670-4bbd-929a-8eeb449be5ec none            swap    sw              0       0

```sorry if I complicated things further- should I start a new topic with this one? I mean, I don't even know whether it's still the same issue now.:rolleyes:
thanks for your time.

---

### Post by oldfred on 2011-02-07
You are now booting, it is just to the command line. And if startx does not work that indicates some sort of video issue.

If you only have one system, you will have to hold shift key from BIOS until menu appears.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

How to set NOMODESET and other kernel boot options in Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Some nVidia chips use the Generic setting.

Some issues may be here, if your model or a similar one is listed.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by ben178 on 2011-02-08
thanks.
before I try that - I installed Ubuntu using the graphic interface and am now typing from Maverick, booted on the same Notebook, from the same (MD5-checked) CD.

so, even though I get the os running from CD in normal graphics mode, I change to low mode for booting from hard disk? just to check back, I'm insecure.:confused:

From what I find online, my Asus X52F-EX513D should have Intel GMA HD; is that already what you would consider an "older" Intel chip? First thing to turn up when I google is a review from January25, 2010. "Intel GMA HD" turns up in none of the linked pages. I don't have the slightest idea which netbooks might be similar to my Laptop, nor do I understand in what regard similar. Graphics card? How do I find out, if not by googling the specifications of every single one of them?
I don't understand that information about nVidia and Generic setting- I don't know what the generic setting is.:confused:
I'll happily follow any instructions to get this done, and I'm fine with learning something on the way.
From what you linked to I get the feeling I will have to dig through techy how-to pages using a language I don't understand for another two days to understand what I'm being proposed to do - could you explain?
:confused:
No offense, I just really don't get it. Sorry if I sound a bit frustrated. I thought of putting up Ubuntu as easy and user-friendly, now I spent two days trying to figure out how stuff works (and learning some, for sure) when I had thought I'd switch to a simple-to-handle, free os to get my work done.

I don't get what I should do with the information in the LiveBootCD-page linked, nor do I understand any of the Kernel Documentation. What is the last line about?
:frown:

---

### Post by coffeecat on 2011-02-08
This...

> **ben178 said:**
> 
when rebooting, I get a text screen prompt saying
```
ubuntu 10.10 [computer_name][COLOR=Red] tty1[/COLOR]
[username] login:
```after logging in, I get a text screen saying
```
Welcome to Ubuntu!
*Documentation: [...]
[username]@[computer_name]: ~$
```entering ```
startx
``` makes the screen go black and stay so.

... means you are booting into tty1, which shouldn't happen, and I can't see why. tty1 is virtual terminal 1 which is command line only and startx won't work from it if the xserver (the basis of the GUI) has already started. When you get to that point, don't login but press the key combination ctrl-alt-F7 and see what happens.

Unless I've missed something, the boot script output looks OK.

> **ben178 said:**
> From what I find online, my Asus X52F-EX513D should have Intel GMA HD; is that already what you would consider an "older" Intel chip? 

You're right. The Intel GMA is not that old. The older Intel chipsets that are giving trouble are the ancient 8** series and, I believe, some of the earlier 9**. So that we can see exactly which Intel chipset that is, when you are next booted into the live CD (or if you manage to get into the GUI with ctrl-alt-F7), open a terminal (Applications > Accessories) and post the output of:

```
lspci | grep VGA
```Have I understood you correctly that you can get into the GUI from the live CD but not from your HD install? If so, that's very odd. But if so, at least that proves the graphics shouldn't be a problem.

---

### Post by ben178 on 2011-02-08
I tried following the instructions provided (by oldfred), but I couldn't get to the menu - so far, GRUB never showed me a menu to choose a boot option from where I could have pressed [e] to access the menu.
So I went into the BIOS menu using [esc], then tried holding [shift] for a minute, went to the boot options, held down [shift] for another minute. Guess I just got you completely wrong there?
:confused:
Holding [shift] during the boot process until I get asked my name and password didn't have any effect, either.

Going to the menu from the LiveCD bootscreen (the purple one with the keyboard icon at the bottom) did work, but that's only for the actual boot from CD, right?

---

### Post by ben178 on 2011-02-08
hi coffeecat,
I posted my last reply before seeing yours.
thanks for help and explanations to all of you.

Yes, I can boot from CD, choosing a [Try Ubuntu]-button in a graphic interface, using my touchpad. I am then perfectly able to connect to the internet using built-in wireless lan and the included firefox so I can post my questions here, not using another machine at all at the moment. I can't see how graphics could be better from what I have now, that's fine, just that I can't boot from the hard disk (so whenever I restart everything I did before is gone).

The terminal output you asked for is

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
```I'll check what ctrl-alt-F7 does and then come back here.

---

### Post by oldfred on 2011-02-08
By looking here I found some similar Asus with GMA. That sent me to a Video card page.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by coffeecat on 2011-02-08
> **oldfred said:**
> 
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

The Poulsbo abomination is the GMA500, but according to this:

[http://www.computeruniverse.net/products/e90397375/asus-x52f-ex513d-freedos.asp](http://www.computeruniverse.net/products/e90397375/asus-x52f-ex513d-freedos.asp)

... the OP has the X4500, which I believe is different. Frustratingly, I couldn't find the X52F-EX513D on the Asus website to get more information and the output of lspci is somewhat taciturn.

I still find it odd that the live CD is giving the OP a GUI, whereas their HD install is booting them into tty1.

---

### Post by ben178 on 2011-02-08
so, first my results with ctrl-alt-F7:
using this both before or after entering my name and password seems to have the same effect.
after waiting for about two minutes with a blinking "_" in my top left corner, I get one line of text flashing up too fast to read, then a black screen, nothing happening after that.
When using the power button to switch off then, I had the purple ubuntu screen with the four (five?) white dots, but with the text
```
killing all remaining processes
```respectively
```
*Asking all remaining processes to terminate
```followed by```

unmounting weak file system ...[fail]
```and four or so more lines that I wasn't quick enough to read, but all ending with ```
...[OK]
```oldfred, so the "hd" in "intel gma hd" is only marketing, not model specification? I could have thought of that...
you think the 500 one is the right one?
I've found "Intel GMA HD (IGP) shared memory" as the specifications on a retailer website, if that helps further... shame on me, I don't even know what  hardware EXACTLY I'm using - I'm not up-to-date and hoped it would work out anyway when my old (OLD) laptop broke down lately.
ok, now...
what do I make out of that:



 Most  things work well, except for the video card, Intel GMA500 (Poulsbo) not  being supported out-of-the-box. It requires installation of binary  drivers that needs to be reconfigured after every kernel update. [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
 

how do I do that? and how come from CD it works just fine, then?

---

### Post by ben178 on 2011-02-08
ah, I was too slow again :)
yes, that's exactly my model you linked as far as I can tell, from pictures and specifications.
the asus website was a complete dead end for me as well, if they have the info somewhere, then really, really well hidden...

---

### Post by ben178 on 2011-02-08
I don't know whether that helps, but I collected three threads that seem to have to do with my problem, kind of; connected to Linux but not Ubuntu - but if I get it right, those graphics card issues are connected to the kernel anyway?
I'll just post the links, if I'm being stupid just ignore them:
[https://bbs.archlinux.org/viewtopic.php?id=73322](https://bbs.archlinux.org/viewtopic.php?id=73322)
[http://forum.kde.org/viewtopic.php?f=111&t=86149](http://forum.kde.org/viewtopic.php?f=111&t=86149)
[http://askubuntu.com/questions/15336/does-unity-work-on-intel-gma-x4500](http://askubuntu.com/questions/15336/does-unity-work-on-intel-gma-x4500)

---

### Post by ben178 on 2011-02-08
How is that- every time I do a new installation, GRUB is written to the MBR anew? So I don't have any leftovers from bad stuff that happened before?
If so, I just might try Lucid later on tonight, if I get a chance to download and burn a disc (that's one of the problems of me booting from CD at the moment, obviously). For now, I'll have to give it a break, I guess.
If any of you speaks german, I think some people are discussing things related to the model in german forums ([http://forum.ubuntuusers.de/topic/erstes-booten-nach-installation-ohne-gui/](http://forum.ubuntuusers.de/topic/erstes-booten-nach-installation-ohne-gui/)) as, as I now realize, the configuration seems to be sold primarily (if not only) by germany-based online retailers. As that's my mother tongue I'll look there further as well and post if I find something that works.
Thanks again so far.

---

### Post by oldfred on 2011-02-08
coffeecat is correct that the 4500 is the version before the 500.
[http://en.wikipedia.org/wiki/Intel_GMA#GMA_X4500](http://en.wikipedia.org/wiki/Intel_GMA#GMA_X4500)

You should be able to use the shift key. Some have to try more than once, and you do have to hold it down the entire time from BIOS until menu appears.

If you boot liveCD and run this, does it show the driver, this is from my install?

fred@fred-LT-A105:~$ sudo lshw | grep -A 11 display
[sudo] password for fred: 
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: [COLOR=Red]driver=i915[/COLOR] latency=0

---

### Post by ben178 on 2011-02-08
the requested terminal shows:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw |grep -A 11 display
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:e080(size=8)
ubuntu@ubuntu:~$ 

```
I'll have to try the [shift] thing again and post later on as I'm away now.

---

### Post by ben178 on 2011-02-09
I still wasn't successful opening any menu with [shift].
I did, however, download and install 10.04.1 - and it's running, no complications but some minor issues with webcam image and waking up from hibernating.
As I'm more interested in using a working OS than in making especially 10.10 work, I guess I'll be fine with that.
Thanks for all the help!!
I'm not sure though whether or not I should flag this thread as [solved], as I rather just found a way not to deal with the problem?

---

### Post by coffeecat on 2011-02-10
Hi - sorry no one responded to your lshw output, but  I'm glad 10.04 is working for you. At least 10.04 is a long-term release and supported for another couple of years, so that's good.

I just thought I would post a few ponderings, because there are aspects to your situation which I find puzzling.

**VIDEO**. I don't believe the video chipset was the problem. The output of both lspci and lshw were remarkably unhelpful (that's down to the hardware - those commands merely reproduce what the hardware reports) but if we believe the link I found and that your Intel chipset is indeed the GMA X4500, then it *should* have worked. I found a few threads on this forum where people with this chipset on other machines were not having your problems. And, besides, you were able to get the GUI from the live CD session. If it works in the live CD then it should work from the HD installation.

But clearly there was some video problem because when you pressed ctrl-alt-F7 to get into tty7 (which is what you should be booting into), you got a black screen. And every time you booted up you were dumped into tty1 - which shouldn't happen. And at first when you tried to boot up you got grub errors - if I read you correctly - which means that Ubuntu hadn't even started booting. All of which suggests a corrupted install, except that you re-installed several times. And **this** suggests a corrupted installation medium. I wonder if your CD was a bad burn.

Last thought about partitions. No doubt you got the idea about a separate boot partition from some guide somewhere. A separate boot partition is really an unnecessary complication in your situation. It wouldn't have been the problem, but I just thought I'd point this out. Also, you used Disk Utility to setup your partitions and you ended up with four primary partitions, which is the maximum numbers of primary partitions allowed with an mbr partition table. It works but most people prefer to set up logical partitions to allow for future flexibility. As, no doubt, you'll be using Ubuntu or some flavour of Linux for some time to come, here's one for your bookmarks:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

There's a lot of useful information there and it tells you how to use Gparted which many people prefer to use - it's on the live CD.

Happy Ubuntu-ing! :)

---

### Post by ben178 on 2011-02-10
Thanks Coffeecat,
as I tried to set the system up again and again, I used Gparted as well. I'll read further. With the /boot partition, I guessed that would be necessary if I used more than one OS - so, to keep that possibility open... :)

I did actually download the 10.10 iso  again, to be sure, checked the MD5, burned slow and had Nero check the burnt CD for errors, then, going to the boot menu from the boot screen (that I could not reach when booting from hard disk, be it for my stupidity or because something went wrong), I had the option of checking the CD, again, and I did. Everything seemed fine, only that the installation would not work (from both CDs!).
I found people over on the german board I mentioned with the same laptop model, having similar problems of booting to a black screen from hard disk (they, with a Windows installation along), but being fine with Lucid as well. So, for the moment, everything I need is working, and that's the important part.
Thanks for help, everybody and for the time you took for explanations!
:D

---

### Post by oldfred on 2011-02-10
If you want /boot you have to have one for every install. Files are not compatible. You can share swap if you do not hibernate. I create a /data so I can share my data and that keeps /home tiny, so now I leave /home inside /.

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by ben178 on 2011-02-11
ah, fine- that's basically what I did under Windows. I thought I had to do it differently under Ubuntu...
I keep learning :)

---

