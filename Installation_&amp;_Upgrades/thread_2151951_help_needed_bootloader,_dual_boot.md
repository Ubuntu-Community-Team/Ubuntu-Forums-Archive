---
title: "help needed: bootloader, dual boot"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2013-06-06
SOLVED.
No thanks to anything obvious to even a novice like me. I read the GRUB2 manual/guide pdf, twice,  finally came up with the solution which was far from obvious. The key  is that[FONT=courier new] fdisk -l [/FONT]gives me e.g. [FONT=courier new]/dev/sda1[/FONT] as my primary active drive  and partition where my Windows7 resides, but that such mapping can often  (according to the Grub pdf manual guide) *not* correlate with drives  and partitions used in Grub. Wow. I was trying to configure Grub with [FONT=courier new]set root=(hd0,msdos1)[/FONT] but when I learned to use the *autocompletion*  feature of command line editing of the Grub menu during boot, I  discovered that to boot Windows7 I had to use [FONT=courier new]set root=(hd2,msdos1)[/FONT]   Go figure. Anyhow, I was finally able to get Grub working to now boot  into my ArtistX drive and also now to Windows7 on its own drive. Enough  dragon slaying quests for today. Needless to say, I know a whole lot  more about Grub2 today, a lot. In fact, to discover which hd*x* to use, I  even took advantage of the filename autocompletion feature of grub's  command line editing function, e.g. I would type: [FONT=courier new]set  root=(hd2,msdos1)/[/FONT] then use TAB to see all the possibilities of  filenames for booting which allowed me to discover that indeed hd2  contained Windows7 (/dev/sda1), not hd0 as one would have suspected.  Again, hd(x) where x is the drive number starting with 0, does not  always correlate with the /dev/sd(x) you get when using the fdisk  command in linux. Golden info I now know.

-------
I am no stranger to linux, in fact I have ArtistX (ubuntu based distro) installed on a drive, Windows 7 on a separate drive. My problem is that Grub2 can not boot to Windows 7 (boots into ArtistX/ubuntu just fine). I edited Grub, added a Windows entry, but the issue as I discovered is a problem/bug involving Grub2 (hereafter called 'grub') and Western Digital (green/ecosmart?) hard drives and sector sizes, etc; so, I am here asking for advice and opinion on a workaround, because tinkering with a bootloader can get a geek into big trouble with an unusable system if not done right. 

So here is my strategy (thoughts?)-- I switch (in the BIOS) the boot drive order from the drive with artistx/linux and grub on it to my Windows 7 x64 drive. Then I boot into Windows 7 as usual, install and use EasyBCD.exe to edit/use the Windows bootloader to create a dual boot system with Windows 7 and Linux. My understanding is that EasyBCD will edit (GUI interface) the Windows 7 boot config and EasyBCD will let me add a menu entry to trigger the grub on the drive with linux.

Another alternative but rather time consuming solution would be to reinstall linux and all that that involves to a drive other than the Western Digital drive that I installed linux onto. it does make me a bit nervous to have my dual boot management on the Windows 7 drive, as I am always skeptical on whether Windows will pull some funky maneuvers to eliminate the dual boot in the future; but I guess if that happened I could use the BIOS to boot into linux, back up my data, reinstall linux on a drive that plays nice with Grub, keep the bootloader as Grub at that time.

---

### Post by oldfred on 2013-06-06
Lets see details. You should be able to have grub in the Ubuntu drive and Windows boot loader in Windows drive and dual boot. A few older systems only booted from sda, but most should dual boot without issue.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

