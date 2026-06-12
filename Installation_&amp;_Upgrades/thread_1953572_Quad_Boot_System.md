---
title: "Quad Boot System"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by daniel4230877 on 2012-04-06
Hi, I have a 1 TB hard drive and i would like to quadboot Windows XP x64 edition, eComStation 2.0, Ubuntu, and Openbsd. How is this possible? Can it be done? Thanks.

---

### Post by CottonCandy on 2012-04-07
[SIZE=1]Here is what I know about multi-booting.  [/SIZE]
 
[LIST]
[*][SIZE=1]Windows should be installed first on a primary partition.     Linux OSs can be installed on logical (extended) partitions.      [/SIZE]
[/LIST]
  
[LIST]
[*][SIZE=1]Each OS **and it's boot loader** should be installed on a     separate partition.[/SIZE]
[/LIST]
 [SIZE=1]**For Ubuntu:** When you get to the install screen where it asks you if you want to erase everything and install Ubuntu, or install Ubuntu along side existing the OS(s), or do something else (it may say configure partitions manually or something like that), choose that last option. This will bring up a screen where you can add/delete/change partitions. When you add the Ubuntu partition use Ext4 file system with a mount point of /. Then, before you click Install, change the location for boot loader installation from the default to the partition you are installing Ubuntu on. (The default is likely something like /dev/sda and you want to change it to something like /dev/sda# where # is the partition where you installed Ubuntu.)  

[/SIZE]  [SIZE=1]Other OSes should have a similar option during their install process. [/SIZE]
[SIZE=1]
NOTE: This method will require you to add a Linux entry to the Windows boot screen using something like [FONT=Liberation Serif, serif][EasyBCD]("http://neosmart.net/EasyBCD/")[/FONT][FONT=Liberation Serif, serif]. This will[/FONT]give you two boot screens, one where you choose Windows or Linux, and then when you choose Linux it will bring up the GRUB boot menu where you choose which OS to boot. If you want GRUB to be in charge of the boot process I think you need to install GRUB to the MBR so when you install the first linux OS,  don't change the default for where to install the boot loader. Only change it for the OSs you install after that.  [/SIZE]

 [SIZE=1]And I think once you are done installing everything you need to run sudo update-grub or sudo update-grub2 in order for GRUB to list all the OSs in the boot menu.  [/SIZE]
 [SIZE=1]
Here is a how to that may be helpful: [/SIZE][How to triple-boot Fedora 15, Ubuntu 11.04 and Windows 7]("http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/")                                                

[LIST]
[*][SIZE=1]The order in which you install the OSs can make a big difference.      [/SIZE]
[/LIST]
 [SIZE=1]Unfortunately I don't know what order will work for you. All i know is it's recommended that Windows is installed first. And when installing more than one version of an OS you should always install in order. (XP then Vista then 7 for example. Or Ubuntu 11.04 then 11.10 then 12.04.)[/SIZE]
 [SIZE=1]I hope this helps. Good luck! :)  [/SIZE]

---

### Post by oldfred on 2012-04-07
I think someone posted that OpenBSD does not play well with other installs and is best installed on a separate drive. I have not tried it, so you may want to research that a bit more. 

Also not familar with eComStation. What boot loader does it use? Back with OS/2, it used to have a utility to rewrite MBR to boot Windows and then in Windows to rewrite MBR to boot OS/2.

Multiple Linux & Windows will work without much issue, if you plan partitions in advance. With grub2 and Ubuntu you do not have to have other boot loaders for most systems as its os-prober finds those and adds them to the boot menu.

---

