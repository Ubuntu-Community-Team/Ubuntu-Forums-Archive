---
title: "Rough outline of USB external drive install ... is this accurate???"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2005-10-20
Hi folks,

After reading a number of posts from people generous enough to share their experiences, I was wondering if this is the basic procedure to successfully install Ubuntu 5.10 on an external USB drive?

I am a definite beginner in the Ubuntu OS world (and Linux in general), so this is my attempt to understand the installation process (and do this correctly). Please feel free to comment on any of the following sections below to correct me or help me in my understanding of the install process. (You just might help someone else in here too!)



MY UNDERSTANDING OF THE USB INSTALL PROCEDURE
(I am assuming the use of the INSTALL CD and not the LIVE CD for installation purposes) 

(1) When installing the OS, type 'expert' at the first prompt and then choose the correct drive where Ubuntu is to be installed (this should be an sda-type drive ... NOT an hda-type drive). One post says the reason for 'expert' mode is to have access to a shell window before rebooting ... supposedly to perform the edits below. (Is this why 'expert' install mode is used?)

(2) Next, complete the partitioning section of the install by letting the install program setup the sda drive (creating an ext3 and swap partition on it)

(3) Let the install program load its required setup files to the disk and finish it's pre-reboot phase of the install. It should then load a shell window.

(4) Edit the '/etc/mkinitramfs/modules' file to add the lines that will eventually startup usb support capabilities before Ubuntu tries to run (But my understanding is that even though you edit this file now ... USB support is not created in the initrd.img file yet?)

The following lines are what get added to this 'modules' file (for support of almost any usb drive ???) ...

sd_mod
ehci_hcd
uhci_hcd
ohci_hcd
usb-storage

(5) Next, edit the '/target/etc/mkinitramfs/initramfs.conf' file to add a line (at the top) that delays the boot process by so many seconds (WAIT=15) so USB support files can get loaded before Ubuntu tries to run at bootup. (According to one post, this WAIT command is not in the initramfs.conf manual) I believe earlier versions of Ubuntu used a DELAY parameter for this purpose (but this line was placed in another file called mkinitrd.conf ???)

(6) To prepare for the next step, we have to run a little command in the terminal window ... 'ls /lib/modules' (ls is short for list?) to have the system tell us what our Ubuntu kernel version is ( Mine was something like 2.6.12-9-386 for the 5.10 Ubuntu version)

(7) After editing the two files above (steps 4 and 5), we recreate the initrd.img file to include these USB changes by running these commands from the terminal window. (this will ovewrite the kernel version in /lib/modules ???)

chroot /target
mount -tproc none /proc
mkinitramfs -o /boot/initrd.img-<kernel version from step 6> /lib/modules/<kernel version from step 6>

