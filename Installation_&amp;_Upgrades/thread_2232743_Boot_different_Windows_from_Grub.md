---
title: "Boot different Windows from Grub"
date: 2014-07-03
forum: Installation &amp; Upgrades
---

### Post by Ivan_Pogrebnyak on 2014-07-03
Hi

I recently bought an SSD. I put it in place of the HDD, and put the HDD where the CD drive was. This is on a laptop. On the HDD, I have Linux mint and Windows 7. I put Windows 7 and then Xubuntu on the SSD (in that order) as I'm planning to migrate to the SSD and use the HDD as a storage space.
Now, in Grub I have 4 entries (besides memtest and other stuff): both versions of Linux, and 2 Windows entries. When I select Ubuntu, I boot into Xubuntu (on SSD), when I select Mint, I boot into mint (on HDD). But regardless of what Windows entry I select, I boot into the one on SSD, and cannot boot into the one on HDD. The two Windows entries are probably not duplicates, because one is labelled as "on sda1" and the other as "on sdb1".

Can this be easily fixed?

Thanks in advance.

PS: The version of Grub I got with Xubuntu is 2.02

---

### Post by yancek on 2014-07-04
If the hard drive with windows 7 was attached when you installed windows 7 on the SSD, I would expect its bootloader to detect it.  I would boot into Xubuntu and run:  sudo os-prober and when it is finished run:  sudo update-grub and watch the output.  If that doesn't do the job, google "bootinfoscript" and go to the site and download and run the script and then post the RESULTS.txt file here as it will show detailed information and someone should be able to help.

---

### Post by nerdtron on 2014-07-04
You still have two different installs of Windows right? One on SSD and one on HDD?

Do it this way.
1. Remove the HDD from the computer and boot the SSD Xubuntu.
2. On Xubuntu, open a terminal and run "sudo update-grub".
3. This will update grub and add entries for only Xubuntu and Windows 7.
4. Shutdown and now plug the HDD and remove the SSD.
5. Boot into Mint on the HDD and run "sudo update-grub" on the terminal.
6. This will update the grub on the HDD and will only add Mint and Windows 7.
Now when you boot the computer, think of it that the two separate independent grubs on each drive so choose which drive to boot on startup.

---

### Post by Bucky Ball on 2014-07-04
Welcome. 

> **yancek said:**
>  If that doesn't do the job, google "bootinfoscript" and go to the site and download and run the script and then post the RESULTS.txt file here as it will show detailed information and someone should be able to help.

Better still, run Boot Repair, and if that doesn't work, that can create a bootinfoscript for you. Write down the link and post it here (if Boot Repair doesn't work). Go for the 'Recommended' option.

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

You can install it into your current install using the instructions at that link.

---

### Post by grahammechanical on 2014-07-04
When I installed Windows 8 pre-view in a second hard disk it installed its boot loader on both hard disks. I think that is what has happened here. The Windows 7 install on to the SSD has put its boot loader files on the hard disk and then Grub os-prober sees a Windows boot loader on sda and on sdb but both reference the same Windows 7 installation.

Installing Grub on to the hard disk should remove the Windows 7 boot loader from the hard disk and then running from Xubuntu

```
sudo update-grub
sudo grub-install /dev/sda
```

and from from Mint

```
sudo update-grub
sudo grub-install /dev/sdb
```

should give you two Windows 7 entries that are actually different installations whichever disk is given boot priority.

Regards.

---

### Post by Ivan_Pogrebnyak on 2014-07-04
Thanks for all of your suggestions.

Unfortunately, I can't use the solution with two different Grubs, one on each disk. I forgot to mention that my BIOS doesn't see the HDD that I connected to ATAPI through an HDD caddy, so I can only boot the OS'es on it through Grub.

Here's the Boot Repair output (from Xubuntu on SSD): [http://paste.ubuntu.com/7747854/](http://paste.ubuntu.com/7747854/)

I think the grahammechanical's explanation is probably closest to what happened in my case, it that both Windows bootloaders that Grub sees point to the same OS. So, this is probably more of a Windows problem. I understand that this is a Linux forum, but maybe somebody know how to fix Windows bootloaders as well?

Thanks

---

### Post by yancek on 2014-07-04
The quote below might explain it.  You could read the responses at the site below where I got this info:

[http://superuser.com/questions/599914/dual-boot-two-instances-of-windows-7-on-different-hard-drives](http://superuser.com/questions/599914/dual-boot-two-instances-of-windows-7-on-different-hard-drives)

> No. I explicitly explained that in my answer.  Once you install windows with your other HDD connected, then it  installs the boot files on the primary HDD. If you lose the 2nd disk,  then it can't boot anymore without the other HDD. Unless that only  applies for the primary HDD ofcourse.. but from what I understand these  HDD's need to work independently from each other

If that is accurate, when you installed windows 7 on the SSD, it put the boot files on sda1 with the other windows 7.  Might work if you did not have the internal attached when you installed 7 to the SSD.

Here is another suggestion at the windows 7 forums.

[http://www.sevenforums.com/hardware-devices/217599-dual-boot-win-7-separate-drives.html](http://www.sevenforums.com/hardware-devices/217599-dual-boot-win-7-separate-drives.html)

I think you need to resolve this from within windows and the links above may help.  I haven't dual-booted windows since W98 and W2K and I do remember that windows 2000 installed on a logicall partition but also put its boot files on a primary partition, the windows 98 partition.  The boot files for W98 were totally different from W2K so it was pretty easy to tell.

---

### Post by Bucky Ball on 2014-07-04
A wild thought, but how about booting into Linux Mint on sdb and:

```
sudo grub-install /dev/sda
sudo update-grub
```

Reboot. I can't see anything glaringly obviously wrong with your bootinfoscript output. :-k

---

### Post by Ivan_Pogrebnyak on 2014-07-04
I solved the problem!
I used a EasyBCD program in Windows on the SSD and added a boot entry for \Windows\system32\winload.exe on the HDD. Now, when I select either of the Windows entries in Grub, it then takes me to the Windows bootloader which gives me two options.
I found how to do this following links from yancek.

Thanks everybody.

---

