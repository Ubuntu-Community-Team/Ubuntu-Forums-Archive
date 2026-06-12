---
title: "GRUB2 does not show Windows-XP in the menu anymore"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by Merel 469 on 2011-05-18
GRUB2 does not show Windows-XP Pro in the menu anymore.

Probably already posted before; however each case usually is somehow different.
I use Ubuntu only occasionally to learn how it works.
My knowledge of Ubuntu and GRUB2 is very basic and I need some help.

After the latest update using Update Manager, quite a few packages were installed without any problem. However GRUB2 does not show the Windows-XP(Prof) partition in the menu anymore. Now I can't boot Windows because I can't select what is not shown.


_1. This what I get with command "sudo fdisk -l" (in the present situation) _

georges@PC1:~$ sudo fdisk -l
[sudo] password for georges: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a2c1a2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4846    38925463+   7  HPFS/NTFS
/dev/sda2            4847       19296   116069162+   f  W95 Ext'd (LBA)
/dev/sda5            4847        7697    22900626    7  HPFS/NTFS
/dev/sda6            7698       10200    20105316    7  HPFS/NTFS
/dev/sda7           10201       15682    44034133+   7  HPFS/NTFS
/dev/sda8           15683       19296    29028352   83  Linux

Disk /dev/sdk: 8011 MB, 8011087872 bytes
32 heads, 63 sectors/track, 7761 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40dc405e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1        7761     7823056+   b  W95 FAT32

Disk /dev/sdg: 64 MB, 64094208 bytes
4 heads, 32 sectors/track, 978 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         977       62512    6  FAT16
georges@PC1:~$

[U]
2. I tried command "sudo update-grub" and this is the result :[/U]

georges@PC1:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
georges@PC1:~$ 


[U]3. The Windows partition has been detected on dev/sda1
[/U]As shown in point 2, the Windows XP has been detected, but it does not appear in the GRUB2 bootmenu ! 

QUESTION :
It is already the second time that GRUB2 changes the menu items as it pleases, messing up the bootmenu.
How can I repair the bootmenu in order to be able to boot Windows-XP, as before the updates ?

The current Ubuntu version is now 10.4 LTS
The current GRUB version is  "GNU GRUB version 1.98 Ubuntu10"

Thank you for any assistance.

---

### Post by Quackers on 2011-05-18
Do the present grub menu entries take up the whole screen?
Maybe the Windows Loader is lower down?

---

### Post by Merel 469 on 2011-05-18
I will check if menu takes all screen.
But before I reboot (cold boot), let me first show the contents of the file "grub" which is supposed to "update" the Grub2 menu, with the command update-grub. I don't see any text which is pointing to a Windows XP partition. Logically, I can't expect it to appear in the bootmenu.

I guess that I should edit this file manually. But I'm not familiar with the syntax to be used. (By the way, I don't even know what all those options are about, but that's another issue to discuss)

Here follows what I copied from the file : 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=14
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by kansasnoob on 2011-05-18
The long list of kernels is probably just pushing Windows off the bottom of the screen:

> Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1

But the down arrow key should still "scroll" you there. 

You could remove some of the older kernels. It's generally wise to keep the two newest known working kernels, eg; 2.6.32-31 and 2.6.32-30.

The way I like to do that is using a bit of 'copy-n-paste' in synaptic, like just highlight and copy the oldest kernel, eg; 2.6.32-24, and then open Synaptic, click on Search and in that window paste the kernel number. Then you can mark those packages for removal.

This is a screenshot of the basic idea in Maverick:

[ATTACH]192528[/ATTACH]

Just be sure to keep the two newest kernels and after applying the changes in synaptic be sure to run "sudo update-grub" again.

---

### Post by drs305 on 2011-05-18
It wouldn't surprise me either if Windows had scrolled off the menu.

As far as what the options mean, they are explained a bit in this post:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

For removing some of the older kernels, here is a guide I made a while back. I recommend Ubuntu Tweak, a GUI app that can remove kernels and do a lot more. It's covered in the guide.
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")
When kernels are removed from the system the post-installation process also removes them from the Grub menu.

---

