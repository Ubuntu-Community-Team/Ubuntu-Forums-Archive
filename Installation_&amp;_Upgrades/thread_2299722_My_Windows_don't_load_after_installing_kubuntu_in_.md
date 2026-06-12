---
title: "My Windows don't load after installing kubuntu in dual boot"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by Ludovic_Vimont on 2015-10-20
Hi guys !

I know there are a lot of posts like this on the forum, but I don't want to make a mistake. So I had a SSD 256 GB with Windows 7. I installed the last version of kubuntu. But after the installation I was unable to load Windows 7 from the grub. I have the option available but when I try to click on it. Seems to load but after few seconds come back to the grub.

I installed boot-repair and made a check up, here is the result : [http://paste.ubuntu.com/12879090/](http://paste.ubuntu.com/12879090/)
If you can help me to solve my problem.

Best regards,
Ludovic

---

### Post by yancek on 2015-10-20
First off, you still have windows code in the MBR which you can see at the very top of the boot repair output.
The reason you see Grub when you boot is because you have somehow managed to put Grub on the ntfs/windows partition.  You have likely overwritten the windows boot code in the IPL of the windows partition and the common method of repairing that is to use the windows installation medium.  There may be other ways to do it but I don't use windows so you'll have to wait for suggestions from other if you do not have the install medium.  If you do have the install disk, the link below explains how to repair.

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by Ludovic_Vimont on 2015-10-21
[COLOR=#000000]Hi ! 

Thanks for you answer !
The problem occured on a laptop so I don't have the install disk. So if there any other options, it can be interesting, else I will try to find one install disk.

Again thank you.
Best regards,
Ludovic[/COLOR]

---

### Post by kloszard on 2015-10-21
Your log seems to be similar to mine. The grub is on the NTFS partition. Your windows installation, however, has more than one partition which is differs your case from mine. You may see the answers in my [thread]("http://ubuntuforums.org/showthread.php?t=2299579") and check that testdisk tool.

---

### Post by mastablasta on 2015-10-22
> **Ludovic_Vimont said:**
> [COLOR=#000000]Hi ! 
The problem occured on a laptop so I don't have the install disk. So if there any other options, it can be interesting, else I will try to find one install disk.
[/COLOR]


yeah restore form backup.

also to reinstall windows boot loader you do not need install disk but rescue disc should do.:

[http://windows.microsoft.com/en-us/windows7/create-a-system-repair-disc](http://windows.microsoft.com/en-us/windows7/create-a-system-repair-disc)

or use Hiren's boot Cd or UltimateBootCD

then when you get to CLI in repair disk...: [https://support.microsoft.com/en-us/kb/927392](https://support.microsoft.com/en-us/kb/927392)

also, this forums is for Ubuntu support. so a better question would be "where do I install grub in manual partitioning mode?"

---

