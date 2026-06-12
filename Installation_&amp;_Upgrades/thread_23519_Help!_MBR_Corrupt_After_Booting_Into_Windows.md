---
title: "Help! MBR Corrupt After Booting Into Windows"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by bfisher on 2005-04-02
Forgive me if this thread is somewhere else - I searched but could not find anything.

I have been playing with the Hoary the last few days, and I have found a problem that I have never seen before. I have a 40 GB drive divided into a WinXP SP2 partition and my Hoary partition on a Dell Latitude D600. Hoary installs and runs great. The problem is that as long as I boot into Hoary, GRUB works flawlessly. Once I boot into Windows just once and shut down, on all future boots my laptop continually reboots before I am even presented with a GRUB menu screen. After the POST tests, I briefly see a line saying "GRUB loading stage1.5." As soon as that appears, the screen goes black and the laptop reboots. This process repeats endlessly.

Does anyone know why this happens? I can fix the problem using my WinXP CD and repairing the MBR, but of course I then I have to reinstall Hoary. Does WinXP SP2 mess wih the MBR on shutdown? Any help as to why booting into Windows breaks GRUB would be greatly appreciated!

---

### Post by seven on 2005-04-02
try to reinstall grub:
if you are on windows create a grub floppy disk - [http://www.dolda2000.com/~fredrik/grub.img](http://www.dolda2000.com/~fredrik/grub.img)
and write it with [http://www.dolda2000.com/~fredrik/rawrite.exe](http://www.dolda2000.com/~fredrik/rawrite.exe)
basiclly u'll need to boot from the floppy and write install(hdx,x) 
where x,x is your partition  \ disk's MBR

use this great guide for more instructions:
[http://www.linuxforums.org/tutorials/1/tutorial-19999.html](http://www.linuxforums.org/tutorials/1/tutorial-19999.html)

good luck

---

### Post by MetalMusicAddict on 2005-04-02
I wonder if changing the "Access Mode" of the drive to "LBA" in the BIOS of the laptop would change anything? Its 1 thing you need to do on a desktop if your dual-booting.

---

### Post by bfisher on 2005-04-04
Thanks for the suggestions, but neither solution was a go. Other Linux distros work fine (Fedora, VidaLinux, etc.), but I still have the problem with Ubuntu mentioned in my first post. I am going to reinstall Ubuntu once Hoary is final, and we'll see if the problem disappears. If there are any suggestions before them, fire away and I'll give it a shot!

---

### Post by bored2k on 2005-04-04
[QUOTE=bfisher]Thanks for the suggestions, but neither solution was a go. Other Linux distros work fine (Fedora, VidaLinux, etc.), but I still have the problem with Ubuntu mentioned in my first post. I am going to reinstall Ubuntu once Hoary is final, and we'll see if the problem disappears. If there are any suggestions before them, fire away and I'll give it a shot![/QUOTE]
 1a. Download mbrtool and clear your mbr .
1b. Be smart and download Hiren's Boot CD [homework1: find it, don't ask here] and use its tools to fix/repare MBR's/Systems. Then recreate grub from Ubuntu disc if necessary.

---

### Post by tetsuo29 on 2005-04-11
I had this same problem on my Latitude D800. I must have installed ubuntu about 6 times using various recipes I found in the forums. I fixed my mbr with tools from hiren's cd. I tried installing grub on the partition where I installed my root linux partition. I tried so many ways of setting up ubuntu. I was trying to preserve my existing Windows install. Everytime I booted to WinXP, it would destroy the mbr and cause the endless cycle of grub starting and then the machine just rebooting.

In the end, nothing worked and I just bit the bullet and erased all partitions, booted from the WinXP CD, created my FAT32 partition again, installed windows, booted from the ubuntu CD and installed ubuntu, told it to use all available space, and let it install grub on the mbr. Everything is happy and I'm successfully dual booting.

My current theory is that ubuntu didn't know how to install grub on the mbr after my previous distro (Suse 9.2 Pro) had done its thing with grub on the mbr. I'm sure someone more talented than me could have straightened things out without resorting to wiping all partitions and starting over, but it's working now and I've almost got both WinXP & Ubuntu set up like I like them.

---

### Post by jackymac on 2005-04-14
Having the exact same problem as the original poster.  Dual-booting WinXP SP2 and a fresh install of Hoary Final.  I was dual-booting the same windows install with Hoary-upgraded-from-Warty and didn't have any problems.  I've been fixing the endless reboot cycle by booting a Knoppix cd and then using grub to fix the mbr.  everyhting is fine after that until I boot into Windows again.

Can't afford to wipe Windows to fix this.  I filed a bug in the Ubuntu bugzilla ([Bug #9224](https://bugzilla.ubuntu.com/show_bug.cgi?id=9224)), so hopefully it'll ping the devs radar screen.  In the meantime, Knoppix is my friend...

BTW, instructions for manually setting up the MBR using grub can be found in the [gentoo handbook](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2).  Look at the "Alternative: Setting up GRUB using manual instructions" section.  Run grub as root from a Knoppix disk (or any livecd that has grub on it), and then follow the instructions on that page.  It'll save you from having to reinstall Ubuntu!

---

### Post by tetsuo29 on 2005-04-16
I figured it out! After wiping all partitions, installing WinXP on a FAT32 partition, and then installing Hoary and letting grub install on the mbr, I had reported that I was successfully dual booting. It only lasted 4 days. I booted today and I was caught in the endless grub starts to load, then the machine just reboots. Over and over.

Anyway, I couldn't stomach the thought of redoing the whole thing again and I didn't trust grub to be my bootloader anymore. Here's what I pieced together to fix things.

-Booted from the WinXP install cd into the Recovery Console
-Ran "fixmbr"
-Rebooted
-Now I could at least boot WinXP
-Burned an Ubuntu Live CD (I wish I could have figured out how to boot from my ubuntu paritition on my hard drive from the install CD, is this possible?)
-Booted from it
-Mounted my ubuntu partition and ran grub from it (some articles I found said to run grub from the Live CD, but I couldn't find grub on the Live CD)
-used the interactive grub program to reinstall grub to my ubuntu partition, not to the mbr
-mounted my fat 32 partition
-used the dd command to write the first sector of my ubuntu partition as a .bin file on my c: drive
-rebooted from the hard drive to windows
-edited my boot.ini file to include an option to run c:\ubuntu.bin from the ntbootloader menu
-rebooted, got the ntbootloader menu, selected the option for ubuntu

It worked!

In case you need some more specifics on some of that:

How I mounted my ubuntu partition when I was booted from the live CD:
-fdisk -l (to see which /dev/hd## my ubuntu partition is)
-mkdir hdl (need a directory as a mount point)
-mount /dev/hda2 ./hdl

How I ran grub once I had mounted my ubuntu partition:
(took these steps from [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html))
-cd hdl
-./sbin/grub
(you'll then be at the interactive grub prompt)
-find /boot/grub/stage1 (i got back "(hd0,1)", this is my ubuntu boot partition)
-root (hd0,1)
-setup(hd0,1)
-quit

how i mounted my fat32 partition:
-cd (back to root's home dir)
-mkdir c (need a folder to mount to)
-mount -t vfat /dev/hda1 /root/c/ (use "fdisk -l" if you're not sure where your fat partition is)

how i wrote the first sector of my ubuntu partition to drive c:
(this is from [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo))
-dd if=/dev/hda2 of=/root/c/ubuntu.bin bs=512 count=1

how i edited my boot.ini:
(again from [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo))
-rebooted
-removed the Live CD
-now in windows
-right cicked on My Computer
-chose Properties
-went to the Advanced tab? (I'm not in windows right now, so I'm going from memory here)
-clicked the Startup Options button, this should get you into the boot.ini file
-added: C:\ubuntu.bin="Ubuntu Linux 5.04 'Hoary Hedgehog'"
-closed the file and answered yes to save it
-rebooted and chose "Ubuntu Linux 5.04 'Hoary Hedgehog'" from the menu

My system is now dual booting and since the MBR was written by Windows and it is using the NT boot loader, I am optimistic that things will continue to work properly.

---

