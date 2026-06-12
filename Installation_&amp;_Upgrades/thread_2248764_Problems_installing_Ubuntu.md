---
title: "Problems installing Ubuntu"
date: 2014-10-16
forum: Installation &amp; Upgrades
---

### Post by augustineleudar on 2014-10-16
Hi I have a toshiba laptop running windows 8 64 bit. Normally I just mount the ISO open wubi , it asks me how much harddrive space I want to allocate and the machine automatically restarts and thats that. However with the AMD 64 bit iso Ive downloaded I dont get these options just a boot from Cd option. I have made a flashg drive ubuntu and told bios to boot from that but it doesnt work - I get the twin boot option but clicking Ubuntu just goes to a black screen asking me to repair windows. I boot again ansd get into windows but I want Ubuntu as well. Any suggestions ?

---

### Post by fantab on 2014-10-16
Wubi does not work with Windows8 and hence useless for you. Its development has stopped, if I am correct.
You have to install ubuntu as true dual boot, that is, on its own partition.

I recommend that you go through this wiki page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since you have Win8, I presume you have UEFI...

---

### Post by yancek on 2014-10-16
For information on a wubi install, the official wubi site below is the best source, in particular the second paragraph regarding windows 8:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

My understanding is that it is not currently being developed or supported.

---

### Post by hakuna_matata on 2014-10-17
> **augustineleudar said:**
> Normally I just mount the ISO open wubi , it asks me how much harddrive  space I want to allocate and the machine automatically restarts and  thats that. However with the AMD 64 bit iso Ive downloaded I dont get  these options just a boot from Cd option.
Normally? These options have been removed since 12.04: [http://askubuntu.com/questions/145071/how-to-install-ubuntu-12-04-within-windows-7-with-a-cd-image-of-ubuntu-without](http://askubuntu.com/questions/145071/how-to-install-ubuntu-12-04-within-windows-7-with-a-cd-image-of-ubuntu-without)

IMHO there is only a theoretical official support for Wubi. 

The most common issues of Wubi are:


[LIST]
[*]Wubi doesn't work in UEFI mode: [https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242) 
[*]It doesn't work for 14.04.**1**: [https://bugs.launchpad.net/wubi/+bug/1367071](https://bugs.launchpad.net/wubi/+bug/1367071) 
[*]If you don't change kernel options to "rw", "serious errors" occur:  [https://bugs.launchpad.net/ubuntu/+bug/1317437](https://bugs.launchpad.net/ubuntu/+bug/1317437)  and [http://ubuntuforums.org/showthread.php?t=2217829&p=12992482#post12992482](http://ubuntuforums.org/showthread.php?t=2217829&p=12992482#post12992482) 
[/LIST]

Therefore I don't recommend Wubi, although It is still possible to use Wubi if you patch the existing wubi.exe or if you use a patched version:[http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598](http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598)

---

### Post by Bucky Ball on 2014-10-17
Welcome. Although it's available, Wubi is no longer supported by Canonical, nor these forums. Please see [HERE]("http://ubuntuforums.org/showthread.php?t=2229766"). Go for a dual-boot with Ubuntu installed on its own partition. There is very little support for Wubi now.

[QUOTE=hakuna_matata]IMHO there is only a theoretical official support for Wubi.[/QUOTE]

There is NO official support for Wubi now.

---

### Post by hakuna_matata on 2014-10-17
> **Bucky Ball said:**
> There is NO official support for Wubi now.
```
ubuntu-support-status --list | grep lupin
```
says that the main packages of Wubi are still suported in 14.04:
```
lupin-casper                          5y
lupin-support                         5y
```
Additionally, is it possible to release something to an official download site and to official iso files without any official support by Canonical ?

Nevertheless, there is only a theoretical difference between no official support and theoretical official support. Therefore all recommendations are: Don't use Wubi.

---

### Post by Bucky Ball on 2014-10-17
As mentioned previously, see [HERE]("http://ubuntuforums.org/showthread.php?t=2229766").

And agreed, avoid Wubi.

---

### Post by hakuna_matata on 2014-10-17
> **Bucky Ball said:**
> As mentioned previously, see [HERE]("http://ubuntuforums.org/showthread.php?t=2229766").

@Bucky Ball: My question "is it possible to release something to an official download site and to  official iso files without any official support by Canonical ?" was only a rhetorical question. I expected no answer. It should only show that IMHO it is not a good way to release something in an official way and then say there is "no support".

---

### Post by Bucky Ball on 2014-10-17
> **hakuna_matata said:**
> It should only show that IMHO it is not a good way to release something in an official way and then say there is "no support".

I agree. The option shouldn't be available. ;)

---

### Post by augustineleudar on 2014-10-17
Couldnt I just partition the harddrive and then use my usb flash to install ubuntu on the second partition ?

---

### Post by Bucky Ball on 2014-10-17
> **augustineleudar said:**
> Couldnt I just partition the harddrive and then use my usb flash to install ubuntu on the second partition ?

Yes. Exactly what you should do. ;)

You will need at least two partitions for Ubuntu, though, three if you are wanting a separate /home partition. At the very least you will need:

/ = Where Ubuntu goes. If you have a separate /home partition, then 25Gb is plenty. If not, make this as large as you can afford to;
/swap = akin to Windows pagefile; 2Gb is fine (unless you hibernate often with lots open in which case the same size as your installed RAM or larger).

If you are not using UEFI, you are limited to four partitions per each physical hard drive. This can be overcome by creating an extended partition, which is seen as one partition, and putting / and /swap in there as logical partitions. As they are inside the 'container' that is the extended partition, the system only looks at the one extended partition. Good luck.

---

### Post by fantab on 2014-10-17
You can. However you have to *[SHRINK]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/")* one of the Windows partitions and make space for Ubuntu. Leave the space you've created as 'unallocated space'. This space will be further managed with Ubuntu/Gparted.
While you are in Windows, [disable *FastStartup*]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")...
Disable '*Fastboot*' (some OEMs have this in Windows and some in UEFI/Bios menu).
If you have an Intel mobo, and if you have pre-installed SSD then the chances are you have* Intel SRT*, you have to disable it as well.
Some OEMs can boot with '*Secure Boot*' disabled some cannot... (Disable Secure Boot if it causing boot issues with Ubuntu however this not a must).

If I were you, I would BACK UP my HDD and its partitions with [Macrium Reflect]("http://www.macrium.com/reflectfree.aspx") or any other third-party partition back up tool.

Boot Ubuntu DVD/USB. When you install Ubuntu with the option 'Install alongside Windows', the installer will create two partitions from the 'unallocated space' and install Ubuntu to it.
To manually take care of the parttions choose 'Something Else' option... I'd recommend this method.

---

