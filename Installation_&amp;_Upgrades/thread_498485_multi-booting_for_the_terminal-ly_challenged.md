---
title: "multi-booting for the terminal-ly challenged"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by fanderal on 2007-07-11
I'm new to Linux. After burning a dozen or so different distros to try
them out, I decided to partition my hard disk and install several of
them. I'm posting my experiences with multi-booting (minus the gory
details) and a few things I discovered.

Seems each distro has its own "menu.lst" file (/boot/grub/menu.lst)
which contains its own, individual boot instructions. When the
computer starts or restarts, this is the file which grub reads to know
how to boot the distro.

As each new distro is installed, it recognizes other Linux distros and
includes them in the newly created menu.lst file. This new menu.lst
file becomes the default for grub to read, and contains the boot
instructions for all other distros.

The problem, I discovered, is that each time a distro is installed, it
doesn't copy/paste the boot instructions for the other distros in its
menu.lst file. Rather, it rewrites them in its own format. And those
new instructions do not always allow other distros to boot properly.

The following stanzas are examples of how Kubuntu's boot instructions
were changed. When I first installed Kubuntu, it looked like this -

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel  /boot/vmlinuz-2.6.20-16-generic root=UUID=71056583-1994-41b6-b19a-5bdd6f9d96c5 ro quiet splash
inird           /boot/inird.img-2.6.20-16-generic
quiet
savedefault

After I installed PCLinuxOS, PCLinuxOS's menu.lst file became the
default. The boot instructions for Kubuntu were changed to this -

title         Kubuntu, kernel 2.6.20-16-generic (on /dev/hda5)
root         (hd0,4)
kernel     /boot/vmlinuz BOOT_IMAGE=Kubuntu_(on_/dev/hda5) root=/dev/hda5 ro
initrd      (hd0,4)/boot/initrd.img

After I installed PuppyLinux, Puppy's menu.lst file became the default
and the boot instructions for Kubuntu were changed to this -

title         Kubuntu, kernel 2.6.20-16-generic (on /dev/hda5)
root         (hd0,4)/boot/vmlinuz-2.6.20-16-generic
kernel      /boot/vmlinuz root=/dev/hda5 ro

After I installed Debian, it too changed all the previous boot
instructions. Three of the changes allowed Kubuntu to boot, but with
minor problems. Puppy's changes caused a kernel panic for Kubuntu.

Being terminal challenged and needing a gui, my workaround turned out
to be relatively easy. I opened each distro's menu.lst file and copied
the correct boot instructions. Since Debian was the last distro
installed and was the default menu.lst file, that's the file into
which I copy/pasted the correct boot instructions for the other
distros. After I did that, all four distros booted properly. Below are
the active stanzas in Debian's menu.lst file.

title          Kubuntu (hda5)
root          (hd0,4)
kernel      /boot/vmlinuz-2.6.20-16-generic root=UUID=71056583-1994-41b6-b19a-5bdd6f9d96c5 ro quiet splash
inird         /boot/inird.img-2.6.20-16-generic
quiet
savedefault

title          PCLinuxOS (hda6)
root         (hd0,5)
kernel      /boot/vmlinuz BOOT_IMAGE=PCLinuxOS root=/dev/hda6 acpi=on
resume=/dev/hda9 splash=silent vga=788
initrd       (hd0,5)/boot/initrd-2.6.18.8tex5.img
boot

title          PuppyLinux (hda7)
root          (hd0,6)
kernel       /boot/vmlinuz root=/dev/hda7 ro vga=normal

title          Debian (hda8 )
root          (hd0,7)
kernel        /boot/vmlinuz-2.6.18-4-686 root=/dev/hda8 ro
initrd         /boot/initrd.img-2.6.18-4-686

title           Windows XP
root           (hd0,0)
savedefault
makeactive
chainloader  +1


I have a question with muli-booting, but first I'll clarify. I wrote
that Debian's menu.lst file is the default file for grub. What I mean
is, any changes to grub (which distros boot, in what order, the
default distro, etc) can only be made in Debian's menu.lst file. I can
make those same changes in Kubuntu's menu.lst file, but it has no
effect on grub.

Question: How do I make Kubuntu's menu.lst the default file for grub
to read, rather than Debian's menu.lst?

