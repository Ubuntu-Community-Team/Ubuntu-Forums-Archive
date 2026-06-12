---
title: "Problem with booting GRUB and device.map"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by triwave on 2007-05-25
Hi,

I am having trouble for 1 week now that I can't solve :confused: so hoping a boot/grub expert can provide some tips or troubleshooting advive.

I have a dual boot machine with WinXP and PCLinuxOS on it. 2 drives -> WinXP on hd0 and PCLOS on hd1. Windows MBR remains on hd0 and PCLOS was installed to hd1. My BIOS boot screen gives a choice which drive to boot so this worked pretty well. derfault is hd0 so if the kids boot it goes to Windows ... if you change to drive 1 it loads grub. So far so good.

I made additional partitions on hd1 to install ubuntu7.04 and the install went OK but nothing would boot. Thanks to previous problems I became pretty good at using GRUB and poked around a bit. I was able to boot both PCLOS and ubuntu from the grub command line.

To do it I had to mess with the grub drive labels because for some reason when you check the geometry the hd0 drive shows up as sdb and the hd1 drive as sda. This messes up the whole menu.lst file which was produced with hd0 -> sda and hd1 -> sdb

I check device.map and it was backwards. So I fixed it.

But I reboot and even with device.map listing the correct relationship grub doesn't work. (still get file not found errors). Go to command line and sure enough the drives are backwards again.

Help!

My file system is OK but I'd sure like GRUB to work properly and for the life of me I can't figure out why the drives suddenly reversed after ubuntu was installed. How can I get things back in order? If I manually edit menu.lst how do I know next boot the drives stay in the reversed order? I have booted many times before and they have always been been consistent.

Additionally, if I boot into any live CD the order is always correct. If I boot onto the 2nd hd then when it gets to grub menu it's reversed. Where does that map come from??


[COLOR="Red"]My drive details:[/COLOR]

* using fdisk -l I get:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23189   186265611    7  HPFS/NTFS [COLOR="DarkOrange"]*this is windows[/COLOR]
/dev/sda2           23191       24321     9084757+   c  W95 FAT32 (LBA) [COLOR="DarkOrange"]* this is a windows restore partition[/COLOR]

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10226    82140313+   7  HPFS/NTFS [COLOR="DarkOrange"]* this is windows file storage area[/COLOR]
/dev/sdb2   *       10227       11442     9767520   83  Linux [COLOR="DarkOrange"]* this is root for PCLOS[/COLOR]
/dev/sdb3           11443       24321   103450567+   5  Extended
/dev/sdb5           24042       24321     2249100   82  Linux swap / Solaris [COLOR="DarkOrange"]* PCLOS swap area[/COLOR]
/dev/sdb6           17926       24041    49126707   83  Linux [COLOR="DarkOrange"]* /home [common to both linux systems][/COLOR]
/dev/sdb7           11443       12092     5221062   83  Linux [COLOR="DarkOrange"]* this is root for ubuntu[/COLOR]
/dev/sdb8           12093       12359     2144646   82  Linux swap / Solaris [COLOR="DarkOrange"]* ubuntu swap area[/COLOR]

---

### Post by confused57 on 2007-05-25
Since you boot your different drives using bios, which designates your Window's drive as hd0 and your Linux drive as hd1...this would be the reverse of how grub recognizes your hard drives.  In grub your Linux drive is (hd0)...this is where grub is installed to the mbr & you're able to boot your Linux OS by selecting to boot this drive first.   The important thing with Feisty is that the root has to be (hd0,x) in your menu.lst...it doesn't matter if Feisty recognizes the drive as sda, instead of sdb because it uses UUID's in the menu.lst kernel line and in /etc/fstab(Edgy also used UUID's in fstab).

I believe all you'll need to do is to make sure your Feisty root is (hd0,x) in your menu.lst...you'll also need to change this in your groot line:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
if you don't, a kernel update uses groot when update-grub is run to assign your root.

I'm not sure if I understand exactly what your problem is, but hope I've helped a little.  I had a similar problem recently when I installed Sabayon, which had the hd0 and hd1 drives reversed compared to my other Linux installs...I just changed the root from (hd0,5) to (hd1,5) in the grub.conf & it booted fine(wouldn't boot otherwise).

Added:  I found some info on Herman's site about editing device.map, he mentions grub-install has to be run for changes to the device.map to become effective:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)
you'll have to scroll down some to find the sections on editing device.map

---

### Post by triwave on 2007-05-25
Thanks confused ... I have used Herman's site extensively while learning about Grub and booting, it's a great resource! By reading that page I was able to boot both systems without problems, mount drives, and cat / edit menu files, device.map, etc. 

What I'm confused by is the device.map and grub relationship. I edited device.map as suggested; set hd0->sda and so forth, even run update-grub, but it appears to have no effect. It's like I could put anything in there and grub still says windows is hd1. How does it establish that link?

If I boot into a live CD then grub establishes a different relationship where windows drive is hd0. It's still Grub so why is it different? Keeps making me think something about the ubuntu install is mixing the drives up. When I had just PCLOS and Windows they were setup up correctly and that was with grub too.

Guess I'm concerned that when I muck around with menu.lst the changes will work for a while until some event changes the drives around again. (updating a kernel?)   I'm also a bit confused if I set root (hd0,x) in the menu , do all my references to linux partitions now have to be sda instead of sdb ?

Thanks for your advice.

---

