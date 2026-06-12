---
title: "Boot problems with Xubuntu installation on external hard drive"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2013-10-29
Hi,

I am getting quite frustrated trying to run Xubuntu 12.04 from an external hard drive.

The installation process carried through successfully, but I cannot boot from the drive. I get the following error:

error : out of disk.
grub rescue>

I have tried reinstalling grub onto the linux partition of the external hard drive, by following the instructions on [this page]("http://ubuntuforums.org/showthread.php?t=1195275"), but it makes no difference.

Any help gratefully received.

Many thanks.

---

### Post by oldfred on 2013-10-29
Do you have a very large / (root)?

We have seen issues with large / partitions where some boot files may be near beginning of partition but others are far into partition. Not sure if BIOS, grub2 or USB driver or some combination.
Either smaller / or separate /boot at beginning of drive usually then works. Often a quick test is just to shrink / or make it fully within the first 100GB of USB drive. Then make rest of drive /home or /mnt/data partition.

Post this:
sudo fdisk -lu

---

### Post by rdh61 on 2013-10-29
> **oldfred said:**
> 

Post this:
sudo fdisk -lu

```

robert@robert-desktop:~$ sudo fdisk -lu
[sudo] password for robert: 


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244156414   484487167   120165377    5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244156416   484487167   120165376   83  Linux


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa7d7


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   154222591    77110272   83  Linux
/dev/sdb2       154224638   156301311     1038337    5  Extended
/dev/sdb5       154224640   156301311     1038336   82  Linux swap / Solaris
robert@robert-desktop:~$ 
```


Thank you.

---

### Post by oldfred on 2013-10-29
You do have to install grub to the MBR, not a partition. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by leeper69 on 2013-10-29
Hi have you tryed to set your bios to boot from your external device? if you chose to install grub to the root partision on your external drive which looks like this / and not the MBR this should work if your bios has this choice.

---

### Post by rdh61 on 2013-10-29
> **oldfred said:**
> You do have to install grub to the MBR, not a partition. 


I would have thought the installation disk should have known that! I chose the automatic installation to use the whole disk, i.e. I had no input into where grub was installed. (And when it didn't boot I followed *to the letter *the instructions to reinstall grub given in the link in my original post).

Thank you for the boot-info and boot-repair links you posted. I'll get round to it tomorrow or the next day and post back - no time now.

---

### Post by rdh61 on 2013-10-29
> **leeper69 said:**
> Hi have you tryed to set your bios to boot from your external device?

Yes.

---

### Post by rdh61 on 2013-10-29
> **oldfred said:**
> 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

OK, I did have time today. I ran boot-repair and it told me it repaired boot successfully.

However, I still cannot boot into xubuntu on the external HD. When I try, I get the boot loader screen with options to boot Xubuntu on sda (my internal HD) or sdb (my external HD).  If I choose the latter, I get the following errors:

error: out of disk
error : you need to load the kernel first

(If I choose the former - internal HD - it boots normally).

---

### Post by oldfred on 2013-10-29
Post the link that Boot-Repair give you so we can see if we see anything that may help.

---

### Post by rdh61 on 2013-10-30
Ah, sorry, I omitted the Boot-Repair link. Here it is:

[http://paste.ubuntu.com/6325833/](http://paste.ubuntu.com/6325833/)

---

### Post by leeper69 on 2013-10-30
can you read the external drive from file manager from your working ubuntu drive?

---

### Post by rdh61 on 2013-10-30
> **leeper69 said:**
> can you read the external drive from file manager from your working ubuntu drive?

Yes, I can. I can see on it the system directories (bin, boot, cdrom, dev, etc, and so on) and their sub-directories and files.

---

### Post by oldfred on 2013-10-30
why you said the external drive was an internal drive, it installed grub from internal drive to both drives.
> 
 User choice: Is sda (250GB) a removable disk? [COLOR=#ff0000]no[/COLOR]


If you say yes then it will install grub of external drive to MBR of external drive. Or you can change from auto repair to manual update of MBR and choose which system to install to which MBR.

---

### Post by rdh61 on 2013-10-31
> **oldfred said:**
> why you said the external drive was an internal drive, it installed grub from internal drive to both drives.

If you say yes then it will install grub of external drive to MBR of external drive. Or you can change from auto repair to manual update of MBR and choose which system to install to which MBR.

Sorry if I'm being obtuse oldfred, but I don't understand. sda (250GB) is *not* a removable disk, it is the internal disk, sdb is the external one.

---

### Post by oldfred on 2013-10-31
Then somehow Boot-Repair is mixed up  as well as oldfred. It seemed to see an external drive but had wrong one.

You still can use Boot-Repair but uncheck the auto repair. The auto repair automatically installs grub to every hard drive. But then check update MBR and you can choose which operating system to install its boot loader and which drive to install into. So choose the install in your external and install that system's grub to the MBR of the external drive.

---

### Post by rdh61 on 2013-10-31
> **oldfred said:**
> 

You still can use Boot-Repair but uncheck the auto repair. The auto repair automatically installs grub to every hard drive. But then check update MBR and you can choose which operating system to install its boot loader and which drive to install into. So choose the install in your external and install that system's grub to the MBR of the external drive.

Hi oldfred,

I did as you suggested, and then when I tried to boot from the external HD, I was told "Missing operating system", or words to that effect.

[http://paste.ubuntu.com/6335905/](http://paste.ubuntu.com/6335905/)

So I decided to reinstall, this time manually instead of the automatic option (erase everything and install xubuntu) I chose last time. But this changed nothing, so it's back to square one:

[COLOR=#000000]error : out of disk.[/COLOR]
[COLOR=#000000]grub rescue>

Methinks Ubuntu still has some way to go before it can be considered ... I was going to say "idiot proof", but that is the wrong expression... instead I'll say "to reasonably easily fulfil the functional needs of the averagely intelligent, averagely computer-literate person".[/COLOR]

---

### Post by oldfred on 2013-10-31
You are not getting grub installed to sdb. Your boot report still showed syslinux which is a Windows type boot loader and would give a boot error. Boot-Repair seems to think it was installing a Windows boot loader. Drive order is still mixed up for some reason. 

Or did you say to install a Windows boot loader to sdb? You have to select the correct system as you have 3, Windows & Ubuntu on the 250 and Ubuntu on the 80 and then say to install the version of Ubuntu on the 80 to the MBR of the 80GB drive.

---

### Post by rdh61 on 2013-10-31
I'll have to leave this for a couple of days as I'm travelling. When I get back to it I'll use Boot-Repair again, and report to you exactly what I do, step by step, and the result - that should help you to tell me what, exactly, I do wrong. In the meantime, thank you for your efforts so far.

---

### Post by rdh61 on 2013-11-02
Here's an update.

I have booted Xubuntu from the same external drive on a different computer - a very old laptop. (In fact I am logged in on the system on the external drive now). I immediately got the splash screen, then a message came up under the Xubuntu logo saying there was an error on the disk and inviting me to press the "F" key to fix it (plus other options which I can't remember). I pressed "F" and after a few moments the system continued to boot. I rebooted successfully with no further issues. I cannot try the disk on the original computer (my desktop at home) for another two weeks, as I'll be away until then.

Any comments in the light of our previous conversation?

Thanks.

---