I know if I reinstall Kubuntu, Kubuntu's menu.lst file will once again
become the default, but I'd prefer a simpler method. I've tried
reinstalling grub from within Kubuntu, and (in Debian's menu.lst file)
changing grub's default drive number, groot, savedefault and several
others, as well as placing just the Kubuntu stanza inside the
automagic kernels list, but no joy. I'm thinking the grub command line
is where I need to do the edit, but which command will do it?

Any help appreciated!

---

### Post by longlegs on 2007-07-12
Hi !
I'm new to Linux but I can give a little info. When you install a distroX, it writes it's menu.lst , then modifies the MBR (first sector of boot drive) so that distroX's loader is called. When you install distroZ, the MBR is modified so distroZ loader is called. 
To change which loader is called, just modify the MBR. Sounds easy, and probably is if you know all the commands and option switches to use in terminal. 
There is a way to copy the PBR (partition boot record) to a file in what would be the C: drive in windows.The MBR calls a loader that displays a menu of OS's to boot. On selecting one, the loader calls the PBR for that OS, which then boots the desired OS.
This CAN, if you already have windows installed, allow you to use NTLdr and boot.ini to do your multibooting, without affecting the windows boot at all. If you choose this method, install windows first and DO NOT modify the MBR after installing other OS's. Instead, modify boot.ini to add the other OS's.

Good luck!
longlegs

---

### Post by Herman on 2007-07-12
Hello fanderal,
> I'm new to Linux but I can give a little info. When you install a distroX, it writes it's menu.lst , then modifies the MBR **[COLOR=Red](first sector of boot drive)[/COLOR]** so that distroX's loader is called. When you install distroZ, the MBR is modified so distroZ loader is called. 
To change which loader is called, just modify the MBR. Sounds easy, and probably is if you know all the commands and option switches to use in terminal. That's right. longlegs, you did an excellent job explaining that, here are the terminal commands you can use,  [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD, and  [A Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

Actually, you don't even need to do that. It doesn't matter at all which operating system's GRUB you're booting from. All you really need to do is replace the GRUB booting entries for the other operating systems not in th debian automagic kernels list with 'configfile' boot entries instead. Then your GRUB from the operating system that happens to be unstalled last will search for the file called /boot/grub/menu.lst and bring up the GRUB menu from whatever operting system you specified.
GRUB is able to do that because GRUB understands file systems. Here's how to set that up, illustrated, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards, Herman

EDIT: > the MBR **[COLOR=Red](first sector of boot drive)[/COLOR]** Ah, not quite right, the MBR is situated in sector number 0, which is the first sector of the hard disk.
The first sector of the first partitions is sector number 63. 
The MBR is not part of the Windows file system. 
Neither GRUB nor Ubuntu write anything to the Windows 'boot' drive at all.
If you try out the command 'sudo fdisk -lu', you will see that no partition begins until sector 63. If one does then your disk partition has a bad problem.```
sudo fdisk -lu
```
:) Regards, Herman :)

---

### Post by fanderal on 2007-07-14
Thanks guys, I figured there was a way. Since I made the first post, I changed the distros to mostly Kubuntu as I keep coming back to it. The full version is on hda5 and I use the other two to experiment (eg kde-base only, etc). The last one I installed is on hda6, so that's the default menu.lst file. Here's the new lineup -

title   Kubuntu (16-generic on hda5)
root   (hd0,4)
kernel  /boot/vmlinuz-2.6.20-16-generic root=UUID=71056583-1994-41b6-b19a-5bdd6f9d96c5 ro quiet splash
initrd  /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title   Kubuntu (16-generic on hda6)
root   (hd0,5)
kernel   /boot/vmlinuz-2.6.20-16-generic root=UUID=2202d9c8-effc-417a-b9778fd85d92a1bc ro quiet splash
initrd   /boot/initrd.img-2.6.20-16-generic
quiet

title   Kubuntu (16-generic on hda7)
root   (hd0,6)
kernel   /boot/vmlinuz--2.6.20-16-generic root=UUID=320e8d9e-d9e8-4caf-8c2a-c7343a355481 ro quiet splash
initrd   /boot/initrd.img-2.6.20-16-generic
quiet

title   Debian (hda8 )
root   (hd0,7)
kernel   /boot/vmlinuz-2.6.18-4-686 root=/dev/hda8 ro
initrd   /boot/initrd.img-2.6.18-4-686

title   Windows XP
root   (hd0,0)
savedefault
makeactive
chainloader +1

Hi Longlegs. You wrote, "...just modify the MBR. Sounds easy, and probably is if you know all the commands and options..." LOL, I don't, and that's my problem. Just as big a problem is sitting in front of the grub help screen with the list of commands, investigating each, trying to figure out the purpose and the context for which they're used. I'd like to tell you your last two paragraphs solved it for me because I understand what you wrote, but I haven't a clue as to which tool to pull out of the bag to do it. Its one of those, 'I don't know what you think I know' though... I do appreciate your response.

Hi Herman. I visited (and bookmarked) your 'Multiple Booting' page and went with the 'configfile boot entry.' I put hda6's original menu.lst file in a blank folder inside the grub folder and then created a new menu.lst file with just this in the active portion -

title        Kubuntu Feisty
configfile   (hd0,4)/boot/grub/menu.lst

When I rebooted, the screen showed one choice - Kubuntu Feisty. When I hit return, I got a duplicate screen except it now has five choices - three Kubuntu's, Debian and WinXP. Since I'd edited the titles in hda5 as they are above, I knew grub was reading hda5's menu.lst file. 

I didn't realize it wasn't a permanent configuration, but I found out soon enough. Hda6's menu.lst is still the default file, and, as you wrote, "The configfile command will tell GRUB to find the other Linux's menu.lst." I set the timeout to 0 so the first screen just flicks by. 

Thank You!

---

