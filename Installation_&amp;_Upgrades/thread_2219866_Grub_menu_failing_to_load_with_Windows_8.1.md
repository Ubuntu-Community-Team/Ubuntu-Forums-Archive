---
title: "Grub menu failing to load with Windows 8.1"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by bignoisetransmissi on 2014-04-25
Hello, I am somewhat of a newbie to Linux systems, I have a HP Pavillion, Intel Core i7 2600 CPU 3.4GHz.

After doing a clean fresh install of dual booting Windows 8.1 on one partition (300GB) then shortly after Ubuntu 14.04 on seperate partition (651.2GB) while following the video via this link ([https://www.youtube.com/watch?v=MWYjZ2j7HrE](https://www.youtube.com/watch?v=MWYjZ2j7HrE)) After my first and many attempts when booting up from the Hard Drive, it goes straight to loading up Ubuntu passing the Grub menu with Windows 8.1 (Strangly Windows had lost it dominance of the PC) so currently I am unable to load up Windows. Any help here would be fully appricaited! 

Ryan

---

### Post by oldfred on 2014-04-26
Is one system in UEFI mode and the other in BIOS boot mode?

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

### Post by jdhamric on 2014-04-26
I'm having a similar problem. Upgraded from 13.10 to 14.04 via Update Manager, rebooted and it went directly to Windows 8.1; no GRUB menu. Checked all the UEFI settings in Windows and BIOS and they all seem OK.  


Any solutions on how to solve this?

Addendum: Found this command (run in a windows Admin command prompt): 
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

which worked!

So now I can boot to Ubuntu or Windows. 

Now I have missing panel indicators, but thats a different thread....

---

### Post by bignoisetransmissi on 2014-04-27
Hello, yes since this post I have found a way around this! **TAKE NOTE PEOPLE**

[B]Boot-Repair is a simple tool to  repair frequent boot issues you may encounter in Ubuntu like when you  can't boot Ubuntu after installing Windows or another Linux  distribution, 
or when you can't boot Windows after installing Ubuntu, or  when GRUB is not displayed anymore, some upgrade breaks GRUB, etc. 
[/B]
[B]
Boot-Repair  lets you fix these issues with a simple click, which (generally  reinstalls GRUB and) restores access to the operating systems you had  installed before the issue.
[/B]
Following the link here >>[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)<< you can either burn this "Boot-Repair" onto DVD/USB (Which I originally did but had no luck in fixing but do try yourself first I hear people have various results)
Failing that, you can open this software within Ubuntu itself. But if you can only boot into Windows only, I would burn Ubuntu on to DVD/USB then open it up that way. (Description below on how to load on Ubuntu) 

I have no guarantee this would work for all machines but it certainly did for me, (within Ubuntu it worked better anyway) but certainly seems more promising and easiest out of all solutions.
Link below will give you more information on Boot-Repair and the intructions on getting it working!

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Goodluck! Hope this workout well for you.

---

