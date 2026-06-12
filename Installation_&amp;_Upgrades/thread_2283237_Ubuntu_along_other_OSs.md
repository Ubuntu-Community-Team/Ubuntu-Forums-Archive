---
title: "Ubuntu along other OSs"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by Lucia_Lisovska on 2015-06-20
Hello. I have Windows Server 2008 and 2012 installed on separate hard drives (500GB each). Then I decided to install Linux alongside Windows to learn it. I installed Ubuntu 15.04 along Windows 2008 (from live CD). Everything was working - I could boot into any 3 OSs. Then I also decided to install PCLinuxOS (from live CD) - along Windows 2012. It installed well and I could still boot into both Windows. But I was unable to boot in Ubuntu anymore - it was trying to find a boot partition but couldn't. What should I do to repair it? Please help anyone who knows Linux very well, as I'm a beginner to it. 
Thanks in advance.

Lucia

---

### Post by grahammechanical on 2015-06-20
There are two or three things that you can do.

1) create a boot repair disk.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair will create a bootinfo summary and store it in Pastebin and give you a URL which you can put in this thread and then we can view the Boot Repair report and give you advice.

Boot Repair will offer a recommended repair which we do not have to accept but unless we accept the recommendations Boot Repair will not actually repair anything. And things will stay as they are.

2) You can give us more information about the hardware. Is Windows Server 2008 on the first hard disk (called sda in Linux)? Is Ubuntu on the same disk? Is PCLinux on the same disk? What boot system does the motherboard have? BIOS? or UEFI?

The usual recommendation from boot repair is to re-install the Grub boot loader into the MBR of all hard disks. We can change that. But if Grub is installed into the MBR of the disk with Windows Server 2012 on then it will overwrite the Windows boot loader and you may not want that to happen.

When we install a Linux distribution it will install the Linux boot loader (in Ubuntu it is called Grub). The last Linux distribution to be installed will take control of the boot menu. And that is what has happened here. PCLinux is in charge and for some reason its boot menu is not correctly pointing to Ubuntu. I know nothing about PCLinux so I cannot even guess why it has failed.

Regards.

---

### Post by yancek on 2015-06-20
Your best option is to run boot repair with the Create Bootinfo Summary.  The default installation of PCLinux for the Grub bootloader is to the MBR of the first disk just as it is for any Linux I have ever used and if you accepted this, it has overwritten your Ubuntu Grub code in the MBR.   Grub2 is available in PCLinux but last I checked the default was still Grub Legacy which of course can still be used to boot other systems so posting the output of boot repair will tell use which it is.  It is possible to select a different location to install the bootloader to and you could have installed it to the second drive MBR with windows 2012 or to the / partition of PCLinux.  Posting the info and explaining what you want to do as far as a bootloader would be a help.

---

### Post by Lucia_Lisovska on 2015-06-20
Thanks, guys. Ok will give the information about disks as grahammechanical suggested:

_**sda partitions:**_ (as it appears in PCLinux control centre)

sda2: WinServer2012 155GB  | sda5: / 98GB | sda7: /boot 203GB | sda6: swap 7.9GB
[B][U]
sdb patitions:

[/U][/B]sdb1: WinServer2008  232GB  | sdb2: Ubuntu 77GB  | sdb5: 147GB nothing appears on it but it says 31%, so wondering what is there | sdb6: swap

So, don't really know where PCLinux is installed on sda - looks like on sda5, but what is on sda7, then? the partition is 203GB!

I'm not really very strong in partitioning. Any advice would be appreciated. Yeah, and it's true that PCLinux is now in charge as this is the first what appears with the options to boot into other OSs.

Will try running Boot Repair Utility when have time.****

---

### Post by yancek on 2015-06-20
It would be better if you posted the actual output of the command as people here will be able to explain it.  It looks like you have a Linux install on sda5 of 98GB and a separate boot partition of 203GB on sda7.  8GB is a little excessive for swap.

---

### Post by Lucia_Lisovska on 2015-06-21
Yancek what command do you mean that you advise me to post? And, do you get any idea what would be on sdb5 which has 147GB and 31% (free space?) as nothing appears but something must take space there? Might be that Ubuntu loader was there but now disappeared after I installed PCLinux? Gosh, this Linux thingy seems to be much more complicated than Windows.

---

### Post by sudodus on 2015-06-21
> **grahammechanical said:**
> There are two or three things that you can do.

1) create a boot repair disk.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair will create a bootinfo summary and store it in Pastebin and give you a URL which you can put in this thread and then we can view the Boot Repair report and give you advice.
...

Please give us that ***bootinfo summary***, but ***do not do anything else!*** It is too early to let it try to repair the booting.

---

### Post by yancek on 2015-06-21
>  			 			Yancek what command do you mean that you advise me to post?

I meant from PCLinux logged in to a terminal as root run:  fdisk -l(Lower Case Letter L) and try:  parted /dev/sda print all (not sure the second will output anything, you may need to install parted but the fdisk output should be enough).

As to what is on sdb5, posting the output of the fdisk command would give us an idea but the boot repair output suggested above would be better.  Additionally, the default behavior for pretty much any operating system is to instll it's bootloader to the mbr which is what would have happened with PCLinux.  If that is the case, you could put an entry in its boot file for the Ubuntu on sdb2.  Best to post the boot repair output before getting more specific instructions.

 > Gosh, this Linux thingy seems to be much more complicated than Windows. 		


