---
title: "WUBI.exe gets me a grub prompt"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by hbaird on 2010-07-28
I got a 10.04 CDROM with the Ubuntu Linux Bible. I installed Ubuntu with Wubi.exe. After install the Grub menu offers WinXP and Ubuntu. The WinXP works as expected. The Ubuntu selection gives me a grub prompt. I removed and reinstalled with the same results. I can't tell if the install is complete or not.  I am a long time Linux and Unix user currently running Fedora 13. Fedora will sometimes make problems with uncoordinated updates so I am trying Ubuntu. Not a good start. Any help?

---

### Post by stevedub40 on 2010-07-28
I am also having trouble with wubi. I installed wubi ubuntu on a second HDD that I was not using, which worked fine until I did some updates and a reboot. Now, I am presented with grub> and cannot get past it. I've read some fixes that use the root=loop0 command, but it requires you to load the kernel, and I have no clue what that is for 10.04. Here is the commands I am referring to:
 
```

[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]set root=(loop0)[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]initrd /boot/initrd.img-2.6.31-14-generic[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]boot[/COLOR]** 

```
 
I just don't know what the kernel is or what sd I am on. I think it's the 3rd sata drive in my setup, so if anyone has any suggestions I would greatly appreciate them. I also only get grub>, and not sh:grub>.

---

### Post by sikander3786 on 2010-07-28
There are a few half solved threads. Did you go through these?

[http://ubuntuforums.org/showthread.php?t=1521340](http://ubuntuforums.org/showthread.php?t=1521340)

[http://newyork.ubuntuforums.org/showthread.php?t=1358188](http://newyork.ubuntuforums.org/showthread.php?t=1358188)

[http://georgia.ubuntuforums.org/showthread.php?p=9552126](http://georgia.ubuntuforums.org/showthread.php?p=9552126)

Might be you get something from these.

Anyway if you want to install Ubuntu on the HDD, why WUBI? Why not a clean install? You can get lots and lots of guides for dual booting from Google. And anyone here will be able to help you a lot better if you have any queries or problems for dual booting.

Regards.

---

### Post by bcbc on 2010-07-28
> **stevedub40 said:**
> I am also having trouble with wubi. I installed wubi ubuntu on a second HDD that I was not using, which worked fine until I did some updates and a reboot. Now, I am presented with grub> and cannot get past it. I've read some fixes that use the root=loop0 command, but it requires you to load the kernel, and I have no clue what that is for 10.04. Here is the commands I am referring to:
 
```

[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]set root=(loop0)[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]initrd /boot/initrd.img-2.6.31-14-generic[/COLOR]** 
[COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]boot[/COLOR]** 

```
 
I just don't know what the kernel is or what sd I am on. I think it's the 3rd sata drive in my setup, so if anyone has any suggestions I would greatly appreciate them. I also only get grub>, and not sh:grub>.

A recent grub update is installing grub2 to the MBR, overwriting windows. This impacts wubi users.The fix is to replace the grub2 bootloader with windows' bootloader. Or you can use lilo - boot a live CD and run
```
sudo apt-get install lilo
sudo lilo -M **/dev/sda** mbr

```
Change /dev/sda if necessary to the drive you boot from. "sudo fdisk -l" (small L) will tell you if you aren't sure.

---

### Post by bcbc on 2010-07-28
> **hbaird said:**
> I got a 10.04 CDROM with the Ubuntu Linux Bible. I installed Ubuntu with Wubi.exe. After install the Grub menu offers WinXP and Ubuntu. The WinXP works as expected. The Ubuntu selection gives me a grub prompt. I removed and reinstalled with the same results. I can't tell if the install is complete or not.  I am a long time Linux and Unix user currently running Fedora 13. Fedora will sometimes make problems with uncoordinated updates so I am trying Ubuntu. Not a good start. Any help?

That first menu is the windows boot manager (should say so on top). It sounds like you didn't successfully install wubi. You can look in or post here the wubi.log file. To find it, go to windows explorer and enter %temp% in the address bar. (Post it in between [CODE[SIZE="1"] [/SIZE]][/CODE] tags for readibility and note it has some identifying info such as user name and location...)

---

