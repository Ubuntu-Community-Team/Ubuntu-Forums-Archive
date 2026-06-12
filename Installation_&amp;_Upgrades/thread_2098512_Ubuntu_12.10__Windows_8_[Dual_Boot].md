---
title: "Ubuntu 12.10 / Windows 8 [Dual Boot]"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by Serson_Person on 2012-12-26
Hey,

I used Wubi to install Ubuntu 12.10 alongside Windows 8, but when the computer loads and I choose Ubuntu it comes up with and error and I have to restart.

Any ideas?

---

### Post by ramaswamyps on 2012-12-26
windows 8 has a fast restart setup wen shuts down which gives problems to start any other windows linux etc.
boot widows 8 and set it to do shutdown without fast restart.
if you are in doubt dont do anything to save windows 8.
google for windows 8 shutdown problems

---

### Post by oldfred on 2012-12-26
Another thread posted that wubi does not work with gpt partitions. And with Windows 8 pre-installed you have gpt partitioning. 

You can install to a flash drive or create partitions and install to those partitions. The new 64bit version of Ubuntu 12.10 will install to secure boot systems. But becomes more difficult to uninstall if you decide you do not like Ubuntu.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by Serson_Person on 2012-12-26
Thanks for the advice guys, I've been trying what's said so far, up until now.  I don't have a USB drive with me a the moment unfortunately, I've burn the image to disc though, will that still work with the same instructions you gave?

---

### Post by oldfred on 2012-12-26
Not sure.

I think someone posted they had issues. Best just to see if you can boot in UEFI mode from DVD.

If not you literally can install in BIOS/legacy/CSM mode. Then you can use Boot-Repair from your liveDVD to convert to UEFI boot. Not the best way to install but possible as we have seen many users install incorrectly and Boot-Repair fixes it. You will need Boot-Repair anyway to fix a bug in grub as it does not create correct chain boot entries for Windows.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


Some threads on users who managed to install.
       
 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by Serson_Person on 2012-12-27
Thanks oldfred.  I'm going to download the 64-Bit Version and try the link to the Asus product that worked, if not I'll try some of the other links and keep at it.  :)

I will mark this as solved if I do get it working.  Thanks for the help!

---

### Post by Serson_Person on 2012-12-27
Screw it!  Lol, Windows isn't worth this hassle.

I'm just going to put a fresh Ubuntu on it, then Wine should work wonders for what I'm planning on using.  Easily.  Now, should I stick with the 32-Bit Version or use the 64-Bit version?  I'll probably throw some other Linux's later on, perhaps some other Ubuntu versions, not sure yet, for now this.

If a mod wants to delete this post they can, or should I mark it solved although I gave up on what I was originally intending?

I guess in a way it's solved in the best way possible... ousting windows :P

---

### Post by oldfred on 2012-12-27
I changed to 64bit with 9.10 or 3 years ago on both my desktop & laptop. My laptop does not really have enough RAM with only 1.5GB but it works, but needs swap sometimes.

If you have 3GB of RAM or more and a 64bit system, you really should install 64 bit. We are down to one or two applications that may not work and those are not commonly used as far as I know.

---