Not really.  You've just been using windows so you are used to it.  It's much easier to install Linux and use it to dual-multi boot which is incredibly convoluted with windows.

---

### Post by Lucia_Lisovska on 2015-06-21
This is the URL I got - bootinfosummary. I looked at it - that's too much for me to comprehend!

[http://paste.ubuntu.com/11751764/](http://paste.ubuntu.com/11751764/)

Thanks guys for all your support.

---

### Post by yancek on 2015-06-21
The info you posted indicates that you are using the Grub Legacy of PCLinux to boot and that you have a separate boot partition on sda7.  Log in to PCLinux, open a text editor from a terminal while logged in the terminal as root user then navigate to the /boot/grub/menu.lst file and copy/paste the entry below for Ubuntu and save the file and reboot to test. 

> title Ubuntu-14.04
root (hd1,4)
kernel /boot/grub/i386-pc/core.img


If that doesn't work, you can try a simple chainloader command such as below:

> title Ubuntu
root (hd1,4)
chainloader +1


---

### Post by sudodus on 2015-06-28
@ Lucia

The most recently installed operating system grabs the booting (installs its own bootloader), so pclinuxos grabbed it. Unfortunately it could not identfy Ubuntu.

[B]
1.[/B] Did you try according to yancek's advice? In that case, what happened? I think it should work if you boot into pclinuxos and tweak the file

```
/boot/grub/menu.lst
```

according to yancek.

[B]
2.[/B] If it does not work according to yancek's advice, you have two options.

2.1 Reply with details of what you did and what happened and wait for further instructions from yancek.

2.2 Try to boot from Ubuntu instead. I read the boot-info summary carefully. In this case, use the automatic advice at the end of the bootinfo summary. I think it can work.

> =================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot

=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (500GB) disk!


In other words, run ***Boot-Repair*** again, and this time let it perform the default repair (the standard recommended repair).

After reboot Ubuntu will not recognize pclinuxos (because it was not there, when Ubuntu was installed), but when Ubuntu is running, you run the following command in a terminal window

```
sudo update-grub
```

and I think Ubuntu will identify all the operating systems in the connected drives (including the Windows versions and pclinuxos). So the next time you boot, there should be a grub menu with all of them.

---

### Post by Lucia_Lisovska on 2015-07-12
Dear all who tried to help me to resolve the above problem, 

I'm so sorry I wasn't replying for so long - I was busy with many things and thought that doing what was suggested here would take a lot of time. But yesterday I got a chance to try it out - it took just a few mins, and after Ubuntu boot repair I was able to boot into all four OSs straight away, even into PCLinuxOS! I didn't even have to run sudo update-grub. Of course Ubuntu is now in charge as one of you said.

Could I also ask if you can look at the output of boot repair and see whether all the partitions are alright - to me it looks like both Linux OSs take two partitions each (too much space on the drives). Is it not possible to 're-arrange' the space somehow, for example, allocate more space to Server 2012? I'm not very fluent in partitioning, but I think I would need to delete a volume that is next to the right side from Server 2012. Would it be possible at all? 

Here is the file: [http://paste.ubuntu.com/11861640/](http://paste.ubuntu.com/11861640/)

Thanks for all your help.

---

### Post by sudodus on 2015-07-12
To allocate more space to Server 2012:

The easiest option is to use gparted and use drive space 'after' or 'to the right' of its partition /dev/sda2.

```

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
[COLOR="#007700"]/dev/sda2             718,848   327,450,615   326,731,768   7 NTFS / exFAT / HPFS[/COLOR]
[COLOR="#FF0000"]/dev/sda3         327,452,895   976,771,071   649,318,177   5 Extended
/dev/sda5         327,452,958   533,615,039   206,162,082  83 Linux
/dev/sda6         960,063,488   976,771,071    16,707,584  82 Linux swap / Solaris
/dev/sda7         533,615,103   960,060,464   426,445,362  83 Linux
[/COLOR]...
"blkid" output:

Device           UUID                                   TYPE       LABEL
/dev/sda1        4AF0CA30F0CA21D5                       ntfs       System Reserved
/dev/sda2        2296CC4796CC1D63                       ntfs       WinServer2012
/dev/sda5        9de8a155-839b-4240-9ac5-697b8e956595   ext3       PCLinuxOS

```

That means moving or deleting PCLinuxOS. Deleting is simple. Moving the head end of the partition /dev/sda5 (and also the extended partition) would mean that grub would need to be reinstalled to boot directly into it, but since you boot via Ubuntu's grub, there should be no problem as long as you do not change the UUID of the partition.

What data is stored in /dev/sda7 ? It is a linux partition, but not bootable.

Anyway, whatever you want to do, remember that editing partitions is risky, and ***backup all important data before*** doing it.

Finally, it might be faster/easier to backup the important data, delete the partitions (/dev/sda3...), increase the size the partition you want (/dev/sda2) and reinstall PCLinuxOS than to move it. In that case you might need Boot-Repair again to get to booting correct.

---