### Post by Merel 469 on 2011-05-18
I restarted my PC without making any changes (cold boot) and YES dear **Quackers**and other forum members, you are right : the bottom two lines were not displayed until I clicked on a very little and almost invisible "scroll down" arrow : yet another memory test more and finally at the bottom, the Windows XP operating system.

(I know how to put it on top and set it as default with bootmanager in Ubuntu) 


Very happy with that simple "solution" ! Thank you for this fast and efficient help. I'm probably not the only one who  encountered that stupid problem, which is actually not a bug. I'm now writing here using a Windows browser.

To be honnest, I have hard feelings towards Grub2. (I hope you are not involved in the process of making this bootloader; I certainly don't want to offend anyone, but many people will agree with me ... it is a piece of software that requires too much user's attention and is not very simple to handle)

I have read the last posts (just now), and will proceed to remove other not required entries.

Finally I would like to add [SOLVED]in this topic title, but it looks as if topic titles can't be edited ?
Thanks again to all

---

### Post by drs305 on 2011-05-18
> **Merel 469 said:**
> 
Finally I would like to add [SOLVED]in this topic title, but it looks as if topic titles can't be edited ?
Thanks again to all
You can mark the thread solved via the 'Thread Tools' link at the top right of the first post. Thanks for doing so.

Happy Ubuntu-ing !

---

### Post by Quackers on 2011-05-18
Glad that helped :-)
If you delete some older kernels the grub menu will be much shorter.
Alternatively you could change the size of the text and get it all on one page then :-)

Grub2 is a niiiiice bootloader :-)  It's just a bit different, that's all.
It actually does quite a lot of jobs, it's quite customisable and you can boot some iso files directly from it's menu. (Thanks drs305). 
That's good :-)

---

### Post by kansasnoob on 2011-05-18
> **drs305 said:**
> It wouldn't surprise me either if Windows had scrolled off the menu.

As far as what the options mean, they are explained a bit in this post:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

For removing some of the older kernels, here is a guide I made a while back. I recommend Ubuntu Tweak, a GUI app that can remove kernels and do a lot more. It's covered in the guide.
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")
When kernels are removed from the system the post-installation process also removes them from the Grub menu.

I've had both Ubuntu Tweak  and the Grub Customizer eat my lunch so I'm back to manual mode :D

---

### Post by drs305 on 2011-05-18
> **kansasnoob said:**
> I've had both Ubuntu Tweak  and the Grub Customizer eat my lunch so I'm back to manual mode :D

Have you had a bad experience with Ubuntu Tweak removing kernels? It's been solid for me but I'd like to know if your kernel experience was different. For instance, I *never* recommended System Janitor...

---

### Post by Merel 469 on 2011-05-19
Actually, I can't even install Ubuntu-Tweak !! There is some **error message **right at the start when attempting to install it following instructions as described here before. 

The message is not giving the user any clue what to do.
Hmm... "Ubuntu...the LINUX for human beings" ? 

I opened another topic for this issue. 
[http://ubuntuforums.org/showthread.php?t=1761713](http://ubuntuforums.org/showthread.php?t=1761713)


**[COLOR="Blue"]EDIT :[/COLOR]**
Ubuntu-Tweak is now installed, as explained in the topic above.
I made a first use of this program to remove only ONE older kernel, as a test.

Remarks :
- Two files are be deleted for each referenced old kernel.
- Using "GruB Customizer" editor will only **_hide_** one (or more) list entry, but it _will not remove_ the corresponding kernel. 


I learned a lot here, yet much more will be needed to persuade me that (for "human beings") Ubuntu would be any easier to use than Windows. 
However, all things considered, "ordinary simple users" should continue to support Linux and hope for easier use. To be honest, without plenty of "mandatory" documentation and extensive forum help, it's almost impossible to easily get along with. I believe that there is no such thing as a good operating system.


This somehow "hidden" boot entry in Grub2 made me loose too much time ! Such stupid things could easily be avoided.

I don't see the point either keeping ALL previous kernels ! Why not remove older obsolete kernels automatically, instead of assuming the user would do such things himself (by letting him _discover_ by accident that this might perhaps be a thing to do ?

Instead of some installation interface which ASKS or suggests to the user which entries he wants to keep. !? Why must a third part company do the job for features, which should already have been included in GRUB2 ?!

Thanks for received assistance

---

