---
title: "Install GRUB in MBR First then install and link to Ubuntu and Win 98, xp, and 2003"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by jamiekao526 on 2005-08-23
Well I've been thinking for a while after my dad assigned me the job of reformatting his computer because he doesn't know alot about computers and he knows that i like to experiment with them.


Anyways this is what he wants on a single hard drive of 80 gigs
- Ubuntu Linux for downloading files and searching the internet <-- only one with internet connection since 99% of the viruses and bugs only attack windows.
- Windows 2003 Server for microsoft visual studio and stuff like that
- Windows XP for other uses
- Windows 98 for old programs that don't support xp or higher
- A partition to share files
- All OSes can only view the partition it is installed on and the shared partition.
- No uses of 3rd party multi-boot programs (they cost money to buy)


I'm using an old hard drive of 8 gigs for test and I decided that the easiest way that avoid the most confusion to this problem is to install the MBR fist then the OSes after. So I plan to installing the grub boot loader Only in the MBR First then set it up so that after the computer boots, it goes into grub and i'll have the option of booting from the cd (for 2003 and ubuntu) and booting from the floppy(for xp and 98 ) and preceed with the setup. After the setup, I can add the options of ubuntu, win98, winxp and win2003.

However i have no idea on how grub installs and some ideas on how it works (as i am a newbie), and i know that NTLDR overwrites the MBR and some programs complains that it must be installed in the main partition.

I know that grub have functions like map and hide and unhide that might be useful but like i said i don't know how to set it up.


can someone lend me a hand to this problem?

---

### Post by nad on 2005-08-23
The first problem is partitioning. x86 Architecture allows only 4 primary partitions per hard drive. I would do any partitioning first using the live CD of your choice or even tomsrtbt (huh?).

I believe each of the MS OS's will require one each. That leaves the fourth partition with at least 3 logical partitions, share, ubuntu and linux swap. On top of this is a hidden partition that XP uses for something (maybe 2003 also) that may cause problems. Let us know.

Try starting with 98 ( 3 - 5GB ), then XP ( 5 - 10GB ), and 2003 (5 - 10GB). XP and 2003 should recognize the previous installations and include them in the boot menu.

Now you've got about a 40GB share partition, then an ubuntu partition ( 5 - 10GB ), some free space for whatever (who knows, you may need it) and swap space ( 250 - 750MB ).

Grub should also recognize all the previous installations and it may end up being a no-brainer. However, there are several threads here discussing using grub with all the above.

---

### Post by Chris Cromer on 2005-08-23
Please note that when you install windows it will delete grub from the MBR and replace it with it's own boot program. So it's best to install windows before you install linux and the grub boot loader.

---

### Post by jamiekao526 on 2005-08-24
I agree that the partitioning will be first so i'm going to do that tomorow or this afternoon seeing that it is 0:35am here now and i need sleep.

hey i did some search on internet and it seems like I can install bootloader onto a floppy and i can trick the OS into believing that the partition it is on is the primary one!
maybe i can use the live cd to partition hard drive like this

1 - primary - bootloader (hidden) (hd1,0)
2 - Shared Drive (hd1,1)
3 - Extended
------Win98 (hd1,2)
------WinXP (hd1,3)
------Win2003 (hd1,4)
4 - Extended
------Ubuntu (hd1,5)
------Linux Swap (hd1,6)

then install grub onto floppy stage 1 and stage2
dd if=stage1 of=/dev/fd0 bs=512 count=1
dd if=stage2 of=/dev/fd0 bs=512 seek=1
or
/sbin/grub-install /dev/fd0


since the website that I was looking in said this:
---
The "map" lines under the Windows 98 section are essential for getting your installation to work. These are the magical lines that trick Windows into believing that it's installed on the first partition of the first disk. If you don't map the Windows partition to (hd0,0), Windows will destroy your partition table and you won't be able to boot anything. (source 3)
---

so i'll edit the menu config file so it says

----------------------------------------------------------
default=0
timeout=10
splashimage=(hd1,0)/grub/splash.xpm.gz

title Boot From CD
chainloader (hd0)+1

title Boot From Floppy
chainloader (fd0)+1

title Win98 Install
hide (hd1)
unhide (hd1,2)
map (hd1,0) (hd1,2)
chainloader (fd0)+1

title WinXP Install
hide (hd1)
unhide (hd1,3)
map (hd1,0) (hd1,3)
chainloader (fd0)+1

title Win2003 Install
hide (hd1)
unhide (hd1,4)
map (hd1,0) (hd1,4)
chainloader (hd0)+1

title Ubuntu Install
hide (hd1)
unhide (hd1,4)
unhide (hd1,5)
map (hd1,0) (hd1,4)
map (hd1,1) (hd1,5)
chainloader (hd0)+1
----------------------------------------------------------

then After I do the install the System, I would change the menu to

----------------------------------------------------------
default=0
timeout=10
splashimage=(hd1,0)/grub/splash.xpm.gz

title Ubuntu
hide (hd1)
unhide (hd1,4)
unhide (hd1,5)
map (hd1,0) (hd1,4)
map (hd1,1) (hd1,5)
root (hd1,0)
kernel /vmlinuz-2.4.18-11 ro root=/dev/hdb1
initrd /initrd-2.4.18-11.img


title Win2003
hide (hd1)
unhide (hd1,4)
unhide (hd1,1)
map (hd1,0) (hd1,4)
rootnoverify (hd1,0)
chainloader +1

title WinXP
hide (hd1)
unhide (hd1,3)
unhide (hd1,1)
map (hd1,0) (hd1,3)
rootnoverify (hd1,0)
chainloader +1

title Win98
hide (hd1)
unhide (hd1,2)
unhide (hd1,1)
map (hd1,0) (hd1,2)
rootnoverify (hd1,0)
chainloader +1

title Boot From CD
chainloader (hd0)+1

title Boot From Floppy
chainloader (fd0)+1
----------------------------------------------------------

Then test the system then copy the grub boot loader into hd0,0 which I will need help on since i'm pretty sure the floppy won't contain grub-install.

do you think that this will work? i'm not really familier with the hd numbers and the options so any adjustments are welcome.

Do i need rootnoverify or makeactive or boot in the options?


------sources-------
[1](http://www.linuxgazette.com/issue64/kohli.html) 
[2](http://www.icculus.org/~lucasw/Linux/Linux%20and%20XP%20Bootloading.html) 
[3](http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html)

---

