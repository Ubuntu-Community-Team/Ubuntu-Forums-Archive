---
title: "revert boot sector"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by erupter on 2010-09-09
Hello.
On my main rig i have a software array (Intel Matrix 0+1) and a spare disk.
I partitioned the spare disk, setup the bios in order to use the spare as boot (my windows installation uses the raid array as boot disk) and installed kubuntu 10.04.
Now not only Linux doesn't start (after install, it rebooted and hanged there without any message) but it also sent my windows boot sector fubar.
Now two things:
1st) how do i get back to normal
2nd) if i explicitly told the system that my boot disk was another one, why did the installer mess with another disk it wasn't supposed to???
Pls help, i need to work, this is my heavy duty machine.

Oh and in the grub menu there is no linux voice, there about 10 windows voices (none working obviously) but no linux

---

### Post by erupter on 2010-09-10
Can anybody tell me how to avoid changing a disc boot record?
The installer does not see my raid array (i tried the alternate installer too), so i change the disc used to boot by the bios, but the installer messes with another disc's boot sector.
Why?
And how do i avoid it?
I want two MBRs: the windows one on the raid array, and the linux one on the spare disk.
So i can use the bios to select which system to start.
It has worked for years with windows OSes, why can't it work with linux too?

---

### Post by oldfred on 2010-09-10
You need to use the advanced button to choose which drive to install grub to, otherwise it defaults to usually sda.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

To reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