(8) Finally we load GRUB on the sda drive and NOT the hda drive. We then edit the menu.lst file so grub will boot up Ubuntu correctly .(The file to edit grub setting is '/target/boot/grub/menu.lst ???)

(9) Exit out of the installer program and reboot ... hope it works.

THAT IS MY UNDERSTANDING OF THE PROCESS AFTER READING LOTS OF POSTS

And, I am sure my understanding is probably wrong on a number of things. What sections do I have incorrect or out of order on this outline. I have just recently purchased a small 40GB external drive and would really like to get Ubuntu 5.10 on it.

Any help would be greatly appreciated.


_____
DAVE

---

### Post by replacement on 2005-10-20
hi, Dave

i confirm this procedure worked for me. i used to use DELAY in initramfs.conf and only ehci_hcd in modules.conf, it partially worked for kernel 2.6.12-8 (had to keep the install CD in the drive bay, otherwise it will say "i can't find /dev/sda2), and didn't work for kernel 2.6.12-9 at all. now thanks for your post and LOTS of reading, it now even works for 2.6.12-9 fully, meaning i don't need the CD any more. it seems the author of initramfs-tools works(ed) for ubuntu.com. but heck, where is the documentation of initramfs.conf!

---

### Post by pbrockway2 on 2005-10-22
Hi Dave,

Thanks for posting this.

I am in the middle of installing 5.10 and, while following the
notes I made about installing to USB with 5.04, I noticed that
nothing was where it should have been.  I was just about to
start crying...

However the steps you described sucessfully allowed a reboot
to take place and the installation is finishing as I write.

Cheers,

Peter

---

### Post by netztier on 2005-10-24
Dave, this is a VERY FINE example of a "howto" document, much appreciated!

[QUOTE=DaBruGo]Hi folks,

(1) When installing the OS, type 'expert' at the first prompt and then choose the correct drive where Ubuntu is to be installed (this should be an sda-type drive ... NOT an hda-type drive). One post says the reason for 'expert' mode is to have access to a shell window before rebooting ... supposedly to perform the edits below. (Is this why 'expert' install mode is used?)
[/QUOTE]

Tonight, I had a go at it (HP nc6000, 1.8 GHz Pentium M, 512MByte RAM, ATI Radeon-something with a 1400x1050 screen, and an external USB2 disk enclosure). For the installation process, I removed the internal HD to make absolutely sure that it could not be touched in any way.

Using "expert"  - and setting a root password during setup (because i was asked to) - somehow broke Ubuntu's sudo way of dealing with the root account - and I wasn't able to recover it from that situation [no, "sudo passwd -l root" didn't fix it].

So I started over and let a normal install process run, and, right after the CD was ejected,  I switched to a second console (Alt-F2) and did the modifications to '/target/etc/mkinitramfs/modules' and '/target/etc/mkinitramfs/initramfs.conf', as described in steps (4) and (5). After that, I chrooted into /target and built the a new initrd.img, as described in step (7). Then I went back to the install console (Alt-F1), went "back" one step to the installation menu, and repeated the step of installing grub. 

That was it - reboot and the system started, finished installation and GDM was there, and everything I had hoped for: Audio, Wireless, Frequency Scaling and...
hey. I didn't even use one of the special "HP Laptop" versions of Ubuntu. At first, I had intended to, and tonight  just plain forgot that they existed. 

I did not have to modify any grub menus, since I configured the boot sequence in BIOS to boot from USB before booting from Harddisk - and that's it:
Plug the USB  drive in: Ubuntu
leave it away: Windoze.

Thanks a bunch!

Marc

---

### Post by DaBruGo on 2005-10-24
Hi Folks,

Since my first post on this topic a few days ago, I have learned quite a bunch about the UBUNTU install process ... and managed to successfully load UBUNTU a number of times on my external USB drive. (Call me crazy, but I wanted to run the install a few times to make sure that what I was doing would work every time.)

I would like to share my updated outline with others who may also be struggling with this process.

BACKGROUND: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a Seagate 40GB Portable External Hard Drive that was purchased at Walmart for around $120

Here is what I now do to successfully load UBUNTU v5.10 on this EXTERNAL USB DRIVE ...

(1) Instead of using "expert" mode to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).

(2) During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning ... which sets up an ext2 or ext3 partition and a swap partition for you.)

NOTE: Look for the line during the partitioning phase that might say ...
erase entire disk SCSI (0,0,0) (sda)

BE VERY CAREFUL on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!

Once again ... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!

(3) When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.

The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the SDA (external USB) drive where we want to install the GRUB bootloader.
(Mine was /dev/sda)

NOTE: at this point, the install program loads some stuff and ejects the CD ... wanting you to do a reboot.

(4) BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode)

Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.

(5) When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your drive from the list.
(Mine was mount /dev/discs/disc1/part1)

(6) When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.

(7) Type in these lines before we start editing out files ...

mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>

NOTE: I used vim to edit the files. It is weird to use at first until you learn what a few keys do in it ... The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ... And hitting : x (colon x) saves the file and exits out of vim.

( 8 ) Run vim to edit the modules file to make sure USB support is added/loaded during UBUNTU startup ...

vim /etc/mkinitramfs/modules <enter>

Right below the last line of text, enter these lines ...

ehci-hcd
usb-storage
scsi_mod
sd_mod

Be sure to save the file changes (using : x)

(9) Run vim to edit the initramfs.conf file to make sure enough time elapses for USB support to load before UBUNTU gets running ...

vim /etc/mkinitramfs/initramfs.conf

At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up ...

WAIT=12 (in all caps here, not sure if necessary though)

Be sure to save the file changes (using : x)

NOTE: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.

(10) Recompile (recreate) the initrd.img file to include USB support from these edited files ...

mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386

(11) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst

Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 

NOTE: You may want to change the root line for the Windows XP section to (hd1,0) just in case you want to boot XP from this menu.

Be sure to save the file changes (using : x)

(12) Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.

BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS

(13) After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU


That's the process I've successfully used to install UBUNTU v5.10 on an external USB drive. I hope this helps anyone whose been wrestling with this process. Let me know if it works out for you.

DAVE

---

### Post by DaBruGo on 2005-10-24
Hi Folks,

Some people have had problems getting Windows XP to boot from GRUB.

By putting these lines in the menu.lst file (/boot/grub/menu.lst) that GRUB uses, I was able to get XP to boot properly from the GRUB menu ...

title Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
chainloader +1

NOTE: I installed GRUB (and UBUNTU) to my external USB hard drive during installation and NOT to my internal hard drive (where XP is loaded).

Hope this helps,
DAVE

---

### Post by DaBruGo on 2005-11-17
SUCCESS !!!

I finally got everything running right. I started a new thread with complete setup instructions at ...

[www.ubuntuforums.org/showthread.php?t=80811](www.ubuntuforums.org/showthread.php?t=80811)



DAVE

---

